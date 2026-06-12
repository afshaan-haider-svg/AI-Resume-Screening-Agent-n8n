# AI Resume Screening Agent using n8n

An AI-powered Resume Screening Automation built with **n8n, Gmail, Google Sheets, PDF Extraction, and AI**.

This project helps HR teams automate the initial resume screening process by receiving candidate CVs through Gmail, extracting resume content from PDF attachments, analyzing candidates against job requirements, saving results in Google Sheets, and creating professional Gmail drafts for HR review.

---

## Project Overview

HR teams often receive many resumes through email. Manually opening each CV, checking skills, comparing requirements, updating sheets, and writing replies can take a lot of time.

This project automates the first screening step using an AI workflow.

The agent:

* Receives candidate CVs through Gmail
* Checks PDF resume attachments
* Extracts text from CVs
* Analyzes resumes against job requirements
* Generates candidate score and recommendation
* Saves candidate details in Google Sheets
* Creates Gmail drafts for shortlisted, maybe, and rejected candidates

---

## Problem Statement

Recruitment teams spend a significant amount of time on repetitive tasks such as:

* Opening each candidate email
* Downloading CV attachments
* Reading resumes manually
* Comparing candidate skills with job requirements
* Updating candidate tracking sheets
* Writing response emails

This project solves the problem by automating these repetitive steps while keeping final hiring decisions under human control.

---

## Solution

The AI Resume Screening Agent uses n8n to connect Gmail, PDF extraction, AI screening, Google Sheets, and Gmail draft creation.

The system screens resumes based on job-related criteria such as:

* Education
* Experience
* Technical tools
* Skills
* Role fit
* Location fit
* Communication skills

The agent does not make final hiring decisions. It only supports HR teams in the initial screening process.

---

## Workflow

```text
Gmail Trigger
↓
Get CV Attachment
↓
PDF Attachment Check
↓
Extract CV Text
↓
AI Resume Screener
↓
Parse AI JSON
↓
Prepare Sheet Row
↓
Save Result in Google Sheets
↓
Shortlist Check
├── Score >= 70 → Create Shortlist Draft
└── Score < 70 → Maybe Check
        ├── Score >= 50 → Create Maybe Draft
        └── Score < 50 → Create Rejection Draft
```

---

## Features

* Automated Gmail CV detection
* PDF attachment validation
* Resume text extraction
* AI-based resume screening
* Candidate score generation
* Candidate recommendation generation
* Google Sheets candidate tracker
* Gmail draft creation
* Shortlist, Maybe, and Reject workflow
* Human review support
* No automatic final hiring decision

---

## Tools and Technologies Used

* n8n
* Gmail
* Google Sheets
* AI Model
* PDF Extraction
* JavaScript Code Node
* Workflow Automation
* No-code / Low-code Automation

---

## Candidate Screening Logic

The AI agent evaluates candidates against predefined job requirements.

Example job role used in this project:

```text
Role: Architectural Engineer
Location: Riyadh
```

Job requirements:

```text
- Bachelor's Degree in Architecture
- Experience in architectural design
- Experience in engineering consultancy projects
- AutoCAD
- Revit
- SketchUp
- Good communication skills
- Riyadh role location fit
```

Scoring logic:

```text
85 - 100  = Strong Match
70 - 84   = Good Match
50 - 69   = Maybe / HR Review
Below 50  = Reject
```

---

## Google Sheets Tracker Columns

The screening result is saved in Google Sheets with the following fields:

```text
Date
Candidate Name
Email
Phone
Role Applied
Current Location
Current Job Title
Total Experience
Degree
Key Skills
Tools
Matched Requirements
Missing Requirements
Score
Recommendation
Reason
Human Review Required
CV File Name
Email Subject
Status
```

---

## Gmail Draft Responses

The workflow creates different Gmail drafts based on the candidate score.

### Shortlisted Candidate

Created when candidate score is 70 or above.

```text
Subject: Shortlisted for Architectural Engineer Position
```

