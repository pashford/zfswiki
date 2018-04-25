# Workflow

This page briefly describes the *normal* workflow for a developer working on ZFS code.

The workflow used in the ZFS project is based on the Integration-Manager Workflow from the [Pro Git][pro-git] book:
![alt text](https://git-scm.com/book/en/v2/images/integration-manager.png "Workflow")

* Install Git and set up your environment (Link)
* Create a Github account and set it up (Link)
* Get the source code (Link)
* For each Issue being worked:
   * Create a Branch (Link)
   * Do:
       * Do:
           * Make the appropriate change
           * Rebase the update (Link)
           * Commit the changes (Link)
           * Test the changes (Link)
       * Until the change does what it should
       * Squash the commits (Link)
       * Generate a PR (first pass) or Update a PR (subsequent passes) (Link - 2)
   * Until the PR is Accepted (Link)
   * Merge the PR (Link)
   * Delete the Branch (Link)

There are also a few *abnormal* workflow steps that occur from time to timeL

* Close a Pull Request (Link)
* Adding Large Features (Link)

Other helpful pages:
* https://guides.github.com/introduction/flow/
* http://scottchacon.com/2011/08/31/github-flow.html
* http://nvie.com/posts/a-successful-git-branching-model/
* https://help.github.com/articles/github-flow/
* https://services.github.com/on-demand/downloads/github-git-cheat-sheet/
* https://help.github.com/articles/associating-text-editors-with-git/
* https://help.github.com/articles/keeping-your-account-and-data-secure/
* https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/
* https://help.github.com/articles/adding-a-fallback-authentication-method-with-recover-accounts-elsewhere/
* https://github.com/servo/servo/wiki/Beginner%27s-guide-to-rebasing-and-squashing
* https://github.com/tiimgreen/github-cheat-sheet

NOTE:  Many of the above links will be removed or relocated to a child page as the Workflow documentation approaches completion.

[pro-git]: https://git-scm.com/book/en/v2
