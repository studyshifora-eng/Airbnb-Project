#  Global Airbnb Performance Dashboard

A Power BI dashboard built to analyze Airbnb's listing growth, market distribution, pricing, ratings, and guest review behavior across major global cities.

The goal of this project was not just to create visuals, but to understand what the data says about Airbnb's marketplace — how it has grown, where the supply is concentrated, how pricing varies by property type, and how guests interact with the platform.

---

##  Project Overview

Airbnb operates across different cities, property types and customer segments, making it interesting to look at the platform from both a marketplace and customer-experience perspective.

In this project, I used Power BI to explore:

- How Airbnb listings have grown over time
- Which cities have the largest listing volumes
- How pricing varies by room/property type
- Differences in guest ratings across cities
- How frequently users leave reviews
- Seasonal patterns in review activity
- Identity verification and its role in marketplace trust

The final output is a 3-page interactive dashboard.

---

##  Tools Used

- **Power BI** – Data visualization and dashboard development
- **DAX** – Measures and calculations
- **Power Query** – Data preparation and transformation
- **Excel** – Initial data exploration and preparation

---

##  Dashboard Pages

### 1. Overview — New Listings

This page looks at Airbnb's listing growth over time and shows how different property types contributed to the marketplace.

Key areas covered:

- Total Listings
- Number of Cities
- Number of Hosts
- Property Types
- Total Reviews
- Listing growth over time
- Property-type trends

### Key finding

Airbnb's listing growth peaked around 2015, followed by a slowdown as the marketplace matured. There was a modest recovery around 2018–19 before a sharp decline in 2020.

This shows how Airbnb moved from a rapid expansion phase toward a more mature marketplace and how strongly the platform was affected by external disruptions.

---

### 2. Ratings — Market & Pricing Analysis

This page focuses on differences between cities, property types and guest ratings.

It includes:

- Listing distribution by city
- Superhost vs non-Superhost listings
- Cumulative market share
- Average price by room type
- Overall ratings by city

### Key findings

- Paris has the largest listing volume among the cities analyzed.
- Market size does not necessarily translate into higher guest ratings.
- Hotel rooms and entire-place listings have substantially higher average prices than private rooms.
- Guest ratings vary across cities, showing that marketplace scale and customer experience are not necessarily the same thing.

One interesting pattern was the difference in pricing by room type. The data suggests that guests pay a significant premium for privacy and exclusivity.

---

### 3. Reviews — Customer Behaviour & Trust

The final page looks at how guests interact with Airbnb through reviews and how review activity changes across cities and months.

It includes:

- Review frequency
- Cumulative review frequency
- Seasonal review activity
- Identity verification

### Key findings

The review frequency analysis was one of the most interesting parts of the project.

**86.5% of reviewers leave only one review**, while the cumulative share reaches **96.6% after two reviews** and **98.8% after three reviews**.

This suggests that Airbnb's review ecosystem is driven mainly by a large number of occasional reviewers rather than a small group of highly active reviewers.

The seasonality analysis also showed that review activity differs across cities, suggesting that Airbnb does not have one uniform global seasonal pattern.

The trust analysis showed that **66.9% of users in the analyzed data are identity verified**, highlighting the importance of verification within a marketplace where guests and hosts interact with people they may not know personally.

---

##  Some Interesting Insights

### 1. Airbnb's growth changed after 2015

Listing growth reached a major peak around 2015. After that, growth slowed, suggesting a transition from rapid marketplace expansion toward maturity.

### 2. Privacy comes at a premium

Average prices vary considerably by room type, with hotel rooms and entire places commanding higher prices than private rooms.

### 3. Bigger markets aren't automatically better-rated

The cities with the largest listing volumes are not necessarily the strongest across every guest-rating metric.

### 4. Most reviewers are one-time contributors

With 86.5% of reviewers leaving only one review, the review ecosystem is driven more by the number of unique users than by repeat reviewing.

### 5. Airbnb has different seasonal patterns across cities

Review activity changes differently across destinations throughout the year, suggesting that local market conditions matter when analyzing demand.

---

##  Dashboard Design

I kept the dashboard relatively simple and focused on making the main patterns easy to understand.

The report contains:

- KPI cards for high-level metrics
- Line and area charts for trends
- Combination charts for cumulative analysis
- Bar charts for price and rating comparisons
- A stream/area visualization for seasonality
- Custom DAX measures for review-frequency analysis

The dashboard uses Airbnb's visual identity as inspiration, with a simple white, green and coral/red color palette.

---

##  Some DAX Measures

A few of the measures used in the project include:

```DAX
Reviewers =
DISTINCTCOUNT(Reviews[reviewer_id])

Total Reviews =
COUNT(Reviews[review_id])

Total Reviewers =
CALCULATE(
    [Reviewers],
    REMOVEFILTERS(Reviews[Reviews per Reviewer])
)

Cumulative Reviewers =
VAR CurrentReviews =
    MAX(Reviews[Reviews per Reviewer])
RETURN
    CALCULATE(
        [Reviewers],
        FILTER(
            ALL(Reviews[Reviews per Reviewer]),
            Reviews[Reviews per Reviewer] <= CurrentReviews
        )
    )

Cumulative % review frequency =
DIVIDE(
    [Cumulative Reviewers],
    [Total Reviewers],
    0
)

```

## 📸 Dashboard Preview

### Overview
![Airbnb Dashboard - Overview](https://github.com/studyshifora-eng/Airbnb-Project/blob/main/Snapshot%20of%20the%20dashboard.png)

### Ratings
![Airbnb Dashboard - Ratings](https://github.com/studyshifora-eng/Airbnb-Project/blob/main/Snapshot%20of%20the%20dashboard%20(2).png)

### Reviews
![Airbnb Dashboard - Reviews](screenshots/reviews.png)
