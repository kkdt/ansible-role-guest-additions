# Ansile Role: virtualbox-guest-additions

> Install VirtualBox Guest Additions.

## Requirements

1. The system must be configured with a YUM repository.
1. The control system must have VirtualBox installed along with the `VBoxGuestAdditions.iso` file

## Role Variables

The default Ansible variables are in [defaults](defaults/main.yml). 

```yaml
VBoxGuestAdditions_iso_local: The full path to the VBoxGuestAdditions.iso file on the control system
VBoxGuestAdditions_iso_remote: The location to copy the VBoxGuestAdditions.iso file on the remote system
VBoxGuestAdditions_mnt: The mount location on the remote system
```

## Dependencies

None

## Ansible Galaxy 'requirements.yml' Configurations


```yaml
# Git/HTTPS
- name: kkdt.vagrant
  src: git+https://github.com/kkdt/ansible-role-guest-additions.git
  scm: git
  version: master

# Git/SSH
- name: kddt.vagrant
  src: git+git@github.com:kkdt/ansible-role-guest-additions.git
  scm: git
  version: master

# Git/File
- name: kddt.vagrant
  src: git+file:///home/kkdt/ansible-role-guest-additions
  scm: git
  version: master
```

```shell
ansible-galaxy role install --role-file requirements.yml --roles-path ~/.ansible/roles --force -vvv
```

### Playbook

```yaml
- hosts: localhost
  connection: local
  roles:
    - role: kkdt.vagrant
      vars:
        VBoxGuestAdditions_iso_local: /Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso
        VBoxGuestAdditions_iso_remote: /tmp/VBoxGuestAdditions.iso
        VBoxGuestAdditions_mnt: /mnt/iso
```