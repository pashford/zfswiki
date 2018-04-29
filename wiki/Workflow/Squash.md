# Squash the Commits

**Needs work**

Often, several commits will have been made to the local repository, and possibly to your Github repository.  To convert these commits to a single commit for merging into the main ZFS repository, it is necessary to squash the multiple commits into a single commit.

To squash multiple commits into a single commit, the ```git rebase -i``` command should be run.  This command will bring up a text editor with a number of *pick* lines.  The first of these *pick* lines should be left unchanged.  The other *pick* lines should have the *pick* replaced with *squash*.  When the lines have been changed, you should save the file and exit the editor.

After the rebase is finished, another editor will appear.  Use this editor to write the commit message for the new commit.

When a prompt is returned, use the ```git push -f``` command to update your Github repository.

https://github.com/servo/servo/wiki/Beginner%27s-guide-to-rebasing-and-squashing
