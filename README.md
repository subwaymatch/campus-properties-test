# Campus Comps

## What this site is for

Campus Comps gives home buyers, students and anyone curious about college-town housing a quick way to compare completed home sale prices across 18 U.S. towns. The town table can be searched and sorted by median price or recorded sales.

## Live site

https://subwaymatch.github.io/campus-properties-test/

## Preview it on your own computer

From the repository folder, start a local web server:

```bash
python -m http.server 8000
```

Then open http://localhost:8000/. The page fetches `data/college_town_home_sales.csv`, so opening `index.html` directly from the file system will not load the data.

## Data notes

The page reads the committed CSV directly in the browser; it has no build step or external library. Every CSV row contributes to recorded-sale counts. The city-level and overall median sale prices include sale prices of $1,000 or more, excluding the low values flagged as implausible in the data description. There is no upper-price cutoff. Medians, rather than averages, reduce the influence of extreme values. Rows are not deduplicated by street address because an address can represent multiple homes or sales.

Days on market, property type and assessed value are not used in the analysis. In particular, a blank list or contract date is not treated as zero days, `home_type` is unreliable, and assessed value is not the sale price. Values are as reported by the collection source and have not been independently verified against county records. See [the data description sheet](docs/data_description_sheet.md) for definitions and limitations.

## How we checked our numbers

We checked the page's summary calculations independently against the SQLite copy of the dataset. The median checks use Python's `statistics.median` on values selected from SQLite.

| Number on the site | Where it appears | How we checked it | Result |
|---|---|---|---|
| 35,442 recorded sales | Overview card | `SELECT COUNT(*) FROM home_sales` | 35,442 |
| 18 towns | Overview card | Count rows from `SELECT city, state FROM home_sales GROUP BY city, state` | 18 |
| $410,000 overall median | Overview card | Select `sale_price >= 1000`, then calculate the median | $410,000 |
| $350,000 Gainesville median | Town comparison | Select Gainesville sales with `sale_price >= 1000`, then calculate the median | $350,000 |

## Tools we used

GitHub Copilot; plain HTML, CSS and JavaScript; Python's local HTTP server for previewing and Python's standard-library SQLite and statistics modules for independent checks. No frontend libraries or build tools.

## Citation

College-town home sales dataset, version 1.0 (2026). University of Illinois-Deloitte Foundation Center for Business Emerging Technologies. Data collected March 2026.
