<div align="center">

<img src="assets/airbnb-logo.png" width="260" alt="Airbnb logo"/>

# 🏠 Global Airbnb Listings & Reviews Dashboard

### An interactive Power BI dashboard analyzing **279,712 listings** and **5.37M reviews** across 10 major cities worldwide

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-32%20measures-blue?style=for-the-badge)](#-dax-measures)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

</div>

---

## 📌 Overview

This project is a 3-page Power BI report exploring global Airbnb listing data — pricing, hosts, room types, review scores, and booking behavior — across **Paris, New York, Sydney, Rome, Rio de Janeiro, Istanbul, Mexico City, Bangkok, Cape Town, and Hong Kong**.

| Page | What it covers |
|---|---|
| **Overview** | Market-level KPIs — total listings, hosts, reviews, ranked cities, listing growth trend |
| **Ratings** | Review score breakdowns (accuracy, cleanliness, check-in, communication, location, value), host quality signals |
| **Reviews** | Review volume trends over time, reviewer frequency/loyalty, seasonality |

> 📸 *Add your own dashboard screenshots to `assets/` and reference them here — e.g. `![Overview page](assets/overview.png)` — once you export them from Power BI Desktop.*

---

## 📊 Key Insights

- **Scale:** 279,712 active listings from **182,024 unique hosts**, backed by **5.37M reviews** from **4.45M unique reviewers**.
- **City mix:** Paris leads with 64,690 listings (23%), followed by New York (37K) and Sydney (34K); Hong Kong is the smallest market in the dataset (7K).
- **Listing type:** 65% of listings are **entire places**, 31% are **private rooms**, and just ~4% are hotel/shared rooms — this is overwhelmingly a whole-home marketplace.
- **Superhosts perform better:** Superhosts (18% of hosts) average a **97.0** review score vs **92.3** for non-superhosts — a consistent ~5-point quality gap.
- **Trust signals are strong:** 99.6% of hosts have a profile picture and 72% have verified identity.
- **Booking friction:** Only 41% of listings are instant-bookable — most hosts still manually approve requests.
- **Ratings are uniformly high:** Average overall rating is **93.4/100**, suggesting rating scores are heavily right-skewed (as is typical for Airbnb).
- **Size drives price more than quality:** `accommodates` and `bedrooms` correlate with price (r ≈ 0.15), while review score barely does (r ≈ 0.02) — bigger listings cost more, but being highly rated doesn't.
- **Entire places command a premium:** median price for an entire place is ~1.6× a private room, roughly in line across markets (each priced in local currency).
- **Review volume tracks Airbnb's growth curve:** yearly reviews grew from ~1K (2011) to a peak of **1.63M in 2019**, then dropped sharply in 2020–2021 — a clear COVID-19 travel signature in the data.
- **Response culture varies:** of hosts who disclose a response time, the majority (61%) respond "within an hour," but a meaningful long tail takes "a few days or more."

*(Note: `price` is stored per-listing in each market's local currency in the source data — cross-city price comparisons should be currency-normalized before drawing conclusions.)*

---

## 🧮 DAX Measures

The model includes **32 custom DAX measures**, including:

- `Total Listings`, `Total Reviews`, `Hosts Total`, `Total Reviewers`
- `City Rank` (RANKX over cities by listing count)
- Room-type splits: `Entire Place Count`, `Private Room Count`, `Hotel Room Count`, `Shared Room Count`
- Host quality segments: `Verified Profile`, `Verified NoProfile`, `NotVerified Profile`, `NotVerified_NoProfile` (+ % of host base for each)
- Superhost splits: `Superhost Count`, `Non-Superhost Count`
- Cumulative/running measures: `Cumulative Listings`, `Cumulative Reviewers`, `% of Total Reviews`
- Average review sub-scores: accuracy, cleanliness, check-in, communication, location, value

---

## 🗂️ Data Model

| Table | Rows | Description |
|---|---|---|
| `Listings` | 279,712 | One row per listing — host, location, pricing, amenities, review scores |
| `Reviews` | 5,373,143 | One row per review — listing, reviewer, date, review frequency flags |
| `LocalDateTable_*` / `DateTableTemplate_*` | — | Auto-generated Power BI date tables for time intelligence |

**Key columns (Listings):** `listing_id`, `host_id`, `host_since`, `host_is_superhost`, `host_response_time`, `neighbourhood`, `city`, `property_type`, `room_type`, `accommodates`, `bedrooms`, `price`, `review_scores_*`, `instant_bookable`

**Key columns (Reviews):** `listing_id`, `review_id`, `date`, `reviewer_id`, `Reviews per Reviewer`

---

## 📁 Repository Structure

```
airbnb-dashboard/
├── dashboard.pbix          # Power BI report file
├── README.md                # You are here
├── LICENSE
├── docs/
│   └── key-insights.md      # Extended write-up of findings
└── assets/
    ├── airbnb-logo.png
    ├── cover-banner.png
    └── (add screenshots here)
```

---

## 🚀 Getting Started

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows only).
2. Clone this repo:
   ```bash
   git clone https://github.com/KaranRawat840/Global_Airbnb_Performance_Dashboard.git
   ```
3. Open `dashboard.pbix` in Power BI Desktop.
4. Explore the **Overview**, **Ratings**, and **Reviews** pages, or connect it to Power BI Service to publish/share.

---

## 🛠️ Tech Stack

- **Power BI Desktop** — report authoring & data modeling
- **DAX** — custom measures and calculated logic
- **Power Query (M)** — data cleaning/shaping (in the `Connections`/query layer of the .pbix)

---

<div align="center">
<sub>Built with Power BI · Data as of March 2021</sub>
</div>
