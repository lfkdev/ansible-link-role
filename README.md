# Ansible-Link Role

Role to install and configure [Ansible-Link](https://github.com/lfkdev/ansible-link). For now only the debian family is supported.

## Requirements

None, simply add the role to your ansible-node playbook
```yaml
- hosts: my-ansible-node
  roles:
    - role: lfkdev.ansible_link
```
Ansible-Link needs access to your playbooks (e.g. `/etc/ansible`).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

---
```yaml
ansible_link_version: "1.2.5"
```
The version of Ansible Link to install. This should match a release version from the Ansible Link GitHub releases.

```yaml
ansible_link_dir: "/srv/ansible-link"
```

The directory where Ansible Link will be installed.

```yaml
ansible_link_venv: "{{ ansible_link_dir }}/.venv"
```
The path to the Python virtual environment for Ansible Link.

```yaml
ansible_link_user: root
ansible_link_group: root
```
The user and group under which Ansible Link will run. (make sure this user can run your ansible-playbooks)

```yaml
ansible_link_webhook_url: ""
ansible_link_webhook_type: "slack"
ansible_link_webhook_timeout: "5"
```
Configuration for webhook notifications. Set ansible_link_webhook_url to enable notifications.

```yaml
ansible_link_host: "127.0.0.1"
ansible_link_port: "5001"
```
The host and port on which Ansible Link will listen.

```yaml
ansible_link_ansible_output: false
ansible_link_omit_event_data: false
ansible_link_only_failed_event_data: false
```
Configure Ansible output and event data handling.

```yaml
ansible_link_playbook_dir: "/etc/ansible/"
ansible_link_inventory_file: "/etc/ansible/environments/hosts"
```
The directory containing Ansible playbooks and the inventory file path.

```yaml
ansible_link_job_storage_dir: "/var/lib/ansible-link/job-storage"
```
The directory where Ansible Link will store job data.

```yaml
ansible_link_log_level: "INFO"
```
Set the log level for Ansible Link.

```yaml
ansible_link_playbook_whitelist: []
```
A list of playbooks that are allowed to be executed. An empty list allows all playbooks.