This is a tutorial to running Balatro natively on Linux with mods.

All credit to [EthanGreen](https://github.com/ethangreen-dev/lovely-injector/) for making lovely injector and to [VGskye](https://github.com/vgskye/lovely-injector/tree/linux-support) for modifying the build code to generate a linux library. I just merged vgskye's modifications with the latest (0.60) lovely-injector version and uploaded it to make it easy to build. 

Skip the building and installation of lovely-injector if you aren't interested in the modding aspect.

## Building
cd into the root lovely-injector directory, and run cargo build --release.
The resulting liblovely.so file will be in $directory/target/release

## Installation of Lovely-Injector

## Integrating a .desktop
I have a simple .desktop file for Balatro that executes a script in my game directory with the terminal command
