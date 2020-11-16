The Mongoose OS command line tool
=================================

## Flash to single binary image for ESP8266
This fork extends the flashing capability to create a single binary firmware image for ESP8266 devices.
It uses the same process like real flashing, but without the need of a connected device.

The intention was to create flash images which we individualize during build process and then simply flash 
a single file without the need of mos tool in manufacturing process.

Copy modified mos(.exe) to root folder of mongoose project and run it from there.

./mos flash build/fw.zip TARGET-IN-FILE FLASH-SIZE

```
$ ./mos flash build/fw.zip ./final.bin 32m 

```
$ esptool.py --port /dev/cu.usbserial-143240 write_flash 0x0 final.bin

```


## Building manually

You will need:
 * Git
 * Go version 1.10 or later
 * GNU Make
 * Python 3
 * libftdi + headers
 * libusb 1.0 + headers
 * Docker - optional, only for building Windows binaries on Mac or Linux.

Commands to install all the build dependencies:
 * Ubuntu Linux: `sudo apt-get install build-essential git golang-go python3 libftdi-dev libusb-1.0-0-dev pkg-config`
 * Mac OS X (via [Homebrew](https://brew.sh/)): `brew install coreutils libftdi libusb-compat pkg-config`
 * Windows 10: `TODO`

Clone the repo (note: doesn't have to be in `GOPATH`):

```
$ git clone https://github.com/mongoose-os/mos
$ cd mos
```

Fetch dependencies (only needed for the first build):

```
$ make deps
```

Build the binary:

```
$ make
```

It will produce `mos/mos` (or `mos/mos.exe` on Windows).
