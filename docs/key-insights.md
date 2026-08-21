# Key Insights — Global Airbnb Listings & Reviews

Dataset: 279,712 listings · 182,024 hosts · 5,373,143 reviews · 4,450,005 unique reviewers
Cities: Paris, New York, Sydney, Rome, Rio de Janeiro, Istanbul, Mexico City, Bangkok, Cape Town, Hong Kong
Review data spans **Nov 2008 – Mar 2021**.

## 1. Market Composition

| City | Listings | Share |
|---|---:|---:|
| Paris | 64,690 | 23.1% |
| New York | 37,012 | 13.2% |
| Sydney | 33,630 | 12.0% |
| Rome | 27,647 | 9.9% |
| Rio de Janeiro | 26,615 | 9.5% |
| Istanbul | 24,519 | 8.8% |
| Mexico City | 20,065 | 7.2% |
| Bangkok | 19,361 | 6.9% |
| Cape Town | 19,086 | 6.8% |
| Hong Kong | 7,087 | 2.5% |

Paris alone accounts for nearly a quarter of all listings in the dataset — almost double the next largest market (New York).

## 2. Listing Types

- **Entire place:** 65.1%
- **Private room:** 31.1%
- **Hotel room:** 2.1%
- **Shared room:** 1.7%

The most common property type overall is a straightforward "Entire apartment" (139K listings, 50% of the dataset), followed by "Private room in apartment" (47K).

## 3. Host Quality & Trust

- 182,024 unique hosts manage 279,712 listings — an average of **~1.5 listings per host**, though this is skewed by multi-property hosts.
- **17.97%** of hosts are Superhosts.
- Superhosts average a **96.99** review score vs **92.26** for non-superhosts — a consistent quality premium.
- **99.6%** of hosts have a profile picture; **71.9%** have a verified identity.
- Host response time (where disclosed): within an hour (61%), within a few hours (21%), within a day (17%), a few days or more (11%).

## 4. Pricing

- Median listing price: **150** (local currency of the listing's market).
- Entire places carry roughly a **1.6× price premium** over private rooms, and hotel rooms price highest of all categories.
- Price correlates weakly with `accommodates` (r ≈ 0.15) and `bedrooms` (r ≈ 0.14), and barely at all with review score (r ≈ 0.02) — **bigger listings cost more; better-reviewed listings don't necessarily cost more.**
- ⚠️ Because prices are stored in each market's local currency, don't compare raw price figures across cities without first converting to a common currency.

## 5. Reviews & Seasonality

- Review volume grew steadily from a handful of reviews in 2009 to a peak of **1.63M reviews in 2019**.
- **2020 volume collapsed to 755K and 2021 (partial year, through March) to just 82K** — a clear, dataset-wide COVID-19 travel disruption signature.
- Average overall review score across the platform is **93.4/100**, consistent with Airbnb's well-documented rating inflation (most guests who leave reviews rate highly).

## 6. Booking Behavior

- Only **41.3%** of listings are instant-bookable — the majority still require host approval, even among high-volume markets.

## Ideas for Further Analysis

- Normalize `price` to USD using a per-city exchange-rate table for true cross-market comparison.
- Segment Superhost premium by city to see where the "Superhost effect" on price/rating is strongest.
- Build a cohort view of reviewer loyalty using `Reviews per Reviewer`.
- Overlay listing growth against known regulatory changes (e.g., short-term rental caps) per city.
