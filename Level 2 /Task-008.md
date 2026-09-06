# AWS Level 2 – Task 008: Data Migration Between S3 Buckets Using AWS CLI

## Scenario
The Nautilus DevOps team needs to migrate all data from an existing S3 bucket to a new private S3 bucket using the AWS CLI.

## Requirements

- **Region:** `us-east-1`
- **Source Bucket:** `devops-s3-28900`
- **Destination Bucket:** `devops-sync-2461`
- Create the destination bucket as private
- Migrate all existing data
- Verify both buckets contain the same data
- Perform the task using AWS CLI

## Steps

### 1. Verify AWS Access

```bash
aws sts get-caller-identity
```

Set the region:

```bash
export AWS_DEFAULT_REGION=us-east-1
```

### 2. Verify the Source Bucket

```bash
aws s3 ls s3://devops-s3-28900
```

List all existing objects:

```bash
aws s3 ls s3://devops-s3-28900 --recursive
```

### 3. Create the New S3 Bucket

Since the bucket is being created in `us-east-1`:

```bash
aws s3api create-bucket \
  --bucket devops-sync-2461 \
  --region us-east-1
```

Verify:

```bash
aws s3 ls
```

### 4. Ensure the New Bucket Is Private

Enable S3 Block Public Access:

```bash
aws s3api put-public-access-block \
  --bucket devops-sync-2461 \
  --public-access-block-configuration \
  BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true
```

Verify:

```bash
aws s3api get-public-access-block \
  --bucket devops-sync-2461
```

All four settings should return `true`.

### 5. Migrate the Data

Synchronize the source bucket to the destination:

```bash
aws s3 sync \
  s3://devops-s3-28900 \
  s3://devops-sync-2461
```

Migration path:

`devops-s3-28900 → aws s3 sync → devops-sync-2461`

### 6. Verify the Migrated Objects

Source:

```bash
aws s3 ls s3://devops-s3-28900 --recursive
```

Destination:

```bash
aws s3 ls s3://devops-sync-2461 --recursive
```

### 7. Compare Object Counts and Total Size

Check the source:

```bash
aws s3 ls s3://devops-s3-28900 \
  --recursive \
  --summarize
```

Check the destination:

```bash
aws s3 ls s3://devops-sync-2461 \
  --recursive \
  --summarize
```

Verify that both buckets have the same:

- `Total Objects`
- `Total Size`

### 8. Final Sync Verification

Perform a dry run:

```bash
aws s3 sync \
  s3://devops-s3-28900 \
  s3://devops-sync-2461 \
  --dryrun
```

If no files are displayed, there are no remaining objects that AWS CLI detects as needing synchronization.

## Validation

Confirm:

- `devops-sync-2461` exists in `us-east-1`
- The destination bucket has public access blocked
- All source objects were migrated
- Source and destination object counts match
- Source and destination total sizes match
- Final `aws s3 sync --dryrun` reports no remaining changes

## Result

The migration was successfully completed using:

`devops-s3-28900 → AWS CLI sync → devops-sync-2461`

The source and destination buckets were verified to contain the same migrated data.

**Task Status:** ✅ Completed
