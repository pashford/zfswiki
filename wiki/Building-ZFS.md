## GitHub Repositories

The official source for ZFS on Linux is maintained at GitHub by the [zfsonlinux][zol-org] organization.  The project consists of two primary git repositories named [spl][spl-repo] and [zfs][zfs-repo], both are required to build ZFS on Linux.  

* **SPL**: The SPL is thin shim layer which is responsible for implementing the fundamental interfaces required by OpenZFS.  It's this layer which allows OpenZFS to be used across multiple platforms.
* **ZFS**: The ZFS repository contains a copy of the upstream OpenZFS code which has been adapted and extended for Linux.  The vast majority of the core OpenZFS code is self-contained and can be used without modification.

## Installing Dependencies

The first thing you'll need to do is prepare your environment by installing a full development tool chain.  In addition, development headers for both the kernel and the following libraries must be available: **zlib, libattr, libuuid, libblkid, selinux, and libudev**.  Finally, if you wish to run the ZFS Test Suite **ksh** must be installed.

For Debian and Ubuntu:

```
$ sudo apt-get install build-essential autoconf libtool gawk alien fakeroot linux-headers-$(uname -r)
$ sudo apt-get install zlib1g-dev uuid-dev libattr1-dev libblkid-dev libselinux-dev libudev-dev
$ sudo apt-get install libssl-devsudo apt-get install parted lsscsi ksh
```

For RHEL and CentOS:

```
$ sudo yum groupinstall "Development Tools"
$ sudo yum install kernel-devel zlib-devel libuuid-devel libattr-devel libblkid-devel libselinux-devel
$ sudo yum install libudev-devel openssl-devel parted lsscsi ksh
```

For Fedora:

```
$ sudo dnf groupinstall "C Development Tools and Libraries"
$ sudo dnf install kernel-devel zlib-devel libuuid-devel libattr-devel libblkid-devel libselinux-devel
$ sudo dnf install libudev-devel openssl-devel elfutils-libelf-develsudo parted lsscsi ksh
```

## Build Options

There are two options for building ZFS on Linux, the correct one largely depends on your requirements.

* **Packages**: Often it can be useful to build custom packages from git which can be installed on a system.  This is the best way to perform integration testing with systemd, dracut, and udev.  The downside to using packages it is greatly increases the time required to build, install, and test a change.  See the [[custom-packages]] page for additional information on building packages.

* **In-tree**: Development can be done entirely in the SPL and ZFS source trees.  This speeds up development by allowing developers to rapidly iterate on a patch.  When working in-tree developers can leverage incremental builds, load/unload kernel modules, execute utilities, and verify all their changes with the ZFS Test Suite.

The remainder of this page focuses on the **in-tree** option which is the recommended method of development for the majority of changes.

### Developing In-Tree

#### Clone from GitHub

Start by cloning the SPL and ZFS repositories from GitHub.  The repositories have a **master** branch for development and a series of **\*-release** branches for tagged releases.  After checking out the repository your clone will default to the master branch.  Tagged releases may be built by checking out spl/zfs-x.y.z tags with matching version numbers or matching release branches.  Avoid using mismatched versions, this can result build failures due to interface changes.

```
git clone https://github.com/zfsonlinux/spl
git clone https://github.com/zfsonlinux/zfs
```

#### Configure and Build

For developers working on a change always create a new topic branch based off of master.  This will make it easy to open a pull request with your change latter.  The master branch is kept stable with extensive [regression testing][buildbot] of every pull request before and after it's merged.  Every effort is made to catch defects as early as possible and to keep them out of the tree.  Developers should be comfortable frequently rebasing their work against the latest master branch.

In this example we'll use the master branch and walk through a stock **in-tree** build.  As mentioned above ZFS layers on top of the SPL so its necessary to build this repository first.  Start by checking out the desired branch then build the SPL source in the tradition autotools fashion.
```
$ cd spl
$ git checkout master
$ sh autogen.sh
$ ./configure
$ make -s -j$(nproc)
```

**tip:** `--with-linux=PATH` and `--with-linux-obj=PATH` can be passed to configure to specify a kernel installed in a non-default location.  This option is also supported when building ZFS.  **tip:** `--enable-debug` can be set to enable all ASSERTs and additional correctness tests.  This option is also supported when building ZFS.  

Next move to the ZFS source tree and build it the same way.

```
$ cd ../zfs
$ git checkout master
$ sh autogen.sh
$ ./configure
$ make -s -j$(nproc)
```

**tip:**  `--with-spl=PATH` and `--with-spl-obj=PATH`, where `PATH` is a full path, can be passed to configure if it is unable to locate the SPL. 

After the software has been built, one of three tasks is usually performed:

* **[Build packages for distrubition][[Custom-Packages]]**
* **[Test from Build Directory](#test-from-build-directory)**
* **[Install for Production](#install-for-production)**

#### Test from Build Directory

There are a few helper scripts provided in the top-level scripts directory designed to aid developers working with in-tree builds.

* **zfs-helper.sh:** Certain functionality (i.e. /dev/zvol/) depends on the ZFS provided udev helper scripts being installed on the system.  This script can be used to create symlinks on the system from the installation location to the in-tree helper.  These links must be in place to successfully run the ZFS Test Suite.  The **-i** and **-r** options can be used to install and remove the symlinks.

```
$ sudo ./scripts/zfs-helpers.sh -i
```

* **zfs.sh:** The freshly built kernel modules can be loaded using `zfs.sh`.  This script can latter be used to unload the kernel modules with the **-u** option.

```
$ sudo ./scripts/zfs.sh
```

* **zloop.sh:** A wrapper to run ztest repeatedly with randomized arguments.  The ztest command is a user space stress test designed to detect correctness issues by concurrently running a random set of test cases.  If a crash is encountered, the ztest logs, any associated vdev files, and core file (if one exists) are collected and moved to the output directory for analysis.

```
$ sudo ./scripts/zloop.sh
```

* **zfs-tests.sh:** A wrapper which can be used to launch the ZFS Test Suite.  Three loopback devices are created on top of sparse files located in `/var/tmp/` and used for the regression test.  Detailed directions for the ZFS Test Suite can be found in the [README][zts-readme] located in the top-level tests directory.

```
$ sudo ./scripts/zfs-tests.sh -vx
```

**tip:** The **delegate** tests will be skipped unless group read permission is set on the zfs directory and its parents.

#### Install for Production

In some instances, installation from locally compiled source will be preferred over use of packages (either custom or pre-built).  After the packages have been built, as described above, the following should be run.  This will install a functional and ready to use ZFS environment.

```
# cd spl
# make -j1 install
# cd ../zfs
# make -j1 install
# cd ..
# ldconfig
```

[zol-org]: https://github.com/zfsonlinux/
[spl-repo]: https://github.com/zfsonlinux/spl
[zfs-repo]: https://github.com/zfsonlinux/zfs
[buildbot]: http://build.zfsonlinux.org/
[zts-readme]: https://github.com/zfsonlinux/zfs/tree/master/tests
