# Testing Changes to ZFS

The code in the ZFS on Linux project is quite complex. A minor error in a change could easily introduce new bugs into the software, causing unforeseeable problems. In an attempt to avoid this, ZTS (ZFS Test Suite) was developed. This test suite is run against multiple architectures and distributions by the Github system when a PR (Pull Request) is submitted.

A subset of the full test suite can be run by the developer to perform a preliminary verification of the changes in their *local* repository.

## Style Testing

The first part of the testing is to verify that the software meets the project's style guidelines.  To verify that the code meets those guidelines, run ```make checkstyle``` from the *local* repository.

## Basic Functionality Testing

The second part of the testing is to verify basic functionality.  This is to ensure that the changes made don't break previous functionality.

There are a few helper scripts provided in the top-level scripts directory designed to aid developers working with in-tree builds.

* **zfs-helper.sh:** Certain functionality (i.e. /dev/zvol/) depends on the ZFS provided udev helper scripts being installed on the system.  This script can be used to create symlinks on the system from the installation location to the in-tree helper.  These links must be in place to successfully run the ZFS Test Suite.  The `-i` and `-r` options can be used to install and remove the symlinks.

```
$ sudo ./scripts/zfs-helpers.sh -i
```

* **zfs.sh:** The freshly built kernel modules from the *local* repository can be loaded using `zfs.sh`.  This script will load those modules, **even if there are ZFS modules loaded** from another location.

This script can latter be used to unload the kernel modules with the `-u` option.

```
$ sudo ./scripts/zfs.sh
```

* **zfs-tests.sh:** A wrapper which can be used to launch the ZFS Test Suite.  Three loopback devices are created on top of sparse files located in `/var/tmp/` and used for the regression test.  Detailed directions for the ZFS Test Suite can be found in the [README][zts-readme] located in the top-level tests directory.

**WARNING**:  This script should **only** be run on a development system.  It makes configuration changes to the system to run the test, and it *tries* to remove those changes after completion, but the change removal could fail, and dynamic canges of this nature are usually undesirable on a production system.

```
$ sudo ./scripts/zfs-tests.sh -vx
```

**tip:** The **delegate** tests will be skipped unless group read permission is set on the zfs directory and its parents.

* **zloop.sh:** A wrapper to run ztest repeatedly with randomized arguments.  The ztest command is a user space stress test designed to detect correctness issues by concurrently running a random set of test cases.  If a crash is encountered, the ztest logs, any associated vdev files, and core file (if one exists) are collected and moved to the output directory for analysis.

```
$ sudo ./scripts/zloop.sh
```

## Change Testing

Finally, it's necessary to verify that the changes made actually do what they were intended to do.  The extent of the testing would depend on the complexity of the changes.

After the changes are tested, if the testing can be automated for addition to ZTS, it should be.  A separate Issue should be opened for any new tests to be added to either the full test suite or to the smaller test suite distributed with ZFS.

It should be noted that if the change adds too many lines of code that don't get tested by ZTS, the change will not pass testing.

[zts-readme]: https://github.com/zfsonlinux/zfs/tree/master/tests
