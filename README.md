Accel Biz in 10 Minutes

One app where a small office is advised, priced, verified and tracked in about 10 minutes, with a person stepping in only when needed.

A clickable, browser-based prototype of a mobile journey that takes a small Indian office from first contact to a paid first order for an Airtel Accel business bundle (broadband, business SIMs, email and security), without a salesperson visit.

All data in this repository is synthetic. Registries, payment, billing, consent logging and encryption are simulated.

Table of contents
The problem
The solution
Features
Quick start
Demo walkthrough
Bundles and pricing
Hand-off to a person
AI advisor setup (optional)
Pilot metrics dashboard
Sample applicants (K01 to K12)
Project structure
Architecture
Privacy and trust
Known limitations
Pilot plan and targets
Team
The problem

From a sample of 5,000 leads (Apr to Jun 2026, case data), Accel is not mainly losing small offices on price. It is losing them at five "not now" moments:

Where the lead is lost	Lost
Can't get hold of them	1,124
No time for a visit	827
Price or a cheaper rival	621
Quote slow or confusing	385
Paperwork stalls	273
Install or payment slips	126
59% of lost businesses left at one of the five moments (2,735 of 4,632).
Only 13% left over price or a cheaper rival (621).
Today it takes 17.6 days and about 3 chase calls from first contact to go-live.
The solution

A six-step phone journey where each step removes one "not now" moment:

#	Step	Owner does	App does	Fixes
1	Advise	Answers 4 quick questions or types a sentence	Picks Lite, Standard or Plus	No time for a visit
2	Price	Toggles add-ons	Shows one monthly price	Slow or confusing quote
3	Agree	Accepts consent	Logs purpose and time	Trust (DPDP Act 2023)
4	Verify	Photographs documents	Checks them and names the exact fix	Paperwork stalls
5	Pay	Confirms and pays	Creates order, books install	Payment failures
6	Track	Opens the status page	Sends status updates	Install delays

Target: a first order in about 10 minutes, against 17.6 days and about 3 chase calls today.

Features
Rules-based advisor. Four tap questions (kind of office, headcount, number of work numbers, GST yes/no). City comes from the lead record and decides availability (for example Fibre 1G is Tier 1 only).
Optional AI free-text advisor. The owner can type a sentence instead. A GenAI model fills the same four answers, and the rules engine still picks the bundle from the catalogue, so every bundle passes catalogue rules.
Offline fallback. With no key, no internet or a bad reply, an English-only keyword reader fills what it can and is clearly labelled "not AI".
Single-price quote with add-ons. WhatsApp, SMS and calling add-ons unlock once GST is verified.
Consent first. Purpose and time are shown before any document is taken.
Automated document checks with specific fix messages (GSTIN lookup and checksum, name match, image sharpness, address-proof age, required-documents checklist, empty-field check).
Camera OCR for GSTIN extraction using Tesseract.js, with look-alike character correction (for example O/0, I/1).
Hand-off router that passes hard cases to a field agent with the case pre-filled.
Order tracker with a simulated install slot and live status.
Referral step after the order ("Know another small office?") with a WhatsApp or copy-link share. The link is a placeholder (accelbiz.example).
Live pilot metrics dashboard computed from the journeys run in the current browser tab.
Multilingual UI. English, Hindi, Marathi and Tamil are built. Six more languages are listed with a "coming soon" notice.
Quick start

No build step and no dependencies. It is plain HTML and JavaScript.

Option 1: open directly

Double-click index.html.

Option 2: serve locally (recommended)

bash
git clone https://github.com/Harshio1/Accel-biz.git
cd Accel-biz
python -m http.server 8000

Then open http://localhost:8000.

Serving over http://localhost is recommended over opening the file directly, because some browsers restrict camera access and cross-origin API calls from file:// pages. If the repo keeps the app inside a subfolder (for example airtel_biz_prototype/), cd into that folder first.

Requirements: a modern desktop browser. Internet is only needed for the optional AI advisor and for first-use loading of Tesseract.js (camera OCR).

Demo walkthrough

Pick an applicant from the left panel, then follow the journey. Suggested demo order:

Applicant	What it shows
K03 Ganesh Woodcraft	Happy path: everything passes first time
K07 Neelgiri Physio	Name mismatch, fails twice, hand-off to a person
K04 Saffron Dental Care	Blurry GST photo, fixed on re-upload
K11 Trinity Bake House	Electricity bill too old, fixed on re-upload

Other things to try:

On the advisor screen, type a sentence instead of tapping.
Answer "No" to the GST question, then tap a locked add-on to trigger a hand-off.
Press "Simulate stalled order" in the left panel to trigger the stalled-order hand-off.
Open "Pilot metrics" after running a few journeys.
After ordering, try the referral share step.
Bundles and pricing

Starting prices sit at the low end of Accel's catalogue price range, on a 12-month contract with ₹0 setup. Every bundle is built from the 25-product catalogue and passes its rules.

