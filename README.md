This repository contains the source code for the ARM side libraries used on Raspberry Pi with modified version of raspivid and raspistill with additional "--layer" (and shorter "-la") command line argument. By default raspivid uses dispmanx layer 2 and Qt with EGLFS uses layer 1 so in consequence raspivid renders in front of Qt. This modification helps to solve this issue.

## Build

```
sudo apt update
sudo apt install cmake

git clone https://github.com/whitebatman2/raspivid-setlayer.git

cd raspivid-setlayer
mkdir build
cd build

cmake ..
```
Build only 'raspivid' and 'raspistill' with required dependencies:
```
make raspivid
make raspistill
```

## Install
Backup original 'raspivid' and 'raspistill'
```
sudo mv /usr/bin/raspivid /usr/bin/raspivid_
sudo mv /usr/bin/raspistill /usr/bin/raspistill_
```
Copy new binaries to /usr/bin

    sudo cp bin/* /usr/bin/

## Example
This command will launch preview without timeout on dispmanx layer 0:

    raspivid -t 0 --layer 0
    
This command is equivalent:

    raspivid -t 0 -la 0
