# Ansible MySQL Installation Playbook

## Overview

This project provides a simple Ansible playbook to automate the installation and initial setup of MySQL Server on Red Hat Enterprise Linux (RHEL) systems.

The playbook performs the following tasks:

- Installs the MySQL Server package
- Enables the MySQL service at boot time
- Starts the MySQL service
- Verifies that the MySQL service is running

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
├── install_mysql.yml
└── README.md
```

## Inventory Example

```ini
[mysql_servers]
db01 ansible_host=192.168.1.101
db02 ansible_host=192.168.1.102
```

## Playbook Usage

Run the playbook using the following command:

```bash
ansible-playbook -i inventory install_mysql.yml
```

## Verification

After the playbook completes, verify the MySQL installation:

```bash
mysql --version
```

Check the MySQL service status:

```bash
systemctl status mysqld
```

## Expected Result

After successful execution:

- MySQL Server is installed
- The `mysqld` service is enabled
- The `mysqld` service is started
- The server is ready for further MySQL configuration

## Example Playbook

```yaml
---
- name: Install MySQL Server
  hosts: mysql_servers
  become: true

  tasks:
    - name: Install MySQL Server package
      ansible.builtin.dnf:
        name: mysql-server
        state: present

    - name: Enable MySQL service
      ansible.builtin.systemd:
        name: mysqld
        enabled: true

    - name: Start MySQL service
      ansible.builtin.systemd:
        name: mysqld
        state: started

    - name: Verify MySQL service is running
      ansible.builtin.command: systemctl is-active mysqld
      register: mysql_status
      changed_when: false

    - name: Display MySQL status
      ansible.builtin.debug:
        msg: "MySQL service status: {{ mysql_status.stdout }}"
```

## Future Enhancements

Possible future improvements:

- Configure MySQL root password
- Secure MySQL installation
- Create databases automatically
- Create MySQL users and privileges
- Configure firewall rules
- Configure MySQL replication
- Add backup and restore automation

## License

This project is provided as-is for educational and demonstration purposes.
