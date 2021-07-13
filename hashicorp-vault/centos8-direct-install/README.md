# CentOS 8 Vault Install Using Ansible

The below install steps are taken from the HashiCorp "Getting Started with Vault" guide.

### Ansible Playbook

*This playbook is meant to be run using the `--ask-become-pass` flag*

```yaml
---
- name: Configure Vault
  hosts: dev-box
  become: yes
  tasks:
     - name: Install Yum Utils
       yum:
         name: yum-utils
         state: present
     - name: Add HashiCorp Repo
       command: "sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo"
     - name: Install Vault
       yum:
         name: vault
         state: present
```

The following command will execute a Vault installation using Ansible

```bash
user@hostname:~$ ansible-playbook --ask-become-pass centos8-vault-direct-install.yaml
```
