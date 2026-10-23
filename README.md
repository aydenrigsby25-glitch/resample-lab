# Resample Lab

A browser-based statistics tool for exploring any dataset. Paste data from a spreadsheet or upload a CSV, then describe it, build bootstrap confidence intervals, compare two groups with a randomization test, and fit a regression line.

**Live site:** _add your Netlify link here_

## Features

| Tool | What it does |
| --- | --- |
| **Data** | Upload a CSV or paste cells from Excel/Google Sheets. Columns are auto-detected as numbers or categories, and you can switch a column's type by clicking it. |
| **Describe** | Dot plot, histogram (adjustable bins) or box plot of one variable, with n, mean, standard deviation, five-number summary, IQR and range. |
| **Bootstrap CI** | Resamples the data with replacement 1, 10, 100 or 1,000 times at a click and builds a percentile confidence interval for the mean, median or standard deviation. |
| **Compare groups** | Randomization test for a difference in means or medians between two groups, with one- or two-sided p-values. |
| **Relationship** | Scatterplot with the least-squares line, correlation r, r², slope and intercept. |

## How the methods work

**Bootstrap confidence interval.** Your sample is the best picture you have of the population. A bootstrap sample draws *n* values from your data with replacement, so some values repeat and others drop out, and then computes the statistic. Repeating this thousands of times shows how much the statistic varies from sample to sample. For a 95% interval, the tool takes the 2.5th and 97.5th percentiles of those bootstrap statistics.

**Randomization test.** The null hypothesis says the group labels don't matter. If that's true, shuffling the labels and recomputing the difference should produce gaps as large as the real one fairly often. The p-value is the share of shuffles at least as extreme as the observed difference. A small p-value means chance alone is a poor explanation for the gap.

**Least-squares regression.** The fitted line ŷ = b₀ + b₁x minimizes the sum of squared vertical distances from the points to the line, with slope b₁ = r · (s_y / s_x).

## Tech

- Plain HTML, CSS and JavaScript in a single `index.html`, with no frameworks and no build step
- Charts drawn by hand on the HTML Canvas API, with high-DPI support and redraw on resize
- CSV parser that handles quoted fields and comma, tab, semicolon or space delimiters
- Light and dark themes that follow the system setting
- The last dataset is saved in the visitor's own browser with `localStorage`; nothing is sent to a server

## Run it locally

Open `index.html` in any browser. That's it.

## Deploy

Hosted on Netlify. Connect this repo, leave the build command empty and set the publish directory to `.`.

## Credits

The tool set is inspired by [StatKey](http://www.lock5stat.com/StatKey/), the free simulation-based statistics apps by the Lock family. Resample Lab is an independent implementation with its own code and design.

Built by **Ayden Rigsby**, Computer Science student at Capital University.
