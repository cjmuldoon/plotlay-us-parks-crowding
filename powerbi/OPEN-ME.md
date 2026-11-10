# Opening the Power BI report

`USParksCrowding.pbip` is a Power BI Project: the report (`USParksCrowding.Report`, PBIR format) and the semantic model (`USParksCrowding.SemanticModel`, TMDL) saved as text, so the repo can show every change. Power BI Desktop opens it like a `.pbix`.

## What you need

- Power BI Desktop for Windows, a recent version (2026). Projects and the PBIR report format are standard in current versions. If Desktop is older than about mid 2025, turn on **File, Options and settings, Options, Preview features, Power BI Project (.pbip) save option** and **Store reports using enhanced metadata format (PBIR)**, then restart Desktop.
- The repo folder on the Windows machine. In Parallels the Mac home folder is usually shared as `\\Mac\Home`.

## Open it

1. In Windows, go to the repo's `powerbi` folder and double-click `USParksCrowding.pbip`, or in Desktop use **File, Open report, Browse reports** with the file type set to *Power BI project files (\*.pbip)*.
2. The visuals are empty the first time. Select **Refresh** on the Home ribbon.
   - By default the data is read from the repo's public copy on GitHub (`DataFolder` is `https://raw.githubusercontent.com/cjmuldoon/plotlay-us-parks-crowding/main/data/`). If Desktop asks how to connect, choose **Anonymous** and then **Connect**.
   - To read the files from disk instead, go to **Home, Transform data, Edit parameters** and set `DataFolder` to the full path of the repo's `data` folder, **ending with a backslash** (for example `\\Mac\Home\plotlay-us-parks-crowding\data\`). Then select **OK** and **Apply changes**.
   - If Desktop warns about privacy levels, choose **Ignore privacy levels** (all the sources are public open data).
3. Check the numbers (below).

If the report was updated while open, close Power BI and reopen the .pbip rather than using Apply external changes. (After Apply external changes one export drew the page at about 57% inside a much larger canvas; a full close and reopen put it right.)

## Check the numbers after Refresh

After **Refresh**:

| Page | Card or visual | Should read |
|---|---|---|
| The parks | Parks | 25 |
| The parks | Recreation visits, 2025 | 75,221,037 |
| The parks | The first bar | Zion, 405 |
| Month by month (Zion, as it opens) | The core line's highest point | 668 (2021-06) |
| Park by park | Zion's row | 602 km² park, 33.7 km² core, 4,984,525 visits |


## The model

- **Parks**: one row per park (`data/tables/parks.csv`): unit code, name, state, area, visitor core area and share, 2025 visits, the busiest month, and visits per km² a day of the park and of the core in 2025. `roads_source` says where the core's roads came from (NPS, or Census TIGER for four parks). Measures: `Park count`, `Visits`, `Visits per km² of park a day`, `Visits per km² of core a day`, `Times denser`.
- **Months**: one row per park and month, January 2015 to December 2025 (`park_months.csv`), related to Parks by `unit_code`. `month` is the text month the slicer shows; `month_date` the same as a date, for the line chart. Measures: `Monthly visits`, `Core visits a day per km²` (the month's visits over the core area and the days, added up first). The monthly lines show 2019 to 2025 (over about 90 months Desktop scrolls the axis).

## The maps

- **Shape Maps** (page 3, The cores). Three parks at their own scale (Zion, Great Smoky Mountains, Yellowstone): each map file, saved inside the report, holds one park's core (from `data/geometry/cores.topojson`) with the park boundary (`data/geometry/parks.geojson`) drawn round it in a pale ground tone. The core takes the map's colour.
- **Shape Map** (page 1, The parks). Each park as a dot at its position, the dot's size set by its 2025 visits (radius 22 km for the fewest up to 70 km for the most) and its shade by visits per km² of core a day. The US states (US Census TIGERweb, public domain) are drawn round them, with Alaska and Hawaii moved in as insets south-west of the lower 48. It was an Azure Maps visual, which comes out blank in a PDF export.

## Save a .pbix too

After the refresh, use **File, Save as** with the type **Power BI file (\*.pbix)** to save `powerbi\USParksCrowding.pbix`. It includes the data, so it opens without a refresh.

## Publish (only if you choose to)

Use **Home, Publish**. In the Power BI service, set the semantic model's **Data source credentials** for the GitHub address to **Anonymous**. Scheduled refresh then works with no gateway. **Publish to web** makes a public link, so only use it if you mean the report to be public.

## Shot list for the website and the video

| # | Shot | How | Length |
|---|---|---|---|
| 1 | The parks | As it opens | still |
| 2 | Core against park | The bars, 2025 | still |
| 3 | Month by month | Park: Zion | still |
| 4 | The cores | The Shape Map, zoomed to Utah | still |
