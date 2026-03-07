# Phase 3 Intake Workflow (Single Stream)

## Goal
Capture all parent inquiries in one master pipeline so nothing gets lost across forms, emails, texts, or PDFs.

## Primary Intake Path
- Website form on `https://midland-montessori.ca/`
- Form action: Formspree endpoint (`/f/meelngga`)
- Primary source tag: `website_primary_registration_form`

## Master Pipeline System
Use one Google Sheet named: **Tiffin Bay - Master Intake**

### Required columns
1. submitted_at
2. source
3. parent_name
4. email
5. phone
6. preferred_contact
7. child_name
8. child_dob
9. preferred_start_date
10. days_needed
11. message
12. consent_contact
13. status
14. owner
15. last_contacted_at
16. notes

Default values:
- status = `New`
- owner = blank

## Intake Rules
1. **Forms (primary):** Auto-create row via Zapier/Make.
2. **Email inquiries:** Staff creates a row manually and sets source=`email_manual`.
3. **Text inquiries:** Reply with website form link; if details already provided, create row with source=`text_manual`.
4. **PDF submissions:** Store PDF in Drive folder and create row with source=`pdf_email` + link in notes.

## SLA / Follow-up
- New records should be contacted within **1–2 business days**.
- Any `status=New` older than 48h should be reviewed daily.

## Status Pipeline
- New
- Follow-up
- Waitlist Confirmed
- Offered Spot
- Enrolled
- Closed

## Daily Operations Checklist
- [ ] Filter rows where status = New
- [ ] Assign owner
- [ ] Send response/update
- [ ] Update last_contacted_at
- [ ] Move status forward

## Weekly Review
- [ ] Count new leads this week
- [ ] Count response time >48h
- [ ] Identify drop-off reasons in notes
- [ ] Update FAQ/copy if repetitive questions appear
