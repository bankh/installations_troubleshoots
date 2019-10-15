#### Ubuntu Core - Changing the WiFi Connection
There are a few posts I've seen such as this (one)[https://askubuntu.com/questions/1015632/ubuntu-core-wifi-configuration-issue]
The solution requires an ethernet connection to the wifi router from the Ubuntu Core device. Once you have IP address it will show the 
```
ssh {user_name}@{IP} with some of the keys. 
```
I assume that your system has the necessary key files for ssh connection. Use the following command for connecting from the client to the ubuntu core installed device.
```
$ ssh {user_name}@{IP}
```
Then make sure that you are not in classic mode. Otherwise, the wifi changes will not work.
```
$sudo console-config
```
Follow the intuitive instructions to setup the Wifi. Some of the potential confusion would be for the static IP case and the following will help you. We assume that the computer is on 192.168 domain and this may change. To find out first try the following:
```
$ ifconfig
```
See the network properties and if the domain is 192.168.0.xx apply the following
```
SubNet: 192.168.0.0/24
IP: 192.168.0.{Whatever_static_range_is_available_on_the_router}
Gateway: 192.168.0.1
```
Then restart your raspi and disconnect ethernet. You should see the new IP with the same way as
```
ssh {user_name}@{NEW_IP}
```
You can connect as you connected earlier steps via ssh by using new IP -no need to renew the keys.

#### Firmware Development Tools - Installation of Platform IO (Add to main guidelines)
Platform IO is a framework which consists different types of controllers including ARM, AVR, RISC-5
based or others x86 or x64 to name a few.It is a plugin which can be interfaced to Visual Studio
Code.
Once you installed that in Ubuntu StLink will result in an error. The board will be defined as a
media device which one can upload firmware file from the compiled code. However, this approach
is problematic for on-system debugging. Thereby, one needs to change the rule set in Ubuntu to
be able to open the USB port. Otherwise the error looks like below:
```
Error: libusb_open() failed with LIBUSB_ERROR_ACCESS
Error: no device found
```
The location of OpenOCD is a result of 
$ locate openocd
/usr/local/share/openocs/contrib/
Copy 60-openocd.rules to /etc/udev/rules.d/ as a super user and reboot the system.
$ sudo cp 60-openocv.rules /etc/udev/rules.d/
$ sudo reboot

Now you can build and upload the code as well as debug by using the framework's PIO debugger.

#### Installation of FreeCAD for Ubuntu 16.04

Follow the procedure at https://www.freecadweb.org/wiki/CompileOnUnix#Debian_and_Ubuntu
- Installation:
```
$ git clone https://github.com/FreeCAD/FreeCAD.git
$ cd FreeCad
$ mkdir freecad-build
$ cd freecad-build
$ cmake -DFREECAD_USE_EXTERNAL_PIVY=1 -DCMAKE_BUILD_TYPE=Release make -j8 .. 
# Note: to speed up build use all CPU cores: make -j$(nproc). The one above is for octacore
$ make
# Install the global structure
$ sudo make install
```

#### How to use Eagle and export .brd to 3D CAD file
- The default installation moves the files into /opt/eagle-{version}. 
- Run ./eagle (if the ownership was on root run with sudo)
- Go online on Control Panel of Eagle.
- Open .brd file that you want to convert in 3D. 
  - Please remark if you don't have the 3D components, it will only convert the
  foot prints.
- In the board window, go to File > Export > Step. It will start to generate 
3D model. Once the generation of the model completed, you will see the file
on Control Panel main window under "Recently Generated 3D Files."
- Click that file to download. 
- Use it with your favorite CAD software (e.g. FreeCAD).

#### Copy the files from the PC to MyCloud via ssh

1- ssh service should be enabled first. Default user name is sshd.

2- Connect the MyCloud via ssh in the terminal and check the folders in
/nfs/:
```
$> ssh sshd@{MyCloud_s IP address}
* in myCloud

#> cd /nfs/
#> ls
* Make sure the location of copy
```
3- Copy the files from the location 

```
$ scp -r /{folder to copy} sshd@{MyCloud_s IP address}:/{the target location}
```

#### Troubleshoot: 

* The mouse pointer stuck at the top of the screen Ubuntu 14.04.

```

#Check the input list
$> xinput list 
* Disable the input item (e.g. touchpad)
* You may disable the keyboard watch out what you disabled
$> xinput disable <ID>
* Enable the input item
$> xinpit enable <ID>
* Restart the computer
$> sudo shutdown -r now

```

#### Moving the windows in Ubuntu 

```

* Make sure that you have the compizconfig-settings-manager
* Search for Grid
* Generate a combination for Put+Top or Put+Bottom

e.g., 

<Ctrl><Shift><Alt>Up for Put+Top
<Ctrl><Shift><Alt>Up for Put+Bottom

This shortcuts will help you to move the window to the upper half
of the screen and lower half of the screen.
```
#### Installation of Electron
* In order to install latest version of nodejs. Use the following command.
```
Nodejs:
$> curl -sL https://deb.nodesource.com/setup_10.x | sudo bash -
$> node -v
The installation of npm and 
#> npm install npm@latest -g
#> npm install electron -g --save --unsafe-perm=true


```
