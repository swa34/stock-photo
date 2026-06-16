# Portfolio Summary: Storage, Backups, and Storefront Options

This document outlines the technical findings and workflows for organizing master archives, implementing a 3-2-1 backup strategy, and reviewing the three primary e-commerce platforms for the storefront.

---

## 1. Cloud Storage Tier Comparison

Photographers working at scale face specific storage bottlenecks. Standard cloud sync platforms become highly inefficient and expensive once data archives exceed a few terabytes.

| Storage Category | Primary Use Case | Key Advantages | Major Limitations / Costs |
| :--- | :--- | :--- | :--- |
| **Cloud Sync**<br>*(Google Drive, Dropbox)* | Active projects, current-year edits, and client gallery delivery. | Cross-device accessibility; deep app integrations. | High costs above 2TB; desktop app indexing freezes with heavy file volumes. |
| **Object Storage**<br>*(Backblaze B2, AWS S3)* | Permanent, long-term master RAW archiving. | Infinite scalability; linear pricing (~$7/TB on B2); keeps local SSDs clear. | No native folder sync; requires FTP client or clone tools to push/pull files. |
| **True Backup**<br>*(Backblaze Personal, IDrive)* | Automated desktop disaster recovery. | Flat annual rate; passively mirrors external drives attached to desktop. | Files cannot be natively shared; mirroring copies file deletions immediately. |

---

## 2. The 3-2-1 Backup Strategy

To prevent irreversible data loss from hardware failure, software corruption, or physical disasters, professionals adhere to the **3-2-1 Rule**:

*   **3 Total Copies:** Keep one primary working copy plus a minimum of two separate backup copies.
*   **2 Different Media Types:** Store files on distinct physical devices to prevent single-point hardware failures (e.g., Laptop SSD vs. External Hard Drive).
*   **1 Off-Site Location:** Keep one copy entirely separate from the physical workspace using secure cloud infrastructure.

### The Implementation Workflow
1.  **Copy 1 (Active):** High-speed Local SSD handles active edits in Lightroom.
2.  **Copy 2 (Local Mirror):** A local external drive mirrors the active workspace automatically every night via cloning utilities (like Carbon Copy Cloner or GoodSync).
3.  **Copy 3 (Off-Site):** Backblaze Personal operates in the background, continuously backing up the local drives to remote servers.

---

## 3. Storefront Platform Options for Elizabeth to Research

Because her photos are already high-resolution JPEGs and she is fluent in Lightroom, her workflow will be highly automated. All three of these platforms read the keywords and titles she types into Lightroom automatically, making her site fully searchable for customers out of the box.

### Option 1: SmugMug Pro
*   **What it is:** A fully hosted, turnkey platform designed specifically for photographers to sell digital downloads and prints.
*   **How it works:** You install their official Lightroom plugin. You drag keyworded photos into a folder inside Lightroom and click "Publish." It automatically watermarks them, creates the storefront layout, and handles the sales. 
*   **Pros:** Easiest to use, zero coding required, and reliable customer support.
*   **Cons:** Charges a monthly subscription fee and takes a percentage of sales.

### Option 2: PhotoShelter
*   **What it is:** An industry-standard platform geared heavily toward professional archives, corporate photography, and serious stock image licensing.
*   **How it works:** Identical workflow to SmugMug. It connects directly into the Lightroom "Publish Services" sidebar to push files, embed metadata, and manage galleries straight from her local catalog.
*   **Pros:** Extremely powerful internal search engine for buyers, advanced commercial licensing frameworks.
*   **Cons:** Pricier monthly subscription fees, steep learning curve for the backend backend settings.

### Option 3: WordPress + Symbiostock
*   **What it is:** A self-hosted, independent storefront route using WordPress and a plugin built strictly for independent stock photographers.
*   **How it works:** You run a standard WordPress site. Symbiostock handles the heavy lifting—processing image uploads, auto-watermarking, reading Lightroom metadata, and converting them into searchable e-commerce products.
*   **Pros:** Zero monthly platform fees, zero sales commissions, and complete control over the design and business model. 
*   **Cons:** Requires manual technical setup and maintenance. (Note: To keep the site fast, a media offloading plugin should be used to store the shop's JPEGs on cheap Backblaze B2 storage rather than bloating the web server).

---

## 4. The RAW-Archive vs. JPEG-Storefront Workflow

The stock storefront only hosts high-resolution JPEGs. Her heavy RAW files can live safely in cold storage without breaking her live website.