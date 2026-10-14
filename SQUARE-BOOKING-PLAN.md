# Square booking page cleanup plan

Status: **proposal only. Nothing has been changed in Square.** Each step needs the owner's yes before it is applied (see `CLAUDE.md`).

Based on a read-only review of the Square catalog on 2026-10-14.

## What's good

- Laser package prices in Square match the website's price finder (`main.js`) for every size and session count.

## Problems found

### 1. Free consult is not first
"Free consultation" and "Free phone Consultation" have no category, so they sit at the bottom of the booking page. The website sends everyone to "Book a free consult."

**Proposal:** new top category "Start Here: Free Consultation", ordered first, holding both consult services.

### 2. Fees and admin items show as bookable services
These are set as bookable appointment services with no category:
- Booking Deposit Fee ($25) and Booking Deposit Fee ($50): two items with the same name
- No Show Cancellation Fee ($25)
- Monthly Membership ($0)

**Proposal:** turn off online booking for all four (they stay usable at checkout). Owner to decide if one of the two deposit fees should be deleted.

### 3. Services missing a category
- Organic Coral Peel ($199), Vivant Chemical Peel ($300) → move to **Facials** (the site page is "Facials and Peels")
- Lymphatic Massage w/ Photo Therapy & RF Skin Tightening, 5 Sessions ($500) → move to **Lymphatic Post-Surgery**, next to the single and 10-session versions
- Electrolysis 30min 5 treatments ($260) → move to **Electrolysis**

### 4. Duplicate and empty categories
Two copies each of Facials, Massage, Electrolysis, Photo Therapy, Lymphatic Post-Surgery, Moisturizers, Toners, Intimate Skin Lightening and Package Deal. One copy of each holds the items; the others are empty. "Intimate Skin Lightening" and "Package Deal" are empty in both copies.

**Proposal:** delete the empty duplicates. Owner to confirm whether Intimate Skin Lightening and Package Deal are still offered.

### 5. Laser names are inconsistent
Same service, five naming styles: "Laser Hair Removal 4 sessions Small area", "Laser Hair Removal 12 Sessions Small Area", "X-Small 4 Treatments Laser Hair Removal", "Laser Hair Removal 1 Touchup Small Area", "X-Small Touch Up Laser Hair Removal Treatment".

**Proposal:** one pattern, sorted by size, using the website's size names:
`Laser Hair Removal: Small Area, 4 Sessions` … `Laser Hair Removal: Small Area, Touch-Up`
and keep "Unlimited 1 Year Laser Hair Removal Promo ($499)" at the top of the Laser category.

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
- **Body Contouring** (Cavitation & RF, 1 and 6 sessions): no variation is bookable online, but the site has a Body Contouring page. Turn booking on?
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

- Category order on the booking page may need to be set in the Square Dashboard (Appointments settings) rather than through the API. Check before promising it.
- Retail products (serums, cleansers, fajas) aren't on the booking page; they belong to the shop and are out of scope here.
