Accel Biz in 10 minutes - prototype (Airtel Sync 2026 | Digital Track | Team Nebula, Vellore Institute of Technology)
- Without an API key the free-text advisor uses an offline keyword reader (English only), labelled 'not AI'. Add a free Gemini key to see the AI version.
- Typed advisor text is sent to the chosen AI provider. Do not type phone or ID numbers.
- The advisor asks four questions; city comes from the lead record.

Run: open index.html (double-click), or in this folder: python -m http.server 8000 -> http://localhost:8000
Demo flow: K03 (happy path) -> K07 (name mismatch, fix twice, hand-off) -> K04 (blurry photo, fixed on re-upload) -> K11 (old bill, fixed).
Data: real case pack (registries, catalogue, specimen documents K01-K12). All synthetic.

NEW in this version
1. AI advisor (free text). On the advisor screen the owner can type a description instead of tapping. A GenAI model reads it and fills the same four answers the taps fill; the rules engine then picks the bundle from the catalogue, so every bundle still passes the catalogue rules. Anything it cannot tell is left to the tap questions.
   - Choose the provider in the left panel: Google Gemini (a free key from aistudio.google.com, rate-limited, no billing needed) or Anthropic Claude (paid API key). Paste the key; it is kept in this browser tab only and never saved to a file. Model names are editable in the panel (defaults: gemini-2.5-flash, claude-sonnet-5-5); set them from your own console's model list if one is rejected.
   - No key, no internet, or a bad reply: a free offline keyword reader fills what it can and the chat labels it "Offline keyword reader, not AI". It is English only. Otherwise the tap questions work as before.
   - Only the typed text is sent. The owner's name, contact and documents are never sent. Note: Google says free-tier requests may be used to improve its products; the privacy note should mention that typed text goes to an AI service.
2. Referral step. After the order, "Know another small office?" gives a share link (WhatsApp or copy). The link is a placeholder (accelbiz.example).
3. Pilot metrics. "Pilot metrics" in the left panel opens a dashboard computed live from the journeys run in this tab: started, verified, ordered, handed to a person, conversion, days to go live, follow-up calls, time to order, cost per customer. Today and target columns come from the deck. Cost per customer uses the deck's channel costs as assumptions. The side-panel "Chase calls" and "Days to order" now update live.
4. Hand-off triggers now: failed twice, owner asks, GST-only add-on chosen without a GST number (answer "No" to the GST question, then tap a locked add-on), and stalled order (no activity for the timer on the price, consent, verify or pay screens; default 120 s, change it in the left panel, or press "Simulate stalled order"). 16+ staff only shows a soft "specialist will also call" note; it does not force a hand-off (the deck says the same).

Known limits
- Fix behaviour is scripted: K04, K05 and K11 pass on re-upload; K01, K06 and K07 always fail again. The ID check always passes. Consent is displayed but nothing is logged.
- The "200+" sharpness threshold in the blur message is our own choice.
- Hindi, Marathi and Tamil text is not yet checked by a native speaker (new strings in this version included).
- Camera-photo OCR loads Tesseract.js from the internet on first use.

- Language picker: ten languages are listed. English, Hindi, Marathi and Tamil are fully built. Tapping one of the other six shows a short 'coming soon' notice and stays in the current language.
