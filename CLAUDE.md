# Notes for Claude

## Square: approval rule

**Never change anything in Square without the owner's explicit approval.**

- Reading Square (catalog, bookings, sales, customers) is fine.
- Any write (create, update, delete, rename, re-categorize, price change, booking setting, inventory, refund, anything) needs a preview first: show exactly what will change, before and after, then wait for a clear "yes" to that specific preview.
- A general request like "organize the store" is not approval for individual changes.
- After an approved change, read it back from Square and report only what the read confirms.

The booking-page cleanup plan lives in `SQUARE-BOOKING-PLAN.md`. Steps 1 to 5 were applied on 2026-10-14; the rest is not applied yet.

## Square account

- Location: Relax and Cruz spa, `LR7VH9PK37BJG`, America/New_York
- Booking page: `https://book.squareup.com/appointments/5c3y8w34fg9goo/location/LR7VH9PK37BJG/services` (linked from every Book button on the site)
- Laser prices in `main.js` (`TIERS`) must match the Square laser packages.
