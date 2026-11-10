# Sale Promo Planner

Sharp Ninja Academy. A step-by-step planner a mentee fills out on their own phone to plan a Cutco
Sale Promo: dates, channels (mail, email, text, voice drop, extension), the phone plan, a day-by-day
game plan, the launch checklist, the call-list routine (CRM or Google Sheet), and their numbers.

Live: https://allinalan.github.io/sna-sale-promo/

Built on the Sale Promo Max method from Vast Action, Inc., written in our own words. Do not paste
Vast Action's PDFs or worksheets into this repo: they are marked "do not copy without written approval".

## Alan's rules the page enforces
- Under 500 customers: the rep calls every customer personally and follows up with every one
  (`CALL_EVERYONE_UNDER`). The phone plan defaults "customers to call" to the whole list.
- Texting from their own iPhone: 50 texts a day, no more (`IPHONE_PER_DAY`). Step 4 splits each text
  into 50-a-day batches and step 2 flags dates that overlap.
- No CRM: recommend one by emailing Vast Action at lifesrabbithole@gmail.com (pre-filled mailto).

## How it works
- The whole app is `index.html`. No build, no server, no accounts.
- The plan saves in the browser's `localStorage` (key `sna-sale-promo-v1`) on the mentee's own
  device. Nothing is sent anywhere; coaches see it only when the mentee turns in their plan link.
- **Plan link**: the page URL plus `#d=<the plan, base64>`. A `#fragment` never reaches a server.
  Opening it loads the plan (asks first if the device has one). It is outside input: `clean()`
  rebuilds it through the `F` schema with type and length caps, and typed text never reaches
  `innerHTML` (rules and verdicts are built from numbers and fixed strings only).
- **Download my plan (PDF)**: jsPDF 2.5.1 from cdnjs (pinned, with SRI) builds a real PDF file.
  If it fails to load, the button falls back to `window.print()` with a print stylesheet.
- This repo is PUBLIC (required for GitHub Pages). Never commit names, phone numbers, emails or keys.
- Deploy: edit `index.html`, commit, push to `main`. Pages serves the repo root in about a minute.

Known limits of on-device saving (same as the Design Your Life worksheet): Private mode does not save
(the page says so), a different browser or phone starts blank, and iPhone Safari clears data for a
site not opened in 7 days. The plan link and the PDF are the backups.
