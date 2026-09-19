# Azure Refund Request Process

How to get a refund from Microsoft for an Azure billing charge, using Claude + the Chrome browser skill.

## 1. Find the invoice

Invoices show up on the Desktop as PDFs named like `G183360200.pdf`. Read the PDF to get:
- Invoice number (e.g. `G183360200`)
- Total amount
- Billing period (e.g. `08/01/2026-08/31/2026`)
- Charge breakdown (e.g. Security $86.36, Networking $6.49)

## 2. Try the self-service refund tool first

Navigate to:
```
https://portal.azure.com/#view/Microsoft_Azure_GTM/RefundRequestOverview.ReactView/subscriptionId/<SUBSCRIPTION_ID>
```

Fill in: Invoice ID, Reason for refund, then Transactions tab → select all → Review + Submit.

**Note:** This tool has a hidden "expedited refund" limit per billing account. After the first refund in a session (or period), it will say **"Expedited refund limit reached — Submit a support request to get a refund"** for every subsequent request. This is expected, not an error — proceed to step 3.

Tip: the blade's "..." menu → "Toggle full-screen view" gives much more usable space and made clicking reliable in a small browser window.

## 3. File a support ticket instead

When you hit the limit, click **"Submit a support request"**. This will appear to dump you on the Azure Home page — that's normal. Check the notification bell (top right); if a ticket was actually created, you'll see a "New Support Request" notification with a ticket ID within a few seconds.

### If it goes to the wrong place, or you want to start a ticket directly

Navigate to:
```
https://portal.azure.com/#view/Microsoft_Azure_Support/NewSupportRequestV4Blade
```

Fill in the wizard:
- **Issue type:** Billing
- **Subscription:** (the one that incurred the charge)
- **Summary:** e.g. "Refund request for invoice G176921491"
- **Problem type:** Credit request
- **Problem subtype:** "Help with credit request for a scenario not listed"
- Click **Next**

### The "Solutions" trap

Clicking Next almost always opens a **"Solutions" self-help overlay** on top of the wizard, with a link that says **"Return to support request."** This link is often completely unresponsive to clicks/double-clicks/keyboard nav — this cost the most time in this process.

**The fix:** don't click "Return to support request." Instead, click the overlay's own **X (close) button**, top right. This closes the Solutions overlay and reveals the actual wizard underneath, already sitting at **"2. Recommended solution"** with working Previous/Next buttons. Click **Next** again to proceed normally to "3. Additional details."

### Filling in "3. Additional details" (Credit request subtype)

Fields that show up for a credit request:
- **Problem start date:** first day of the billing period, time `12:00 AM`
- **Accidentally incurred charges (Y/N)?** → `Y`
- **Confirm account type requesting credit** → Paid (for a pay-as-you-go sub) / Free (for a trial)
- **Requested credit amount** → the invoice total
- **Reason for the credit** → "Inexperienced user issue (misunderstood pricing, service left on, etc.)" fits "forgot to cancel a resource"
- **Related Azure service** → pick whichever charge category is largest (e.g. "Identity and security" for Security charges, "Networking" for Networking charges)
- **Provide additional details** → free text, e.g.:
  > I am requesting a refund of $X for invoice <ID> (billing period <dates>), covering <charge breakdown> on subscription "<name>" (<id>). These charges were incurred because I forgot to cancel/delete the associated resources. Please process a refund for the full invoice amount.
- **Allow collection of advanced diagnostic information?** → No (not needed for a billing issue)
- **Preferred contact method** → Email

Click **Next** → review the "4. Review + create" summary → click **Create**.

### Confirming it worked

Like the refund-tool submit, clicking Create redirects to Azure Home. Check the notification bell — a "New Support Request" notification with a ticket ID (e.g. `2609190040001441`) confirms success. You can also check under Help + support → All support requests.

## Known flakiness notes

- Dropdowns and text fields in these Azure blades sometimes don't register the first click — if nothing happens, just click again (2nd or 3rd click usually works).
- If a search/text field seems to eat your typed text or select the whole page instead, double-click into the field first to force focus before typing.
- The browser window/viewport in automated sessions can be very short — use the "..." → "Toggle full-screen view" option on a blade when you need more vertical room to see Next/Submit buttons.
