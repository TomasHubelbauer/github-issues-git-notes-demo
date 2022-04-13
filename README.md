# GitHub Issues Git Notes

This repository contains a prototype GitHub Actions workflow that takes the
GitHub Issues associated with the repository (but backed by the GitHub database
and not the Git repository itself) and backs them up in the Git repository's
[Git Notes](https://git-scm.com/docs/git-notes) every time the issues change.

## To-Do

### Make the workflow script push the change back to the GitHub repository

### Consider a two-way sync / diff option where changes to Git Notes sync back

This would be significantly more complex, but it could be useful. However, all
of the changes done outside of GitHub and transferred back to the GitHub Issues
by the workflow would be authored by the GitHub Actions service account and not
the pusher as the workflow, while cognizant of their Git identity, does not have
the ability to impersonate them in order to effect these changes.
