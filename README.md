# fedora37_kde_selinux_reconciliation

## Introduction
This repository is about making the KDE desktop system on the Fedora 37 KDE Spin 
cooperate with SELinux.

If you want to make user accounts on a PC running Fedora with "user_u" restrictions,
then you will need to modify how SELinux and KDE configuration files interact.
These modifications will allow you to create such restricted accounts that will login successfully
when SELinux is in "enforcing" mode.

There are different policy customizations you can install along 
with modifications to a master login script.

The "sh.local" file represents changes you can make to the 
"/etc/profile.d/sh.local" file.

This script file assumes that each user has a "tmp" directory.
I had someone tell me that you should list all directories 
that you want end-users to have under /etc/skel (including the tmp directory).
This will help the "adduser" command setup the account property.
You will be able to type "sudo adduser -Z user_u <loginname>" to setup such restricted accounts.

There are different "te" SELinux policy source files that you can compile
or you can use "sudo semodule -i" to install the corresponding pp files.

## Caveats/Disclaimer

The restricted accounts may still have the icons in their taskbars that you will need to remove manually.
You may want to add or remove such icons as the network icon or the updates icon in the taskbar.


