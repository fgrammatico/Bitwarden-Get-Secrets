# Ansible Role: Bitwarden SSH Key Management

This Ansible role manages SSH keys using Bitwarden. It ensures the `.ssh` directory exists, retrieves an SSH key from Bitwarden, and saves it to a file.

## Requirements

- Ansible 2.9+
- Bitwarden CLI (`bws`) installed and configured
- Environment variable `BWS_ACCESS_TOKEN` set with a valid Bitwarden session token

## Role Variables

The following variables can be configured in `defaults/main.yml` or overridden in your playbook:

- `home_dir`: The home directory of the user. Default is `{{ lookup('env', 'HOME') }}`.
- `ssh_directory`: The directory where SSH keys are stored. Default is `.ssh`.
- `user`: The user who owns the SSH directory and keys. Default is `{{ lookup('env', 'USER') }}`.
- `ssh_key_name`: The name of the SSH key file. Default is `id_rsa`.

## Usage

Example playbook to use this role:

```yaml
---
- hosts: all
  roles:
    - role: bitwarden-ssh-key-management
      vars:
        home_dir: "/home/myuser"
        ssh_directory: ".ssh"
        user: "myuser"
        ssh_key_name: "id_rsa"