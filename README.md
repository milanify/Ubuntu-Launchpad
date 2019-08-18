# Ubuntu-Launchpad
The Ubuntu version of Apple's/MacOS Launchpad application

# Requirements
sudo apt install xdotool

# Development Tutorial
Ran sudo gedit .bashrc
Added the following to the end of the file: 

export DEBEMAIL="https://github.com/milan102"
export DEBFULLNAME="Milan Mishra"

Created a folder called launchpad-1.0 and placed the shell script inside
Added a .desktop file and a .png file
Edited the .desktop file to Exec where the shell script will be placed and set Path to that folder (more on that below)

From inside the launchpad-1.0 folder, ran dh_make --indep --createorig --copyright gpl3

Inside the newly generated debian folder: 
Created a install file that specifies where the files in launchpad-1.0 get installed to
Edited the rules file and added override_dh_usrlocal:
Edited the control file by changing Homepage, Depends, and Description

Created a folder outside launchpad-1.0 called drag-into-debian-folder
Backed up the finalized install, rules, and control files in here so that they don't need to be created on future runs of dh_make and can instead be copy+pasted into the generated debian folder

From inside the launchpad-1.0 folder, ran debuild -us -uc


# Notes
Thanks to https://blog.packagecloud.io/eng/2016/12/15/howto-build-debian-package-containing-simple-shell-scripts/ for providing a great starting point with regards to packaging shell scripts into deb files
