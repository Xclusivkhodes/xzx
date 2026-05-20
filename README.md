# Waitlist — Design Specification

> _the stage is set — and you're early._

A single-page web waitlist for **StageApp**, Ghana's elite talent booking platform. This is the public-facing surface a curious visitor lands on before product launch. Its job is one thing: capture a qualified email (and a side of context) without breaking the brand's quiet, premium tone.

This document is the canonical spec. Build from it, do not improvise visual language.

---

## 0. Status and scope

| | |
|---|---|
| **Type** | Marketing / pre-launch page (web — first new web surface) |
| **Primary action** | Submit email + role to the waitlist |
| **Secondary actions** | Toggle theme · Read what StageApp is · Share referral link (post-signup) |
| **Surface size** | Mobile-first, 375 → 1440 |
| **Status** | Spec — design ready to build |
| **Out of scope** | Full marketing site, blog, pricing, login, app downloads (none of these exist yet) |

The brand has no prior web surface (see `README.md` → _Caveats_). This design **projects the mobile language onto web**, it does not invent a new one.

---

## 1. Goals & non-goals

### Goals
1. Convert a visitor into a confirmed waitlist signup with one decision (Talent or Client) and one field (email).
2. Communicate _what_ StageApp is in under 5 seconds — Ghana, talent booking, premium.
3. Set the tone — warm, low-key, theatrical — so day-one app users already feel at home.
4. Capture enough segmentation (role, region, talent type) to plan rollout waves.
5. Give the user something to do after submitting — a referral link — so the page keeps working.

### Non-goals
- Selling. There is no price, no plan, no "Get started free."
- Educating in depth. Don't explain escrow, MoMo, or booking lifecycle here.
- Hyping with metrics. No fake "10,000+ joined" counters.
- Imagery-heavy storytelling. We have no brand photography yet — don't fake it.

---

## 2. Audience and entry points

Two audiences, one page. We do **not** fork into separate landings.

| Audience | Came from | What they need to see |
|---|---|---|
| **Talent** (DJ, vocalist, photographer, sound eng., etc.) | WhatsApp group, friend, IG | "I can finally get booked without chasing." |
| **Client** (church admin, event organizer, corporate) | Search, referral, press | "I can finally book verified Ghanaian talent without asking around." |

Both lands on the same hero. The role-picker disambiguates **mid-page** so we don't have to choose for them before they understand what the thing is.

---

## 3. Information architecture (one page, top to bottom)

```
┌────────────────────────────────────────────┐
│ 1. Header                                  │  full-bleed black band
│    [5-bar mark] StageApp        [☼/🌙]    │
├────────────────────────────────────────────┤
│ 2. Hero                                    │
│    The stage is set.                       │  display, period
│    Ghana's elite talent booking platform.  │  sub
│    [pulsing 5-bar mark, beige on dark]     │
│                                            │
│    Join the waitlist  →                    │  in-page anchor to §4
├────────────────────────────────────────────┤
│ 3. What is StageApp                        │  60–80 word block + 3 specifics
│    Two cards side-by-side (stacked on mob):│
│      I'm a Talent · I'm a Client           │  mirrors Welcome screen
├────────────────────────────────────────────┤
│ 4. Waitlist form                           │  the page's actual point
│    Role tabs · Email · Region · Type       │
│    (Go live)                               │  primary CTA
├────────────────────────────────────────────┤
│ 5. Three quiet promises                    │  1-line each, no icons
│    Verified · Escrowed · Local             │
├────────────────────────────────────────────┤
│ 6. FAQ — 4 questions, collapsed by default │
├────────────────────────────────────────────┤
│ 7. Footer                                  │
│    the stage is set    ·  IG  ·  contact   │
└────────────────────────────────────────────┘
```

The page is **vertically long** but visually quiet — each section is a single idea. Scroll feel matters more than density.

---

## 4. Section specs

### 4.1 Header

