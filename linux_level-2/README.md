# KodeKloud Linux Level 2 – Ansible Solutions

This repository contains Ansible-based solutions for KodeKloud Linux Level 2 labs.

## Structure
- inventory/        Shared infrastructure inventory
- group_vars/       Shared variables
- host_vars/        Vault-encrypted sudo credentials
- playbooks/        Per-question playbooks
- roles/            Reusable Ansible roles

## Question 01 – Create a Cron Job
Installs `cronie`, enables `crond`, and creates a root cron job that runs every 5 minutes.

### Run
```bash
ansible-playbook playbooks/q01_cronjob.yml --ask-vault-pass
