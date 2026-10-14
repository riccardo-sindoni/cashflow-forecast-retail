# Cash Flow Forecast Q4 2026 – Retail Chain (demo)

I built an interactive quarterly cash flow forecast for a multi-store retail chain, with scenario analysis and adjustable assumptions. The goal is to show how a finance question can be turned into a model that anyone can change and challenge.

> **Note on data:** all store names, company names and amounts are **synthetic**. I generated them for this project and they do not correspond to a real company.

**Live demo:** https://riccardo-sindoni.github.io/cashflow-forecast-retail/

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
1. **Sales:** I project each store from the same month of the previous year, plus scenario growth. Stores with incomplete history are estimated with a seasonal index based on recent months.
2. **Goods:** a percentage of sales; orders are paid 30% at order and 70% after 30 days. A concession store is modeled at 60% of its sales.
3. **Rents, payroll, financing:** monthly average of recent months, with a 13th-month salary in December.
4. **VAT:** 22% on sales, goods and rents, settled monthly with carried-forward credits.
5. **Out of scope:** one-off costs. The opening balance is the sum of past flows, not a bank balance.

## Key insights
- December concentrates the year's cash generation, but the 70% balance of the Christmas order falls in January, outside the quarter.
- The goods percentage is the most sensitive assumption: small changes move the year-end balance more than the growth scenario.
- Including VAT changes the cash profile noticeably, especially in December.

## How I built it
I defined the business problem, the model logic and every assumption (payment terms, seasonality, VAT timing, scenario design). I built the dashboard with the help of an AI assistant (Claude, by Anthropic), which wrote the HTML and JavaScript from my specifications. My role was to specify what the model had to answer, review the output and check that the numbers were consistent with the rules I had set.

## Tools
HTML, CSS, JavaScript, Chart.js.

## What I learned
Building a forecast whose assumptions can be changed live forced me to make every rule explicit (payment terms, seasonality, VAT timing), which makes the model easier to review and to challenge.
