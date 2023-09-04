# drone
Test project to mess around with the Raspberry Pi Pico and setting up an embedded environment in docker.
## Install
Install docker on your machine(I'm using windows). Navigate to the repo main directory and run the following lines:
```
$ docker build . --tag drone-dev
$ docker run -d -it --name drone-dev --mount type=bind,source=${PWD},target=/home/dev drone-dev
$ docker attach drone-dev
$ cd /home/dev/
$ git submodule update --init --recursive
```
Now you're in the source directory of the repo
## Build
To build simply navigate to the main repo directory and enter the following commands:
```
$ mkdir build && cd build
$ cmake ..
$ make
```
For some reason the first attempt it fails to properly find the cross compiling tools, usually failing on some unknown asm command. To fix this delete the build folder and re-try, it works, idk why but it works. To confirm the issue check the compile_commands.json in the build folder and the cross compiler will be "/usr/bin/cc" instead of the normal arm-none-eabi-gcc.
## Versions
This section lays out the different versions/steps of the project. Since this is an educational project steps may not make the most sense but who cares? More documentation on each version can be found in the "versions" folder.
### Verison 0
The goal of this version is to setup a basic Raspberry Pi Pico development environment and create a program that does the following: receive an echo command over BLE, sends that command to a command processor running on the other core, then sends the response over the BLE, one core blink an LED at 1Hz and the other core blink an LED at 2Hz.