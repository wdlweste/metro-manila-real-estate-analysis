# Metro Manila Real Estate: What Do You Actually Get for ₱13–17M?

**Business question:** If a buyer has around ₱15 million to spend on a property in Metro Manila, where should they buy, and what would they actually get for that budget (floor area, bedrooms, bathrooms)?

## Data
- Source: [Philippine Real Estate dataset](https://www.kaggle.com/datasets/arloblanco/philippine-real-estate) — scraped from lamudi.com.ph (public domain, CC0)
- Scope: Filtered from the full national dataset down to Metro Manila listings only (12 of 17 Metro Manila cities/municipalities were present in the raw data — Caloocan, Malabon, Marikina, Navotas, and Pateros had no listings, which may reflect lower listing activity on this platform rather than the actual market)
- Final working set: 1,042 Metro Manila listings, further filtered to a ₱13M–₱17M price band to match the business question

## Tools
Excel — Text to Columns (parsing the combined "barangay, city" location field), Number Filters, Pivot Tables, AVERAGEIF/AVERAGEIFS

## Process
1. Identified that the raw `Location` field combined barangay and city into one text string (e.g. "Ugong, Pasig") — split it into separate columns before any city-level filtering was possible
2. Built a pivot table of unique city values to confirm exactly which Metro Manila cities were present in the data
3. Filtered to those cities, then further filtered to the ₱13M–₱17M price band
4. Built a summary pivot table: average floor area, bedrooms, and bathrooms by city
5. **Added a listing count per city before drawing any conclusions** — this surfaced a sample size problem (see Limitations)

## Findings

| City | Avg Floor Area (sqm) | Avg Bedrooms | Avg Price | Listings (n) |
|---|---|---|---|---|
| Pasig | 57 | 1 | ₱15.7M | **183** |
| Mandaluyong | 77 | 2 | ₱16.2M | 19 |
| Quezon City | 70 | 2 | ₱14.5M | 13 |
| Pasay | 86 | 2 | ₱15.3M | 7 |
| San Juan | 112 | 3 | ₱14.1M | 3 |
| Taguig | 43 | 2 | ₱14.1M | 2 |

**Reliable finding:** Pasig is the only city with a sample large enough to trust (n=183). At a ₱13–17M budget, Pasig buyers get moderate space (~57 sqm) at a mid-range price — a consistent, well-supported data point.

**Directional, not confirmed:** San Juan and Pasay appear to offer more floor area per peso, but with only 3 and 7 listings respectively, this is too thin a sample to call a real trend. It's flagged here as something worth re-checking with more data, not a recommendation.

## Limitations
- Price bands and "best value" comparisons are based on listing (asking) prices, not sale prices — actual transaction prices may differ
- Several cities have samples too small for the averages to be statistically meaningful (noted above)
- Dataset reflects one listing platform (lamudi.com.ph) at one point in time, not the full market

## Next steps
- Pull a larger sample or a wider price band to validate the San Juan/Pasay signal
- Layer in price-per-sqm as a normalized comparison metric across all cities, not just the ₱13–17M band
