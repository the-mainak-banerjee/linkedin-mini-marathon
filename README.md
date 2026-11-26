# LinkedIn Mini Marathon: landing page

Landing page for the **LinkedIn Mini Marathon** by Reputation Tribe: 6 live sessions from 5 to 23 December, plus D-Day on 26 December.

This is a finished design built as a single HTML file. The plan is to convert it to Next.js.

- **Live preview:** https://claude.ai/artifact/D5JGmg1peHSq41DSuYrrhT

## What's in the repo

```
landing/
  index.html        The whole page: HTML, CSS and JavaScript in one file
  assets/
    bhawin.png          Hero and host photo (transparent cut-out)
    bhawin-outline.png  Blue outline drawn behind Bhawin's hero photo
    mainak-tee.png      Host photo (transparent cut-out)
    virat-v2.png        Host photo (transparent cut-out)
```

Fonts come from Google Fonts (Poppins and Inter). Every illustration on the page is inline SVG inside `index.html`, so there are no icon files.

> **Note:** `index.html` has no `<!doctype>`, `<html>`, `<head>` or viewport tag, because the preview host adds them. Next.js adds these for you. If you open the file on its own, wrap it in a normal HTML skeleton with `<meta name="viewport" content="width=device-width, initial-scale=1">`.

## Brand

| Token | Value | Use |
|---|---|---|
| Tribe Blue | `#0A66C2` | Key words, "in" logo box, links |
| Spark Yellow | `#FFE11B` | Buttons, "Mini" sticker, highlights |
| Ink | `#111111` | Headlines, button text |
| Paper | `#F6F8FC` | Page background |
| Body Grey | `#1F2937` | Paragraphs |
| Muted Grey | `#4A5568` | Secondary text |
| Divider / Card border | `#A0AEC0` / `#E1E8F3` | Lines, card outlines |

- **Headings:** Poppins 700/800. **Body:** Inter 400–600.
- **Buttons:** flat yellow, no border and no shadow.
- **Logo:** the "in" sticker is tilted +6° and the "Mini" sticker −6°, both with an ink border and a small offset shadow. The sticky header shows only these two stickers.

All colours are CSS variables at the top of the `<style>` block.

## Page sections, in order

1. **Sticky header:** "in + Mini" logo, nav links, Register button.
2. **Hero:** logo, tagline, description, dates, time, Register button, Bhawin's photo.
3. **Where you are now:** 6 pain-point cards with illustrations.
4. **The Opportunity Loop:** 6 steps. On desktop a loop diagram stays in view and updates as you scroll. Ends with "The result".
5. **The schedule:** "Add all 6 sessions to cart", then a timeline of 6 session cards (accordions, all open by default) and the D-Day card.
6. **What you'll walk away with:** bento grid with LinkedIn-style mocks.
7. **Who it's for:** 3 cards, plus "This isn't for you if…".
8. **Meet your hosts:** tabs for Bhawin, Virat and Mainak.
9. **Testimonials:** 3 video cards (Rohit, Saranya, Muhammad).
10. **Pricing:** free and paid cards.
11. **FAQ**
12. **Final call to action:** countdown to Session 1, then the footer.

## Interactive behaviour (all in the `<script>` at the bottom)

- **Cart:** "Add to cart" on each session, plus "Add all".
  - A sticky bar at the bottom shows the count and total.
  - "View details" opens a bottom sheet listing the sessions, with Remove links.
  - The cart is saved in `localStorage` under the key `lmm-cart`.
- **Price rule:** paid sessions are ₹160 until the end of 5 December (IST) and ₹250 after that (`PAID_DEADLINE` in the script). The cart and the "Add all" total switch automatically. The static ₹160 labels on the session cards, the hero line and the pricing section do not switch on their own.
- **Countdown:** counts down to Session 1, Sat 5 Dec at 8 PM IST, and hides itself once that time passes.
- **Other:**
  - The header shrinks when you scroll.
  - A blue timeline line fills in as you scroll.
  - The host tabs switch between hosts.
  - Small toast messages appear at the top right.

## Still to do before launch

- [ ] **Registration:** both cart Register buttons only show a "coming soon" message. Connect them to the registration or payment flow.
- [ ] **Testimonials:** add 3 YouTube videos, quotes and roles for Rohit, Saranya and Muhammad.
- [ ] **D-Day card:** write the full description for "The Second Income Project" cohort.
- [ ] **Bhawin's photo:** get a higher-resolution photo. The current one is 537×444 and looks soft at full hero size.
- [ ] **After 5 December:** update the static ₹160 text to ₹250, or drive it from the same date rule.
- [ ] **Close each session 1 hour before it starts:** on each event day, from 7 PM IST (sessions start at 8 PM IST), disable that session's **Add to cart** button and show a label like "Registration closed" instead.
  - **What stays as is:** the "Register now" buttons in the header and hero.
  - **Other sessions:** they stay open until their own cut-off.
  - **Cart:** a closed session should also be removed from, or blocked in, the cart, and left out of the "Add all" action and its total.
  - **Dates:** Sat 5 Dec, Wed 9 Dec, Sat 12 Dec, Wed 16 Dec, Sat 19 Dec, Wed 23 Dec, all 8 PM IST (UTC+5:30). So each cut-off is 7 PM IST, which is 13:30 UTC.
