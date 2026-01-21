# Question 01 – Create a Cron Job (Ansible)

## Task Description
The Nautilus system administrators want to automate daily operational tasks using cron.
As a first step, a sample cron job must be configured on all Nautilus application servers.

The requirements are:
- Install the `cronie` package
- Ensure the `crond` service is running
- Add a cron job for the `root` user that runs every 5 minutes
- The cron job should write `hello` to `/tmp/cron_text`

All steps must be implemented using **Ansible**.

---

## Why Ansible?
This task is implemented using Ansible to:
- Ensure consistency across multiple servers
- Avoid manual configuration drift
- Make the task repeatable and idempotent
- Follow infrastructure-as-code best practices

Ansible allows us to describe the *desired state* instead of running imperative shell commands.

---

## Ansible Role Overview

This role performs the following actions:
1. Installs the cron package (`cronie`)
2. Starts and enables the cron service (`crond`)
3. Creates the required cron job using the Ansible `cron` module

The role is designed to be reusable and idempotent.

---

## Files Involved

```text
roles/q01_cronjob/
├── tasks/
│   └── main.yml
└── README.md
