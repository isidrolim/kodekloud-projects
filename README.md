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

Each KodeKloud question is implemented as a **self-contained directory**, containing:
- The Ansible playbook
- Inventory for the task
- Task-specific variables (if needed)
- Documentation
- Verification steps

This structure mirrors how KodeKloud presents problems and prioritizes **clarity and learning**
over premature optimization.

---

## Repository Structure

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
