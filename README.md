# [Ansible role swap](#ansible-role-swap)

Configure swap files on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-swap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-swap/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-swap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-swap)|[![downloads](https://img.shields.io/ansible/role/d/buluma/swap)](https://galaxy.ansible.com/buluma/swap)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-swap.svg)](https://github.com/buluma/ansible-role-swap/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-swap/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: buluma.swap
      swap_files:
        - path: /my.swap
          size: 1024
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-swap/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: false
  become: true

  roles:
    - role: buluma.bootstrap
    - role: buluma.sysctl
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-swap/blob/master/defaults/main.yml):

```yaml
---
# defaults file for swap

# Set the swappiness, 60 is default for Fedora 31.
swap_swappiness: 60

# A list of swap files to add. The list must container **path** (an absolute path to a file) and **size** (an integer in megabytes).
# swap_files:
#   - path: /my.swap
#     size: 1024

# You can disable swap if required.
swap_enabled: true
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

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-swap/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|all|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[opensuse](https://hub.docker.com/r/buluma/opensuse)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|
|[Kali](https://hub.docker.com/r/buluma/kalilinux)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-swap/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-swap/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

