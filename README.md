# Purchase Request Approval Workflow (Microsoft Power Platform)

A personal project that digitises a manual purchase-request process end to end using SharePoint, Power Apps, Power Automate, Outlook and Power BI.

**Demo video:** [add your video link here]

## The problem
In many teams, purchase requests travel by email and spreadsheet. Requests get lost, approvers lack context, nobody can see what is pending, and there is no reliable view of spend by vendor or category.

## The solution
| Layer | Tool | What it does |
|---|---|---|
| Data | SharePoint list | Stores every request with item, category, amount (€), vendor, justification, status, approver comments and decision date |
| App | Power Apps (canvas) | Staff submit and track requests. Requester email and submitted date fill in automatically, status defaults to Pending, and approver-only fields are hidden on new requests |
| Workflow | Power Automate | Starts an approval when a request is created, then updates the SharePoint item (status, comments, decision date) and emails the requester on approval or rejection |
| Notification | Outlook | Approver receives an actionable approval email with request details and a link to the item |
| Insight | Power BI | Dashboard showing total requests, total spend, requests by status, spend by vendor and spend by category, with a category filter |

## How it works
1. A user submits a request in the Power Apps app. RequesterEmail, SubmittedDate and Status (Pending) are set automatically.
2. Power Automate triggers on the new SharePoint item and sends an approval with the item, amount, vendor, category, requester and justification.
3. The approver approves or rejects in Outlook and can add a comment.
4. A condition routes the outcome. The flow writes Approved or Rejected, the approver's comment and the decision date back to SharePoint and emails the requester.
5. The Power BI dashboard summarises the pipeline and spend.

## Web dashboard
`index.html` is a standalone dashboard of the same data (total requests, total spend, approval rate, average days to decision, status split, spend by vendor and category, and a request ledger with category filters).
- **Live demo:** [add your GitHub Pages link here]
- **Refresh:** export the SharePoint list with Export → Export to CSV, click **Refresh data** and choose the file. All figures recalculate in the browser. Nothing is uploaded anywhere.

## Business rules
- Amount and Justification are required.
- Status, approver comments and decision date are hidden on the new-request form and set only by the workflow.
- Requesters are notified of every decision with the approver's comment.

## Testing
- Approve path tested end to end: request created in app, approval actioned in Outlook, SharePoint status updated to Approved with comment and decision date, confirmation email received.
- Reject path tested end to end with a rejection email including the approver's comment.

## Screenshots
- `screenshots/app.png` – Power Apps request screen
- `screenshots/approval-email.png` – approval request in Outlook
- `screenshots/rejection-email.png` – rejection email sent to the requester
- `screenshots/flow.png` – Power Automate flow design and successful run
- `screenshots/sharepoint-list.png` – updated SharePoint list
- `screenshots/dashboard.png` – Power BI dashboard

## What I would add next
- Second-level approval for requests over €1,000
- AI-generated one-line summary of the justification for approvers
- Live Power BI connection to the SharePoint list with scheduled refresh
- Filter so requesters see only their own requests

## Skills demonstrated
Requirements and process design, SharePoint list design, Power Apps (Power Fx), Power Automate approvals and conditional logic, Outlook integration, Power BI reporting, end-to-end testing, solution documentation.

*Built by Nikhita Sulake as a personal learning project using sample data.*
