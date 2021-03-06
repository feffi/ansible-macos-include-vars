# ansible-include-vars

Ansible role to include custom YAML files from configured path(s).

[![Build Status](https://img.shields.io/travis/feffi/ansible-macos-include-vars.svg)](https://travis-ci.org/feffi/ansible-macos-include-vars) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-macos-include-vars/total.svg)](https://github.com/feffi/ansible-macos-include-vars) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-macos-include-vars.svg?style=social&label=Fork)](https://github.com/feffi/ansible-macos-include-vars) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-macos-include-vars.svg?style=social&label=Star)](https://github.com/feffi/ansible-macos-include-vars) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-macos-include-vars.svg?style=social&label=Watch)](https://github.com/feffi/ansible-macos-include-vars) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1) [![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/feffi/ansible-macos-include-vars/blob/master/LICENSE)

## Requirements

- Ansible 2.3

### ansible.cfg

```yaml
hash_behaviour = merge
```

## Install

Just add the role to your ``requirements.yml`` file:

```yaml
- src: https://github.com/feffi/ansible-include-vars.git
  name: ansible-include-vars
```

## Role Variables

All role based variables are listed below, along with default values:

```yaml
macos_include_vars:
  # List of local paths to search for YAML files that will be included as Ansible vars.
  paths:
    - "{{ inventory_dir }}/.secrets"

  # Extension of files to include.
  extensions:
    - "yml"

  # Exclude files matching this names
  excludes:
    - "requirements.yml"

  # Directory depth to used search for files
  # 1 = only files directly in include_vars_dir_paths
  depth: 1
```

## Dependencies

None.

## Example Playbook

```yaml
    - hosts: all
      vars:
        # Include custom vars from defined locations
        macos_include_vars: {
          paths: [
            "/Users/<USERNAME>/.secrets"
          ]
        }
      roles:
        - { role: ansible-include-vars }
```
