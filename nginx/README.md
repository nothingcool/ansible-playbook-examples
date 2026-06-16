# Ansible Nginx Installation Playbook

## Overview

This project provides a simple Ansible playbook to automate the installation and initial setup of Nginx Server on Red Hat Enterprise Linux (RHEL) systems.

The playbook performs the following tasks:

- Installs the Nginx Server package
- Enables the nginx service at boot time
- Starts the Nginx service
- Verifies that the Nginx service is running

This example is intended for learning, demonstration, and basic automation reference.

## Supported Platforms

- Red Hat Enterprise Linux 8
- Red Hat Enterprise Linux 9
- Rocky Linux 8/9
- AlmaLinux 8/9

## Prerequisites

Before running this playbook, ensure the following requirements are met:

- Ansible is installed on the control node
- SSH access to the target server is available
- The target server has sudo/root privileges
- Python is available on the managed node
- The target server has access to the required package repositories

## Repository Structure

```text
.
├── inventory
├── install_nginx.yml
└── README.md
```

## Inventory Example

```ini
[nginx_servers]
nginx01 ansible_host=192.168.1.101
nginx02 ansible_host=192.168.1.102
```

## Playbook Usage

Run the playbook using the following command:

```bash
ansible-playbook -i inventory install_nginx.yml
```

## Verification

After the playbook completes, verify the Nginx installation:

```bash
Browse URL http://<server_ip:<port_number>
```

Check the Nginx service status:

```bash
systemctl status nginx
```

## Expected Result

After successful execution:

- Nginx Server is installed
- The `Nginx ` service is enabled
- The `Nginx ` service is started
- The server is ready for further Nginx configuration

## Example Playbook

```yaml
---
- name: Install Nginx Server
  hosts: nginx_servers
  become: true

  tasks:
    - name: Install Nginx Server package
      ansible.builtin.dnf:
        name: nginx
        state: present

    - name: Enable Nginx service
      ansible.builtin.systemd:
        name: nginx
        enabled: true

    - name: Start Nginx service
      ansible.builtin.systemd:
        name: nginx
        state: started

    - name: Verify Nginx service is running
      ansible.builtin.command: systemctl is-active nginx
      register: nginx_status
      changed_when: false

    - name: Display Nginx status
      ansible.builtin.debug:
        msg: "Nginx service status: {{ nginx_status.stdout }}"
```

## License

This project is provided as-is for educational and demonstration purposes.
