# Data Protection

After deploying the storage architecture, Azure data protection features were configured to safeguard business data from accidental deletion, unintended modifications, and data loss.

Rather than relying on a single recovery mechanism, multiple Azure features were implemented to provide layered protection for stored backup files.

---

# Business Requirement

Backups are only valuable if data can be successfully recovered when something goes wrong.

Organizations frequently encounter situations such as:

- Accidental file deletion
- Users overwriting important documents
- Corrupted backup files
- Unexpected application changes

To minimize the risk of permanent data loss, multiple Azure Blob Storage protection features were enabled.

---

# Blob Soft Delete

Blob Soft Delete protects files that have been accidentally deleted.

Instead of being permanently removed from storage, deleted blobs remain recoverable for a configured retention period before Azure permanently removes them.

For this project, Blob Soft Delete was configured with a **30-day retention period**.

## Why?

Accidental deletion is one of the most common causes of data loss. Soft Delete provides administrators with an opportunity to restore deleted files without relying on external backup copies.

---

# Container Soft Delete

Container Soft Delete extends the same protection to entire Blob Containers.

If a container is accidentally deleted, Azure preserves both the container and its contents during the configured retention period.

## Why?

Protecting entire containers prevents large-scale data loss caused by accidental administrative actions.

---

# Blob Versioning

Blob Versioning automatically creates previous versions whenever a blob is modified.

Rather than replacing an existing file, Azure preserves earlier versions that can be restored if needed.

## Why?

Versioning protects against accidental file modifications and allows previous versions of important documents to be recovered without restoring an entire backup.

---

# Blob Change Feed

Blob Change Feed records storage events such as blob creation, modification, and deletion.

Azure continuously logs these events to provide a historical record of activity within the Storage Account.

## Why?

Maintaining a history of storage activity improves auditing, troubleshooting, and visibility into changes affecting backup data.

---

# Disaster Recovery Validation

To verify the effectiveness of these protection features, a recovery test was performed using a sample business document.

The validation process included:

- Uploading a test document
- Deleting the blob
- Verifying Soft Delete
- Restoring the deleted blob
- Confirming successful recovery

This demonstrated that backup files remained recoverable throughout the configured retention period.

---

## Blob Soft Delete Test

<img width="962" height="870" alt="Backup Project Soft Deletion confirmation" src="https://github.com/user-attachments/assets/740c0ff5-a9b3-4d89-a788-2c338476dca7" />

*Deleting a blob moves it into a soft-deleted state instead of permanently removing it, allowing recovery during the retention period.*

---

## Blob Recovery

<img width="960" height="866" alt="Backup Project Restoring Confirmation" src="https://github.com/user-attachments/assets/df95d027-8c88-4339-ae67-6e08816d5845" />

*Azure successfully restored the deleted blob using the built-in Undelete feature.*

---

## Recovery Verification

<img width="1919" height="877" alt="Backup Project Restoring Confirmation 2" src="https://github.com/user-attachments/assets/53bd5c45-6c8b-4255-81bc-2b5a60d9b05c" />

*Recovery testing confirmed that deleted backup data could be successfully restored, validating the disaster recovery configuration.*

---

# Why Layered Protection?

Rather than relying on a single backup copy, multiple Azure protection features work together to improve resilience.

This layered approach provides protection against:

- Accidental deletion
- File overwrites
- Unintended modifications
- Administrative mistakes
- Permanent data loss

Implementing multiple recovery mechanisms strengthens business continuity while reducing the likelihood of irreversible data loss.

---

# Outcome

At the completion of this phase, the Azure Storage environment included multiple layers of protection capable of preserving business data, maintaining previous file versions, and recovering deleted content.

These protections formed the foundation of the project's disaster recovery strategy and ensured that backup data remained recoverable throughout its retention period.
