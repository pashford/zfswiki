# Create a Branch

With small projects, it's possible to develop code as commits directly on the *master* branch.  In the ZFS-on-Linux project, that sort of development would create havoc and make it more difficult to open a PR later.  For this reason, development in the ZFS-on-Linux project is done on branches.

To create a branch, navigate to the base directory of your local Git repository and use the ```git branch (branch-name)``` command.  The name of the branch should be either the name of the feature (preferred for development of features) or an indication of the issue being worked on (preferred for bug fixes).
