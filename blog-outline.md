---
title: "Top 200 Utah Restaurants"
---

## Introduction and Motivation

As a foodie, I wanted to rank the top 200 restaurants in Utah using a composite score built from Google ratings and review counts. Restaurant rankings are usually subjective, but by combining a quality signal (rating) with a popularity signal (number of reviews), it's possible to surface places that are both highly reviewed and widely visited. This project documents how I gathered, cleaned, and ranked that data.

## Motivating Question

According to Google, what are the "best" restaurants in Utah? 

## Ethics and Data Collection Practice

I gathered the restaurant data ethically by:

- Using the **Google Places API** — an official, documented access method — with an authenticated API key
- Collecting only business-level metadata needed for the analysis (no personal data)
- Practicing responsible request behavior: pagination limits, pauses between calls, timeouts, and error handling

## Summary of Steps

1. **Define the goal** — identify the top 200 Utah restaurants using a data-driven composite score
2. **Collect data** — query the Google Places API across multiple Utah cities using paginated requests with polite delays
3. **Clean** — remove duplicate businesses (by `place_id`), drop records with missing ratings, and filter out entries with zero reviews
4. **Transform** — calculate a composite score for each restaurant and rank the full list
5. **Export** — keep only the top 200 rows, validate quality, and save to CSV

## Overview of Final Dataset

- **Rows:** 200  
- **Columns:** 6  
- **Unit of observation:** one Utah restaurant per row  

| Column | Type | Description |
|---|---|---|
| `rank` | integer | Overall rank (1 = best) |
| `name` | text | Restaurant name |
| `city` | text | Utah city where the restaurant is located |
| `rating` | numeric | Google star rating (1–5) |
| `total_reviews` | integer | Number of Google reviews |
| `composite_score` | numeric | `rating × log(1 + total_reviews)` — balances quality and popularity |

The exported file contains no missing values. Duplicates were removed using the Google `place_id` field before ranking.

## Code

The full collection and cleaning pipeline is available here:  
[github.com/Stat386-Winter-2026/TopUtahRestaurants](https://github.com/Stat386-Winter-2026/TopUtahRestaurants)