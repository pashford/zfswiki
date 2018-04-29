# Workflow

This page briefly describes the *normal* workflow for a developer working on ZFS code.

The workflow used in the ZFS project is based on the Integration-Manager Workflow from the [Pro Git][pro-git] book:
![alt text](https://git-scm.com/book/en/v2/images/integration-manager.png "Workflow")

* [Install Git and set up your environment][W-install]
* [Create a Github account and set it up][W-github-account]
* [Get the source code][W-get-code]
* For each Issue being worked:
   * [Create a Branch][W-create-branch]
   * Do:
       * Do:
           * Make the appropriate changes to the software
           * [Test the changes][W-test]
           * [Rebase the changes][W-rebase] on the current *master* branch
           * [Commit the changes][W-commit] to your *topic* branch
       * Until the change does what it should
       * [Squash the commits][W-squash]
       * [Generate a PR][W-generate] (first pass) or [Update a PR][W-update] (subsequent passes)
   * Until the [PR is Accepted][W-accept]
   * [Merge the PR][W-merge]
   * [Delete the Branch][W-delete-branch]
There are also a few *abnormal* workflow steps that occur from time to time:
* [Fix conflicts][W-conflicts]
* [Close a PR][W-close]
* [Adding large features][W-large]
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
[W-install]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Install-Git.md
[W-github-account]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Create-Github-Account.md
[W-get-code]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Get-Source.md
[W-create-branch]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Create-Branch.md
[W-test]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Test.md
[W-rebase]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Rebase.md
[W-commit]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Commit.md
[W-squash]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Squash.md
[W-generate]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Generate.md
[W-update]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Update.md
[W-accept]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Accept.md
[W-merge]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Merge.md
[W-conflicts]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Conflicts.md
[W-close-PR]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Close-PR.md
[W-large]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Large-Features.md
[W-delete-branch]: https://github.com/pashford/zfswiki/blob/master/wiki/W-Delete-Branch.md
