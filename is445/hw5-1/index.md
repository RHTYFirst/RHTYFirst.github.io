---
layout: page
title: IS445 HW5.1 — Two Visualizations
permalink: /is445/hw5-1/
---

<div style="margin: 1rem 0; display:flex; gap:.5rem; flex-wrap:wrap;">
  <a style="padding:.5rem .75rem; border:1px solid #ddd; border-radius:8px; text-decoration:none;"
     href="https://github.com/RHYTFirst/RHYTFirst.github.io/blob/main/analysis/hw5_1.ipynb">The Analysis</a>
  <a style="padding:.5rem .75rem; border:1px solid #ddd; border-radius:8px; text-decoration:none;"
     href="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv">The Data</a>
</div>

## Plot 1 — Top 15 Agencies by Total Sq Ft
<iframe src="{{ site.baseurl }}/assets/hw5-1/plot1.html" width="100%" height="560" style="border:1px solid #ddd;border-radius:8px;"></iframe>

**What it shows.** Total square footage by agency; bars are the top 15 agencies by total footprint.  
**Design choices (encodings).** *x*: total square footage (Q), *y*: agency (N), sorted descending; bar mark with tooltips.  
**Color.** Single hue to keep focus on ranking and length comparison.  
**Transformations (Python).** Converted types, dropped NAs, aggregated `sum(SQFT)` grouped by agency, ranked with a window transform, filtered to `rank ≤ 15`.

---

## Plot 2 — Buildings by Year and Size (interactive)
<iframe src="{{ site.baseurl }}/assets/hw5-1/plot2.html" width="100%" height="620" style="border:1px solid #ddd;border-radius:8px;"></iframe>

**What it shows.** Scatter of year constructed (x) vs square footage (y) for all buildings.  
**Design choices (encodings).** Circle mark; background points faint for all buildings; selected agency drawn larger with a black outline; tooltips show agency (and building name if present).  
**Color.** Selected points colored (or by Primary Use if available); background gray to emphasize the selection.  
**Transformations (Python).** Type coercion and NA drop; brushing filters by year; window rank labels the top 5 largest buildings within the selected agency.  

---

## Interactivity
A dropdown lets you **choose an agency**; those points become large/colored with labels for the **top 5** largest buildings in that selection. A **brush** on the x-axis lets you drag to filter years, which updates the visible points and labels. This combo makes it easy to contrast one agency against the full inventory and to focus on specific eras.
