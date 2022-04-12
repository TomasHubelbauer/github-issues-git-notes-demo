# GitHub Issues Git Notes

In this repository, I am going to prototype a script (or maybe a GitHub Actions
action) which takes the GitHub issues associated with the GitHub repository and
stores them in Git Notes of the Git repository.

This way, one can build automation and systems based on GitHub issues without
worrying about portability, because the issues while stored separately from the
repository by GitHub, will also by automatically backed up to Git Notes by this
script / GitHub Actions action on any `issues` workflow event.

## To-Do

### Prototype the script

Use the integration PAT to pull the issues from the GitHub API and store them in
GitHub Notes. Use the Git client configured with the GitHub Actions service
account Git identity to push the Git Notes back to the GitHub repository from
the GitHub Actions workflow. Run on all events in the `issues` trigger scope.

### Consider a two-way sync / diff option where changes to Git Notes sync back

This would be significantly more complex, but it could be useful, too.
