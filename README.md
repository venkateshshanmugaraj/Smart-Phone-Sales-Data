# Smart-Phone-Sales-Data
This dashboard provides a clear view of smartphone sales across models, regions, and channels. It highlights key metrics like revenue, units sold, and ASP, and uses visual charts to show trends. Filters and drilldowns help identify top products, slow movers, and issues such as high returns or low stock.

## 1) Purpose & audience (start here)

 * State the dashboard’s goal in one sentence: e.g. “Help product, sales and operations teams quickly see how smartphone models and channels are selling, spot trends and underperformers, and take actions to hit revenue/stock targets.”

 * Define the audience and their needs: e.g. Sales Manager (daily ops), Product Manager (weekly trends), Finance (monthly revenue), Executive (top-level health).

## 2) Source data & refresh

 * Primary files/tables assumed: Orders (order_date, sku/model, units, unit_price, revenue, channel, region), Inventory, Returns, Cost (COGS), Promotions.

 * Refresh cadence: daily or weekly (mention whichever applies).

 * Note ETL steps: join by SKU, standardize dates, normalize channel names, handle missing values.

## 3) Data model & transformations (high level)

 * Build a single fact table (Sales) and small dimension tables (Product, Channel, Region, Date).

 * Typical transforms:

     * Parse order_date → Year, Month, Week.

     * Compute Revenue = units * unit_price (if not provided).

     * Flag returns and adjust net units/revenue if needed.

     * Create category (flag flagship / midrange / budget) from model names.  

## 4) Key metrics (KPIs) to show — what and why

 * Total Revenue — top-line performance.

 * Units Sold — volume indicator.

 * Average Selling Price (ASP) = Revenue / Units Sold — pricing trend.

 * Units / Revenue by Model — identify best/worst SKUs.

 * Revenue by Channel (online, retail, distributor) — channel mix.

 * Revenue by Region/State — geographic strength.

 * Month-on-Month (MoM) growth — momentum.

 * Return Rate = Returned Units / Sold Units — product quality / satisfaction signal.

 * Inventory Days / Stock Level — supply risk.

 * Promotion Lift — compare promoted vs non-promoted sales.

## 5) Suggested dashboard layout (top → bottom, left → right)

 * Header row: Dashboard title, date of last refresh, global filters (Date range, Region, Channel).

 * Top KPIs row (big number cards): Total Revenue, Units Sold, ASP, MoM %.

 * Trend area: Time series chart (Revenue and Units over time) with month selector.

 * Breakdown area: Bar charts / treemap for Revenue by Model and Revenue by Channel.

 * Market map / Geo: Map for Revenue by Region (if geography matters).

 * Detail table: Top 10 SKUs (units, revenue, ASP, return rate) with ability to drill.

 * Operational alerts: Inventory warnings, high return SKUs, declining models.

 * Notes / Actions: Short column listing recommended actions or insights.

## 6) Recommended visual types & why

 * KPI cards — immediate snapshot.

 * Line chart (dual axis) — revenue + units trend; dual axis helps compare price vs volume.

 * Stacked column — revenue by channel over time.

 * Bar chart (descending) — top/bottom SKUs; easy to spot outliers.

 * Treemap — market share by model category.

 * Map — region performance visually.

 * Table with conditional formatting — details and color flags for quick triage.

## 7) Interactivity & user controls

 * Global filters: Date range, Region, Channel, Product Category.

 * Drill-through: Click a model → show transactions, return reasons, and promotions affecting it.

 * Hover tooltips: show exact numbers and YoY or MoM change.

 * Bookmarks / Views: Prebuilt views (Executive view, Sales Ops view, Inventory view).

## 8) Key calculations / example formulas

 * ASP (Excel): =SUM(Revenue) / SUM(Units)

 * MoM growth (Excel): =(ThisMonthRevenue - PrevMonthRevenue) / PrevMonthRevenue

 * Return Rate: =SUM(ReturnedUnits) / SUM(SoldUnits)

 * Net Revenue after returns: =SUM(Revenue) - SUM(ReturnsRevenue)

 * YTD Revenue: sum of revenue where date <= selected date and year = selected year.

(If using Power BI / Tableau you’d convert these to DAX / calculated fields — e.g. DAX ASP = DIVIDE(SUM(Sales[Revenue]), SUM(Sales[Units])).)

## 9) How to read each section — interpretation guide (talking points)

 * If Total Revenue ↑ but Units ↓ — ASP rose (higher price or more premium mix). Investigate price changes or SKU mix.

 * If Units ↑ but Revenue flat — selling more lower-priced models; margin may be shrinking.

 * High return rate for an SKU — product defect or mismatch in expectations — escalate to QA/Product.

 * Channel shift — if online grows and retail drops, consider inventory reallocation & channel promotions.

 * Geography heatmap — identify expanding or contracting markets; use for targeted promotions.

 * Inventory warnings — low stock on top SKUs = risk of lost sales; reorder or adjust promotions.

## 10) Actionable alerts & thresholds

 * Flag when:

     * Revenue MoM < -10% (urgent review).

     * Inventory for top-10 SKUs falls below X days.

     * Return Rate > 5% for any SKU.

 * For each alert show suggested actions (e.g., “investigate returns”, “increase reorder”).

## 11) Storytelling / presentation order (how to present to stakeholders)

 * Start with top KPIs (headline).

 * Show trend (what changed over time).

 * Highlight drivers (which SKUs / channels / regions contributed).

 * Point out risks (returns, inventory).

 * Recommend actions (promotions, inventory moves, product fixes).

## 12) Technical & performance considerations

 * Aggregate at the right level (daily or monthly) to avoid too large datasets in visuals.

 * Precompute heavy measures (e.g., attribution, complex joins) in ETL.

 * Limit visuals to ≤ 10 on a single page for speed.

 * Cache refreshes if using Power BI / Tableau server.

## 13) Security & sharing

 * Row-level security by region or business unit.

 * Export options: PDF for execs, CSV/Excel for operations.

 * Set view/edit permissions based on role.

## 14) Example quick script of talking points (30–45 seconds)

“Dashboard last refreshed on [date]. Revenue is ₹X (MoM Y%). Units sold are Z, with ASP ₹A indicating a [price/mix] effect. Top SKU is S1 (₹R, U units) — however return rate for S1 is R% which needs product QA. Region South shows strongest growth; inventory for S2 is low — recommend expedite reorder. Details and drilldowns available by SKU and channel on the right.”

## 15) Next steps you can take (practical)

 * Validate data quality: check duplicates, missing SKUs, price mismatches.

 * Add one operational alert and test how stakeholders respond.

 * Schedule a 10-minute walkthrough with the team using the “story” steps above.

 * If you want, I can draft the 30–45 sec spoken script for your HR presentation tailored to your exact numbers (paste them here).
