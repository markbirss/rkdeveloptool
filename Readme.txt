rkdeveloptool gives you a simple way to read/write rockusb device.let's start.

compile and install
1. install libusb and libudev
	sudo apt-get install pkg-config libusb-1.0-0-dev libudev-dev dh-autoreconf autotools-dev autoconf automake libtool
2. go into root of rkdeveloptool
3. ./autogen.sh
4. ./configure
5. make

rkdeveloptool usage,input "rkdeveloptool -h" to see


rkdeveloptool db MiniLoaderAll.bin
rkdeveloptool rfi
rkdeveloptool cs 1
rkdeveloptool rfi


[Onboard SPI Nand Flash 256MB]
Flash Info:
        Manufacturer: SAMSUNG, value=00
        Flash Size: 255 MB
        Flash Size: 523264 Sectors
        Block Size: 128 KB
        Page Size: 2 KB
        ECC Bits: 0
        Access Time: 40
        Flash CS: Flash<0>
        
        
[SDCard 16GB]        
Flash Info:
        Manufacturer: SAMSUNG, value=00
        Flash Size: 15193 MB
        Flash Size: 31116288 Sectors
        Block Size: 512 KB
        Page Size: 2 KB
        ECC Bits: 0
        Access Time: 40
        Flash CS: Flash<0> 


example:
1.download kernel.img
sudo ./rkdeveloptool db RKXXLoader.bin    //download usbplug to device
sudo ./rkdeveloptool wl 0x8000 kernel.img //0x8000 is base of kernel partition,unit is sector.
sudo ./rkdeveloptool rd                   //reset device

compile error help
if you encounter the error like below:
./configure: line 4269: syntax error near unexpected token `LIBUSB1,libusb-1.0'
./configure: line 4269: `PKG_CHECK_MODULES(LIBUSB1,libusb-1.0)'

You should install pkg-config libusb-1.0:
	sudo apt-get install pkg-config libusb-1.0
