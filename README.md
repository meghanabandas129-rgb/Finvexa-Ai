# Finvexa AI

A small-business cash-flow and order decision tool built for the F-03 hackathon problem statement. It helps answer: **Can we afford to accept this order, and what payment terms maintain our cash reserve?**

## Getting started

Download `Finvexa_AI.py` from this repository and open PowerShell in the folder containing it.

Requires Python 3.10 or newer. No package installation or API key is required.

```powershell
python .\Finvexa_AI.py
```

Open **http://localhost:8066**. Keep PowerShell open; press Ctrl+C to stop.

If the port is occupied:

```powershell
python .\Finvexa_AI.py --port 8067
```

Then open http://localhost:8067.

## Features

- 30-, 60- and 90-day cash forecasts with charts, cash status and reserve warnings.
- Editable income and expense records, search, filters and CSV export.
- Monthly expense creation and upcoming/overdue bill reminders.
- Order comparison with advance payments, late customer payments and a 10% cost increase.
- Suggested whole advance percentage that maintains the chosen reserve when feasible.
- Packaging, delivery, fee and other cost inputs with live estimated profit totals.
- Part-payment recording that updates opening cash and the unpaid balance.
- Saved comparison snapshots and validated JSON backup/restore.

## Demo

1. Review the sample bakery's income and expenses.
2. Check an order worth ₹40,000 with a base cost of ₹18,000.
3. Add packaging of ₹500 and delivery of ₹800.
4. Observe total cost ₹19,300 and estimated profit ₹20,700.
5. Compare payment terms, try the suggested advance, and save the results.

Cash results depend on the existing transactions and forecast settings.

## Technology stack

| Layer | Technology |
| --- | --- |
| Interface | HTML, CSS and JavaScript |
| Backend | Python standard-library HTTP server |
| Financial calculations | Python Decimal |
| Charts | SVG |
| Data persistence | Browser local storage |
| Export and backup | CSV and JSON |

## Project file

`Finvexa_AI.py` contains the complete application. No separate frontend folder, dependency installation or build step is needed.

## How it works

The complete app is contained in one Python file. Python's standard-library HTTP server serves embedded HTML, CSS and JavaScript. A Decimal calculation engine computes daily closing balances and scenario results. Browser local storage retains entries; backups are user-downloaded JSON files.

## Calculation assumptions

Opening cash includes money already paid or received. Recording a payment adjusts opening cash automatically: do not adjust it again for that payment. Only the remaining unpaid balance enters future forecasts. Existing settled records are excluded. Past unpaid records are assumed to settle on the forecast start date. Same-day amounts are netted, so intraday shortages are not detected. Base cost excludes separately entered extras; all order costs and advances occur on the cost date. Payments beyond the selected horizon are excluded. Advance suggestions use normal costs and on-time payment; stress scenarios are separate. Profit excludes taxes or costs not entered. Saved comparisons are historical snapshots.

## Current scope

This is a localhost hackathon MVP with sample data. There is no connected AI model, bank integration, authentication or cloud database. Explanations are calculation based. The server is not configured for public hosting. Data belongs to the current browser origin; use backup/restore to move between browsers or ports.

## Validation

Calculation checks cover shortages, Decimal arithmetic, paid/partial records, advances, delays, cost increases and profit. JavaScript logic checks cover backup validation, recurring dates, filters, export and payment handling. HTTP checks verify embedded assets and the calculation API. Visual browser testing remains incomplete.

## Planned improvements

- AI explanations grounded in the calculated results.
- User authentication and a cloud database.
- Customer payment history and more fulfilment scenarios.
- Public deployment with production server configuration.

These are planned enhancements and are not included in the current application.
