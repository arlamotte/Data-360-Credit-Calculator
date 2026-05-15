### Purpose

This calculator estimates Data Cloud credit consumption for recurring loads across three scenarios:

- `Worst case`
- `Current`
- `Target`

You can model:

- `full` and `delta` loads
- volume per run
- runs per month
- load `usage type`
- `Sandbox` or `Production` environment

### Screen structure

1. **Rate card source via PDF**
   - Salesforce PDF URL input.
   - Button to load rates automatically.
   - Button to restore default rates.
2. **Rate card**
   - Table with `Production` and `Sandbox` values by usage type.
3. **Comparative summary**
   - Monthly and yearly totals by scenario.
   - Savings: target vs current, and target vs worst.
4. **Recurring load scenarios**
   - Separate tabs for `Worst case`, `Current`, and `Target`.
5. **Breakdown by usage type**
   - Consolidated cost by usage type per scenario.
6. **Diagnostics**
   - Risk level and automated recommendations.
7. **Export / import**
   - Save and restore assumptions in JSON format.

### How to load usage types/rates from Salesforce PDF URL

1. Open **Rate card source via PDF**.
2. Paste the public Salesforce pricing PDF URL into **PDF URL**.
3. Click **Load rates from URL**.
4. Check the status message:
   - success: rates updated and number of matched usage types
   - error: HTTP failure, parsing issue, or CORS block
5. Validate the loaded values in the **Rate card** table.

#### CORS note

If the PDF host blocks CORS, browser-side reading may fail. In that case:

- open the HTML through a local web server (not `file://`)
- use a public URL that allows cross-origin reads

### How to configure language

In the **Language** selector, choose:

- `Portuguese`
- `English`
- `Spanish`

UI labels and dynamic messages update immediately. Language is also saved in exported JSON (`language`) and restored on import.

### Recommended workflow

1. Set language and environment.
2. Load rates from PDF URL (or keep defaults).
3. Fill in **Current** first.
4. Build **Target** with optimization assumptions.
5. Use **Worst case** as an upper risk bound.
6. Compare summary KPIs and usage-type breakdown.
7. Export JSON to keep versioned assumptions.

### Best practices

- use clear, standardized load names
- model `full` and `delta` separately
- validate volume unit (`1M rows processed`)
- use worst case as a ceiling, not a baseline
- update assumptions whenever frequency, volume, or strategy changes

### Limitations

- PDF parsing depends on the document text structure
- calculator does not replace contractual/commercial validation
- contract discounts are not automatically applied
- no direct real-time org usage integration
