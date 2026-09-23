# Walnut Creek Aquatics — Pool Relay embed preview

A seven-page replica of the City of Walnut Creek
[aquatics section](https://www.walnutcreekartsrec.org/aquatics): the hub, both swim centers and all
four teams, each with a live [Pool Relay](https://www.poolrelay.com) calendar **scoped to exactly
what that page is about**.

Not an official City of Walnut Creek page. It says so in a ribbon across the top.

## The thing being demonstrated

The published aquatics page is a hub of six cards: Larkey, Clarke Memorial, Swim Lessons, Pool
Rentals, Swim Teams, Swim Passes. Every one is a door to somewhere else.

To answer one ordinary question — *"can my seven-year-old have a lesson at a time when I can also
swim laps?"* — a parent has to open Clarke for the lane table, open Swim Lessons for level
descriptions that carry no times, follow **Group Lessons** out to the city's registration system,
expand **each of seven levels** one at a time, back out to Private Lessons, then go to Swim Teams and
on to the Masters team's own site and its Practice Times page. **Four websites and about a dozen
clicks**, ending with four schedules to compare in your head.

One calendar at the top answers it by looking at Tuesday. The six cards stay exactly where they
were — nothing is taken away, they just stop being the only way in.

## The arithmetic that makes it worth doing

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

## The seven pages

| Page | Calendar it carries | Scoped to |
|---|---|---|
| `index.html` — Aquatics hub | [`HCHCA8lw…`](https://www.poolrelay.com/v/HCHCA8lwePKxAf6EXfIB3H) | both centers, every program, opens on **All** |
| `clarke.html` | [`bgGoKLrx…`](https://www.poolrelay.com/v/bgGoKLrxK8AcpRaiffiEyG) + [`EHMWrlAQ…`](https://www.poolrelay.com/v/EHMWrlAQ2CfgWIKRBXKQAC) | Clarke, with a **Pools** filter; plus the three wading-pool teaching bays |
| `larkey.html` | [`LSVJBxGG…`](https://www.poolrelay.com/v/LSVJBxGGIxadLGeN6FzILO) | Larkey, **a week at a time** |
| `aquabears.html` | Clarke's week | the water they train in — the team itself is absent, which is the point |
| `masters.html` | [`BA51EP0Q…`](https://www.poolrelay.com/v/BA51EP0QyGuJFUr3YTLK4e) | the Masters group only — thirteen practices a week |
| `aquanuts.html` | [`EJycPnzH…`](https://www.poolrelay.com/v/EJycPnzHYwjOEQFFYkpMlI) | the Clarke 25-meter pool only |
| `wcsc.html` | both centers | a summer team, so its season sits outside the current window |

Three of the four teams publish no practice times, so their pages show **the water they use** rather
than an empty grid, and say plainly what is missing. A blank calendar is a bad first impression no
matter how correctly blank it is; a full one with your team visibly absent from it is an argument.

### Larkey, a week at a time

Larkey was first shown a **month** at a time, because an embed always opens on the current period
and Larkey's *week* is empty out of season. It is now the **"Larkey Swim Center — the summer week"**
tab instead (2026-09-23): Clarke's heater failed, its Masters, lap swim and Aquabears practices moved
to Larkey from September 23 through October 1, and a week is the view that shows that move.
Out of season, the week view will be empty again.

Each event square prints its group and its **lane count**, which is what makes the 8 + 12 complement
legible at a glance.

### Scoping one calendar to two facilities

`save_view` scopes a zone to a single class, and Clarke and Larkey are separate top-level facilities
with no shared parent — so the Facilities menu would have offered all 35 facilities in the system.
The fix is `dimFilters.location`, set by `PATCH /api/views/:id` to the **29 leaf ids** under the two
centers. The menu then reads exactly:

```
All · Clarke · Larkey
```

Two further notes, both learned here:

- A page selection stores an **id**, and this view was created *before* the filter was applied — so it
  had already stored `fac:belle-haven`, the first facility in the whole system. The sanitizer only
  fills in an **absent** selection; it does not re-open a stale one. Patch `pageSelections` in the
  same call.
- A stored **empty string** means *All*. That is what makes the calendar open on both centers rather
  than pinned to one, which the page's whole claim depends on.

*Build note:* a view takes its date range from a **Time level in its page filters**, so put one there
before publishing.

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

## Building

The chrome — ribbon, brand bar, the city's nav, the sub-nav, footer — is identical on all seven pages
and lives in `build.py` rather than being pasted seven times. Edit `build.py` (or `style.css`), then:

```
python3 build.py
python3 -m http.server 8824
```

Then open <http://localhost:8824/>. Commit the generated `.html` files; GitHub Pages serves them as
plain static files.
