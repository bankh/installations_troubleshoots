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
