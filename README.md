# n8n-student-performance-workflow-
An automated student performance tracking and alerting system built with n8n. Identifies at-risk students based on scores and attendance, and sends real-time alerts via Gmail, Slack, and WhatsApp.
# 📊 Automated Student Performance Tracking & Alerting System

An end-to-end automation pipeline built with **n8n** to track student performance, identify at-risk students, and send multi-channel notifications via **Slack**, **Gmail**, and **WhatsApp (Twilio)**.

---

## 🚀 Project Overview

In many educational institutions, tracking student performance involves manually collecting marks, attendance, and assignment data from scattered sources. This project eliminates that bottleneck by automating the entire workflow — from data aggregation to stakeholder alerts.

Built using a **two-workflow architecture**, this system separates raw data collection from transformation and notification logic for better scalability and maintainability.

---

## ✨ Features

- **📅 Scheduled Data Aggregation**: Automatically pulls student data from multiple department-wise Google Sheets on a schedule.
- **⚙️ Automated ETL Process**: Calculates weighted scores, attendance %, and transforms the data into actionable insights.
- **🚨 At-Risk Identification**: Flags students with low attendance or poor performance based on configurable thresholds.
- **📬 Multi-Channel Notifications**:
  - **Gmail** – Sends detailed HTML reports to department heads.
  - **Slack** – Pushes concise summaries to teacher/academic groups.
  - **Twilio (WhatsApp)** – Sends urgent alerts to parents directly.
- **🔁 Scalable & Modular**: Easily extendable for new departments, data sources, or communication channels.

---

## 🧰 Tech Stack

- **n8n** – Core workflow engine
- **Google Sheets** – Primary data source
- **Google Drive** – For intermediate CSV storage
- **Gmail** – Email reporting
- **Slack** – Internal alerts
- **Twilio (WhatsApp)** – External parent notifications

---

## 🛠 Workflow Architecture

### 1️⃣ `Read-&-Upload.json` (Data Aggregator)
- **Trigger**: Scheduled (e.g., hourly or daily)
- **Steps**:
  - Reads data from multiple Google Sheets (CSE, Civil, Electrical)
  - Merges and standardizes the data
  - Converts to CSV
  - Uploads to Google Drive
  - **Triggers** the next workflow

### 2️⃣ `Student Performance ETL.json` (Processing & Notification Engine)
- **Trigger**: Executed by the first workflow
- **Steps**:
  - **Extract**: Downloads CSVs from Drive
  - **Transform**:
    - Calculates final scores and attendance %
    - Flags students as "at-risk"
    - Prepares formatted messages
  - **Load/Notify**:
    - Sends Slack, Gmail, and Twilio messages
    - Updates a Master Sheet with final output

---

## 🧾 Prerequisites

- ✅ **n8n instance** (cloud or self-hosted)
- ✅ **Google Cloud Project** (for Sheets, Drive, Gmail)
- ✅ **Slack Workspace** (with App + Bot Token)
- ✅ **Twilio Account** (WhatsApp Sandbox enabled)

---

## 📁 Google Sheets Structure

Ensure all data sheets have the following columns:

```text
StudentID
SubjectCode
SubjectName
Semester
Branch
MidTermMarks
FinalMarks
ClassesAttended
TotalClasses
Assignment-1
Assignment-2
TotalAssign-Score
parent_phone  <-- (e.g., +919876543210)

⚠️ Due to the use of private API credentials (Gmail, Slack, Twilio), this project is not available for public live demo — but happy to walk through the architecture or share setup steps!


## 🔗 LinkedIn Project Post

To see a public summary and walkthrough of this project, check out the LinkedIn post here:  
👉 [View on LinkedIn](https://tinyurl.com/56brafcn)

*Includes context, system architecture, and notification logic breakdown.*
