# [swap](#swap)

Swap file and swap management for Linux.

|GitHub|GitLab|Quality|Downloads|Version|Issues|Pull Requests|
|------|------|-------|---------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-swap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-swap/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-swap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-swap)|[![quality](https://img.shields.io/ansible/quality/54987)](https://galaxy.ansible.com/buluma/swap)|[![downloads](https://img.shields.io/ansible/role/d/54987)](https://galaxy.ansible.com/buluma/swap)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-swap.svg)](https://github.com/buluma/ansible-role-swap/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-swap.svg)](https://github.com/buluma/ansible-role-swap/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-swap.svg)](https://github.com/buluma/ansible-role-swap/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-swap/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true

  vars:
    swap_file_size_mb: '256'
    swap_test_mode: true
    swap_swappiness: 60
    swap_files:
      - path: /my.swap
        size: 1024

  roles:
    - role: buluma.swap
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-swap/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: buluma.bootstrap
    - role: buluma.sysctl
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-swap/blob/master/defaults/main.yml):

```yaml
---

# The location of the swap file on the server.
swap_file_path: /swapfile

# How large (in mebibytes) to make the swap file.
swap_file_size_mb: '512'

# The vm.swappiness value to be configured in sysconfig.
swap_swappiness: '60'

# Controls the tendency of the kernel to reclaim the memory used for caching of VFS caches, versus pagecache and swap
swap_vfs_cache_pressure: '50'

# If you wish to remove your swapfile, and disable swap, set this to absent.
swap_file_state: present

# The command used to create the swap file.
swap_file_create_command: "dd if=/dev/zero of={{ swap_file_path }} bs=1M count={{ swap_file_size_mb }}"

swap_test_mode: false
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-swap/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.sysctl](https://galaxy.ansible.com/buluma/sysctl)|[![Build Status GitHub](https://github.com/buluma/ansible-role-sysctl/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-sysctl/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-sysctl/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-sysctl)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-swap/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|all|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|
|[Kali](https://hub.docker.com/repository/docker/buluma/kali/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-swap/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-swap/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-swap/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

Please consider [sponsoring me](https://github.com/sponsors/buluma).

### [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
