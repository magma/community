# Contribute to the Magma project

* [Code of Conduct](#code-of-conduct)
* [Pull requests](#pull-requests)
* [Certificate of Origin](#certificate-of-origin)
* [GitHub best practices](#github-best-practices)
* [GitHub workflow](#github-workflow)
* [Reviews](#reviews)
* [Contact](#contact)
* [Project maintainers](#project-maintainers)

The Magma project is an open source project licensed under the
[3-clause BSD License](https://opensource.org/licenses/BSD-3-Clause).

It lives in repositories under the [GitHub Magma organisation](https://github.com/magma).

## Code of Conduct

All contributors must agree to the project [code of conduct](CODE_OF_CONDUCT.md).

## Pull requests

All the repositories accept contributions via [GitHub Pull requests (PR)](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests). Submit PRs by following the [GitHub workflow](#github-workflow).

## Developer's Certificate of Origin

In order to have a clear contribution chain of trust we use the [signed-off-by
language](https://developercertificate.org/) and process used by the Linux kernel project.

Every commit should include a Signed-Off-By tag as a certification that the developer has the right to submit the contribution and they are agreeing to the language of the Developer's Certificate of Origin (DCO). PRs cannot be merged without following this process. Use to `-s` or `--signoff` flag with your commit.

```sh
$ git commit -s
```

## Repository specific contribution guides

In addition to the general principles below, other repos may have specific
information for contributing:
* [Magma repo](https://github.com/magma/magma/blob/master/CONTRIBUTING.md)
* [Website repo](https://github.com/magma/magma-website)

## GitHub best practices

### Issue tracking

To report a bug that is not already documented, please open a GitHub issue for the repository in question.

If it is unclear which repository to raise your query against, first try to
get in [contact](#contact) with us. If in doubt, raise the issue
[here](https://github.com/magma/community/issues/new) and we will
help you to handle the query by routing it to the correct area for resolution.

### Closing issues

Adding a `Fixes ####` comment to at least one commit in the PR triggers GitHub to automatically close the issue once the PR is merged:

```
A sample commit message

This is an example of a commit message with a tagged GitHub Issue that will be closed on merge.

Fixes #123

Signed-off-by: Your Name <email@org.com>
```

The issue is automatically closed by GitHub when the
[commit message](https://help.github.com/articles/closing-issues-via-commit-messages/) is parsed.

## GitHub workflow

* Ensure each PR only covers one topic. If you mix up different items in
  your patches or PR, they will likely need to be reworked.

* Follow a [topic branch method](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-branches) for development.

##### Fork and clone

In this example, we configure a Git environment to contribute to this very 
`Community` repo. We create a sample branch, incorporate reviewer feedback, and rebase our commits.

1. Fork the [upstream repository](https://help.github.com/articles/cloning-a-repository):

1. [Clone your forked copy of the upstream repository](https://help.github.com/articles/cloning-a-repository):

1. While on your *forked copy*, select the green button `Clone or download`
   and copy the URL. 

1. Run the commands below and **paste the copied URL** (previous step),
   so your real GitHub user name replaces `your-github-username` below.
  
```sh
$ git clone https://github.com/{your-github-username}/community
$ cd community
```
   
>**Note:** Cloning a forked repository automatically gives a remote `origin`.

##### Configure the upstream remote

Next, add the remote `upstream`. Configuring this remote allows you to
synchronize your forked copy, `origin`, with the `upstream`. The 
`upstream` URL varies by repository. We use the `upstream` from the Community for this example. 

1. Change directory into `community`. 

1. Set the remote `upstream` as follows. 

    ```sh
    $ git remote add upstream https://github.com/magma/community
    ```

1. Run `git remote -v`. Your remotes should appear similar to these:

    ```
    origin  https://github.com/your-github-username/community.git (fetch)  
    origin  https://github.com/your-github-username/community.git (push)  
    upstream  https://github.com/magma/community.git (fetch)  
    upstream  https://github.com/magma/community.git (push)  
    ```

For more details, see how to [set up a git remote](https://help.github.com/articles/configuring-a-remote-for-a-fork).

##### Create a topic branch

1. Create a new "topic branch" to do your work on:

    ```
    $ git checkout -b fix-spelling-errors
    ```

    >**Warning:** *Never* make changes directly to the `master` or `main` 
    > branch--*always* create a new "topic branch" for PR work.

1. Make some editorial changes. In this example, we modify the file that
   you are reading.

    ```
    $ $EDITOR CONTRIBUTING.md
    ```

1. Commit your changes to the current (`fix-spelling-errors`) branch.

    ```
    $ git commit -as
    ```

1. Push your local `fix-spelling-errors` branch to your remote fork:

    ```
    $ git push -u origin fix-spelling-errors
    ```

   >**Note:** The `-u` option tells `git` to "link" your local clone with
   > your remote fork so that it knows from now on that the local repository
   > and the remote fork refer to "the same" upstream repository. Strictly 
   >speaking, this option is only required the first time you call `git push`
   >for a new clone.

1. Create the PR:
  - Browse to https://github.com/magma/community.
  - Click the "Compare & pull request" button that appears.
  - Click the "Create pull request" button.

  >**Note:** You do not need to change any of the defaults on this page.

##### Update your PR based on review comments

Suppose you received some reviewer feedback that asked you to make some
changes to your PR. You updated your local branch and committed those
review changes by creating three commits. There are now four commits in your
local branch: the original commit you created for the PR and three other
commits you created to apply the review changes to your branch. Your branch
now looks something like this:

```sh
$ git log main.. --oneline --decorate=no
4928d57 docs: Fix typos and fold long lines
829c6c8 apply review feedback changes
7c9b1b2 remove blank lines
60e2b2b doh - missed one
```

>**Note:** The `git log` command compares your current branch 
>(`fix-spelling-errors`) with the `main` branch and lists all the commits,
>one per line.

##### Git rebase if multiple commits

Since all four commits are related to *the same change*, it makes sense to
combine all four commits into a *single commit* on your PR. You need to
[git rebase](https://help.github.com/github/using-git/about-git-rebase)
multiple commits on your branch. Follow these steps.

1. Update the `main` branch in your local copy of the upstream
   repository:

    ```
    $ cd magma/community
    $ git checkout main
    $ git pull --rebase upstream main
    ```

    The previous command downloads all the latest changes from the upstream
    repository and adds them to your *local copy*.

1. Now, switch back to your PR branch:

    ```
    $ git checkout fix-spelling-errors
    ```

1. Rebase your changes against the `main` branch.

    ```sh
    $ git rebase -i main
    ```

    Example output:

    ```sh
    pick 2e335ac docs: Fix typos and fold long lines
    pick 6d6deb0 apply review feedback changes
    pick 23bc01d remove blank lines
    pick 3a4ba3f doh - missed one
    ```

1. In your editor, read the comments at the bottom of the screen. 
   Do not modify the first line, `pick 2e335ac docs: Fix typos ...`. Instead, revise `pick` to `squash` at the start of all following lines.

    Example output:

    ```sh
    pick 2e335ac docs: Fix typos and fold long lines
    squash 6d6deb0 apply review feedback changes
    squash 23bc01d remove blank lines
    squash 3a4ba3f doh - missed one
    ```

1. Save your changes and quit the editor. Git puts you *back* into your
   editor. You will see all the commit *messages*. 

1. At top is your first commit, which should be in the 
   [correct format](#patch-format). Keep your first commit and delete 
   all the following commits, as appropriate, based on 
   the review feedback.

1. Save the file and quit the editor. Once this operation completes, the four
   commits will have been converted into a single new commit. Check this by
   running the `git log` command again:

    ```sh
    $ git log master.. --oneline --decorate=no
    3ea3aef docs: Fix typo
    ```

1. Force push your updated local `fix-spelling-errors` branch to `origin`
   remote:

    ```sh
    $ git push -f origin fix-spelling-errors
    ```

>**Note:** Not only does this command upload your changes to your fork, it
>also includes the *latest upstream changes* to your fork since you ran
>`git pull --rebase upstream main` on the main branch and then merged
>those changes into your PR branch. This ensures your fork is now "up to
>date" with the upstream repository. The `-f` option is a "force push". Since
>you created a new commit using `git rebase`, you must "overwrite" the old
>copy of your branch in your fork on GitHub. 

Your PR is now updated on GitHub. To ensure team members are aware of this,
leave a message on the PR stating something like, "Review feedback applied".
This notification allows the team to once again review your PR more quickly.

## Reviews

Before your PRs are merged into the main code base, they are reviewed. We
encourage anybody to review any PR and leave feedback.

The [Reviewing Guide](Reviewing.md) provides more information on the 
responsibilities of maintainers and the process for reviewing a PR.

## Contact

The Magma community can be reached
[through various channels](https://www.magmacore.org).

## Project maintainers

The Magma project maintainers are the people accepting or
rejecting any PR. Although [anyone can review PRs](#reviews), only the
review of a maintainer counts towards the approval of a PR.

Approvers are listed in GitHub teams for each repository. The project
uses the
[GitHub required status checks](https://help.github.com/en/articles/enabling-required-status-checks)
along with the [GitHub `CODEOWNERS`file](https://help.github.com/en/articles/about-code-owners) to specify who can approve PRs. All repositories are configured to require two approvals from the repository-specific approval team.


#### Acknowledgements

Portions of this contributing document are based on the [Kata Containers](https://github.com/kata-containers) contributing documentation.