- Full-bleed black `#0A0A0A` band, 72px tall on desktop / 64 on mobile. **Always black**, regardless of theme — matches the auth-screen rule in the design system.
- Left: 5-bar mark + `StageApp` wordmark (beige `#E8C9A0`, weight 700, +4 letter-spacing, 22px).
- Right: **Spotlight icon** (the theme toggle — see `assets/icon-spotlight-on.svg` / `icon-spotlight-off.svg`). Tap target 44×44.
- No nav links. There is nothing else to navigate to yet.
- Sticky on scroll? **No.** It pins at top, scrolls away. Page has nothing else to anchor to.

### 4.2 Hero

- Theme-aware background: light → `#F5F0E8` parchment, dark → `#0A0A0A`. Solid only. **No gradients.**
- Layout: centered column, max-width `560px`, ~12vh top padding on mobile, ~18vh on desktop.
- Sequence (top → bottom, all centered):
  1. Pulsing 5-bar mark, 64px tall. Each of the five bars animates `scaleY` independently (durations 800–1200ms, delays 0–220ms, targets 0.15–0.35 scale). This is the brand's signature motion moment — keep it.
  2. `The stage is set.` — Display H1: **48px / 1.1 lh / -0.5 tracking, weight 700, period included.** Drops to 34px on mobile.
  3. `Ghana's elite talent booking platform.` — Subhead, 17px regular, color `textMuted`. Single line on desktop, two on mobile.
  4. 32px gap.
  5. Inline anchor: `Join the waitlist →` — sentence case, semibold, beige in dark theme / black in light theme. Underline on hover (1px, 2px offset). Smooth-scrolls to §4.
- Body fades up on load — `opacity 0→1`, `translateY: 20→0`, 600ms, brand spring `cubic-bezier(0.34, 1.4, 0.4, 1)`.

### 4.3 What is StageApp — role primer

This section mirrors the **Welcome screen** card pattern (`reference/auth/Welcome`). Two cards, side-by-side on desktop ≥ 768px, stacked on mobile.

```
┌────────────────────┐   ┌────────────────────┐
│  [music icon]      │   │  [calendar icon]   │
│                    │   │                    │
│  I'm a Talent      │   │  I'm a Client      │
│  Musicians,        │   │  Event organizers, │
│  performers,       │   │  churches,         │
│  engineers         │   │  companies         │
└────────────────────┘   └────────────────────┘
```

