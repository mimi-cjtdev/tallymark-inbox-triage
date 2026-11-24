# Workflow exports

| File | Workflow |
|---|---|
| `client-inbox-triage.json` | Tallymark – Client Inbox Triage |
| `daily-inbox-digest.json` | Tallymark – Daily Inbox Digest |
| `error-alert.json` | Tallymark – Error Alert |

To import: in n8n, create a new workflow → **⋯ → Import from File**, then select your own credentials in each node and replace the placeholders below.

## Placeholders to replace

| Placeholder | Node(s) | What to put there |
|---|---|---|
| `YOUR_CLIENT_DIRECTORY_SHEET_ID` | Read Clients | Your client directory sheet (or pick it from the list) |
| `YOUR_TRIAGE_LOG_SHEET_ID` | Log to Sheet, Read Triage Log | Your triage log sheet (or pick it from the list) |
| `YOUR_UNSORTED_FOLDER_ID` | Client Context | Drive folder for attachments from unknown senders |
| `YOUR_SLACK_CHANNEL_ID` | Slack Urgent Alert, Post Digest, Post Error Alert | Slack channel ID (channel details → About → bottom) |
| `YOUR_LABEL_ID_DOCUMENTS` | Label: Documents | Re-select the `Triage/Documents` label from the list |
| `YOUR_LABEL_ID_BILLING` | Label: Billing | Re-select `Triage/Billing` |
| `YOUR_LABEL_ID_NEW_CLIENT` | Label: New Client | Re-select `Triage/New Client` |
| `YOUR_LABEL_ID_URGENT` | Label: Urgent | Re-select `Triage/Urgent` |
| `YOUR_LABEL_ID_PROCESSED` | Mark Processed | Re-select `Triage/Processed` |

Gmail label IDs are unique to each Gmail account, so the label nodes always need to be re-selected after import.

After importing all three, open the Triage and Digest workflows' **Settings → Error Workflow** and select your imported Error Alert workflow.

Credentials are never included in n8n exports. Each node only references a credential by name, and you'll connect your own.
