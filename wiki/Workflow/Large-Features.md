# Adding Large Features

Normally, a new feature or a bug fix is requested to be made as a single PR.  For large/complex features, it is sometimes preferrable to have multiple PRs that build on each other and don't negatively impact the reliability of the project.  The software should be stable at every step in the path.

As an example, if a developer were to implement a new low-level VDEV, the PRs might be as follows:
1.  Add support for the new VDEV type to the include files and the kernel
1.  Add support for the new VDEV type to the utilities that display status
1.  Add support for the new VDEV type to the *zpool* command
1.  Update the *man* page.
