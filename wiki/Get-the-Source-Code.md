# Get the Source Code

This document goes over the four common ways to get the ZFS source code.  This is required for development and to create custom packages.

* **[Release Tarball](#release-tarball)** - Released and tested
* **[Gir Release Branch](#git-release-branch)** - Released and tested
* **[Git Master Branch](#git-master-branch)** - Latest version
* **[Fork ZFS Master Branch](#fork-zfs-master-branch)** - Development

## Release Tarball

The release tarball contains a fully tested and released version of ZFS.  This is one of the two preferred source code locations for use in production systems.  If you want to use the official release tarballs, then use the following commands to fetch and prepare the source.

```
$ wget http://archive.zfsonlinux.org/downloads/zfsonlinux/spl/spl-x.y.z.tar.gz
$ wget http://archive.zfsonlinux.org/downloads/zfsonlinux/zfs/zfs-x.y.z.tar.gz
$ tar -xzf spl-x.y.z.tar.gz
$ tar -xzf zfs-x.y.z.tar.gz
```

As an example, the release tarball for ZFS 0.7.6 would be ```zfs-0.7.6.tar.gz```.

## Git Release Branch

The Git *release* branch contains the currently released version of the software.  This is one of the two preferred source code locations for use in production systems.  This is the software that the release tarballs are created from, and is fully tested.  If you would like to compile directly from the Git *release* branch, please use the following procedures:

```
$ git clone https://github.com/zfsonlinux/spl.git
$ git clone https://github.com/zfsonlinux/zfs.git
$ cd spl
$ git checkout spl-0.7-release
$ ./autogen.sh
$ cd ../zfs
$ git checkout zfs-0.7-release
$ ./autogen.sh
$ cd ..
```

**How does the user know that upstream has changed?**

This is needed to provide the necessary script segment to auto-update.

## Git Master Branch

The Git *master* branch contains the latest version of the software, and will probably contain fixes that, for some reason, weren't included in the released tarball.  This is the source code location and procedure for users who need a new patch/feature for their system(s).  If you would like to use the Git *master* version, you can clone it from Github and prepare the source like this.

NOTE:  This could introduce problems into yo

```
$ git clone https://github.com/zfsonlinux/spl.git
$ git clone https://github.com/zfsonlinux/zfs.git
$ cd spl
$ ./autogen.sh
$ cd ../zfs
$ ./autogen.sh
$ cd ..
```

## Fork Git Master Branch

The Git *master* branch contains the latest version of the software, and will probably contain fixes that, for some reason, weren't included in the released tarball.  This is the preferred source code location and procecedure for ZFS development.  If you would like to do development work for the [ZFS on Linux Project][zol], you can fork the Github repository and prepare the source by using the following process.

1. If you don't have a Github account, go to https://github.com/ and create one.
1. Go to the [ZFS on Linux Project][zol] and fork both the ZFS and SPL repositories.  This will create two new repositories under your account.  Detailed instructions can be found at https://help.github.com/articles/fork-a-repo/.
1. Clone both of these repositories onto your development system.  As an example, if your account is *newzfsdeveloper*, the commands to clone the repositories would be:
```
$ git clone https://github.com/newzfsdeveloper/spl.git
$ git clone https://github.com/newzfsdeveloper/zfs.git
```
1. Enter the following commands to make the necessary linkage to the main repositories and prepare the source to be compiled:
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
