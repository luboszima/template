# Template

A small repository template for me and for others who want an easy baseline for new projects.
It is based on patterns I liked while working across several companies: pin the tools, keep
common commands in one place, check code before pushing, and keep dependencies updated through
reviewable PRs.

## Tools

### mise

`mise` pins tool versions for the repository. This avoids using whatever version is installed
globally and helps keep the project on versions that were already tested and accepted.

### Task

`Taskfile.yml` keeps important project commands in one place. This helps new developers find
how to build, test, validate, or maintain the project even when older docs are out of date.
Run `task --list` to see the available commands.

### prek

`prek` runs the `.pre-commit-config.yaml` hooks. These hooks help standardize formatting and
catch simple problems before code is committed or pushed.

### Renovate

Renovate opens dependency update PRs for tools and libraries. This template auto-merges all
GitHub Actions, mise, and pre-commit hook updates, but that is intentionally aggressive and
is not a good default for most repositories. Real projects should usually use a stricter
policy, such as manual review, patch-only auto-merge, passing checks, and cooldown periods
for critical tools or application libraries.

### GitHub Actions

GitHub Actions runs the same `prek run --all-files` check on pull requests and pushes to
`main`, so validation does not depend only on a local machine.

## Usage

Install `mise` first. See the
[mise getting started guide](https://mise.jdx.dev/getting-started.html).

Install the configured tools:

```sh
mise install
```

Run all hooks locally:

```sh
task prek
```
