# Commit the Changes

In order for your changes to be merged into the ZFS on Linux project, you must first send the changes made in your *local* repository to your *forked* repository.  This can be done with the ```git commit -sa```.  

The ```-s``` option adds a *signed off by* line to the commit.  This *signed off by* line is an acceptence of the [License Terms][license] of the project.  This is required for the ZFS on Linux project.

The ```-a``` option causes all modified files in the current branch to be *staged* prior to performing the commit.  A list of the modified files in the *local* branch can be created by the use of the ```git status``` command.  If there are files that have been modified that shouldn't be part of the commit, they can either be rolled back in the current branch, or the files can be manually staged with the ```git add (file-name) ...``` command, and the ```git commit``` command can be run without the ```-a``` option.

After the changes have been commited to your *local* repository, they should be pushed to your *forked* repository.  This is done with the ```git push``` command.

[license]: https://github.com/zfsonlinux/zfs/blob/master/COPYRIGHT
