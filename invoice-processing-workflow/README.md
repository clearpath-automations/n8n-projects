# AI Invoice Processing & Billing Notification Workflow
**Automated Invoice Extraction, Database Logging & Internal Billing Alerts**

A production-ready **n8n financial automation workflow** that monitors a Google Drive folder for new invoice PDFs, extracts structured invoice data using AI, logs the information into a centralized database, and automatically notifies the internal billing team.

This system eliminates manual invoice entry, reduces accounting errors, and ensures finance teams are instantly informed when new invoices arrive.

---

## 🎯 What This Workflow Does

- Monitors a dedicated Google Drive folder for new invoice uploads
- Automatically downloads and reads invoice PDFs
- Uses AI to extract structured invoice details
- Logs all invoice data into Google Sheets
- Generates a professional internal billing email
- Notifies the finance team automatically

---

## 🚀 Key Features

### 📂 Automated Invoice Detection
- Polls a specific Google Drive folder every minute
- Triggers only when a new file is created
- Ensures no invoice is missed

---

### 🤖 AI-Powered Data Extraction
Using a structured AI extraction model, the workflow captures:

- Invoice Number  
- Invoice Date  
- Client Name  
- Client Email  
- Client Address  
- Total Amount  
- Due Date  
- Payment Date  

The AI ensures consistent structured output even from differently formatted PDFs.

---

### 📊 Centralized Invoice Database
Extracted data is automatically appended to a Google Sheets database:

- Creates a searchable invoice registry
- Enables reporting & reconciliation
- Reduces manual data entry errors

---

### 📧 Smart Internal Billing Notification
After database update:

- GPT-4.1-mini generates a structured internal email
- Includes invoice summary details
- Provides direct database link for review
- Sends email automatically to the billing team

---

## 🧠 Workflow Architecture Overview

### 1. Invoice Intake
- Google Drive Trigger monitors a specific folder
- Activates when a new PDF file is uploaded

### 2. File Processing
- Invoice PDF is downloaded
- Text content extracted from the document

### 3. AI Information Extraction
- Gemini-based extraction model structures invoice fields
- Enforces required data attributes

### 4. Database Logging
- Extracted data appended to Google Sheets
- Creates centralized invoice tracking system

### 5. Internal Notification
- GPT model drafts internal summary email
- Gmail node sends notification to billing team

---

## 🛠️ Tech Stack

- **n8n** – Workflow orchestration  
- **Google Drive API** – Invoice intake trigger  
- **PDF Extraction Node** – Text extraction  
- **Google Gemini (PaLM API)** – Structured invoice data extraction  
- **Google Sheets API** – Invoice database  
- **OpenAI GPT-4.1-mini** – Internal billing email generation  
- **Gmail API** – Automated notification  

---

## 🗂️ Data Structure (Invoice Database)

| Field | Description |
|-------|------------|
| Invoice Number | Unique invoice identifier |
| Invoice Date | Date issued |
| Client Name | Client organization |
| Client Email | Client contact email |
| Client Address | Client billing address |
| Total Amount | Invoice total |
| Due Date | Payment due date |
| Payment Date | Initial payment date |

---

## ⚙️ Installation & Configuration

### 1. Import Workflow
- Open n8n
- Import `Invoice Workflow.json`
- Activate after credentials are configured

### 2. Configure Credentials

You’ll need:

- Google Drive OAuth2
- Google Sheets OAuth2
- Gmail OAuth2
- Google Gemini (PaLM API)
- OpenAI API Key

### 3. Update Configuration

- Google Drive Folder ID
- Google Sheets Document ID
- Billing team email address
- OpenAI model (optional change)

---

## 🧪 How to Test

### Test Invoice Intake
1. Upload a PDF invoice to the monitored Drive folder
2. Confirm workflow triggers

### Test Extraction
1. Verify structured fields populate correctly
2. Confirm no missing required attributes

### Test Database Logging
1. Open Google Sheets
2. Confirm new invoice entry appears

### Test Email Notification
1. Confirm billing team receives structured invoice summary
2. Verify subject + message formatting

---

## 💡 Use Cases

- Agencies processing vendor invoices
- Accounting automation for startups
- Operations teams managing recurring invoices
- Internal finance automation
- AI-assisted document processing systems

---

## 📌 Notes

- Designed for structured invoice PDFs
- AI improves extraction reliability across formats
- Easily extendable to:
  - Slack notifications
  - Payment status tracking
  - ERP integration
  - Duplicate invoice detection
  - Approval workflows
