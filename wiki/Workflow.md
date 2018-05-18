# Workflow

This page briefly describes the *normal* workflow for a developer working on the ZFS-on-Linux project.  It is intended to help developers who are new to the project get started quickly and easily.

The workflow used in the ZFS project is based on the Integration-Manager Workflow from the [Pro Git][pro-git] book:
![alt text](https://git-scm.com/book/en/v2/images/integration-manager.png "Workflow")

* [Install Git and set up your environment][W-install]
* [Create a Github account and set it up][W-github-account]
* [Get the source code][W-get-code]
* For each Issue being worked:
   * [Create a Branch][W-create-branch]
   * Do:
       * Do:
           * Make the appropriate changes to the software, following the [Sytle Guide][style] - Please remember to [commit often][W-often]
           * [Test the changes][W-test]
           * [Rebase the changes][W-rebase] on the current *master* branch
           * [Commit the changes][W-commit] to your *topic* branch
       * Until the change does what it should
       * [Squash the commits][W-squash] **Incomplete**
       * [Generate a PR][W-generate] (first pass) or [Update a PR][W-update] (subsequent passes) **EMPTY**
   * Until the [PR is Accepted][W-accept]
   * [Merge the PR][W-merge]
   * [Delete the Branch][W-delete-branch]

There are also a few *abnormal* workflow steps that occur from time to time:

* [Fix conflicts][W-conflicts] **EMPTY**
* [Close a PR][W-close-PR] **Incomplete**
* [Adding large features][W-large] **Incomplete**
* [Adding a Test][W-create-test] **EMPTY**

Other helpful pages:

* https://guides.github.com/introduction/flow/
* http://nvie.com/posts/a-successful-git-branching-model/
* https://services.github.com/on-demand/downloads/github-git-cheat-sheet/
* https://github.com/servo/servo/wiki/Beginner%27s-guide-to-rebasing-and-squashing
* https://github.com/tiimgreen/github-cheat-sheet

NOTE:  Many of the above links will be removed or relocated to a child page as the Workflow documentation approaches completion.

[zol]: https://github.com/zfsonlinux/zfs
[pro-git]: https://git-scm.com/book/en/v2
[style]: http://www.cis.upenn.edu/~lee/06cse480/data/cstyle.ms.pdf
[W-install]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Install-Git.md
[W-github-account]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Create-Github-Account.md
[W-get-code]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Get-Source.md
[W-create-branch]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Create-Branch.md
[W-often]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Commit-Often.md
[W-test]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Test.md
[W-rebase]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Rebase.md
[W-commit]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Commit.md
[W-squash]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Squash.md
[W-generate]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Generate-PR.md
[W-update]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Update-PR.md
[W-accept]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Accept-PR.md
[W-merge]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Merge-PR.md
[W-conflicts]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Conflicts.md
[W-close-PR]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Close-PR.md
[W-large]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Large-Features.md
[W-create-test]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Create-Test.md
[W-delete-branch]: https://github.com/pashford/zfswiki/blob/master/wiki/Workflow/Delete-Branch.md
