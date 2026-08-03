---
title: "Local time series regression of Carney government approval and dispproval"
draft: false
slug: "wikipedia-loess"
weight: 1
params:
  hideMeta: true
  hiddenInHomeList: true
---

Created a non-parametric [locally estimated scatterplot smoothing](https://en.wikipedia.org/wiki/Local_regression) time series regression tracking the approval and disapproval rating of the government of Prime Minister Mark Carney, which is currently featured on the Wikipedia pages [pinion polling for the 46th](https://en.wikipedia.org/wiki/Opinion_polling_for_the_46th_Canadian_federal_election#Graphical_summary_3) and [Premiership of Mark Carney]():

![Carney Government Approval/Disproval LOESS Graph](/images/carney-government-approval-polls-for-website.svg)

This was done by formatting the table with data from a variety of Canadian pollsters (such as Abacus Data, Léger, and Ipsos) in [this table in the Wikipedia page]().

The R data pipeline/script 
# Data Collection & Pipeline
* **Polling Data Aggregation:** Extracted and formatted survey results from major Canadian pollsters (such as Abacus Data, Léger, and Ipsos).
* **Data Cleaning:** Standardized percentage formatting, encoded missing values, and restructured approval/disapproval series into a long-format schema for modeling.

### Statistical Modeling & Graphics
* **LOESS Smoothing:** Applied category-specific LOESS smoothers using `ggplot2` in R to estimate non-linear sentiment trends over time.
* **Plot Generation:** Rendered individual poll observations with transparent point markers alongside smooth non-parametric trendlines.
* **SVG Sanitization:** Exported via `svglite` and post-processed to remove incompatible XML/CSS markup for MediaWiki SVG rendering compatibility.