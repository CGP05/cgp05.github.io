---
title: "Local time series regression of Carney government approval and dispproval"
draft: false
slug: "wikipedia-loess"
weight: 1
params:
  hideMeta: true
  hiddenInHomeList: true
---

Created a non-parametric [locally estimated scatterplot smoothing](https://en.wikipedia.org/wiki/Local_regression) time series regression tracking the approval and disapproval rating of the government of Prime Minister Mark Carney, which is currently featured on the Wikipedia pages opinion polling for the :

![Carney Government Approval/Disproval LOESS Graph](/images/carney-government-approval-polls-for-website.svg)

This was done by formatting the table with data from a variety of Canadian pollsters (such as Abacus Data, Léger, and Ipsos) in [this table in the Wikipedia page]().

The embedded R script reads the poll data CSV, cleans percentage and missing-value strings, reshapes the approval/disapproval values into long form, plots poll points and category-specific LOESS trend lines with `ggplot2`, saves the result as an SVG, and then strips `svglite`-specific markup to make the file compatible with Wikipedia.