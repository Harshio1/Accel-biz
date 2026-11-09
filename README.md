# Accel Biz in 10 Minutes

A clickable prototype of a mobile app where a small office is **advised, priced, verified and tracked in about 10 minutes**, with a person stepping in only when needed.

> All data is synthetic. Registries, payment, billing, consent logging and encryption are simulated.

## The idea

Small offices are rarely lost on price. They drop off at "not now" moments: they can't be reached, have no time for a visit, get a slow quote, hit paperwork delays, or face install and payment slips. Today this takes about 17.6 days and 3 chase calls from first contact to go-live.

Accel Biz moves the whole journey into one phone app.

1. **Advise:** answer 4 quick questions, or type a sentence
2. **Price:** see one monthly price and toggle add-ons
3. **Agree:** give consent
4. **Verify:** photograph documents; the app checks them and names the exact fix
5. **Pay:** confirm and pay in the same sitting
6. **Track:** follow live order status

**Target:** a first order in about 10 minutes.

## Bundles

| Bundle | Staff | Price / month |
|---|---|---|
| Office Lite | up to 8 | ₹2,222 |
| Office Standard | 9 to 15 | ₹4,337 |
| Office Plus | 16+ | ₹10,775 |

## Run it

No build step or dependencies.

```bash
git clone https://github.com/Harshio1/Accel-biz.git
cd Accel-biz
python -m http.server 8000
```

Open http://localhost:8000, or just double-click `index.html`.

## Try the demo

Pick an applicant in the left panel:

- **K03:** everything passes first time
- **K07:** name mismatch, fails twice, handed to a person
- **K04:** blurry photo, fixed on re-upload
- **K11:** old electricity bill, fixed on re-upload

## Optional AI advisor

Typing a sentence works offline with a basic keyword reader. For the AI version, paste a free Google Gemini key (from aistudio.google.com) or an Anthropic key in the left panel. The key stays in your browser tab only. Only the typed text is sent, so don't type phone or ID numbers.

## Files

- `index.html`: the app
- `data.js`: sample applicants, GST/Udyam registries and the product catalogue
