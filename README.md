This is a tutorial to running Balatro natively on Linux with mods.

All credit to [EthanGreen](https://github.com/ethangreen-dev/lovely-injector/) for making lovely injector and to [VGskye](https://github.com/vgskye/lovely-injector/tree/linux-support) for modifying the build code to generate a linux library. I just merged vgskye's modifications with the latest (0.60) lovely-injector version and uploaded it to make it easy to build. 

Skip the building and installation of lovely-injector if you aren't interested in the modding aspect and only want to run Balatro natively on Linux.

# Prerequisites
You need the latest version of the Love2D Appimage, the game engine Balatro runs on. You can get this from [their github](https://github.com/love2d/love/releases/). As of this writing, the version used is 11.5.
You need a legitimate Steam copy of Balatro

# Running Balatro on Linux (no mods)
Download the Love2D appimage.
Run the game from the terminal like so:
./path/to/love2d.appimage /path/to/Balatro.exe
Done! Love will use the saves directory listed in the bottom section of this readme
You can also make a single executable by concatenating the exe to love2d like so:
cat ./path/to/love2d.appimage /path/to/Balatro.exe > Balatro.love (It doesn't need an extension, but makes it easier to differentiate). This just adds the full Balatro executable to the end of the love2D file so Love will execute Balatro automatically when you run this.

If this doesn't work, follow the steps below to extract Love2D from the appimage, then concatenate the extracted love binary in bin/love in place of the appimage. Make sure you place the Balatro.love file in the bin folder where the bin/love was, so it can still use its libraries properly. 

# INSTALLING MODS
## Extracting Love2D
In a terminal, run ./path/to/love2d.appimage --appimage-extract
You'll get a squashfs-root folder, copy your Balatro.exe into the bin folder for ease (or copy all these folders into your Balatro installation folder, whatever is easier. You also don't need all the .dlls Steam ships Balatro with. Love2D will use the libraries in the lib folder.

## Building lovely-injector
Clone this repository
cd into the root lovely-injector directory, and run cargo build --release.
The resulting liblovely.so file will be in $directory/target/release
Copy that to the lib folder in your extracted Love2D folder

## Running the game!
Place liblovely.so into the lib folder of your modded Balatro directory.
Use the following terminal command to startup Balatro with lovely-injector. Make sure the paths are correct.
LD_PRELOAD=./lib/liblovely.so ./bin/love ./bin/Balatro.exe

## Mods and Saves Directory
Love will use the $home/.config/love/Mods/ as a mod directory. Place all your mods in there.
Love uses $home/.local/share/love/ as a saves and config directory.

## Notes
You cannot load lovely-injector with a concatenated single binary Balatro file. I tried LD_PRELOADing lovely-injector with a concatenated single binary of Balatro and it would always ignore it and load vanilla Balatro - keep this in mind if you're having issues loading mods. You CAN however call /bin/love to a concatenated Balatro.love and use LD_PRELOAD there to load mods, that works fine.
