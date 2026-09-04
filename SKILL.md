---
name: university-travel-request
description: "Prepare a university travel/expense request end to end — budget check, chartfield/account setup, expense lines, agenda attachment, and the international-travel branch. Adapt the bracketed placeholders to your own institution before using."
---

# University travel request — template

This is a generic pattern extracted from a real skill built by watching a faculty member
file an actual request, screen by screen. Replace every `[BRACKETED]` value with your own
institution's system, policy, and defaults before use. Where a step doesn't apply to your
system, delete it — don't leave it half-filled.

## What you need before starting

Destination · dates · purpose · which account/grant pays · whether an outside institution is
paying any part of the trip. If dates are uncertain, look the conference up on the web and use
the real ones — never guess. If it's a conference, get the venue and city too.

---

# Step 1 — Budget pre-flight (do this even when the account is already decided)

Before touching the form, check the account/grant that will pay for the trip:

- Pull the current balance and travel-line spend for `[YOUR ACCOUNT/COST-CENTRE SOURCE]`.
- State the pull date. If it's more than a couple of days old, say so.
- If the account has no visible travel budget line, or the trip is international and there's
  no foreign-travel line, say that plainly — don't show zero as if it means "nothing allowed."

**Stop and explain — don't proceed —** if the travel line is overspent, the account is in
deficit, or the account's end date has already passed.

---

# Step 2 — Which branch

Decide by **destination country**, not by whatever "foreign travel" checkbox your system shows —
some systems flag this incorrectly for certain countries. Check your institution's actual policy,
not just the software's flag.

- `[COUNTRIES YOUR POLICY TREATS AS FOREIGN EVEN IF THE SYSTEM DOESN'T]` → still run the
  international branch.
- Anywhere outside your home country → full international branch, Step 3.
- Domestic → skip to Step 4.

---

# Step 3 — International prerequisites

Before building the request, gather:

1. Any required export-control or international-travel certification, valid on the travel
   dates, attached to *this specific trip* (many institutions require it per-trip, not once).
2. `[YOUR INSTITUTION'S INTERNATIONAL TRAVEL FORM]` — note who has to sign it (traveler,
   supervisor, admin) and whether it can be filled programmatically or has to be handed to a
   human (some are locked behind cross-origin iframes or e-signature portals).
3. Any required statement of need/benefit if your policy requires one separate from the
   request's own purpose field.
4. Make sure the agenda covers every day of the trip, including personal days if any.
5. If the funding source is federally sponsored, check your institution's flight-carrier
   rule (many require domestic-flag carriers) — flag this while the itinerary is still being
   planned, not after booking.

---

# Step 4 — Build the request

Constants that don't vary for you — write these down once so they're set the same way every
time:

```
Traveler type        [YOUR DEFAULT]
Request policy        [YOUR DEFAULT]
Departure city         [YOUR HOME CITY]
Personal days          [YOUR DEFAULT, usually 0]
Department/unit         [YOUR DEPARTMENT — check the form's actual default first;
                          many systems default to the wrong unit]
```

**Document ID / request name convention:** `[YOUR NAMING PATTERN]` — check your system's
character limit.

**Chartfield / account code, in order:** `[YOUR FULL CODE STRING]`. Note which fields
auto-fill from a project/grant selection and which you must set by hand — don't assume
selecting one field fills the others.

**Destination search gotcha:** many systems' city search returns foreign matches first for
common US city names. Match `<City>, <State/Country>` exactly, or pick the airport entry
directly — a plain city name can silently misprice the estimate.

**Purpose/benefit text:** tie it explicitly to the account being charged. A generic
"attend conference X" on a grant-funded line invites a bounce from the business office.

**No account code available for the intended funding source?** Check your institution's
guidance — some allow using a placeholder project and naming the real funding source in a
comment field. Confirm this is actually permitted before doing it.

---

# Step 5 — Estimate and expense lines

- Tick service checkboxes with real interaction if your system requires it — some reject
  programmatically-set checkboxes even though they display as checked.
- The estimator usually only prices what's ticked — registration, meals, and ground transport
  are often missing from the total. Don't present the estimator's total as the trip's full cost.
- Check whether your system has a real "Registration" expense category — many don't, and it
  has to go under a generic "other incidental" line instead.
- Follow your institution's rule on per-diem/dining lines (some want them, some don't).

---

# Step 6 — The attachment

Every request should carry a supporting document: the conference programme if one exists, or
a day-by-day travel agenda otherwise. Format:

```
Travel Agenda MM/DD/YYYY – MM/DD/YYYY
Day 1   – Travel from <origin> to <destination>; departure/arrival times
Day 2–N – <meeting/activity>, <venue>, <city>
Activities performed: <talks, meetings, sessions>
Day N+1 – Travel home
<flight table>
```

**Real content only.** Use the actual meeting, dates, venue, and funding source. Anything not
yet knowable (session codes, exact flight times) gets marked `TBC` — never invent a specific.
These documents sit inside a financial approval; a fabricated detail is what fails an audit.

---

# Step 7 — Hand over, don't submit

Many systems won't let file attachment be automated (native OS file pickers can't be driven
programmatically) — if so, give the file path and let the human attach it.

**Never click Submit** unless explicitly told to in that turn. Show what's ready and what's
still missing, and stop there.

---

# Stop conditions — halt and explain, never warn-and-continue

| condition | response |
|---|---|
| Required certificate expired, unknown, or not attached to *this* trip | get it renewed/attached, then re-run |
| Foreign destination with no completed export-control or international form | start the form, wait for confirmation before proceeding |
| Sanctioned or restricted-destination country | stop; require explicit institutional sign-off before preparing anything |
| Non-compliant carrier on a federally-funded international itinerary | flag it; rebook or confirm the rule doesn't apply |
| Foreign travel with a required statement not yet drafted | note the requirement, don't try to substitute the purpose field |
| Institutional policy may have changed since last check | say what might have changed; stop rather than guess |
| Can't verify current policy (site down, page moved) | say so — a silent skipped check is worse than a flagged one |

---

# Rails

- Never handle login credentials or two-factor prompts.
- Never click Submit, Attach, or e-signature "Begin Signing" buttons.
- Never invent a date, dollar figure, account code, or URL. A placeholder is fine — as long
  as it's clearly labeled as one, in the place a human reviewer will actually see it.
- Say plainly when a check couldn't be run. Don't let a silent gap look like a pass.
