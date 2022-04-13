# GitHub Issues Git Notes

[Git Notes]: https://git-scm.com/docs/git-notes
[issue-related trigger event]: https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#issues

This repository contains a GitHub Actions workflow that takes the GitHub Issues
associated with the GitHub repository (backed by the GitHub database not the Git
objects) and backs the JSON up in the Git repository's [Git Notes]. The workflow
runs on every issue-related trigger event.

The workflow uses the GitHub API to fetch the GitHub Issues. It pushes the notes
back to the GitHub repository using `git push origin refs/notes/*` and with the
GitHub Actions Git identity.

The note is added to the `main` branch, which means to the branche's tip commit.
If the workflow runs multiple times for the same commit, it will update the note
for that commit.

The Git notes can be fetched locally by using `git fetch` with the `notes` ref:
`git fetch origin "refs/notes/*:refs/notes/*"`.

To view notes for the `main` branch, run the Git `log` command with `%N` format:
`git log --pretty=format:"%ai%n  %H%n  %s%n  %N%n" --show-notes main`.

## To-Do

### Verify running twice for the same commit causes the note to update not fail

It likely won't until I add `--force` to the `git notes add` command.

### Consider a two-way sync / diff option where changes to Git Notes sync back

This would be significantly more complex, but it could be useful. However, all
of the changes done outside of GitHub and transferred back to the GitHub Issues
by the workflow would be authored by the GitHub Actions service account and not
the pusher as the workflow, while cognizant of their Git identity, does not have
the ability to impersonate them in order to effect these changes.
