
---

# 6️⃣ `README.md` (documentation for GitHub)

📄 `q01_create_cron_job/README.md`

```md
# Question 01 – Create a Cron Job

## Task Description
The Nautilus system administrators want to automate routine tasks using cron.
As a sample task, a cron job must be configured on all Nautilus application servers.

Requirements:
- Install the `cronie` package
- Ensure the `crond` service is running
- Create a cron job for the `root` user
- The cron job must run every 5 minutes
- The job should write `hello` to `/tmp/cron_text`

All steps must be implemented using Ansible.

---

## Why Ansible?
Ansible is used to:
- Apply the same configuration across multiple servers
- Ensure consistency and idempotency
- Avoid manual configuration errors
- Follow Infrastructure as Code (IaC) principles

---

## Files Overview

```text
q01_create_cron_job/
├── inventory.ini    # Target servers
├── vars.yml         # Task-specific variables
├── playbook.yml     # Ansible automation
├── verify.md        # Verification steps
└── README.md        # Documentation


## How to Run

```bash
ansible-playbook -i inventory.ini playbook.yml