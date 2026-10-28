# Namma Yatri — Visualisation & Analysis

## Project Overview
This project analyses Namma Yatri ride data in **Microsoft Power BI**. The analysis explores ride demand by time period, revenue patterns, payment-method usage, pickup-zone performance, cancellations, and the search-to-completed-ride funnel. The purpose is to translate the observed patterns into operational and marketing recommendations.

## Business Objectives
- Understand how ride demand changes across time slots.
- Compare revenue contribution across time periods.
- Identify popular payment methods and compare ride frequency.
- Identify pickup zones with high demand, completed-trip volume, and revenue.
- Review customer and driver cancellation rates.
- Analyse the journey from search/quote stages to completed rides.
- Recommend practical actions for driver allocation, conversion, and marketing.

## Tools & Techniques
- **Microsoft Power BI** for data modelling, KPI cards, charts, slicers, and dashboard analysis.
- **Excel/source tables** as the source format described in the methodology report.
- Data preparation, relationship modelling, variable classification, aggregation, segmentation, and visual storytelling.

## Dataset Description
The methodology report describes five tables:

| Table | Fields described in the report | Purpose |
|---|---|---|
| Trip Details | `tripid`, `loc_from`, `searches`, `searches_got_estimate`, `searches_for_quotes`, `searches_got_quotes`, `customer_not_cancelled`, `driver_not_cancelled`, `otp_entered`, `end_ride` | Search funnel, cancellations, and ride completion |
| Trips | `tripid`, `faremethod`, `fare`, `loc_from`, `loc_to`, `driverid`, `custid`, `distance`, `duration` | Trip, fare, distance, and location attributes |
| Payment | `id`, `method` | Payment method labels |
| Duration | `duration_id`, `duration` | Hourly duration/time-slot labels |
| Assembly | `Assembly_ID`, `Assembly` | Assembly/location labels |

### Relationships described
- `Trip Details.tripid` → `Trips.tripid`
- `Trips.faremethod` → `Payment.id`
- `Trips.duration` → `Duration.duration_id`
- `Trips.loc_to` → `Assembly.Assembly_ID`

Please verify actual relationship cardinality, key uniqueness, and filter direction in the `.pbix` file before extending the model.

## Data Preparation
The report describes these preparation steps:
1. Imported the tables into Power BI using Get Data (Excel).
2. Reviewed column names and data types.
3. Created relationships between trip-level data and payment, duration, and location tables.
4. Checked for duplicate `tripid` values.
5. Inspected `fare`, `distance`, and `duration` for missing values; the source report says missing data was deleted or imputed as appropriate, but it does not document exact field-level counts or rules.
6. Validated binary event fields such as `searches_got_estimate`, `searches_for_quotes`, `searches_got_quotes`, `customer_not_cancelled`, `driver_not_cancelled`, `otp_entered`, and `end_ride` as 0/1 fields.
7. Standardised field types, including numeric fare and categorical duration.
8. Reviewed relationships and excluded columns described as non-contributing.

## Dashboard and Analysis Areas
The methodology report includes the following analysis and supporting visuals:
- Overall ride performance overview and KPI cards.
- Ride demand over time.
- Revenue trend and revenue contribution by time slot.
- Trip volume versus revenue by duration.
- Trips by payment method and revenue/payment-method distribution.
- Top pickup zones by ride volume and revenue.
- Zone-wise ride demand and time-period comparisons.
- Customer and driver cancellation-rate cards.
- Customer ride-conversion funnel.
- Duration slicer/filter for interactive comparisons.

## Key Metrics Reported in the Source
| Metric | Reported value |
|---|---:|
| Total trips | 983 |
| Completed rides | 983 |
| Total searches | 2,161 |
| Overall conversion rate | 45.49% |
| Total revenue | 751K (currency not specified in the text) |
| Customer cancellation rate | 48.17% |
| Driver cancellation rate | 47.25% |
| Customer success rate (100% minus cancellation rate) | 51.83% |
| Driver success rate (100% minus cancellation rate) | 52.75% |

