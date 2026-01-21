# KodeKloud Projects

This repository contains my hands-on practice labs from **KodeKloud**, focused on:

- Linux administration
- Git workflows
- Ansible automation
- DevOps fundamentals

All labs are organized by technology and documented with:
- Task descriptions
- Commands used
- Explanations (WHY)
- Verification steps

---

## Repository Structure

All Linux Level 2 labs are implemented using **Ansible** and organized in a reusable,
production-style layout.

```text
linux_level-2/
├── ansible.cfg              # Ansible configuration
├── inventory/
│   └── inventory.ini        # Shared inventory for Nautilus servers
├── group_vars/
│   └── nautilus_app_servers.yml
├── host_vars/               # Vault-encrypted sudo credentials
│   ├── stapp01.yml
│   ├── stapp02.yml
│   └── stapp03.yml
├── playbooks/
│   ├── bootstrap.yml        # Initial SSH bootstrap (one-time)
│   └── q01_create-a-cronjob.yml
├── roles/
│   └── q01_cronjob/
│       ├── tasks/
│       │   └── main.yml
│       └── README.md        # Task description, WHY, and verification
└── README.md
