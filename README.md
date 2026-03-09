# Course_V1

DataLearn10X training website with multi-course pages, payment flow, access verification, and analytics.

## Testing offer pricing (current)
- Advance Excel: Offer ₹1
- Python: Offer ₹1
- Power BI: Offer ₹1
- Tableau: Offer ₹1
- SQL (MySQL): Offer ₹1
- Machine Learning + Deep Learning: Offer ₹1
- Data Analytics Cheat Sheets: Offer ₹1
- 20000+ HR Emails: Offer ₹1
- Data Analytics Combo (all courses + resources): Offer ₹1

## Website flow
1. User lands on `index.html`.
2. User selects one/multiple courses in cart or combo.
3. Payment is done via Razorpay.
4. Payment row is saved to Google Sheet via Apps Script `doPost` payload.
5. On success, user is redirected to `Excel_success_v3.html` with links.
6. Returning users verify via `check_email.html` (Google `doGet` with `email`).

## Apps Script compatibility
Frontend save now uses POST form fields matching provided Apps Script:
- `name, mobile, email, profession, course, total, discount, netpayment, payment_id, order_id, signature`

## Analytics files
- `analytics.js`
- `analytics_dashboard.html`


## Analytics dashboard login
- UserID: `DataLearn10X`
- Access key: `Owner@123`
