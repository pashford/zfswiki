# Workflow

This page briefly describes the *normal* workflow for a developer working on ZFS code.

The workflow used in the ZFS project is similar to the Integration-Manager Workflow from the [Pro Git][pro-git] book:
![alt text](https://git-scm.com/book/en/v2/images/integration-manager.png "Workflow")

* Install Git and set up your environment
* Create a Github account and set it up
* Get the source code
* For each Issue being worked:
   * Create a Branch
   * Do:
       * Change the code
       * Rebase the code
       * Commit the changes
       * Test the code
   * Until the code works properly
   * Squash the commits
   * Generate a PR
   * Update a PR
   * Merge the PR
   * Delete the Branch

There are also a few *abnormal* workflow steps that occur from time to timeL

* Close a Pull Request

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

NOTE:  Many of the above pages will be removed or relocated to a child page as the Workflow documentation approaches completion.

[pro-git]: https://git-scm.com/book/en/v2
