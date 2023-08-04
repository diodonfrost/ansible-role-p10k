Ansible Role: p10k
==================

[![molecule](https://github.com/diodonfrost/ansible-role-p10k/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-p10k/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.p10k-660198.svg)](https://galaxy.ansible.com/diodonfrost/p10k)

Ansible role that installs [powerlevel10k](https://github.com/romkatv/powerlevel10k), Powerlevel10k is a theme for Zsh. It emphasizes speed, flexibility and out-of-the-box experience.

Requirements
------------

None.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
---
# defaults file for ansible-role-p10k

# Powerlevel10k Git repository url
p10k_repository_url: 'https://github.com/romkatv/powerlevel10k.git'

# Install p10k for the following linux users
# Default: the linux user running Ansible
p10k_users:
  - "{{ ansible_user_id }}"

# Zsh plugin used, zsh, ohmyzsh, prezto, Zim, etc..
# All plugin names can be found here https://github.com/romkatv/powerlevel10k#installation
zsh_plugin: zsh

# Setup p10k theme to use
# Valid values: lean, classic, rainbow, pure
p10k_prompt_style: "classic"

# Show current time
# Valid values: no, 24-hour, 12-hour
p10k_prompt_time: "24-hour"

# Prompt sperator
# Valid values: angled, vertical, slanted, round
p10k_prompt_separator: "angled"

# Prompt heads
# Valid values: sharp, blurred, slanted, round
p10k_prompt_head: "sharp"

# Prompt tails
# Valid values: flat, blurred, sharp, slanted, round
p10k_prompt_tails: flat

# Terminal prompt height
# Valid values: one-line, two-lines
p10k_prompt_height: two-lines

# Prompt connection, only used if "p10k_prompt_height" value is "two-lines"
# Valid values: disconnected, dotted, solid
p10k_prompt_connection: disconnected

# Prompt connection color, only used if
# "p10k_prompt_connection" value is "dotted" or "solid"
# or "p10k_prompt_frame" is not "no"
# Valid values: lightest, light, dark, darkest, black, white, green, blue
p10k_prompt_connection_color: "dark"

# Prompt frame connection
# Valid values: no, left, right, full
p10k_prompt_frame: left

# Sparse prompt with an empty line before promp
# Valid values: compact, sparse
p10k_prompt_spacing: compact

# Terminal flow
# Valid values: concise, fluent
p10k_prompt_flow: concise

# Enable transient prompt
# Valid values: yes, no
p10k_transient_prompt: "no"
```

Dependencies
------------

None.

Example Playbook
----------------

Install powerlevel10K:

    - hosts: servers
      roles:
         - { role: diodonfrost.p10k }

Install powerlevel10k for ohmyzsh:

    - hosts: servers
      roles:
         - { role: diodonfrost.omyzsh, ohmyzsh_theme: powerlevel10k/powerlevel10k }
         - { role: diodonfrost.p10k, zsh_plugin: ohmyzsh }

Local Testing
-------------

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://www.virtualbox.org/) (if you test windows system)
* [Vagrant](https://www.vagrantup.com/downloads.html) (if you test windows system)

Testing with Docker
-------------------

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 22.04
molecule test

# Test ansible role with ubuntu 20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test

# Create ubuntu 22.04 instance
molecule create

# Apply role on ubuntu 22.04 instance
molecule converge

# Launch tests on ubuntu 22.04 instance
molecule verify
```

Testing with Vagrant and Libvirt
--------------------------------

```shell
# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with OpenBSD
molecule test -s openbsd
```

License
-------

Apache 2

Author Information
------------------

This role was created in 2021 by diodonfrost.
