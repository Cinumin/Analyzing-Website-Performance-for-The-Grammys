# Did splitting one website into two make the Grammys' audience more engaged?

A five-year analysis of web analytics from The Recording Academy, examining whether the 2022 split of grammy.com and recordingacademy.com improved engagement — and what to recommend next.

`Python` · `pandas` · `Plotly Express` · `Jupyter` · `KPI analysis` · `Competitive benchmarking`

## The brief

In 2022 The Recording Academy's VP of Digital Strategy split a single web property into two: grammy.com for music fans and recordingacademy.com for industry professionals. The business question was whether the split served those two audiences better, and whether an organization whose traffic depends on one night a year can keep people coming back the other 364.

My job was to measure the before-and-after, benchmark against a competitor, and deliver a recommendation: keep the sites separate, merge them back, or something else.

## The data

- **Daily site analytics** — Two files, one per site. Visitors, pageviews, sessions, bounced sessions, average session duration, plus flags for awards week and awards night. 1,857 pre-split days.
- **Age demographics** — Share of visitors by age band for each site, six bands from 18–24 to 65+.
- **Competitor device segments** — American Music Awards desktop and mobile visitor counts across 515 days, joined on date for share-of-traffic analysis.

## How I approached it

1. **Explore and segment** — Loaded the analytics into pandas, charted daily visitors, and cut the timeline at `2022-02-01` to create clean pre-split and post-split frames.
2. **Engineer the engagement metrics** — Derived pages per session across every frame in one loop, and wrote reusable functions for bounce rate and average time on site so each site could be compared on identical definitions.
3. **Profile the two audiences** — Concatenated the demographic files with a site label and charted them side by side to test whether the split had actually separated two different audiences.
4. **Benchmark and recommend** — Merged the competitor's desktop and mobile files to compute its device share, set the Grammys' KPIs against the American Music Awards, and wrote a business memo for the executive sponsor.

## What the numbers said

| Finding | Result |
| --- | --- |
| **The one-night problem** | Show Night averages 1,389,590 visitors against 32,388 on an ordinary day — 43×, or 1.36M extra visitors concentrated in 24 hours, and the core business risk. |
| **Bounce rate improved** | recordingacademy.com bounces at 33.7% and grammy.com at 40.2%, both below the 41.6% combined-site baseline. |
| **Sessions split in two directions** | Professionals stayed 25.7s longer on recordingacademy.com (128.5s); fans stayed 19.9s shorter on grammy.com (83.0s). Pages per session rose above 2.0 on both, up from a 1.2–2.2 range before. |
| **Same people, different intent** | Age mix is near-identical across the two sites — every band within two percentage points, both led by 18–24 at roughly 27%. The split separated intent, not demographics. |

Benchmarked against the American Music Awards (third-party dashboard, April–June 2023): the Grammys wins on bounce rate — 40.2% and 33.7% against the AMA's 54.3% — and matches on pages per visit. It loses badly on dwell time, 5m53s on the AMA site versus roughly 1m23s on grammy.com and 2m09s on recordingacademy.com. The AMA's audience also skews heavily mobile, at 68.2% of visits against 31.8% desktop.

## The recommendation

**Keep the sites separate. Fix retention, not architecture.**

Both properties beat the combined baseline on bounce rate and pages per session, so the split is working. The weak spot is dwell time on grammy.com, where a fan audience arrives for one night and leaves. The fix is content that earns a second visit — exclusive interviews, insider coverage, and lightweight interactive formats — the levers that close a four-minute dwell-time gap against the closest competitor.

## What this project shows

- **pandas fluency** — Date filtering, groupby aggregation, concat and merge joins, column engineering, reusable metric functions.
- **Metric definition** — Building bounce rate, pages per session and time on site from raw counts so four datasets stay comparable.
- **Reading the seasonality** — Tracing off-cycle traffic bumps to submission windows and September membership deadlines, not just Show Night.
- **Executive communication** — Turning four KPIs into a one-page memo with a clear decision, and critically reviewing an AI-drafted version before revising it.

## Running it

```
Analyzing-Website-Performance-Grammys.ipynb
datasets/   — six CSV files
figs/       — competitor dashboard reference
```

```bash
pip install pandas plotly
jupyter notebook
```

Run the notebook top to bottom — charts are interactive Plotly figures. Analytics data is provided under an educational-use license from The Recording Academy; competitor figures come from a third-party traffic dashboard for April–June 2023.
