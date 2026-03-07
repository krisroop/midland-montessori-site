# Zapier Mapping: Formspree -> Google Sheets

## Zap Overview
- **Trigger App:** Formspree
- **Trigger Event:** New Submission
- **Action App:** Google Sheets
- **Action Event:** Create Spreadsheet Row

## Spreadsheet
- Spreadsheet name: `Tiffin Bay - Master Intake`
- Worksheet/tab: `Intake`

## Field Mapping
Map Formspree fields to Google Sheet columns:

- `submitted_at` <- Formspree submission timestamp
- `source` <- `intake_source` (fallback: `website_form`)
- `parent_name` <- `name`
- `email` <- `email`
- `phone` <- `phone`
- `preferred_contact` <- `preferred_contact`
- `child_name` <- `child_name`
- `child_dob` <- `child_dob`
- `preferred_start_date` <- `start_date`
- `days_needed` <- `days_needed`
- `message` <- `message`
- `consent_contact` <- `consent_contact`
- `status` <- static value `New`
- `owner` <- blank
- `last_contacted_at` <- blank
- `notes` <- blank

## Recommended Zap Filters
- Only continue if `email` is not empty
- Optional: require `consent_contact = on`

## Optional Secondary Zaps
1. **New row in sheet -> Gmail notification to admin**
2. **New row with status=New -> Slack/Discord alert**
3. **Scheduled daily digest of New + Follow-up records**

## Test Checklist
- Submit test form from live site
- Confirm row appears in sheet with all mapped fields
- Confirm status defaults to `New`
- Confirm no duplicate row created
