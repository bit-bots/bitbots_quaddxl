# Firmware

## Flash correct EEPROM:
Install drivers from https://www.ftdichip.com/Drivers/D2XX.htm 
Unpack them:
tar -xvf libftd2xx-x86_64-1.4.8.gz

Copy them into the library folder:
sudo cp release/build/lib* /usr/local/lib

Link them:
sudo ln -s libftd2xx.so.1.4.8 libftd2xx.so

Make them executable:
sudo chmod 0755 libftd2xx.so.1.4.8

Unload Serial USB Drivers (these will be reloaded when the device is removed and plugged back in)
sudo rmmod ftdi_sio usbserial 

compile code:
gcc -o write main.c -L. -lftd2xx -Wl,-rpath,/usr/local/lib

execute code:
sudo ./write

remove and plug in the device and it should appear as 4 virtual serial ports

## ros_control drivers

can be found here:
