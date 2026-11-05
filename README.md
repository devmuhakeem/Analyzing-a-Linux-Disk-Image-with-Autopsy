# Analyzing a Linux Disk Image with Autopsy

A hands-on forensics lab using Autopsy, a full forensic analysis platform, to load and examine a complete Linux disk image as a structured case — browsing the file system, reading file contents, reviewing automatically-generated hashes and metadata, and surfacing flagged findings like a password-protected file.

## Scenario
A disk recovered during an investigation had been imaged into a single forensic file (`Linux_Evidence_001.img`). The task was to load that image into Autopsy, set up a properly documented case, and analyze the file system it contained without ever touching original evidence directly.

## What I did

### 1. Created a documented case
- New case name: `Linux_Analysis`, with a dedicated base directory (a folder created specifically for case data, separate from evidence and unrelated files)
- Optional Information: examiner name and case number recorded — reflecting real forensic documentation requirements for chain of custody

### 2. Added the disk image as a data source
- Selected **Disk Image or VM File** as the data source type
- Browsed to and selected `Linux_Evidence_001.img`
- Configured Ingest Modules (automated analysis passes: hashing, metadata extraction, content categorization) and finished setup
- Noted analysis continues in the background without blocking further work

### 3. Browsed the file system directly
- Expanded the image in Data Sources to reveal a navigable, structured file system matching the original disk
- Navigated to `/etc`, selected the `passwd` file, and viewed its contents via the **Text** tab — all read-only, against the image, never touching or modifying the original
- Noted the File Metadata, Hex, and Annotations tabs as additional ways to inspect the same file from different angles

### 4. Reviewed automatically-generated hash and metadata
- Navigated to `SeatPlan.xls` under `/home/roger/Documents`
- Opened **File Metadata**: creation/modification/access timestamps alongside an automatically-calculated MD5 hash (no separate manual hashing step required, unlike an earlier lab using a standalone tool)
- Checked the **Results** tab: Autopsy had automatically flagged the file as **password protected**

### 5. Used the media gallery view
- Opened **Images/Videos** from the toolbar — a consolidated gallery of every image and video file across the entire image, regardless of folder location, generated automatically during ingest

## Key takeaways
- Case documentation (examiner, case number, dedicated base directory) exists for legal/chain-of-custody reasons, not just organizational convenience — it's part of the forensic record from the first step
- All analysis happens against a forensic image, never the original evidence — the entire reason imaging exists as a practice
- Integrated hashing and metadata extraction (automatic, during ingest) is what makes comprehensive analysis practical across a full disk image, versus manually hashing individual files one at a time
- Automated flags (like the password-protected file) direct investigator attention efficiently, without requiring manual testing of every file
- Multiple file views (Text, Hex, Metadata, Annotations) exist because different investigative questions require different perspectives on the same file — no single view is sufficient alone

## Tools
Autopsy 4.14.0

---
*Completed in an isolated training lab environment using a provided forensic disk image (Linux_Evidence_001.img).*
