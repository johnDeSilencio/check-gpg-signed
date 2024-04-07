# check-gpg-signed

`check-gpg-signed` is a custom [`pre-commit`](https://pre-commit.com/) hook that does two things:

1. Checks if the most recent commit (pointed to by `HEAD`) has been signed with your private GPG key
2. If it hasn't been signed with your private GPG key, signs the commit by running `git commit -S --amend`

## Installation & Usage

This project assumes that you have already installed [`pre-commit`](https://pre-commit.com/) and initialized the `.pre-commit-config.yaml` file for your repository.

Copy the following into your `.pre-commit-config.yaml` file:

```yaml
- repo: https://github.com/johnDeSilencio/check-gpg-signed
  rev: v0.0.5
  hooks:
  - id: check-gpg-signed
    stages: [post-commit, post-rewrite]
```

Run the following command to install `pre-commit` into your [`post-commit`]() and [`post-rewrite`]() git hooks:

```none
$> pre-commit install --hook-type post-commit --hook-type post-rewrite
```

Once you've finished these steps, any time you make a commit in this repository (even from a `git rebase`), this hook will run, ensuring that your commit is signed.
