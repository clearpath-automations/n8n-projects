# AI-Powered Customer Support Workflow
**Automated Email Classification & Smart Draft Reply System**

A production-ready **n8n customer support automation** that classifies incoming support emails using AI, applies Gmail labels automatically, generates category-specific draft responses, and logs all activity to a support database.

This system reduces manual triage time, standardizes support tone, and accelerates response workflows — without auto-sending emails.

---

## 🎯 What This Workflow Does

- Monitors incoming Gmail messages in real-time
- Classifies emails into 5 predefined support categories using AI
- Automatically applies the correct Gmail label
- Generates a professional draft reply tailored to the category
- Saves the draft inside the original email thread
- Logs all activity to Google Sheets for tracking and reporting

---

## 🚀 Key Features

### 📥 AI Email Classification
Every incoming email is analyzed and classified into one of the following:

1. Billing & Subscription  
2. Technical Support  
3. Product & Usage Questions  
4. Sales & Partnerships  
5. Complaints & Security Concerns  

The classifier responds with only one exact category to ensure deterministic routing.

---

### 🏷️ Automatic Gmail Labeling
Once classified:
- The appropriate Gmail label is applied
- Emails are instantly organized
- No manual tagging required

---

### 🤖 Category-Specific AI Draft Replies

Each category has its own specialized AI persona:

- **Billing** → Professional support assistant  
- **Technical** → Structured troubleshooting assistant  
- **Product Questions** → Educational guide  
- **Sales** → Engaging sales representative  
- **Complaints/Security** → Senior empathetic specialist  

All replies:
- Follow strict tone guidelines
- Avoid invented policies or guarantees
- Maintain professionalism
- Are saved as **drafts only** (human approval required)

---

### 📊 Support Activity Logging

Every processed email is logged to Google Sheets with:

- Email ID
- Category
- AI-generated Subject
- AI-generated Message

This creates a searchable support log for reporting and QA review.

---

## 🧠 Workflow Architecture Overview

### 1. Email Intake
- Gmail Trigger polls for new incoming messages
- Extracts full email text and metadata

### 2. AI Classification
- GPT model classifies email into one of five categories
- Deterministic single-label output

### 3. Routing & Labeling
- Applies matching Gmail label
- Routes email to category-specific AI drafting node

### 4. AI Draft Generation
- GPT-4 class model generates structured JSON output:
  - Subject
  - Message
- Response tone depends on category type

### 5. Draft Creation
- Draft reply saved inside original Gmail thread
- No automatic sending (human review required)

### 6. Database Logging
- Appends or updates support log in Google Sheets
- Enables analytics and tracking

---

## 🛠️ Tech Stack

- **n8n** – Workflow orchestration  
- **Gmail API** – Email trigger, labeling, draft creation  
- **OpenAI (GPT-4 class models)** – Classification + reply generation  
- **Google Sheets** – Support database logging  

---

## 🗂️ Email Categories & Routing Logic

| Category | Behavior | Tone |
|----------|----------|------|
| Billing & Subscription | Draft professional billing response | Clear & professional |
| Technical Support | Includes troubleshooting steps if needed | Structured & helpful |
| Product & Usage Questions | Educational guidance | Clear & instructive |
| Sales & Partnerships | Engaging response | Professional & persuasive |
| Complaints & Security | Empathetic reassurance | Calm & supportive |

---

## ⚙️ Installation & Configuration

### 1. Import Workflow
- Open n8n
- Import `Customer Support Workflow.json`
- Activate after credentials are configured

### 2. Configure Credentials

You’ll need:

- Gmail OAuth2
- OpenAI API
- Google Sheets OAuth2

### 3. Update Configuration

- Gmail Label IDs (for each category)
- Google Sheets Document ID
- Sheet name
- OpenAI model selection (if desired)

---

## 🧪 How to Test

### Test Classification
1. Send a billing-related email
2. Confirm correct Gmail label is applied

### Test Draft Creation
1. Send a technical support request
2. Verify a draft reply appears in the thread

### Test Logging
1. Confirm entry appears in Google Sheets
2. Validate category and AI-generated content

---

## 💡 Use Cases

- SaaS customer support automation
- Startup support triage systems
- Agencies handling multiple support categories
- Internal helpdesk automation
- AI-assisted but human-reviewed support workflows

---

## 📌 Notes

- Drafts are created but not sent automatically
- AI responses follow strict tone guidelines
- Logging enables performance tracking and QA audits
- Easily extendable to:
  - Slack notifications
  - Auto-escalation workflows
  - CRM integration
  - Sentiment analysis
