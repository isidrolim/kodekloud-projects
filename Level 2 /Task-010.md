# AWS Level 2 – Task 010: Enabling Public Access to an RDS Instance

## Scenario
The Nautilus Development Team needs to allow an external partner to connect remotely to an existing MySQL RDS database.

The existing RDS instance `xfusion-rds` is currently private and must be made publicly accessible on the default MySQL port `3306`.

## Requirements

- **Region:** `us-east-1`
- **Existing RDS Instance:** `xfusion-rds`
- **Publicly Accessible:** Yes
- **Database Port:** TCP `3306`
- Ensure the RDS security group permits the required external access

## Steps

### 1. Locate the Existing RDS Instance

Go to:

`AWS Console → RDS → Databases → xfusion-rds`

Verify that the database exists and check its current configuration.

---

### 2. Enable Public Access

Select:

`xfusion-rds → Modify`

Scroll to **Connectivity**.

Under **Additional configuration / Public access**, change:

`Publicly accessible → Yes`

Keep the database port as:

`3306`

Continue to the modification summary.

Select:

`Apply immediately`

Then click:

`Modify DB instance`

> Applying immediately is appropriate for this lab. In production, modifications should be assessed for impact and normally scheduled through an approved maintenance/change window when appropriate.

---

### 3. Configure the RDS Security Group

While the modification is being applied, go to:

`RDS → Databases → xfusion-rds → Connectivity & security`

Locate the VPC security group attached to the database and open it.

Go to:

`Inbound rules → Edit inbound rules`

Add or verify:

| Type | Protocol | Port | Source |
|---|---|---|---|
| MySQL/Aurora | TCP | 3306 | Required external source |

For this lab, if unrestricted public access is explicitly required, use:

`0.0.0.0/0`

Save the inbound rules.

> In production, never expose MySQL to the entire internet unless there is an exceptional requirement. Restrict TCP/3306 to the external partner's known public IP/CIDR, or preferably use private connectivity such as VPN or another controlled access path.

---

### 4. Wait for the RDS Modification

Return to:

`RDS → Databases → xfusion-rds`

Wait until the database status returns to:

`Available`

Do not submit the task while the instance is still:

`Modifying`

---

## Validation

Open:

`xfusion-rds → Connectivity & security`

Verify:

- **Status:** Available
- **Publicly accessible:** Yes
- **Port:** 3306
- A database endpoint is available
- The attached security group permits TCP/3306 from the required source

The resulting access path is:

`External Client → Internet → RDS Endpoint:3306 → Security Group → xfusion-rds`

## Result

The existing `xfusion-rds` MySQL RDS instance was modified to allow public connectivity on the default MySQL port `3306`.

The security group was configured to permit the required database traffic, and the RDS instance returned to the `Available` state after the modification.

**Task Status:** ✅ Completed