### Maybe / HR Review Candidate

Created when candidate score is between 50 and 69.

```text
Subject: Application Under Review - Architectural Engineer
```

### Rejected Candidate

Created when candidate score is below 50.

```text
Subject: Update on Your Application - Architectural Engineer
```

---

## Screenshots

Add your project screenshots here.

### n8n Workflow

```text
screenshots/n8n-workflow.png
```

### Google Sheets Candidate Tracker

```text
screenshots/google-sheet-tracker.png
```

### Gmail Draft Response

```text
screenshots/gmail-draft-response.png
```

---

## Folder Structure

```text
AI-Resume-Screening-Agent-n8n/
│
├── README.md
├── workflow/
│   └── ai-resume-screening-agent.json
│
├── screenshots/
│   ├── n8n-workflow.png
│   ├── google-sheet-tracker.png
│   └── gmail-draft-response.png
│
├── sample-cvs/
│   ├── matched-candidate-cv.pdf
│   └── unmatched-candidate-cv.pdf
│
└── docs/
    └── workflow-steps.md
```

---

## How It Works

1. A candidate sends an email with a PDF CV attachment.
2. Gmail Trigger starts the workflow.
3. The workflow gets the email and downloads the CV attachment.
4. The IF node checks whether the attachment is a PDF.
5. The PDF text is extracted using the Extract From File node.
6. The AI model analyzes the resume against job requirements.
7. AI returns structured JSON data.
8. Code node parses the JSON response.
9. Candidate details are prepared for Google Sheets.
10. Google Sheets stores the screening result.
11. IF conditions check candidate score.
12. Gmail draft is created based on Shortlist, Maybe, or Reject status.

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/AI-Resume-Screening-Agent-n8n.git
```

### 2. Import n8n Workflow

Open n8n and import the workflow JSON file:

```text
workflow/ai-resume-screening-agent.json
```

### 3. Configure Gmail Credentials

Connect your Gmail OAuth2 account in n8n.

Required Gmail usage:

* Read incoming emails
* Download attachments
* Create Gmail drafts

### 4. Configure Google Sheets Credentials

Connect your Google Sheets account in n8n.

Create a Google Sheet with the required tracker columns.

### 5. Configure AI Model

Connect your preferred AI model in n8n.

Example models:

```text
OpenAI
Groq
Google Gemini
```

### 6. Test the Workflow

Send two test emails:

* One matched CV
* One unmatched CV

Expected results:

```text
Matched CV → Shortlist Draft
Unmatched CV → Rejection Draft
```

---

## Security Notes

Do not upload sensitive credentials to GitHub.

Never upload:

```text
- API keys
- Gmail OAuth tokens
- Real candidate CVs
- Real candidate emails
- Real phone numbers
- Private Google Sheet links
- Company confidential data
```

Use only sample CVs with dummy data.

---

## Future Improvements

* Support DOCX resumes
* Add multiple job roles
* Add HR approval workflow
* Add dashboard analytics
* Add candidate ranking system
* Add automatic labels in Gmail
* Add duplicate candidate detection
* Add interview scheduling integration
* Add Google Calendar integration
* Add recruiter notification through Slack or WhatsApp

---

## Disclaimer

This project is designed to assist HR teams in the initial resume screening process.

It does not make final hiring decisions.

Final candidate selection should always be reviewed and approved by humans.

The system should only evaluate job-related criteria such as skills, education, tools, experience, and role fit.

---

## Project Status

Completed MVP version.

Current workflow supports:

```text
PDF Resume Screening
Google Sheets Candidate Tracker
Gmail Draft Responses
Shortlist / Maybe / Reject Logic
```

---

## Author

Built by **Afshaan Haider**

Project Type: AI Automation / HR Tech / n8n Workflow Automation

---

## Tags

```text
n8n
AI Automation
HR Tech
Resume Screening
Workflow Automation
No Code
Low Code
Gmail Automation
Google Sheets Automation
PDF Extraction
```
