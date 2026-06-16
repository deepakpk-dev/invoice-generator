# SwiftInvo — invoices for freelancers

A free, private invoice generator. Fill in a form, get a clean, professional PDF invoice. **No account, no server, no tracking** — everything runs in your browser and your data never leaves your device.

Built for freelancers, by a freelancer. Free to use, free to fork.

## Features

- **Live paper preview** — see the finished invoice update as you type
- **Saved business profile** — your name, logo, contact details, default currency and payment terms reused on every invoice
- **Brand Kit** — white-label your invoices: pick a preset look (Ledger / Mono Studio / Bold Modern), then fine-tune the accent color, font pairing, layout, thank-you line, and footer text. Saved once, applied to every invoice and PDF
- **Saved clients** — pick a client once, reuse forever
- **Line items** with quantity × rate, plus discount (% or flat) and tax (%)
- **Invoice history** with Draft / Unpaid / Paid status, plus automatic **Overdue** when an unpaid invoice passes its due date
- **Duplicate** any past invoice as a starting point for the next one
- **11 currencies** (USD, EUR, GBP, INR, CAD, AUD, JPY, SGD, AED, BRL, ZAR)
- **Download as PDF** via your browser's print dialog (choose "Save as PDF")
- **Backup & restore** — export everything to a JSON file, import it on any device
- Works **offline**, responsive on mobile, keyboard-accessible, respects reduced-motion

## Use it

Just open `index.html` in any modern browser. That's it — it's a single self-contained file.

To download a PDF: click **PDF**, then in the print dialog choose **Save as PDF** as the destination.

## Host it (free)

Because it's one static file, you can publish it anywhere for free:

- **GitHub Pages** — push this folder, enable Pages
- **Netlify / Vercel / Cloudflare Pages** — drag-and-drop the folder
- Or just email `index.html` to a friend

## Privacy

SwiftInvo stores your business profile, clients, and invoices in your browser's `localStorage`. Nothing is uploaded anywhere — there is no backend. Clearing your browser data will erase your invoices, so use **Export a backup** periodically.

## Tech

Plain HTML, CSS, and vanilla JavaScript. No build step, no dependencies, no frameworks. Fonts (Fraunces, Inter, JetBrains Mono) load from Google Fonts; everything else is local.

## License

MIT — do whatever you like with it.
