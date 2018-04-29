# Rebase the Update

Updates to the ZFS on Linux project should always be based on the current *master* branch.  This makes them easier to merge into the repository.

There are two steps in the rebase process.  The first step is to update the local instance of the *master* branch from the main repository.  This can be done by entering the command ```git fetch upstream```.  This will give you a current version of the *master* branch to rebase to.

The second step is to perform the actual rebase of the change.  This is done by entering the command ```git rebase upstream/master```.  If there are any issues, you will be informed of them, and allowed to correct them.