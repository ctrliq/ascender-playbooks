# Contributing to Ascender Playbooks

Thanks for your interest in contributing to Ascender Playbooks. This document covers the
development setup, testing, and pull request guidelines.

## Development setup

Fork and clone the repository:

```bash
git clone https://github.com/<your-user>/ascender-playbooks.git
cd ascender-playbooks
```

Playbooks here are meant to run unmodified as Ascender job templates, so
behaviour should be exposed through variables rather than edits.

## Running tests

Lint before opening a PR, and run against a disposable host:

```bash
ansible-lint *.yml
ansible-playbook -i inventory --check patching.yml
```

New playbooks should target `all`, declare their tunables under `vars` with
sensible defaults, and document each one in the README.


## Making changes

### Branching

Create a feature branch from `main`:

```bash
git checkout -b my-feature main
```

### Commit messages

Write clear, concise commit messages:

```
Short summary (under 72 characters)

Longer description of what changed and why, if needed.
```

## Submitting a PR

1. Make sure the checks above pass locally.
2. One logical change per PR. Do not bundle unrelated fixes.
3. Target the `main` branch.
4. Explain what changed and why in the PR description.

## Reporting issues

Open an issue at
[github.com/ctrliq/ascender-playbooks/issues](https://github.com/ctrliq/ascender-playbooks/issues).
Include the version you are running and the steps that reproduce the problem.

For security vulnerabilities, follow [SECURITY.md](./SECURITY.md) instead of
opening a public issue.
