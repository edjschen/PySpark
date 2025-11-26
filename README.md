# PySpark & Python Sample code - Data Analytics & Web Scraping Repository

PySpark ETL pipelines and Python web scraping for e-commerce analytics.

---

## Files

### 1.`first_purchase_analysis.ipynb` (PySpark)
**Purpose**: Analyze first-time buyer behavior and customer lifetime value

**Key Outputs**:
- Time-to-first-purchase distribution (registration to first order)
- Daily GMV and transaction counts per user
- Top products purchased by new buyers (within 10 days)
- `output.csv` + `graph.png` visualization

**Filters**: April-May 2023 registrations, active users only, transactions ≤ 200K

---

### 2. `log_processing_pipeline.ipynb` (PySpark)
**Purpose**: Process web server logs into structured session data

**Key Features**:
- Parse gzipped logs with custom delimiter (`<t@s>`)
- Extract UTM parameters, referrer URLs, user agent data
- Session identification (30-minute timeout rule)
- URL classification (find/item/home/social/mail/referral)

**Custom Functions**:
- `classify_url_type()` - Categorize URLs by type
- `parse_os()`, `parse_browser()` - Extract device info from user agent
- `estimate_df_size()` - Calculate DataFrame memory usage

**Output**: 50 partitions/day, ~10 min processing time

---

### 3. `category_scraper.py` (Python/Selenium)
**Purpose**: Scrape product category hierarchies from e-commerce site

**Workflow**:
1. Navigate "3C" and "Home appliances" categories
2. Extract subcategory links and attributes
3. Retry mechanism (6 attempts per element)
4. Resume capability via checkpoint files

**Outputs**: `./data.xlsx` (scraped data), `./done.xlsx` (progress tracker)



---

## Tech Stack

| File | Technology       | Environment |
|------|------------------|-------------|
| 1-2  | PySpark          | Jupyter/Livy notebook |
| 3    | Python, Selenium | Local script |
