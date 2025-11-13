---
layout: page
title: IS445 HW5.1 — Two Visualizations
permalink: /is445/hw5-1/
---

<div style="margin: 1rem 0; display:flex; gap:.5rem; flex-wrap:wrap;">
  <a style="padding:.5rem .75rem; border:1px solid #ddd; border-radius:8px; text-decoration:none;"
     href="https://github.com/RHYTFirst/RHYTFirst.github.io/blob/main/hw5_1.ipynb">The Analysis</a>
  <a style="padding:.5rem .75rem; border:1px solid #ddd; border-radius:8px; text-decoration:none;"
     href="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv">The Data</a>
</div>

## Plot 1 — Top 15 Agencies by Total Sq Ft
<iframe src="{{ site.baseurl }}/assets/hw5-1/plot1.html" width="100%" height="560" style="border:1px solid #ddd;border-radius:8px;"></iframe>

**What it shows.** A horizontal bar chart of the **top 15 agencies** by total building square footage in the dataset. Each bar’s length is the agency’s **sum of square footage** across all of its buildings.

**Design choices (encodings).**  
- **x (quantitative):** `sum(SQFT)` (Total Square Footage).  
- **y (nominal):** `Agency` (one bar per agency).  
- **Sorting:** agencies sorted **descending by x** so the largest agency appears at the top.  
- **Mark & interaction:** bar mark with tooltips showing agency name and total square footage.

**Color.** Single hue for all bars to keep attention on magnitude and ranking rather than categories.

**Transformations (Python).** Coerced square footage and year to numeric and dropped NAs; aggregated `sum(SQFT)` by agency; computed a rank with a window transform and filtered to `rank ≤ 15`.

---

## Plot 2 — Buildings by Year and Size (interactive)
<iframe src="{{ site.baseurl }}/assets/hw5-1/plot2.html" width="100%" height="620" style="border:1px solid #ddd;border-radius:8px;"></iframe>

**What it shows.** A scatterplot of **year constructed** (x) vs **square footage** (y) for all buildings in the inventory.

**Design choices (encodings).**  
- **x (quantitative):** `Year Constructed`.  
- **y (quantitative):** `Square Footage`.  
- **Mark:** circle. Background points show all buildings faintly; points for the **selected agency** are drawn larger with a black outline.  
- **Tooltips:** show building name (when available), agency, square footage, and year.

**Color.** Background points are light gray so they fade into the background; points for the selected agency are colored (or colored by Primary Use if that field is available), making the comparison stand out.

**Transformations (Python).** Coerced year and square footage to numeric and dropped NAs; applied a **brush filter on year** to restrict the visible range; used a window transform to rank buildings by size within the selected agency and labeled the **top 5 largest** buildings.

---

## Interactivity
A dropdown lets you **choose an agency**; that agency’s buildings become large, colored points with labels on the **top 5 largest** buildings in the current view. A **brush** on the x-axis lets you drag to filter by construction year, which updates both the visible points and the labels. Together, these interactions make it easy to compare one agency against the full inventory and to focus on specific time periods.
