# Walnut Creek Aquatics — Pool Relay embed preview

A replica of the City of Walnut Creek
[Clarke Memorial Swim Center page](https://www.walnutcreekartsrec.org/aquatics/swim-center-hours-programs/clarke-memorial-swim-center)
with its **lap-swim lane-allocation table replaced by a live [Pool Relay](https://www.poolrelay.com)
calendar**, plus the current lesson session and the Larkey summer season.

Not an official City of Walnut Creek page. It says so in a ribbon across the top.

## The thing being demonstrated

Walnut Creek does something unusual and genuinely good: it publishes lap swim as a **table of lane
counts** rather than as opening hours.

| Time | Lanes for public lap swim |
|---|---|
| 5:30 – 8:00 am | 8 |
| 8:00 – 10:30 am | 20 |
| 10:30 am – 1:00 pm | 8 |
| 1:00 – 4:00 pm | 14 |
| 7:00 – 8:00 pm | 8 |

That answers *"how many lanes do I get?"* and nothing else. It cannot say what the other twelve
lanes are doing, because **the city does not run them** — the Masters team publishes its own
practice times, on its own website, in a completely different system.

Put both on one calendar and the arithmetic closes exactly:

```
5:30– 8:00   lap swim  8  +  Masters 12  =  20
8:00–10:30   lap swim 20  +  (Masters out of the water)
10:30– 1:00  lap swim  8  +  Masters 12  =  20
7:00– 8:00   lap swim  8  +  Masters 12  =  20
```

Two independent sources reconciling to exactly 20 is much stronger evidence than either one alone,
and it is the reason this page exists. **The complement is the product.** A reader of the city's
table cannot see it; a reader of the calendar cannot miss it.

## The calendars

| | |
|---|---|
| Clarke — this week | [`/embed/bgGoKLrxK8AcpRaiffiEyG`](https://www.poolrelay.com/v/bgGoKLrxK8AcpRaiffiEyG) |
| Learn-to-swim bays | [`/embed/EHMWrlAQ2CfgWIKRBXKQAC`](https://www.poolrelay.com/v/EHMWrlAQ2CfgWIKRBXKQAC) |
| Larkey — the summer week | [`/v/LSVJBxGGIxadLGeN6FzILO`](https://www.poolrelay.com/v/LSVJBxGGIxadLGeN6FzILO) — linked, not embedded: Larkey is closed, so the current week is empty by design |

The Clarke view carries a **Pools** page filter (50-Meter / 25-Meter / Wading) so one embed serves
the whole facility, and each event square prints its group and its **lane count** — which is what
makes the 8 + 12 complement legible at a glance.

*Build note for the next one of these:* a view takes its date range from a **Time level in its page
filters**, so put one there before publishing.

## What the calendar adds over the published page

- **The other twelve lanes.** Masters practice sits beside lap swim instead of being invisible.
- **Which water.** The wading pool runs three teaching bays — East, Middle, West — and the city's
  registration system knows which bay each level is in. **That split is published nowhere on the
  aquatics site**; it only exists inside PerfectMind's class locations. The aquatics page has never
  had anywhere to put it.
- **Today, not "usually".** A four-week lesson session ends on its own date instead of being deleted
  from a page by hand.
- **Collisions.** Ten of them, below.

## Conflicts — all ten are real, none are transcription errors

- **Guppy #85243 and Seal #85260 are both on `50m Lane 01` at 5:10pm**, Tuesdays and Thursdays,
  across all four session dates. That is the city's own registration system double-booking a lane.
- **Saturday 11:00 lessons against Saturday lap swim.** The allocation table hands lanes 1–14 to lap
  swim from 11:00 on weekends, while a Saturday Guppy class and two private lessons sit on Lanes 1
  and 2. Pool Relay suggests moving lap swim to lanes 3–16, which is almost certainly what the deck
  actually does — the page just never says so.

Two further conflicts appeared during entry and **were ours, so they were fixed rather than
reported**: an inferred Monday–Thursday sprayground season ran through Labor Day, colliding with the
Labor Day rec swim the city opened Larkey for. An inference that produces a conflict is evidence the
inference is wrong.

## Questions for the aquatics office

These are marked on the page and on the calendar entries themselves.

| | Question |
|---|---|
| **Conflict** | Evening lap swim is Mon–Thu in the hours box and Mon–Fri in the allocation table directly below it. Entered as Mon–Thu. |
| **Conflict** | Which class is really in 50m Lane 1 at 5:10 — Guppy or Seal? |
| **Conflict** | Does Saturday lap swim shift off Lanes 1–2 at 11:00 for the lessons? |
| **Ours** | Masters lane count. We entered 12 as the balance of the 20-lane short course; the team publishes times but never lanes. The Saturday 9:30–10:45 practice has no published allocation to bound it at all. |
| **Gap** | Water exercise — the page lists Tue/Wed/Thu 8:15 shallow and 9:15 deep, then says *"we do not have an instructor at this time."* Deliberately **not** entered: an event holds water no matter what its description says. Is the water still reserved? |
| **Gap** | Practice times for three of the four teams. **Aquabears** (eight groups, "practices daily at Clarke"), **Aquanuts** (holding the 25m pool year round for synchro) and the summer **Swim Club** publish none. Only Masters does. |
| **Gap** | Weekend rec swim — still running, and in the 50m or the 25m pool? The page lists it under both. |
| **Ours** | Larkey's weekday sprayground-only hours are published without dates. We used the Memorial Day–Labor Day season the swim pass names. |

## What is in Pool Relay behind these pages

**64 events** across two facilities, entered 16 September 2026.

- **Clarke Memorial** (1750 Heather Dr, year round) — 50-Meter Pool → Short Course → Lanes 1–20, a
  25-Meter Pool, a Wading Pool split East / Middle / West, plus South Patio and Pavilions as
  rentable areas. 56 events.
- **Larkey** (2771 Buena Vista Ave, summer only) — Main Pool, Sprayground, Picnic Area. 8 events.
- **Groups** — a *Walnut Creek Aquatics Programs* org (lap swim, rec swim, water exercise, ten
  lesson levels, private lessons, rentals, sprayground-only) and four club orgs: Aquabears with its
  eight practice groups, Masters, Aquanuts, Walnut Creek Swim Club.

Sources: walnutcreekartsrec.org, the city's PerfectMind registration system (class times, lane and
bay assignments), and swim4wc.org (Masters practice times).

## Local preview

```
python3 -m http.server 8824
```

Then open <http://localhost:8824/>.
