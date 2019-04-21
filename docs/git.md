## Git !heading

* Commit and push frequently
* Have git hooks to run lint and unit test
* Fork the repository to start your work (branches are harder to maintain)
* Clone your forked repository (this will be your origin)
* Run `git remote set-url upstream <repository>` with the company repository clone URL
* Work in the `master` branch
* Open Pull Requests (PRs) to the `master` branch
* If you have to change your focus to work on something else, you can:
  * checkout creating a different branch in your machine
  * commit the changes
  * push to your forked repository
  * go back to the master branch and continue your work
* If you already have commited some part of your work and need to change your focus to work on something else, you can:
  * Create/checkout to a branch `git checkout -b your-branch`
  * Commit if you have something else to commit
  * Go back to the `master` branch
  * Undo the commits related to the branch you create, by running a `git reset --soft HEAD^` or `git reset --soft HEAD~2` where `2` is the number of commits. (This will undo a commit, and the second undo 2 commits)
  * If you have already sent some code to the repository, you can perform a `git push --force` on this step
* To update your master you can just run a `git pull upstream master`
* Write proper commit messages (that describe what's in that commit)
  * Write your commit message in the imperative: "Fix bug" and not "Fixed bug" or "Fixes bug."
  * Here is a [template originally written by Tim Pope](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html):

```
Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here

- Use a hanging indent
```
Reference: [git-scm](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project)