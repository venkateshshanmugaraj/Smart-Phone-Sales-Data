# Smart-Phone-Sales-Data
This dashboard provides a clear view of smartphone sales across models, regions, and channels. It highlights key metrics like revenue, units sold, and ASP, and uses visual charts to show trends. Filters and drilldowns help identify top products, slow movers, and issues such as high returns or low stock.

1) Purpose & audience (start here)

 * State the dashboard’s goal in one sentence: e.g. “Help product, sales and operations teams quickly see how smartphone models and channels are selling, spot trends and underperformers, and take actions to hit revenue/stock targets.”

 * Define the audience and their needs: e.g. Sales Manager (daily ops), Product Manager (weekly trends), Finance (monthly revenue), Executive (top-level health).

2) Source data & refresh

 * Primary files/tables assumed: Orders (order_date, sku/model, units, unit_price, revenue, channel, region), Inventory, Returns, Cost (COGS), Promotions.

 * Refresh cadence: daily or weekly (mention whichever applies).

 * Note ETL steps: join by SKU, standardize dates, normalize channel names, handle missing values.

3) Data model & transformations (high level)

 * Build a single fact table (Sales) and small dimension tables (Product, Channel, Region, Date).

 * Typical transforms:

     * Parse order_date → Year, Month, Week.

     * Compute Revenue = units * unit_price (if not provided).

     * Flag returns and adjust net units/revenue if needed.

     * Create category (flag flagship / midrange / budget) from model names.  
