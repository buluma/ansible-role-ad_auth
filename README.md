# [Ansible role ad_auth](#ad_auth)

Bind a system to Active Directory.

|GitHub|Version|Issues|Pull Requests|
|------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-ad_auth/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-ad_auth/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-ad_auth.svg)](https://github.com/buluma/ansible-role-ad_auth/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-ad_auth.svg)](https://github.com/buluma/ansible-role-ad_auth/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-ad_auth.svg)](https://github.com/buluma/ansible-role-ad_auth/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-ad_auth/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.ad_auth
      ad_auth_registration_username: my_username
      ad_auth_registration_password: my_password
      ad_auth_ou: ou=Nerds,ou=Staff
      ad_auth_server: my_server.example.com
      ad_auth_domain: my_domain.local
      ad_auth_join: no
      ad_auth_simple_allow_users:
        - my_user_1
        - my_user_2
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-ad_auth/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no
  vars:
    python_pip_modules:
      - name: pexpect

  roles:
    - role: buluma.bootstrap
    - role: buluma.epel
    - role: buluma.python_pip
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-ad_auth/blob/master/defaults/main.yml):

```yaml
---
# defaults file for ad_auth

# The username to register to AD, for example: "bind_user".
ad_auth_registration_username: "unset"

# The password to register to AD, for example: "MyPaSsWoRd".
ad_auth_registration_password: "unset"

# The OU to search in, for example: "ou=Nerds,ou=Staff".
ad_auth_ou: "unset"

# The server to bind to, for example: "ad.example.com".
ad_auth_server: "unset"

# The domain to use for SSSD configuration, for example: "example.com".
ad_auth_domain: "usnet.local"

# Should this role try to bind to the AD server?
# (This can be unset for automated testing)
ad_auth_join: yes

# To limit selected users to login, fill this list with users that are
# allowed to login:
# ad_auth_simple_allow_users:
#   - my_user_1
#   - my_user_2
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-ad_auth/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Build Status GitHub](https://github.com/buluma/ansible-role-epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-epel/actions)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-epel.svg)](https://github.com/shadowwalker/ansible-role-epel)|
|[buluma.python_pip](https://galaxy.ansible.com/buluma/python_pip)|[![Build Status GitHub](https://github.com/buluma/ansible-role-python_pip/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-python_pip/actions)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-python_pip.svg)](https://github.com/shadowwalker/ansible-role-python_pip)|

## [Dependencies](#dependencies)

Most roles require some kind of preparation, this is done in `molecule/default/prepare.yml`. This role has a "hard" dependency on the following roles:

- {'src': 'buluma.python_pip', 'version': '1.0.7', 'name': 'buluma.python_pip'}

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-ad_auth/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|all|
|[Fedora](https://hub.docker.com/repository/docker/buluma/fedora/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-ad_auth/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-ad_auth/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-ad_auth/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)


### [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
