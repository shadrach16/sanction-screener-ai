# 📡 RadarPro: Regulatory Compliance & Reporting Engine

![Status](https://img.shields.io/badge/Status-Production_Enterprise-success)
![Compliance](https://img.shields.io/badge/Standard-NFIU_&_CBN_Compliant-blue)
![Stack](https://img.shields.io/badge/Stack-Django_|_React_|_Python_Automation-green)

> **⚠️ Portfolio Notice:** This repository serves as a technical case study for **RadarPro**, a proprietary compliance software developed for Adroit Consulting. The source code is confidential. This document details the system architecture and my role in automating regulatory reporting for Nigerian Financial Institutions.

---

## 🏛️ Project Overview

**RadarPro** is a specialized "RegTech" (Regulatory Technology) solution designed to bridge the gap between Financial Institutions and Regulatory Bodies (specifically the **NFIU** - Nigerian Financial Intelligence Unit).

In the banking sector, failing to report specific transactions (like large cash deposits or foreign transfers) within a set timeframe results in massive sanctions. RadarPro automates this entire lifecycle, converting raw banking data into the strict XML/JSON formats required by government portals, eliminating manual error.

---

## 📦 Core Reporting Modules

The system is divided into four critical reporting engines, powered by Python automation scripts:

### 1. CTR (Customer Transaction Reporting)
* **Function:** Automatically detects and reports cash transactions exceeding the statutory limit (e.g., ₦5M for individuals, ₦10M for corporates).
* **Automation:** Daily cron jobs scan the core banking database, aggregate cash lodgments/withdrawals, and generate the NFIU-compliant report file.

### 2. FTR (Foreign Transaction Reporting)
* **Function:** Tracks all cross-border inflows and outflows.
* **Compliance:** Ensures every forex transaction is captured with necessary metadata (Sender, Receiver, Purpose of Payment) before submission to regulatory bodies.

### 3. STR (Suspicious Transaction Reporting)
* **Function:** An intelligent detection module that flags transactions that do not fit a customer's standard profile (e.g., a student account suddenly receiving ₦50M).
* **Workflow:** Generates an internal alert for the Compliance Officer. Once approved, it auto-generates the STR XML package for secure transmission.

### 4. SAR (Suspicious Activity Reporting)
* **Function:** A behavioral monitoring tool used to report suspicious *activities* (not just transactions), such as potential staff collusion or attempted bypass of internal controls.

---

## ⚙️ Technical Highlight: The XML Automation Engine

The most technically challenging aspect of this project was adhering to the strict **goXML / goAML** schema requirements enforced by the NFIU.

* **The Challenge:** A single missing tag or incorrect date format causes the government portal to reject the entire batch of thousands of transactions.
* **My Solution:** I engineered a robust Python parsing engine that:
    1.  **Extracts** data from the internal Oracle/MSSQL databases.
    2.  **Validates** data integrity (checking for missing BVNs, invalid addresses) *before* generation.
    3.  **Serializes** the data into the complex nested XML structure required by the NFIU.
    4.  **Encrypts** the payload for secure transmission.

> **Tech Stack used for Reporting:** `Python lxml`, `Pandas` (for data aggregation), `Celery` (for background report generation).

---

## 🛠️ Application Architecture

* **Frontend:** `React.js`
    * Built a "Compliance Dashboard" where officers can review generated reports before final submission.
    * Features include Data Visualization of reporting trends and " Drill-down" capabilities into specific transaction details.
* **Backend:** `Django (Python)`
    * Handles the heavy lifting of querying millions of transaction records.
    * Manages user permissions (Maker/Checker) to ensure no single officer can submit a report without approval.
* **Database:**
    * Optimized for Read-Heavy operations to scan historical data without slowing down the live banking application.

---

## 👨‍💻 My Role

As the **Lead Developer**, I was responsible for:
1.  **Logic Implementation:** Coding the rulesets for CTR/FTR detection based on current CBN circulars.
2.  **Schema Mapping:** Mapping internal banking database fields to external regulatory schemas.
3.  **Performance:** Reducing report generation time from hours to minutes using efficient SQL queries and Python generators.

---

## 📬 Contact

**Tunde Oluwamo**
*Senior Full Stack Developer & RegTech Specialist*
[ linkedin.com/in/oluwamo-shadrach-740242185]  
