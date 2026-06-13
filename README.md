# Ansible Playbook Examples

A collection of Ansible playbooks demonstrating common system administration, database, middleware, and infrastructure automation tasks.

The goal of this repository is to provide practical examples that can be used for learning, proof-of-concept activities, and as a starting point for enterprise automation projects.

## Repository Structure

| Category | Description |
|----------|-------------|
| mysql | Install and configure MySQL Server |
| postgresql | PostgreSQL installation and management |
| redis | Redis installation and configuration |
| apache | Apache HTTP Server deployment |
| nginx | NGINX installation and configuration |
| linux | Linux administration and automation examples |
| openshift | OpenShift administration playbooks |
| kubernetes | Kubernetes automation examples |
| vmware | VMware automation playbooks |
| oracle | Oracle database automation examples |

## Available Examples

### Database

| Example | Description |
|---------|-------------|
| [MySQL Installation](./mysql) | Install and start MySQL Server on RHEL-based systems |

## Requirements

- Ansible 2.12 or later
- SSH access to managed hosts
- Python installed on managed nodes
- Appropriate privileges such as sudo or root access

## Usage

Clone the repository:

```bash
git clone https://github.com/<your-account>/ansible-playbook-examples.git
cd ansible-playbook-examples
```

Navigate to the desired example directory and follow the instructions in its README file.

Example:

```bash
cd mysql
ansible-playbook -i inventory install_mysql.yml
```

## Repository Objectives

This repository focuses on:

- Infrastructure automation
- Configuration management
- Database administration
- Middleware deployment
- Platform engineering
- DevOps automation
- Red Hat Enterprise Linux administration

## Contributing

Contributions, improvements, and suggestions are welcome.

If you find an issue or have an enhancement, feel free to open an issue or submit a pull request.

## License

This repository is provided for educational and demonstration purposes.
