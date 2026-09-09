# AWS Level 2 – Task 009: Configuring a Private RDS Instance for Application Development

## Scenario
The Nautilus Development Team requires a private MySQL RDS instance for application development and testing. The database must use the AWS Free Tier configuration and remain inaccessible directly from the public internet.

## Requirements

- **Region:** `us-east-1`
- **DB Instance Identifier:** `xfusion-rds`
- **Creation Method:** Full configuration
- **Template:** Free tier
- **Engine:** MySQL
- **Engine Version:** `8.4.x`
- **Instance Class:** `db.t3.micro`
- **Storage Type:** General Purpose SSD (`gp2`)
- **Allocated Storage:** `20 GiB`
- **Storage Autoscaling:** Enabled
- **Maximum Storage Threshold:** `22 GiB`
- **Public Access:** No
- Instance must reach the **Available** state

## Steps

### 1. Create the RDS Database

Go to:

`AWS Console → RDS → Databases → Create database`

Under **Choose a database creation method**:

- Select **Full configuration**

Under **Engine options**:

- **Engine type:** MySQL
- **Engine version:** Select a `MySQL 8.4.x` version

Under **Templates**:

- Select **Free tier**

---

### 2. Configure the Database

Under **Settings**:

- **DB instance identifier:** `xfusion-rds`
- Configure the master username and password as required by the lab

Keep the credentials available until the task is completed.

---

### 3. Configure the Instance Class

Under **Instance configuration**, select:

- **DB instance class:** `db.t3.micro`

---

### 4. Configure Storage

Under **Storage**:

- **Storage type:** General Purpose SSD (`gp2`)
- **Allocated storage:** `20 GiB`

Under **Additional storage configuration**:

- Enable **Storage autoscaling**
- **Maximum storage threshold:** `22 GiB`

Keep the remaining storage settings at their defaults.

---

### 5. Configure Private Connectivity

Under **Connectivity**:

- Select the appropriate/default VPC
- Keep the appropriate DB subnet group
- **Public access:** `No`

Keep the remaining networking settings at their defaults unless the lab requires otherwise.

This ensures the RDS instance does not receive a publicly reachable database endpoint.

---

### 6. Review and Create

Before creating the database, verify:

| Setting | Required Value |
|---|---|
| DB Identifier | `xfusion-rds` |
| Engine | MySQL |
| Version | `8.4.x` |
| Instance Class | `db.t3.micro` |
| Storage | `gp2` |
| Allocated Storage | `20 GiB` |
| Storage Autoscaling | Enabled |
| Maximum Storage | `22 GiB` |
| Public Access | No |

Click:

`Create database`

---

## Validation

Go to:

`RDS → Databases → xfusion-rds`

Wait until the status changes from:

`Creating → Available`

Verify the final configuration:

- **Status:** Available
- **Engine:** MySQL 8.4.x
- **DB class:** db.t3.micro
- **Allocated storage:** 20 GiB
- **Storage type:** gp2
- **Maximum storage threshold:** 22 GiB
- **Publicly accessible:** No

The final architecture is:

`Application / Private VPC Resources → Private RDS Endpoint → xfusion-rds (MySQL)`

## Result

A private MySQL RDS instance named `xfusion-rds` was successfully provisioned using the required Free Tier configuration, with 20 GiB of `gp2` storage and storage autoscaling configured up to 22 GiB.

The database is not publicly accessible and is ready for use once its status reaches **Available**.

**Task Status:** ✅ Completed
