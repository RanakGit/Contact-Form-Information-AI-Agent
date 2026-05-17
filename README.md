# Contact Form Automation – README

## Project Overview

This workflow is built using [n8n](https://n8n.io?utm_source=chatgpt.com) to automate customer query handling for **RAC Insurance**.

The automation performs the following tasks whenever a user submits the contact form:

1. Captures form data
2. Stores the submission in [Google Sheets](https://www.google.com/sheets/about/?utm_source=chatgpt.com)
3. Sends a confirmation email to the customer using [Gmail](https://mail.google.com?utm_source=chatgpt.com)
4. Sends an internal notification to a [Slack](https://slack.com?utm_source=chatgpt.com) channel

---

# Workflow Name

**Contact Form Automation**

---

# Features

* Web-based contact form
* Automatic lead storage in Google Sheets
* Instant email acknowledgment to customers
* Slack notification for internal teams
* OAuth2 authentication support
* Fully automated workflow

---

# Workflow Architecture

```text
Form Submission
       │
       ▼
Store Data in Google Sheets
       │
       ├──► Send Confirmation Email (Gmail)
       │
       └──► Send Slack Notification
```

---

# Nodes Used

## 1. Form Trigger Node

### Purpose

Collects user information through a public form.

### Fields Collected

| Field              | Type  | Required |
| ------------------ | ----- | -------- |
| Name               | Text  | Yes      |
| Email              | Email | Yes      |
| What is your Query | Text  | No       |

### Form Details

* Form Title: `Contact Us - RAC Insurance`
* Description: `Give us your details and we will reach out`

---

## 2. Google Sheets Node

### Purpose

Stores all form submissions in a Google Sheet.

### Operation

`Append Row`

### Stored Columns

| Column | Value          |
| ------ | -------------- |
| Name   | Customer Name  |
| Email  | Customer Email |
| Query  | Customer Query |

### Google Sheet Used

`Contact Form Information`

---

## 3. Gmail Node

### Purpose

Sends an automatic response email to the customer.

### Email Subject

```text
Got New Query
```

### Email Content

```text
Hey [Customer Name]

We have received your query.

Query - [Customer Query]

Regards,
RAC Insurance
```

### Additional Features

* CC enabled
* Attribution disabled

---

## 4. Slack Node

### Purpose

Notifies the internal team whenever a new query is received.

### Slack Message Format

```text
Hey we got a query

Query: [Customer Query]

Name: [Customer Name]

Email: [Customer Email]
```

### Slack Channel

`all-carbon-x-inc`

---

# Technologies Used

| Technology                                                                   | Purpose             |
| ---------------------------------------------------------------------------- | ------------------- |
| [n8n](https://n8n.io?utm_source=chatgpt.com)                                 | Workflow Automation |
| [Google Sheets](https://www.google.com/sheets/about/?utm_source=chatgpt.com) | Data Storage        |
| [Gmail API](https://developers.google.com/gmail/api?utm_source=chatgpt.com)  | Email Automation    |
| [Slack API](https://api.slack.com?utm_source=chatgpt.com)                    | Team Notifications  |

---

# Setup Instructions

## Step 1 — Import Workflow

1. Open n8n
2. Go to **Workflows**
3. Click **Import from JSON**
4. Paste the workflow JSON
5. Save the workflow

---

## Step 2 — Configure Credentials

Connect the following accounts:

* Google Sheets OAuth2
* Gmail OAuth2
* Slack OAuth2

---

## Step 3 — Configure Google Sheet

Create a Google Sheet with the following columns:

```text
Name | Email | Query | Mobile
```

---

## Step 4 — Activate Workflow

Toggle the workflow from:

```text
Inactive → Active
```

---

# Example Workflow Execution

## User Submits Form

```text
Name: John Doe
Email: john@example.com
Query: I need insurance details
```

## Automation Result

### Google Sheets

A new row is added automatically.

### Gmail

Customer receives a confirmation email.

### Slack

Internal team receives an alert message.

---

# Benefits

* Eliminates manual data entry
* Faster customer communication
* Centralized lead management
* Real-time team notifications
* Easy to scale and customize

---

# Future Improvements

Possible enhancements:

* Add phone number validation
* CRM integration
* AI-powered response generation
* Priority tagging
* File upload support
* WhatsApp notifications
* Auto-ticket generation

---

# Author

**Ranak Halder**
B.Tech Biotechnology Student & Automation Enthusiast

---

# License

This project is open for educational and internal business use.
