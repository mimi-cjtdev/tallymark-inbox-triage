# Test emails and expected results

Send these to the firm's inbox to test every path. "Known client" senders must match an `email` in the client directory. Use an address that isn't in the directory for the new-client test.

| # | From | Subject | Body | Expected category | Expected result |
|---|---|---|---|---|---|
| 1 | Harbor Bakery Co | Q3 bank statements | Hi! Attached are our July–September bank statements for the quarterly filing. Thanks! *(attach 1 PDF)* | `document_submission` | PDF saved to Harbor Bakery's folder as `YYYY-MM-DD - filename.pdf`, label `Triage/Documents`, reply draft |
| 2 | Harbor Bakery Co | Payroll records for November | Hi, please find attached our November payroll summary. Let me know if you need anything else. *(attach 2 PDFs)* | `document_submission` | **2** files saved, **1** reply draft |
| 3 | Ridgeline Plumbing | IRS penalty notice - need help by Friday | Hi, we just got a letter from the IRS saying we owe a late-filing penalty and have to respond by Friday. Can you please look at this ASAP? | `urgent_deadline` | Slack alert naming account manager **Jon**, label `Triage/Urgent`, reply draft |
| 4 | Solis Dental Studio | Charged twice for October? | Hi, it looks like we were billed twice for October bookkeeping. Could you check? | `billing_question` | Label `Triage/Billing`, reply draft |
| 5 | *Unknown sender* | Looking for a bookkeeper | Hi, I run a small café and need monthly bookkeeping and tax filing. What are your rates? | `new_client_inquiry` | Logged as `New / Unknown` and `Unassigned`, label `Triage/New Client`, reply draft, listed under **New leads** in the digest |
| 6 | Harbor Bakery Co | Thank you! | Thanks so much for your help this quarter! | `other` | `Triage/Processed` only, **no** reply draft |
| 7 | Solis Dental Studio | Audit letter received - response due in 3 days | Hi Maria, we just received a letter from the state tax department saying our 2025 sales tax return has been selected for review. They're asking for supporting documents within 3 business days. Can you help us figure out what to send? We're a bit worried. | `urgent_deadline` | Slack alert naming account manager **Maria**, reply draft with no tax advice or promised dates |

## Checks after every test

- **n8n Executions:** one successful run per email, with only the expected branch highlighted
- **Gmail:** the correct `Triage/…` label plus `Triage/Processed`, and a draft inside the original thread (except for "other")
- **Triage log:** one new row with the correct client, category and account manager
- **Re-running the workflow** without new emails processes nothing (duplicate protection)

## Results (live test, 23 Nov 2026)

All 7 emails were classified correctly. Confidence was 1.0 for documents, billing and urgent emails, and 0.95 for the new-client inquiry and the thank-you note.