Bundle	Staff	Price / month	Includes
Office Lite	up to 8	₹2,222	Biz Fibre 100, 2 business SIMs, email (5 users)
Office Standard	9 to 15	₹4,337	Biz Fibre 300, 2 business SIMs, email (10 users), antivirus (10 devices)
Office Plus	16+	₹10,775	Fibre 1G (or 300), 3 business SIMs, email (20 users), antivirus (20 devices), 1 TB backup

Add-ons that require a GST number stay locked until GST is verified.

Hand-off to a person

People step in only where they add value. The hand-off sheet arrives pre-filled with the business, contact, bundle and failure reason.

Trigger	How to see it in the prototype
A document fails twice	Run K07 and re-upload
Owner asks for a person	Use the help option on any screen
GST-only add-on without GST	Answer "No" to GST, tap a locked add-on
Stalled order (no activity on price, consent, verify or pay)	Wait for the timer (default 120 s, editable) or press "Simulate stalled order"

Offices with 16+ staff only get a soft "a specialist will also call" note. It does not force a hand-off.

Why save people for these cases: cost per customer won is about ₹11,100 via partner, ₹4,000 via field sales and ₹1,100 via referral.

AI advisor setup (optional)

The advisor works without any key. To try the AI version:

In the left panel, choose a provider:
Google Gemini: get a free key from aistudio.google.com (rate-limited, no billing needed).
Anthropic Claude: paid API key.
Paste the key. It is kept in this browser tab only (session storage) and is never written to a file.
Optionally edit the model name. Defaults are gemini-2.5-flash-lite and claude-sonnet-5-5. If a model is rejected, use one from your own console's model list.
On the advisor screen, type a description such as "We are a 10-person dental clinic in Kolkata, need two work numbers, we have GST."

What is sent: only the typed text. The owner's name, contact details and documents are never sent. Do not type phone or ID numbers. Google notes that free-tier requests may be used to improve its products.

Never commit an API key to this repository.

Pilot metrics dashboard

Open "Pilot metrics" from the left panel. It is computed live from journeys run in the current tab and shows: started, verified, ordered, handed to a person, conversion, days to go live, follow-up calls, time to order and cost per customer. "Today" and "target" columns come from the project deck. Cost per customer uses the deck's channel costs as assumptions. Metrics reset when the tab is closed.

Sample applicants (K01 to K12)

Twelve synthetic applicants with specimen documents (GST certificate, Udyam certificate, ID and electricity bill) live in docs/. Seven have deliberate problems; five match the registry.

Applicant	Problem	Check that catches it
K01 Vindhya Tours	GST cancelled in registry; Udyam number blank	GSTIN status lookup; empty-field check
K02 Harmony Dental	GST certificate tilted (details match)	Straighten the image or ask for re-upload
K04 Saffron Dental Care	GST certificate very blurry	Image-quality check, ask to retake
K05 Balaji Realty	Udyam certificate missing	Required-documents checklist
K06 Saffron Unisex Salon	GSTIN has one digit different from the registry	Exact GSTIN lookup
K07 Neelgiri Physio	Name "Shri Physio Clinic" vs "Neelgiri Physio Clinic"	Name-match check
K11 Trinity Bake House	Electricity bill dated 31 Oct 2025 (over 250 days old)	Address-proof date check (90 days)

K03, K08, K09, K10 and K12 match the registry.

Project structure
.
├── index.html      # The whole app: UI, journey logic, checks, AI advisor, metrics
├── data.js         # window.DATA: 12 applicants (apps), GST/Udyam registries (reg), 25-product catalogue (cat)
├── docs/           # Specimen documents K01 to K12 (GST, Udyam, ID, bill), all synthetic
└── README.txt      # Original prototype notes

Tech: vanilla HTML, CSS and JavaScript. No framework and no build tooling. Tesseract.js 5.1.1 is loaded from a CDN on first use of camera OCR. Optional calls go to the Gemini or Anthropic APIs directly from the browser.

Architecture

The deck's target architecture is a layered set of simple modules with one clear data flow and security on every layer:

Users: business owner, field agent or partner, Airtel operations team.
Mobile app: advisor chat, price and bundle, upload and check, order tracker, agent console.
Services: rules engine, pricing, KYC verification, order and activation, hand-off router, notifications.
Data and systems: product catalogue, lead and order database, document store, GST and Udyam registries, Airtel billing, payment gateway.
Analytics: metrics dashboard.
Cross-cutting: consent, encryption, access control, audit log.

Data flow: Advise and price → Consent → Verify → Order → Track and hand off.

In this prototype everything runs client-side. Registries, payment, billing, consent logging and encryption are simulated.

Privacy and trust

Designed around the DPDP Act 2023:

Consent is requested before any document is taken.
Only needed data is collected, and IDs are masked on screen.
Encrypted storage and an audit log are part of the target design (not implemented in this prototype).
Typed advisor text goes to an AI service, and owners are told not to type phone or ID numbers.
