# Ascender Playbooks

[![CI](https://github.com/ctrliq/ascender-playbooks/actions/workflows/ci.yml/badge.svg)](https://github.com/ctrliq/ascender-playbooks/actions/workflows/ci.yml)
[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](./LICENSE.md)
[![Ansible](https://img.shields.io/badge/ansible--core-%3E%3D2.16-blue.svg)](https://github.com/ansible/ansible)

A small set of ready-to-run Ansible playbooks for use as job templates in [Ascender](https://github.com/ctrliq/ascender). Each one is self-contained, targets `all` hosts, and exposes its behaviour through variables you can override from a job template without editing it.

## Requirements

- `ansible-core` 2.16 or newer, or an Ascender job template
- Enterprise Linux managed hosts, for the patching and SELinux playbooks
- Privilege escalation on the managed hosts, since both playbooks use `become`

## Using the playbooks

Point an Ascender project at this repository and add a job template for the playbook you want. To run one directly:

```bash
ansible-playbook -i inventory patching.yml -e update_kernel=false
```

## Configuration

Each playbook reads variables you can set on the job template:

- `security_updates`: restrict patching to security errata only, default `false`
- `update_kernel`: allow kernel packages to be updated, default `true`
- `reboot_kernel`: reboot after a kernel update, default `true`
- `selinux_state`: target state, default `enforcing`
- `selinux_policy`: target policy, default `targeted`
- `selinux_reboot`: reboot when a relabel requires it, default `true`

## Included content

- [`gather_facts.yml`](./gather_facts.yml): collects package and service facts, skipping Windows
- [`patching.yml`](./patching.yml): applies updates on Enterprise Linux hosts
- [`selinux.yml`](./selinux.yml): enforces a target SELinux state and policy

## The Ascender ecosystem

| Repository | Description |
| ---------- | ----------- |
| [ascender](https://github.com/ctrliq/ascender) | The platform itself: web UI, REST API, and task engine |
| [ascender-install](https://github.com/ctrliq/ascender-install) | Installer for Ascender and Ledger, with Galaxy Proxy support |
| [ascender-k8s-install](https://github.com/ctrliq/ascender-k8s-install) | Kubernetes installer for Ascender, Ledger, and React |
| [ascender-pro-install](https://github.com/ctrliq/ascender-pro-install) | Enhanced installer adding Reaqt, Registry, and Galaxy Proxy |
| [ascender-operator](https://github.com/ctrliq/ascender-operator) | Kubernetes operator that deploys and manages Ascender |
| [ascender-ee](https://github.com/ctrliq/ascender-ee) | Default execution environment image for Ascender jobs |
| [ascender-kit](https://github.com/ctrliq/ascender-kit) | The `ascender` command line client and Python API library |
| [ascender-collection](https://github.com/ctrliq/ascender-collection) | The `ctrliq.ascender` Ansible collection for a controller |
| [ascender-ledger](https://github.com/ctrliq/ascender-ledger) | Reporting tool for host facts and playbook changes |
| [ascender-galaxy-proxy](https://github.com/ctrliq/ascender-galaxy-proxy) | Caching proxy for Ansible Galaxy collection downloads |
| [ascender-playbooks](https://github.com/ctrliq/ascender-playbooks) | Example playbooks for use with Ascender |
## Contributing

- See [CONTRIBUTING.md](./CONTRIBUTING.md) for development setup, testing, and pull requests.
- Report bugs and suggest new playbooks via [GitHub Issues](https://github.com/ctrliq/ascender-playbooks/issues).
- For security vulnerabilities, follow [SECURITY.md](./SECURITY.md) rather than opening an issue.
- Join the [Ascender forum](https://forum.ascender-automation.org) to discuss development topics.

## License

Licensed under the **Apache License 2.0**. See [LICENSE.md](./LICENSE.md) and [COPYRIGHT.md](./COPYRIGHT.md).
