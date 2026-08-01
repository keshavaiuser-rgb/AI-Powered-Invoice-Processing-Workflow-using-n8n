An automated invoice processing system built with n8n that extracts invoice data using AI, validates the extracted information, stores the results in Google Sheets, and sends email notifications.

This project demonstrates how AI and workflow automation can simplify invoice processing while handling multiple input sources and common failure scenarios.

Features
📧 Process invoices received through Gmail attachments
☁️ Process invoices uploaded to Google Drive
📄 Extract text from PDF invoices
🤖 AI-powered invoice data extraction using OpenRouter Chat Model
📋 Structured JSON output using Structured Output Parser
✅ Validate required invoice fields
📊 Store extracted data in Google Sheets
📧 Send success and manual review email notifications
⚠️ Built-in error handling
📈 AI Confidence Score
🕒 Processing Timestamp
📁 Store original invoice files in Google Drive

Workflows Included
1. Gmail Invoice Processing

This workflow automatically monitors Gmail for invoice PDF attachments.

Flow

Gmail Trigger
      ↓
Download Attachment
      ↓
Extract Text from PDF
      ↓
AI Extraction
      ↓
Validation
      ↓
Google Sheets
      ↓
Email Notification

2. Google Drive Invoice Processing

This workflow monitors a Google Drive folder for newly uploaded invoice PDFs.

Flow

Google Drive Trigger
        ↓
Download File
        ↓
Extract Text from PDF
        ↓
AI Extraction
        ↓
Validation
        ↓
Google Sheets
        ↓
Email Notification

AI Extraction

The AI extracts the following information:

Invoice Number
Vendor Name
Invoice Date
Total Amount
Tax Amount
Currency
Invoice Items
Confidence Score

The output is returned as structured JSON.

Validation Logic

The workflow validates three required fields:

Invoice Number
Vendor Name
Total Amount
If all fields are present

Status = Processed
If any field is missing
Status = Needs Manual Review

The workflow also checks the AI confidence score before processing.

Data Stored

The extracted invoice information is saved to Google Sheets.

Stored fields include:

Invoice Number
Vendor Name
Invoice Date
Total Amount
Tax Amount
Currency
Status
Confidence Score
Processing Timestamp

Invoice line items are also stored separately.

Notifications

The workflow automatically sends emails for:

✅ Successfully processed invoices
⚠️ Manual review required
❌ Processing failures
Error Handling

The workflow handles the following scenarios:

Invalid invoice files
PDF extraction failures
AI extraction failures
Missing required fields
Google Sheets errors
Gmail errors
Google Drive errors

Instead of stopping silently, the workflow updates the processing status and sends an appropriate email notification.

Technologies Used
n8n
OpenRouter
OpenRouter Chat Model
Structured Output Parser
Google Gmail API
Google Drive API
Google Sheets API
n8n Nodes Used
Gmail Trigger
Google Drive Trigger
HTTP Request
Download File
Extract From PDF
Edit Fields
AI Agent
OpenRouter Chat Model
Structured Output Parser
IF
Split Out
Aggregate
Google Sheets
Gmail
Error Handling
Bonus Features Implemented
✅ Multiple invoice sources
✅ Separate workflows for Gmail and Google Drive
✅ Structured AI Output (JSON)
✅ AI Confidence Score
✅ Original Invoice Storage
✅ Processing Timestamp
Setup
Import both workflow JSON files into n8n.
Configure the required credentials:
Gmail
Google Drive
Google Sheets
OpenRouter API
Update the Google Sheets document.
Select the Google Drive folder for monitoring.
Activate the workflows.
Project Structure
AI Invoice Processing
│
├── Gmail Invoice Processing Workflow.json
├── Google Drive Invoice Processing Workflow.json
└── README.md
Future Improvements
Duplicate invoice detection
Database storage (PostgreSQL/MySQL)
Slack or Microsoft Teams notifications
OCR fallback for scanned invoices
Multi-language invoice support
Author

Keshav

Built as part of an AI Workflow Automation assignment using n8n, AI Agents, and OpenRouter.