- Card spec: `borderRadius: 20`, hairline `0.5px` border (`#2a2a2a` dark / `#D4CFC6` light), padding `24` all sides, `min-height: 200`.
- Icon: 22px stroked, currentColor, `icon-music.svg` and `icon-calendar.svg` from `assets/`.
- Heading inside card: 20px bold, no period (it's a label, not a sentence).
- Description: 15px regular, `textMuted`. Enumerative — concrete instances, not adjectives.
- Hover/press: spring-scale to `0.97`, 180ms, brand easing. Clicking a card pre-selects that role in the form below and scrolls to §4.

**Above the cards**, a single short paragraph (60–80 words):

> _StageApp connects Ghana's verified performers — vocalists, DJs, sound engineers, photographers — with the people who book them. Payment sits in escrow until the gig is done. MoMo on the way out. We're opening access in waves, starting with Accra and Kumasi._

Body text 17px regular, `text-wrap: pretty`, max-width 560px, centered above the cards.

### 4.4 Waitlist form — the page's actual job

This is **the** moment. Treat it accordingly: more vertical space, more weight than anything else on the page.

**Container**
- Centered column, max-width `480px`.
- `padding-block: 96px` desktop, `64px` mobile.
- Subtle separation from the section above using the parchment-on-card pattern: light-theme form sits on a `#FFFFFF` card with hairline border + radius 20; dark-theme form sits on `#161616`. (Inverse of the page background — pulls the eye in.)
- Inside-card padding: 32 desktop, 24 mobile.

**Heading**

- `Join the waitlist.` — 28px / 34 lh / -0.5, weight 700, period.
- `Tell us who you are. We'll let you in.` — 13px sub, `textMuted`. (No selling.)

**Role tabs** (segmented control, two options, full-width)

```
┌─────────────┬─────────────┐
│ I'm a Talent│ I'm a Client│
└─────────────┴─────────────┘
```

- Pill-shaped wrapper (`borderRadius: 999`), hairline border, `height: 48`.
- Active half: filled with `colors.primary` (black in light, beige in dark), text in `primaryText`.
- Inactive half: transparent fill, text `textMuted`.
- Switching is the **only** thing on this page that morphs other fields — see §5 for what each role asks for.

**Field stack** (all fields stack vertically, `gap: 16`)

Each field follows the auth-screen convention exactly:

- **Label** above input — 11px semibold UPPERCASE, +1.2 letter-spacing, `textMuted`.
- **Input** — `height: 54`, `borderRadius: 12`, hairline border, background `input` token, padding `14 16`, 15px regular. Focus state: border swaps to `colors.text`, grows to `1.5px`. **No floating labels, no inline icons** (except the country prefix pill on phone).
- **Helper text / error** — 13px, on its own line beneath the input.

**Talent fields**
1. `FULL NAME` — placeholder `Kwame Mensah`
2. `EMAIL` — placeholder `you@email.com`
3. `WHAT DO YOU DO?` — chip multi-select, max 3 (mirrors signup step 2). Chips: `Instrumentalist · Vocalist · DJ · Producer · Sound Engineer · Photographer · Videographer · Equipment · Venue`. Selected chip = 1.5px beige border + 9.4% beige fill (`#E8C9A018`). Required: pick at least 1.
4. `BASED IN` — single-select chips, one row: `Accra · Kumasi · Takoradi · Tamale · Cape Coast · Other`. Required.
5. `PHONE (OPTIONAL)` — `[+233]` pill prefix + 10-digit input. Helper text: `For early-access WhatsApp updates.`

**Client fields**
1. `FULL NAME` — placeholder `Ama Owusu`
2. `EMAIL` — placeholder `you@church.org`
3. `BOOKING FOR` — chips, single select: `Individual · Church · Corporate · Event organizer · School · Studio / Venue`. Required.
4. `BASED IN` — same as Talent.
5. `WHAT KIND OF EVENT? (OPTIONAL)` — chip multi-select, no max: `Wedding · Naming ceremony · Crusade / Revival · Funeral · Corporate event · Concert · Birthday · Service · Other`. Helper text: `Pick anything you usually book for.`

**Submit**
- Full-width pill button, `borderRadius: 999`, `height: 54`, weight 600, label `Go live`.
- Dark theme: beige fill, black text. Light theme: black fill, beige-light text. (Mirrors auth.)
- Press state: spring-scale to `0.97`, 180ms.
- Disabled (form invalid): `opacity: 0.4`, no spring.
- Loading: `opacity: 0.7`, replace label with the 5-bar mark scaled to 18px, looping its splash pulse.

**Beneath the button**
- 13px subtle copy: `We won't spam. We won't sell your data. We'll write to you once — when it's your turn.`
- Color `subtleText`, max-width matches the input width.

**Privacy link**
- A small `Privacy →` inline link in 13px `termsText` color. Opens a sheet, not a new page.

### 4.5 Three quiet promises

A row of three short statements, no icons (we tried with icons — they fight the brand's restraint). Stacked on mobile.

```
Verified.            Escrowed.            Local.
ID-checked talent.   Payment held until   Ghana-first — Accra,
Only people who      the gig is done.     Kumasi, Takoradi
show up.             MoMo on the way out. and onward.
```

- Headings 17px bold + period, body 15px regular `textMuted`, `text-wrap: pretty`.
- Section padding-block: 80 desktop, 56 mobile.
- Dividers above and below: a single hairline `0.5px` rule, full-bleed.

### 4.6 FAQ

Four items, collapsed by default. Tap a row to expand. Hairline divider between rows, no card. Plus icon `+` rotates 45° to become `×` on open — 200ms, brand easing.

Questions (final copy):

1. **When does StageApp launch?**
   We're opening in waves through 2026, starting with Accra and Kumasi. Joining the waitlist is how you find out when your wave opens.

2. **Is StageApp free?**
   Joining is free. Posting a gig is free. StageApp takes a small service fee on completed bookings — we'll share exact numbers before launch.

3. **How does payment work?**
   Clients pay into escrow when they book. The talent gets paid to MTN, Telecel or AirtelTigo MoMo once the gig is confirmed complete. If something goes wrong, StageApp mediates before any money moves.

4. **What if I'm not in Accra or Kumasi?**
   Sign up anyway. Your region tells us where to open next. We're going national.

- Row padding: `20 0`.
- Question 17px semibold, answer 15px regular `textMuted`, max-width 560px.

### 4.7 Footer

- Full-bleed, parchment background (light) / `#0A0A0A` (dark) — same as page background, so it disappears into the page.
- Tagline `the stage is set` — lowercase, +8 letter-spacing, 13px regular, `textMuted`. Centered.
- Below: `IG · hello@stage.app · Accra, Ghana` — single line, 13px, `·` separators, `subtleText`.
- Padding-block: 64 desktop, 48 mobile.

---

## 5. Post-submit state

After a successful submit, the form swaps in place (no route change, no modal). 300ms cross-fade.

```
┌───────────────────────────────────────────────┐
│              [5-bar mark, beige]              │
│                                               │
│              You're in line.                  │  display
│   We'll write to you when it's your wave.     │  sub
│                                               │
│   ┌─ Your referral link ─────────────────┐    │
│   │  stage.app/i/k7m4p              Copy │    │
│   └──────────────────────────────────────┘    │
│                                               │
│   Each friend who joins moves you up one.     │  subtle
└───────────────────────────────────────────────┘
```

- `You're in line.` — 28px bold, period.
- Sub — 13px `textMuted`.
- Referral link in a tile (`borderRadius: 12`, hairline border, `padding: 14`). The `Copy` action is a 13px inline action that becomes `Copied ✓` for 1.5s then reverts.
- Below the referral, a single sentence in 13px `subtleText`: _Each friend who joins moves you up one._
- No social-share buttons. Copying the link is the whole interaction — it works in WhatsApp, IG, anywhere.
- A small `← Edit submission` link bottom-left in 13px, for the person who realized they picked the wrong role.

---

## 6. States — full table

| State | Trigger | What happens |
|---|---|---|
| **Default** | Page load | Hero fades up. Bars pulse. Form is collapsed-feeling — empty fields, disabled CTA. |
| **Field focus** | Tap input | Border → `text` color, 1.5px. No label morph. |
| **Field error** | Submit-time validation fails | `ShakeField` shake (4 cycles, ±6px, 60ms each). Border → `error` color (`#DC2626` light / `#FF6B6B` dark). 13px error message in error color below the field. |
| **Form valid** | All required fields satisfy schema | CTA pops to full opacity. No other change — no green checks, no celebration. |
| **Submitting** | CTA press | CTA `opacity: 0.7`, label replaced by mini pulsing 5-bar mark. Form inputs lock (no `disabled` styling, just non-editable). |
| **Network error** | Submit fails | Inline message above CTA: `Couldn't reach us. Try again in a moment.` 13px error color. CTA returns to enabled. No retry button — pressing the CTA again is the retry. |
| **Duplicate email** | Server says "already on waitlist" | Form swaps to the post-submit state directly, but with a different sub: `You're already in line — we have you down as a Talent. We'll write soon.` (Show the role we have on file. Reassuring, not corrective.) |
| **Offline at load** | `navigator.onLine === false` | The hero still loads. A small banner appears below the header: `You're offline. The form will work when you're back.` — matches the `OfflineBanner` component pattern in the codebase. |

---

## 7. Validation rules

| Field | Rule | Error message |
|---|---|---|
| Email | Non-empty + valid format | `Enter a valid email.` |
| Full name | Non-empty, min 2 chars | `Tell us your name.` |
| Talent type | At least 1 chip, max 3 | `Pick at least one — up to 3.` |
| Booking for | Exactly 1 chip | `Pick one.` |
| Region | Exactly 1 chip | `Where are you based?` |
| Phone (optional) | If present, valid Ghana mobile (`/^[2-9]\d{8}$/` after stripping +233) | `That doesn't look like a Ghana number.` |

All error copy: sentence case + period. Reassuring, not scolding.

---

## 8. Visual tokens — the actual ones to use

Pulled directly from `colors_and_type.css` and `src/theme/index.ts`. **Do not invent new tokens.**

| Use | Light | Dark |
|---|---|---|
| Page background | `#F5F0E8` | `#0A0A0A` |
| Card background | `#FFFFFF` | `#161616` |
| Primary text | `#0A0A0A` | `#F5F0E8` |
| Muted text | `#867865` | `#797171` |
| Subtle text | `#6b5d4a` (`subtleText`) | `#6b5d4a` |
| Border (hairline) | `#D4CFC6` | `#2a2a2a` |
| Primary CTA fill | `#0A0A0A` | `#E8C9A0` |
| Primary CTA text | `#FFFFFF` | `#0A0A0A` |
| Accent | `#E8C9A0` | `#E8C9A0` |
| Selected chip fill | `#E8C9A018` | `#E8C9A018` |
| Selected chip border | `#E8C9A0` 1.5px | `#E8C9A0` 1.5px |
| Error | `#DC2626` | `#FF6B6B` |

**Type**

| Use | Size / weight / tracking |
|---|---|
| Display (hero) | 48 / 700 / -0.5 (desktop) → 34 / 700 / -0.5 (mobile) |
| H2 (section openers, form heading) | 28 / 700 / -0.5, period |
| H3 (card title) | 20 / 700 / 0 |
| Body | 17 / 400 / 0 (desktop), 15 mobile |
| Sub | 13 / 400 / 0 |
| Label | 11 / 600 / +1.2 UPPERCASE |
| Tagline | 13 / 400 / +8 lowercase |
| Wordmark | 22 / 700 / +4 |

**Radii**: 8 / 12 / 20 / 999. Cards `20`, inputs `12`, chips `999`, buttons `999`. **No `16`** in this surface — keeps the rhythm tight.

**Spacing**: 4 / 8 / 16 / 24 / 32 / 48. Section blocks padded `64–96`; card padding `24–32`; field gap `16`; chip gap `8`.

**Border weight**: hairline `0.5px` everywhere, `1.5px` only for focus + selected.

---

## 9. Motion budget

This page should feel **calm**. Total motion across a single visit:

1. **On load:** pulse mark (loops), hero content fade-up (one-shot, 600ms).
2. **On scroll into view (form, FAQ, promises):** body fade-up + 20px rise, 600ms, **once per session**, observer-triggered.
3. **On press:** spring-scale `0.97` (180ms) for cards/CTA; `0.92` for icon-only buttons.
4. **On focus:** input border swaps in `120ms ease-out`.
5. **On theme toggle:** background and text crossfade `220ms ease-out`. No flash.
6. **On submit success:** form ↔ confirmation crossfade `300ms`.

Anything else is too much. **No scroll-jacking, no parallax, no marquee, no Lottie.**

---

## 10. Accessibility

- All inputs have visible labels (`<label>` linked by `for`), not placeholders-as-labels.
- Tap targets ≥ 44×44. Chips are `min-height: 36` visual / 44 tap.
- Color contrast: every text-on-background pair meets WCAG AA (we've validated the token pairs in `colors_and_type.css`).
- Focus rings: a `2px` beige outline with `2px` offset on keyboard-only focus (`:focus-visible`). Suppressed on mouse focus.
- Theme toggle has an `aria-label` that reflects current state: `Switch to dark theme.` / `Switch to light theme.`
- Reduced motion (`@media (prefers-reduced-motion: reduce)`): kill the bar pulse, kill the fade-ups, kill the press-scale. Crossfades shorten to `60ms`.
- Form errors are announced via `aria-live="polite"` regions, one per field.
- The referral-link `Copy` button announces `Copied to clipboard.` via `aria-live`.

---

## 11. Edge cases worth thinking about now, not later

| Case | Handling |
|---|---|
| **User submits with a `.edu` or international email** | Accept. We're not gatekeeping. |
| **User picks "Other" for region** | Show a single text input below the chip row: `Tell us where →`. Required if "Other" is selected. |
| **User picks Talent + 3 talent types, then switches to Client** | Form is per-role state. Switching role wipes the role-specific fields (with a 200ms collapse). Email/name persist. |
| **Page rendered at < 320px (old Android)** | Header wordmark hides, only the mark remains. Hero display drops to 28px. Chips wrap freely. |
| **Page rendered at > 1440px (desktop)** | Center the page at `max-width: 1200`. Hero stays at `560px` column. No layout sprawl. |
| **JS disabled** | The form posts to a server endpoint with a vanilla `<form action method>` fallback. The bar-pulse skips. Hero still readable. |
| **User refreshes after submit** | Read referral code from `localStorage`. If present, render the post-submit state on load. Add an unobtrusive `Submitted from a different device? Re-enter your email →` link. |
| **User pastes a 10-digit phone with `+233` already in it** | Strip the prefix and the country pill stays. Don't error. |

---

## 12. Content — final copy in one place

Designers and writers, this is the canonical block. **Do not paraphrase in the build.** If something here needs to change, change it here first.

```
HEADER
StageApp                           [theme toggle]

HERO
The stage is set.
Ghana's elite talent booking platform.
Join the waitlist →

PRIMER
StageApp connects Ghana's verified performers — vocalists, DJs,
sound engineers, photographers — with the people who book them.
Payment sits in escrow until the gig is done. MoMo on the way out.
We're opening access in waves, starting with Accra and Kumasi.

  I'm a Talent
  Musicians, performers, engineers

  I'm a Client
  Event organizers, churches, companies

FORM
Join the waitlist.
Tell us who you are. We'll let you in.

[ I'm a Talent | I'm a Client ]

FULL NAME            Kwame Mensah  /  Ama Owusu
EMAIL                you@email.org
WHAT DO YOU DO?      Instrumentalist · Vocalist · DJ · Producer ·
                     Sound Engineer · Photographer · Videographer ·
                     Equipment · Venue
                     (talent only — pick up to 3)
BOOKING FOR          Individual · Church · Corporate ·
                     Event organizer · School · Studio / Venue
                     (client only — pick one)
BASED IN             Accra · Kumasi · Takoradi · Tamale ·
                     Cape Coast · Other
WHAT KIND OF EVENT?  Wedding · Naming ceremony · Crusade / Revival ·
                     Funeral · Corporate event · Concert · Birthday ·
                     Service · Other
                     (client only — optional)
PHONE                [+233] 24 000 0000
                     (talent only — optional)

( Go live )

We won't spam. We won't sell your data.
We'll write to you once — when it's your turn.
Privacy →

PROMISES
Verified.    ID-checked talent. Only people who show up.
Escrowed.    Payment held until the gig is done. MoMo on the way out.
Local.       Ghana-first — Accra, Kumasi, Takoradi and onward.

FAQ
When does StageApp launch?
Is StageApp free?
How does payment work?
What if I'm not in Accra or Kumasi?

POST-SUBMIT
You're in line.
We'll write to you when it's your wave.

Your referral link
stage.app/i/{code}                                            Copy
Each friend who joins moves you up one.

← Edit submission

FOOTER
the stage is set
IG · hello@stage.app · Accra, Ghana
```

---

## 13. Build notes

- **Stack-agnostic** — the design holds whether built in React, Astro, plain HTML, or as a Next route in the future product repo.
- Pull tokens from `colors_and_type.css` directly. Do not re-declare.
- Pull icons from `assets/`. Do not re-draw inline.
- Pull the 5-bar mark animation from the splash in `ui_kits/mobile-app/`. Same timings.
- For the form backend, anything that accepts `(role, email, name, type[], region, event_type[]?, phone?)` and dedups by email works. Out of scope here.
- **Single HTML file** is fine for v1 — this is one page.

---

## 14. Open questions for the team

These do not block the design but should be answered before launch.

1. Domain — is it `stage.app`, `stageapp.gh`, or something else? Affects referral URL shape.
2. Service fee — once confirmed, do we want to disclose the percentage on the page, or keep it for the launch email?
3. Press / partnership inquiries — same `hello@` mailbox, or separate? Affects footer.
4. Do we collect WhatsApp opt-in here, or only after the user is admitted to the app?
5. Wave-rollout language — are we naming waves (Wave 01 — Accra, etc.), or just calling them "your turn"? Affects the post-submit copy.
6. Photography — is anything in the pipeline? If yes, the hero might get a single full-bleed image. If no, this design holds and looks intentional.

---

_Last updated alongside the StageApp Design System v1. Treat as a living document. When the marketing site grows past one page, this file gets split — but for now, one waitlist, one spec._
