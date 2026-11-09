# Accel Biz in 10 Minutes

A prototype mobile app where a small office is **advised, priced, verified and tracked in about 10 minutes**, with a person stepping in only when needed.

> All data is synthetic. Registries, payment, billing and consent logging are simulated.

## The problem

Small offices are rarely lost on price. In a sample of 5,000 leads, only 13% left over price or a cheaper rival, while 59% dropped off at five "not now" moments: couldn't be reached, no time for a visit, slow or confusing quote, paperwork delays, and install or payment slips. Today that means about 17.6 days and 3 chase calls from first contact to go-live.

## The solution

One phone app that handles the whole journey:

1. **Advise:** the owner answers 4 quick questions or types a sentence, and the app picks a bundle
2. **Price:** one monthly price in plain words, with add-ons
3. **Agree:** consent is shown and accepted before any document is taken
4. **Verify:** the owner photographs documents; the app checks them and names the exact fix if something fails
5. **Pay:** the owner pays in the same sitting and the install is booked
6. **Track:** live order status, with a person available if the owner is stuck

**Target:** a first order in about 10 minutes.

## Key features

- **Rules-based advisor:** a rules engine picks the bundle from the product catalogue, so every bundle follows catalogue rules
- **Free-text advisor:** the owner can type a sentence instead of tapping; an AI model fills in the same answers, with an offline keyword reader as fallback
- **Automated document checks:** GSTIN lookup, name match, image sharpness, address-proof age and a required-documents checklist
- **Human hand-off:** a field agent takes over when a document fails twice, an order stalls, a GST-only add-on is chosen without GST, or the owner asks for help. The case arrives pre-filled
- **Multilingual:** English, Hindi, Marathi and Tamil
- **Pilot metrics dashboard:** conversion, time to order, hand-offs and cost per customer, computed live

## Bundles

| Bundle | Staff | Price / month |
|---|---|---|
| Office Lite | up to 8 | ₹2,222 |
| Office Standard | 9 to 15 | ₹4,337 |
| Office Plus | 16+ | ₹10,775 |

## Files

- `index.html`: the app
- `data.js`: sample applicants, GST/Udyam registries and the product catalogue
