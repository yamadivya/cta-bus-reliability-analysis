# CTA Bus Reliability Analysis

Statistical analysis of Chicago Transit Authority (CTA) bus reliability: which routes are least reliable, when service breaks down, and what is associated with it.

## Key findings
- **Route matters.** Route explains about a third of the variation in regularity (partial eta-squared 0.32). Route 66 had 3.7x the odds of a long service gap compared with Route 60.
- **Time of day matters.** The weekday PM peak (3 to 7 pm) had 2.8x the odds of a long gap compared with the morning.
- **Weekends are not worse.** The only clear difference is that weekday mornings are less regular than weekend mornings.
- **Weather.** No detectable effect of rain on regularity.


## Approach
- **Data:** Mansueto Institute StopWatch, which provides estimated CTA bus arrival times (April to June 2026). 12 high-frequency routes, 91 days, 185,851 headways.
- **Measuring reliability:** no schedule was available, so reliability is measured from *headways* (minutes between consecutive buses at a stop), normalized by each route's usual headway. A "big gap" is a headway more than twice the usual.
- **Methods:** Welch ANOVA, Kruskal-Wallis, Holm-corrected pairwise tests, OLS with route fixed effects and date-clustered standard errors, Friedman tests, cluster bootstrap by day, logistic regression.

## Limitations
- Arrival times are interpolated estimates, not observed times.
- The routes are not a random sample of the network: they were hand-picked, then filtered for data quality.
- Observational data, so results show associations, not causes. There are about 91 effectively independent days.

## Repository contents
| Path | Description |
|---|---|
| `Public_Transportation_Reliability_Analysis_explained.ipynb` | Full analysis with an explanation above every cell |
| `CTA_Bus_Reliability_Report.pdf` | Written report with charts (PDF) |

## How to run
1. Install Python 3.9 or newer and Jupyter.
2. Install the libraries: `pip install pandas numpy scipy statsmodels matplotlib pyarrow requests jupyter`
3. Open the notebook and choose **Restart and Run All**. It downloads the data it needs into `data/raw/` automatically (the data is not stored in this repository because of its size).

## Data credit
Data comes from the Mansueto Institute's [CTA StopWatch](https://github.com/mansueto-institute/cta-stop-watch) project. Check their repository for terms of use.