### Payment-method counts reported
| Payment method | Trips | Share |
|---|---:|---:|
| Credit card | 262 | 26.65% |
| Debit card | 243 | 24.72% |
| UPI | 243 | 24.72% |
| Cash | 235 | 23.91% |
| **Total** | **983** | **100%** |

## Key Findings
1. Ride demand varies across time slots. The report describes selected early-hour and daytime slots (including 0–1 and around 11–14) as relatively active, with lower activity during some late-night/off-peak periods.
2. Revenue contribution varies by time period and is not evenly distributed throughout the day.
3. Trip volume and revenue generally move in the same direction, but revenue per ride may vary with distance and fare.
4. Payment-method use is relatively balanced across credit card, debit card, UPI, and cash; credit card has the highest count in the report.
5. A small number of pickup zones are described as contributing strongly to ride demand, completed trips, and/or revenue.
6. The report highlights customer and driver cancellation rates of 48.17% and 47.25%.
7. The reported search-to-completed-ride conversion rate is 45.49% (983 completed rides out of 2,161 searches).
8. The report identifies the driver-allocation-to-OTP stage as a possible point of drop-off.

## Recommendations from the Analysis
- Align driver availability with time-slot demand.
- Prioritise high-demand and high-revenue zones for driver positioning and dispatch efficiency.
- Investigate cancellation patterns by time, zone, fare, distance, and other available fields before choosing interventions.
- Review driver arrival time, ETA accuracy, fare transparency, and the post-allocation customer journey.
- Test off-peak offers and zone-specific campaigns; measure completed rides and incremental revenue rather than searches alone.
- Evaluate driver incentives and digital-payment promotions against a clear baseline.
- Use the duration filter and zone-level visuals for recurring operational reviews.

## Data Quality and Interpretation Notes
- The report states **983 total trips** and **983 completed rides**, while also reporting customer and driver cancellation rates of **48.17%** and **47.25%**. The figures may use different denominators or filter contexts, but the source does not explain the discrepancy. Reconcile measure definitions and filters in Power BI before presenting them as directly comparable.
- The text reports revenue as **751K** but does not specify the currency.
- Exact top-five zone names and values are not clearly transcribed in the report text; refer to the original dashboard visuals or underlying data for precise zone labels.
- Explanations involving population density, commercial activity, and transport connectivity are interpretations suggested in the report, not causal findings established by the dataset alone.
- Missing-value counts and field-specific imputation rules are not documented.

## Repository Structure (Suggested)
```text
DV_Namma_Yatri/
├── README.md
├── reports/
│   └── DV_Namma_Yatri_Detailed_Report_With_All_QA_Screenshots.pdf
├── dashboard/
│   └── Namma_Yatri_Dashboard.pbix
└── data/
    └── source_files_here
```
This is a suggested structure. Add only files that actually exist and that you are allowed to share. Do not upload private or restricted data.

## Repository Contents

- **Project Documentation:** Overview, business objectives, tools, dataset structure, analysis approach, findings, and recommendations.
- **PDF Reports:** Project report and available dashboard export.
- **Presentations:** Project presentation files.

## Project Limitations

The Power BI `.pbix` file and original source dataset are not included in this repository version because they are currently unavailable. The repository documents the analysis and includes the available exported deliverables.

## Future Improvements

- Add the Power BI `.pbix` file when available.
- Include the source dataset if it can be shared publicly and its usage permissions allow it.
- Add dashboard screenshots to make the visual analysis easier to review.


## How to Explore the Project
1. Open the Power BI `.pbix` file if included in the repository.
2. Review the model relationships and confirm measure definitions.
3. Use the duration filter to compare different time slots.
4. Explore the demand, revenue, payment, zone, cancellation, and conversion visuals.
5. Read the full methodology report for each original task question, its written answer, and supporting screenshots.

## Conclusion
The analysis highlights time- and zone-based variation in demand and revenue, relatively balanced payment-method usage, and cancellation/conversion challenges. The key opportunities are demand-aware driver allocation, investigation of cancellation and funnel drop-off, and carefully measured targeted promotions. KPI definitions should be reconciled before final publication.

---
*Prepared from the supplied Namma Yatri methodology report. Metrics and findings above are reproduced as reported; uncertainties are explicitly called out rather than silently changed.*
