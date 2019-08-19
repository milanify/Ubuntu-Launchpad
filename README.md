# Ubuntu-Launchpad
The Ubuntu version of Apple's/MacOS Launchpad application. The shortcut is meant to be placed on a dock as a keyboard-free alternative to pressing Super+A.

![alt tag](https://raw.githubusercontent.com/milan102/Ubuntu-Launchpad/master/launchpad-1.0/launchpad.png =250x250)

## Installation
In Terminal run:
```
sudo apt install xdotool
```

[Download the deb file](https://github.com/milan102/Ubuntu-Launchpad/raw/master/launchpad-1.0.deb)

Open the file and proceed with installation

Open Terminal and run:
```
xdg-open /usr/share/applications
```
or navigate to /usr/share/applications manually

![alt tag](https://raw.githubusercontent.com/milan102/Ubuntu-Launchpad/master/images/applications-folder.png)

Drag the Launchpad icon onto the dock

![alt tag](https://raw.githubusercontent.com/milan102/Ubuntu-Launchpad/master/images/dock.png)

Done!

## Development Tutorial
In Terminal run:
```
sudo apt install dh-make devscripts
```

Then run:
```sudo gedit .bashrc
```

Add the following to the end of the file:
```
export DEBEMAIL="https://github.com/milan102"
export DEBFULLNAME="Milan Mishra"
```

Create a folder called launchpad-1.0 and place the shell script inside
- Add a .desktop file and a .png file
- Edit the .desktop file to Exec where the shell script will be placed and set Path to that folder (more on that below)

From inside the launchpad-1.0 folder, run:
```
dh_make --indep --createorig --copyright mit
```

Inside the newly generated debian folder:
- Create an install file that specifies where the files in launchpad-1.0 get installed to (the paths are used in the .desktop file)
- Edit the rules file and add ```override_dh_usrlocal:```
- Edit the control file by changing Section, Homepage, Depends, and Description

Create a folder outside launchpad-1.0 called ```post-dh_make-files```
Back up the finalized install, rules, and control files in here so that they don't need to be created on future runs of dh_make and instead can be copied+pasted into the generated debian folder

From inside the launchpad-1.0 folder, run: 
```debuild -us -uc
```

Distribute the generated .deb file as an application installer

## Notes
Thanks to https://blog.packagecloud.io/eng/2016/12/15/howto-build-debian-package-containing-simple-shell-scripts/ for providing a great starting point with regard to packaging shell scripts into deb files

Icon made by Pixel Buddha from www.flaticon.com
