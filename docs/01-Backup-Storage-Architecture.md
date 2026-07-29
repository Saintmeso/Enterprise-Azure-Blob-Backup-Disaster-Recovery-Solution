# Backup Storage Architecture

The foundation of this project was the design and deployment of a centralized Azure Blob Storage environment capable of securely storing business backup data.

Before implementing automation, disaster recovery, and lifecycle management, a scalable storage architecture was required to organize business files and support future growth.

---

# Business Requirement

Northwind Technologies required a centralized cloud storage solution to replace scattered and manually managed backups.

The environment needed to:

- Store multiple categories of business data
- Organize backups logically
- Support future automation
- Scale as storage requirements increased

Azure Blob Storage was selected because it provides highly available, durable, and scalable object storage designed for backup, archival, and disaster recovery workloads.

---

# Azure Storage Account

The first step was deploying an Azure Storage Account, which serves as the central storage service for all backup data.

The Storage Account acts as the management boundary for:

- Blob Containers
- Security settings
- Data protection features
- Lifecycle Management
- Storage monitoring

Without the Storage Account, the remaining backup services could not be configured.

---

## Storage Account Configuration

<img width="1919" height="874" alt="backup project blob storage configurations" src="https://github.com/user-attachments/assets/1e609ec5-1086-4a77-88e7-d651473d930f" />


*Azure Storage Account configured with Blob Versioning, Soft Delete, Container Soft Delete, and Blob Change Feed to provide a resilient foundation for cloud backup storage.*

---

# Blob Container Design

Rather than storing every backup inside a single container, the storage environment was divided into separate Blob Containers based on workload type.

Three containers were created:

- **documents**
- **application-files**
- **database-backups**

This organizational approach mirrors enterprise storage environments where different categories of data are managed independently.

---

## Storage Containers

<img width="1919" height="877" alt="backup project containers" src="https://github.com/user-attachments/assets/8f5dfb19-dc56-4ceb-adb5-326b0a420bb7" />

*Azure Blob Storage containers organized by workload type to improve manageability and support future scalability.*

---

# Documents Container

The **documents** container stores business documents that require long-term protection.

Examples include:

- Employee records
- Payroll files
- Sales reports
- Inventory data

Keeping business documents in their own container simplifies administration and allows future lifecycle policies to be applied independently if required.

<img width="1919" height="875" alt="backup project documents container" src="https://github.com/user-attachments/assets/f11eb49c-22b2-4700-84c2-579e88dec2ee" />

*Dedicated Blob container used to store business documents and operational files.*

---

# Application Files Container

The **application-files** container stores application configuration files used by business systems.

Examples include:

- appsettings.json
- web.config
- WebsiteConfig.json

Separating application configuration from business documents improves organization and supports application recovery scenarios.

<img width="1919" height="877" alt="backup project Application files container" src="https://github.com/user-attachments/assets/e9b53540-5005-4ad6-b934-0f44a44e7d20" />

*Dedicated Blob container used to store application configuration and deployment files.*

---

# Database Backup Container

The **database-backups** container stores database backup files independently from other business data.

Examples include:

- SQL backup files
- Database backup archives

Keeping database backups separate allows organizations to manage retention policies and storage growth independently from documents and application files.

<img width="1919" height="876" alt="backup project database backup container" src="https://github.com/user-attachments/assets/d75574b4-bc21-476c-9f3e-ee0d5b74a7bf" />
*Dedicated Blob container used to store database backup files.*

---

# Why This Design?

Rather than storing every backup in one location, separating workloads into dedicated Blob Containers provides several advantages:

- Improves organization
- Simplifies administration
- Supports future scalability
- Enables workload-specific lifecycle policies
- Makes backup management easier as the organization grows

This design reflects common enterprise cloud storage practices where different types of business data are managed independently while remaining centralized within a single Storage Account.

---

# Outcome

At the completion of this phase, Northwind Technologies had a centralized Azure Blob Storage environment capable of securely storing business documents, application files, and database backups.

This storage architecture served as the foundation for implementing data protection, lifecycle management, automation, and disaster recovery throughout the remainder of the project.
