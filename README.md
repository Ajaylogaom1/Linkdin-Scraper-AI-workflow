# Linkdin-Scraper-AI-workflow

# 🧾 Form Submission → AI Extraction → External API → Google Sheets (n8n Workflow)

This workflow captures website form submissions, processes the data using Google Gemini AI, optionally enriches it through a third-party API call, and finally logs the structured output into a Google Sheet.

# 🚀 What This Workflow Does

Triggers when a user submits a form

Sends the form content to an AI Agent (Gemini) for extraction/formatting

Parses response into a clean JSON structure

Uses HTTP Request to fetch additional data if needed

Inserts final structured result into a Google Sheet

# 🧩 Workflow Steps Overview

1️⃣ Form Submission Trigger – Captures incoming form data
2️⃣ AI Agent (Google Gemini Chat Model) – Extracts / formats / enriches form text
3️⃣ Structured Output Parser – Converts AI text into usable JSON fields
4️⃣ Edit Fields – Manually adjusts or maps values if needed
5️⃣ HTTP Request – Calls external API (ex: Apify lookup, enrichment, validation)
6️⃣ Append Row in Sheet – Saves final formatted information to Google Sheets

# 🛠️ Requirements

n8n cloud or self-hosted

Google Sheets API credentials

Google Gemini API Key

Form submission endpoint (Webform, Webflow, Make, HTML form, etc.)

Optional: 3rd-party API key used in HTTP request node

# 🔧 Setup Instructions

1️⃣ Import workflow JSON into n8n
2️⃣ Configure nodes with credentials:

Google Gemini – API key

Google Sheets – Spreadsheet access

HTTP Request – Custom API key & URL (if used)

3️⃣ Update Google Sheet ID in Append row in sheet node
4️⃣ Connect form → n8n webhook URL
5️⃣ Submit a test form and verify final row is created in sheet

# 🧠 AI Processing Logic

Gemini transforms raw text into structured data such as:

{
  "name": "",
  "email": "",
  "company": "",
  "message_summary": "",
  "lead_score": ""
}


You may modify the prompt inside AI Agent → "Chat Model Prompt" to change behavior (lead scoring, summarization, tagging, etc.)

# 🐞 Troubleshooting
Issue	Fix
Form not triggering automation-	Confirm webhook URL configured in form
Output is not structured- Check Structured Output Parser schema
Sheet row blank	- Ensure mapped fields match parser output
HTTP Request fails-	Verify API URL + Authentication Header
