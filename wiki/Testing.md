# Testing changes to ZFS

After changes are made to the ZFS on Linux software, it is necessary to test the changes.

There is a complete test suite that is performed on multiple architectures and distributions when a PR is submitted.  There is also a subset of this test suite that is part of the ZFS repository.  This subset can be run on demand by ZFS developers.

## Style Testing

The first part of the testing is to verify that the software meets the project's style guidelines.  To verify that the code meets those guidelines, run ```make checkstyle``` from the local directory containing the git repository.

## Basic Functionality

The second part of the testing is to verify basic functionality.  This is to ensure that the changes made don't break previous functionality.

There are a few helper scripts provided in the top-level scripts directory designed to aid developers working with in-tree builds.

* **zfs-helper.sh:** Certain functionality (i.e. /dev/zvol/) depends on the ZFS provided udev helper scripts being installed on the system.  This script can be used to create symlinks on the system from the installation location to the in-tree helper.  These links must be in place to successfully run the ZFS Test Suite.  The **-i** and **-r** options can be used to install and remove the symlinks.

```
$ sudo ./scripts/zfs-helpers.sh -i
```

* **zfs.sh:** The freshly built kernel modules can be loaded using `zfs.sh`.  This script can latter be used to unload the kernel modules with the **-u** option.

```
$ sudo ./scripts/zfs.sh
```

* **zloop.sh:** A wrapper to run ztest repeatedly with randomized arguments.  The ztest command is a user space stress test designed to detect correctness issues by concurrently running a random set of test cases.  If a crash is encountered, the ztest logs, any associated vdev files, and core file (if one exists) are collected and moved to the output directory for analysis.

```
$ sudo ./scripts/zloop.sh
```

* **zfs-tests.sh:** A wrapper which can be used to launch the ZFS Test Suite.  Three loopback devices are created on top of sparse files located in `/var/tmp/` and used for the regression test.  Detailed directions for the ZFS Test Suite can be found in the [README][zts-readme] located in the top-level tests directory.

```
$ sudo ./scripts/zfs-tests.sh -vx
```

**tip:** The **delegate** tests will be skipped unless group read permission is set on the zfs directory and its parents.

## Change Testing

Finally, it's necessary to verify that the changes made actually do what they were intended to do.  The extent of the testing would depend on the complexity of the changes.

After these changes are tested, it would be good if the testing could be automated for addition to the test suite.  A seperate Issue should be opened for the additional test.
