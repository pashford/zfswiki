## Get the Source Code

This document goes over the three common ways to get the ZFS source code.  This is required for development and to create custom packages.

* **[Released Tarball](#released-tarball)** - Released and tested
* **[Git Master Branch](#git-master-branch)** - Latest version
* **[Fork ZFS Master Branch](#fork-zfs-master-branch)** - Development

### Released Tarball

The released tarball contains the latest fully tested and released version of ZFS.  This is the preferred source code location for use in production systems.  If you want to use the official released tarballs, then use the following commands to fetch and prepare the source.

```
$ wget http://archive.zfsonlinux.org/downloads/zfsonlinux/spl/spl-x.y.z.tar.gz
$ wget http://archive.zfsonlinux.org/downloads/zfsonlinux/zfs/zfs-x.y.z.tar.gz
$ tar -xzf spl-x.y.z.tar.gz
$ tar -xzf zfs-x.y.z.tar.gz
```

As an example, the released tarball for ZFS 0.7.6 would be ```zfs-0.7.6.tar.gz```.

### Git Master Branch

The Git *master* branch contains the latest version of the software, and will probably contain fixes that, for some reason, weren't included in the released tarball.  This is the preferred source code location and procedure for users who need a new patch/feature for their system(s).  If you would like to use the git version, you can clone it from Github and prepare the source like this.

```
$ git clone https://github.com/zfsonlinux/spl.git
$ git clone https://github.com/zfsonlinux/zfs.git
$ cd spl
$ ./autogen.sh
$ cd ../zfs
$ ./autogen.sh
$ cd ..
```

### Fork ZFS Master Branch

The Git *master* branch contains the latest version of the software, and will probably contain fixes that, for some reason, weren't included in the released tarball.  This is the preferred source code location and procecedure for ZFS development.  If you would like to do development work for the [ZFS on Linux Project][zol], you can for the Github repository and prepare the source by using the following process.

1. If you don't have a Github account, go to https://github.com/ and create one.
1. Go to the [ZFS on Linux Project][zol] and fork both the ZFS and SPL repositories.  This will create two new repositories under your account.
1. Clone both of these repositories into your development system.
1.  Enter the following commands:
```
$ cd spl
$ ./autogen.sh
$ git remote add upstream https://github.com/zfsonlinux/spl.git
$ cd ../zfs
$ ./autogen.sh
$ git remote add upstream https://github.com/zfsonlinux/zfs.git
cd ..
```


Once the source has been prepared you'll need to decide what kind of packages you're building and jump the to appropriate section below.  Note that not all package types are supported for all platforms.

[zol]: https://github.com/zfsonlinux
