<!--- When this page is updated, please also check the 'Get-the-Source-Code' page -->

# Get the Source Code

This document goes over how a developer can get the ZFS source code for the purpose of making changes to it.  For other purposes, please see the [Get the Source Code][https://github.com/zfsonlinux/zfs/wiki/Get-the-Source-Code] page.

## Fork Git Master Branch

The Git *master* branch contains the latest version of the software, and will probably contain fixes that, for some reason, weren't included in the released tarball.  This is the preferred source code location and procecedure for ZFS development.  If you would like to do development work for the [ZFS on Linux Project][zol], you can fork the Github repository and prepare the source by using the following process.

1. If you don't have a Github account, go to https://github.com/ and create one.
1. Go to the [ZFS on Linux Project][zol] and fork both the ZFS and SPL repositories.  This will create two new repositories under your account.  Detailed instructions can be found at https://help.github.com/articles/fork-a-repo/.
1. Clone both of these repositories onto your development system.  As an example, if your account is *newzfsdeveloper*, the commands to clone the repositories would be:
```
$ mkdir zfs-on-linux
$ cd zfs-on-linux
$ git clone https://github.com/newzfsdeveloper/spl.git
$ git clone https://github.com/newzfsdeveloper/zfs.git
```
4. Enter the following commands to make the necessary linkage to the main repositories and prepare the source to be compiled:
```
$ cd spl
$ ./autogen.sh
$ git remote add upstream https://github.com/zfsonlinux/spl.git
$ cd ../zfs
$ ./autogen.sh
$ git remote add upstream https://github.com/zfsonlinux/zfs.git
cd ..
```

[zol]: https://github.com/zfsonlinux
