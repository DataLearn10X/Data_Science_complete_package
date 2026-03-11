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


## After copying this website to a new repository
Update these values first so links and integrations work correctly:
- `config.js`
  - `SHEET_WEBAPP_URL`: your Google Apps Script Web App URL
  - `WHATSAPP_NUMBER`: your support number in international format (e.g. `91XXXXXXXXXX`)
  - `WHATSAPP_TEXT`: default WhatsApp prefilled message
  - `AD_IMAGES_BASE_URL`: your GitHub folder base URL (Raw), e.g. `https://raw.githubusercontent.com/<user>/<repo>/<branch>/ads`
  - `AD_IMAGES`: image file names from that folder OR full image URLs

Example with a GitHub folder:
```js
AD_IMAGES_BASE_URL: "https://raw.githubusercontent.com/your-user/your-repo/main/ads",
AD_IMAGES: ["ad1.jpg", "ad2.jpg", "ad3.jpg"]
```

All pages read these values automatically (`index.html` and `check_email.html`).

## Advertisement slider (image size + adding 5 ads)
- Slider display ratio is **16:5** (set in CSS as `aspect-ratio:16/5`), so use banners in the same ratio for best fit.
- Recommended ad image size: **1600 x 500 px** (or any 16:5 size such as 1280x400, 1920x600).
- Put ad images inside the `ads/` folder.
- Then update `config.js` -> `AD_IMAGES` with each file name.

Example for 5 ads:
```js
AD_IMAGES_BASE_URL: "ads",
AD_IMAGES: ["ad1.jpg", "ad2.jpg", "ad3.jpg", "ad4.jpg", "ad5.jpg"]
```

> Important: in the current static setup, ads are **not auto-discovered** from folder contents.
> You must list each file in `AD_IMAGES` for it to appear in the slider.
> The slider now auto-checks each configured file and skips broken/missing paths, so one wrong filename will not break the whole rotation.

### Quick sync after renaming ad files
If you rename/add/remove files inside `ads/`, run:
```bash
python3 scripts/sync_ads_config.py
```
This updates `config.js` -> `AD_IMAGES` to match current files in the folder.

