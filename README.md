# KodeKloud Projects

This repository contains my hands-on practice labs from **KodeKloud**, focused on:

- Linux administration
- Git workflows
- Ansible automation
- DevOps fundamentals

All labs are documented with:
- Task descriptions
- Commands used
- Explanations (WHY)
- Verification steps

---

## Linux Level 2 – Overview

All **Linux Level 2** tasks are solved using **Ansible**.
Each KodeKloud question is implemented as a **self-contained folder**, making it easy to
understand, run, and verify each task independently.

The focus of this repository is **learning and clarity**, not premature optimization.

---

## Repository Structure

Each Linux Level 2 question has its own directory containing:
- The Ansible playbook
- Inventory
- Variables (if needed)
- Documentation
- Verification steps

```text
linux_level-2/
├── q01_create_cron_job/
│   ├── README.md       # Task description and explanation (WHY)
│   ├── inventory.ini   # Target servers for this task
│   ├── playbook.yml    # Ansible solution
│   ├── vars.yml        # Task-specific variables
│   └── verify.md       # Verification steps
├── q02_linux_banner/
│   └── ...
├── q03_collaborative_directories/
│   └── ...
└── README.md
