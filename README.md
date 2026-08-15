# Customer Follow-up Automation (n8n)

An automated workflow that identifies customers who haven't been contacted 
in 3+ days and are still marked "pending," then sends them a personalized 
follow-up email — all without manual tracking.

## Problem it solves
Manually tracking which leads/customers need a follow-up is time-consuming 
and easy to forget. This workflow automates the entire process using free tools.

## Tech Stack
- **n8n** (self-hosted) — workflow automation
- **Google Sheets** — customer data storage
- **Gmail API** — automated email sending
- **JavaScript** (Code node) — custom follow-up logic

## How it works
1. **Schedule Trigger** — runs on a set interval
2. **Google Sheets (Get Rows)** — pulls customer data
3. **Code Node** — calculates days since last contact and flags customers 
   who need a follow-up (status = "pending" AND 3+ days since contact)
4. **IF Node** — routes flagged customers to the email branch
5. **Gmail Node** — sends a personalized follow-up email
6. **Google Sheets (Update Row)** — marks the customer as "follow up sent"

## Setup
1. Import `workflow.json` into your n8n instance
2. Connect your Google Sheets and Gmail credentials
3. Update the Google Sheet ID/name in the Sheets nodes
4. Adjust the follow-up threshold (default: 3 days) in the Code node

## Sheet structure required
| Column | Description |
|---|---|
| name | Customer name |
| email | Customer email |

## Workflow Overview
![Workflow Screenshot](customer_followup
_automation.png)

| last contact date | YYYY-MM-DD format |
| status | pending / followed up / close |
| follow up sent | yes / no |
