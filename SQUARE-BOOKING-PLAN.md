# Square booking page cleanup plan

Status: steps 1 to 5 **applied** on 2026-10-14 with the owner's approval and verified in Square. Everything else is still a proposal. Each step needs the owner's yes before it is applied (see `CLAUDE.md`).

Based on a read-only review of the Square catalog on 2026-10-14.

## What's good

- Laser package prices in Square match the website's price finder (`main.js`) for every size and session count.

## Problems found

### 1. Free consult is not first (DONE 2026-10-14)
"Free consultation" and "Free phone Consultation" have no category, so they sit at the bottom of the booking page. The website sends everyone to "Book a free consult."

**Done:** created category "Start Here: Free Consultation" (`TPF6XZ6JCSF2ELZJHFZO67JX`), visible online, sort order set below every other category. Both consults are in it. Still to check: that it actually shows first on the live booking page; if not, drag it up in Dashboard > Appointments > Services.

### 2. Fees and admin items show as bookable services (DONE 2026-10-14)
These are set as bookable appointment services with no category:
- Booking Deposit Fee ($25) and Booking Deposit Fee ($50): two items with the same name
- No Show Cancellation Fee ($25)
- Monthly Membership ($0)

**Done:** online booking turned off for all four. Prices, names and descriptions unchanged; they can still be charged at checkout. Still open: whether one of the two deposit fees should be deleted.

### 3. Services missing a category (DONE 2026-10-14)
- Organic Coral Peel ($199), Vivant Chemical Peel ($300) → move to **Facials** (the site page is "Facials and Peels")
- Lymphatic Massage w/ Photo Therapy & RF Skin Tightening, 5 Sessions ($500) → move to **Lymphatic Post-Surgery**, next to the single and 10-session versions
- Electrolysis 30min 5 treatments ($260) → move to **Electrolysis**

**Done:** all four moved into the populated copy of each category. Nothing else on them changed.

### 4. Duplicate and empty categories (DONE 2026-10-14)
Two copies each of Facials, Massage, Electrolysis, Photo Therapy, Lymphatic Post-Surgery, Moisturizers, Toners, Intimate Skin Lightening and Package Deal. One copy of each holds the items; the others are empty. "Intimate Skin Lightening" and "Package Deal" are empty in both copies.

**Done:** deleted the 8 empty copies (Facials, Massage, Electrolysis, Photo Therapy, Lymphatic Post-Surgery, Moisturizers, and the 2024 copies of Intimate Skin Lightening and Package Deal). Verified gone; the populated copies are intact.

Still open:
- Toners has two copies and both hold "Daily Repair Pads". Left alone.
- Intimate Skin Lightening and Package Deal (original 2020 copies, both empty): owner will decide later.

### 5. Laser names are inconsistent (DONE 2026-10-14)
Same service, five naming styles: "Laser Hair Removal 4 sessions Small area", "Laser Hair Removal 12 Sessions Small Area", "X-Small 4 Treatments Laser Hair Removal", "Laser Hair Removal 1 Touchup Small Area", "X-Small Touch Up Laser Hair Removal Treatment".

**Proposal:** one pattern, sorted by size, using the website's size names:
`Laser Hair Removal: Small Area, 4 Sessions` … `Laser Hair Removal: Small Area, Touch-Up`
and keep "Unlimited 1 Year Laser Hair Removal Promo ($499)" at the top of the Laser category.

**Done:** all 24 renamed and verified; prices, deposits, durations, descriptions and booking settings unchanged. The promo kept its name.

**Order did not apply:** Square ignored the sort order sent through the API (all 25 positions unchanged). The owner sets it by dragging in Dashboard > Items > Categories > Laser Hair Removal (or Appointments > Services): promo, then Extra-Small, Small, Medium, Large, Extra-Large, Full Body, each as 4, 8, 12 Sessions, Touch-Up.

### 6. Deposit math that doesn't add up
"Pay in full" minus "Deposit" should equal "Post Deposit":
| Service | Full | Deposit | Post deposit | Expected |
| --- | --- | --- | --- | --- |
| High Frequency / Microdermabrasion | $120 | $25 | $85 | $95 |
| Microdermabrasion Back Facial | $160 | $25 | $125 | $135 |
| Unlimited 1 Year Laser Promo | $499 | $0 | $474 | $499, or a $25 deposit |

Owner to give the correct numbers. No guesses.

### 7. Categories to check with the owner
- **Lash extensions** (Classic, Hybrid, Wispy): no variation is bookable online. Still offered? If not, archive.
- ~~Body Contouring not bookable~~ Correction: the first review misread this. The Pay in full and Deposit options for both Cavitation & RF services are bookable; only the Post Deposit option is off, same as most services. Nothing to do here.
- Category names with stray trailing spaces ("Acne Treatment ", "Body Contouring Treatments ", "Lash extensions ").

## Suggested booking page order

1. Start Here: Free Consultation
2. Laser Hair Removal
3. Electrolysis
4. Facials and Peels
5. Lymphatic Post-Surgery
6. Body Contouring
7. Massage
8. Photo Therapy
9. Add-ons (Singing Bowls, HydroJelly Mask, RF Skin Tightening add-on)

## Notes

- Sort order is not settable through the API: Square kept its own positions when item order was sent in step 5. Category and service order have to be dragged into place in the Square Dashboard. This likely applies to the "Start Here" category from step 1 too.
- Retail products (serums, cleansers, fajas) aren't on the booking page; they belong to the shop and are out of scope here.

## Step 7: booking page section labels (DONE 2026-10-14)

Renamed the service categories (the section headings on the booking page) to match the website's page names. Verified in Square; only the names changed.

| Before | After |
| --- | --- |
| Electrolysis | Electrolysis (Permanent Hair Removal) |
| Facials | Facials and Peels |
| Lymphatic Post-Surgery | Post-Op Lymphatic Massage |
| Body Contouring Treatments (trailing space) | Body Contouring |
| Massage | Swedish Massage |
| Photo Therapy | LED Light Therapy |
| Add on | Add-Ons |
| Lash extensions (trailing space) | Lash Extensions |

Unchanged: Start Here: Free Consultation, Laser Hair Removal, and all retail categories. Section order still has to be set by dragging in the Square Dashboard.

## Live booking page check (2026-10-14)

Checked the live page at phone size (`book.squareup.com/.../services`) after steps 1 to 7.

- Her booking page is **one flat list with no section headings**. Category names (steps 1 and 7) don't show there; they only affect Square reports, POS and the Square Online store.
- Order is Square's own, not category order: 60min Swedish Massage is first, the free consults are about two-thirds down, and the $499 promo is last. Order has to be set by dragging in Dashboard > Appointments > Services (or the booking site settings).
- Fees and the $0 membership are gone (step 2 worked).
- Laser names show the new pattern (step 5 worked).
- **Almost every service shows "Price varies"**, including both free consults. Square shows that whenever a service has more than one price option (Pay in full / Deposit / Post Deposit), or uses variable pricing (the consults). Services with one fixed price show it (Singing Bowls $7.00, Organic Coral Peel $199.00).

Proposed next fixes (need owner approval):
- Free consults: change from variable pricing to a fixed $0 so they stop saying "Price varies".
- Check in Dashboard whether the booking site has a "group services by category" or ordering option.
