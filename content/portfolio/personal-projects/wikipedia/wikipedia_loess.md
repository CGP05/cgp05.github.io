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

This was done by formatting the table with data from a variety of Canadian pollsters (such as Abacus Data, Léger, and Ipsos) in [this table in the Wikipedia page](https://en.wikipedia.org/wiki/Opinion_polling_for_the_46th_Canadian_federal_election#Table_of_polls_2).

The R data pipeline extracted and formatted survey results from major Canadian pollsters such as Abacus Data, Léger, and Ipsos, standardizing percentage formatting, encoding missing values, and reshaping approval/disapproval series into a long-format schema for modeling, then used category-specific LOESS smoothing with `ggplot2` to estimate non-linear sentiment trends, rendered individual poll observations with transparent points alongside smooth trendlines, and exported a sanitized SVG via `svglite` for MediaWiki compatibility.