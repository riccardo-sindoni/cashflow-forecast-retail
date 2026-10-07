# Cash Flow Forecast Q4 2026 – Retail Chain (demo)

Interactive quarterly cash flow forecast for a multi-store retail chain, with scenario analysis and adjustable assumptions.

> **Note on data:** all store names, company names and amounts are **synthetic**. They were generated for this project and do not correspond to a real company. The structure and logic of the model are inspired by a real retail finance case.

**Live demo:** `https://riccardo-sindoni.github.io/cashflow-forecast-retail/`

## Business problem
A retail group with 23 stores needs to know, month by month, whether cash will cover the Christmas season: incomes peak in December, but goods ordered in November are paid 30 days later, and a 13th-month salary and VAT payments fall in the same weeks.

## What the dashboard does
- Three scenarios (prudent, base, optimistic) based on sales growth vs. the previous year
- Adjustable assumptions: goods cost on sales, extra monthly outflows, opening balance
- Optional VAT module: monthly settlement paid on the 16th of the following month, plus the December advance (88%)
- KPIs for the quarter: inflows, outflows, net cash flow, end-of-year balance
- Charts: inflows vs. outflows, month-end balance by scenario, outflow mix, sales by store (filterable by company)
- Detailed monthly table with all items

## Method
1. **Sales:** same month of the previous year per store, plus scenario growth. Stores with incomplete history are estimated using a seasonal index from recent months.
2. **Goods:** percentage of sales; orders paid 30% at order and 70% after 30 days. A concession store is modeled at 60% of its sales.
3. **Rents, payroll, financing:** monthly average of recent months, with a 13th-month salary in December.
4. **VAT:** 22% on sales, goods and rents, settled monthly with carried-forward credits.
5. **Out of scope:** one-off costs; the opening balance is the sum of past flows, not a bank balance.

## Key insights
- December concentrates the year's cash generation, but the 70% balance of the Christmas order falls in January, outside the quarter.
- The goods percentage is the most sensitive assumption: small changes move the year-end balance more than the growth scenario.
- Including VAT changes the cash profile noticeably, especially in December.

## Tools
HTML, CSS, JavaScript, Chart.js. A companion Excel model with formulas is planned.

## What I learned
Building a forecast whose assumptions can be changed live forces every rule (payment terms, seasonality, VAT timing) to be explicit, which makes the model easier to review and to challenge.
