---
title: "Local time series regression of Carney government approval and dispproval"
draft: false
slug: "wikipedia-loess"
weight: 1
params:
  hideMeta: true
  hiddenInHomeList: true
---

Created a non-parametric [locally estimated scatterplot smoothing](https://en.wikipedia.org/wiki/Local_regression) time series regression tracking the approval and disapproval rating of the government of Prime Minister Mark Carney, which is currently featured on the Wikipedia pages [Opinion polling for the 46th Canadian federal election
](https://en.wikipedia.org/wiki/Opinion_polling_for_the_46th_Canadian_federal_election#Graphical_summary_3) and [Premiership of Mark Carney](https://en.wikipedia.org/wiki/Premiership_of_Mark_Carney):

![Carney Government Approval/Disproval LOESS Graph](/images/carney-government-approval-polls-for-website.svg)

This was done by:
- Converting the table with data from a variety of Canadian pollsters (such as Abacus Data, Léger, and Ipsos) in [this table on Wikipedia](https://en.wikipedia.org/wiki/Opinion_polling_for_the_46th_Canadian_federal_election#Table_of_polls_2) to CSV.
- Standardized percentage and date formats for all the poll data.
- Used category-specific LOESS smoothing with `ggplot2` to estimate non-linear sentiment trends.
- Rendered individual poll observations with transparent points alongside smooth trendlines.
- Exported the SVG via `svglite` for compatibility with Wikipedia's WikiMedia software.

I am dedicated to continuously updating the CSV, rendering the SVG then uploading it to Wikipedia as new polls are released.