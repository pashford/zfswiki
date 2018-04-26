# Test the Changes

The code in the ZFS on Linux project is quite complex.  A minor error in a change could easily create bugs in the software which could unforseen problems.  In order to attempt to avoid this sort of problem, a test suite has been developed.

To run the test suite, 

https://github.com/zfsonlinux/zfs/wiki/Building-ZFS#running-zloopsh-and-zfs-testssh

In addition, the ZFS on Linux project has style standards.  To verify that the code meets those standards, run ```make checkstyle``` from the local directory containing the git repository.
