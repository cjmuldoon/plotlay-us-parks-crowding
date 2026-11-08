# The data

Made from National Park Service and U.S. Census Bureau data (public domain), see [`../NOTICE`](../NOTICE); our cores and tables are CC BY 4.0.

- `tables/parks.csv`: one row per park (25). `unit_code`, `name`, `state`, `group` (top 20 or contrast), `roads_source` (NPS, or Census TIGER), `area_km2`, `core_km2`, `core_share_pct`, `visits_2025`, `visits_2019`, `peak_month` (2025) and its visits and visits per km² of core a day, `per_day_park_2025` and `per_day_core_2025` (2025 visits over the area and 365 days), `core_vs_park`, `lat`, `lng` (a point inside the park).
- `tables/park_months.csv`: one row per park and month, January 2015 to December 2025 (`month` is its first day): `visits` (recreation visits), `visits_per_km2_park_per_day`, `visits_per_km2_core_per_day`; `park`, `year`, `month_of_year`.
- `tables/park_years.csv`: every National Park's recreation visits each year from 1979.
- `tables/cores.csv`: how each core was made: the road, trail and facility parts, segment counts, the road source and the projection.
- `geometry/parks.*`: the park boundaries (NPS Land Resources Division), simplified. `geometry/cores.*`: the visitor cores. Both keyed by `unit_code`.
