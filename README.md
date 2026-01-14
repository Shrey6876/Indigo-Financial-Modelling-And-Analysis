IndiGo Route-Level Economic Analysis
A comprehensive route profitability assessment framework for IndiGo’s top domestic routes in India.
​

Overview
This project performs a route-level unit economics analysis for IndiGo’s top 30 domestic routes by estimating route revenue, operating cost, and gross margin using a transparent modeling approach (yield-based revenue and CASM-based cost).
​
It produces a consolidated route economics dataset and a set of strategic insights around which route types (tier and distance bands) are structurally higher margin.
​

What the project does
Builds a route dataset with route name, origin, destination, flights, annual passengers, tier, load factor, IndiGo share, and distance (where available).
​

Models route revenue using a base yield per passenger and tier-based yield premiums.
​

Models route cost using ASK (Available Seat Kilometers) and a base CASM assumption, with seat-count estimated by distance band.
​

Computes profitability metrics such as gross margin, margin percent, and per-flight profit metrics.
​

Exports results (CSV/Excel/JSON outputs are generated in the notebook workflow).
​

Repository contents (recommended)
notebooks/

Indigo-Route-Level-Economic-Analysis.ipynb (main notebook)
​

Untitled.ipynb (backup/alternate run)
​

src/

indigo_project.py (Python script version / core logic)
​

docs/

Code-explanation.docx (methodology and documentation)
​

outputs/ (generated)

IndiGoRouteEconomicsAnalysis.csv and other exported artifacts depending on the run
​

If you want, I can generate an exact GitHub-ready folder structure and tell you which files to move where.

Data inputs
The notebook expects a domestic routes table containing columns similar to: Rank, Route, Flights 2023, Annual Passengers (M), Tier, IndiGo Share, Load Factor, Origin, Destination, and Distance (km).
​
Distance values are added/validated in the workflow, and some routes may have missing distance values (which can affect cost calculations).
​

Methodology
Revenue model
Base yield is set to INR 7,754 per passenger.
​

Tier-based yield premiums are applied: Tier-2 uses +5% and Tier-3 uses +12% relative to Tier-1.
​

Route revenue is computed from annual passengers and yield (converted into INR Crores).
​

Cost model
Base CASM is set to INR 3.88 per ASK.
​

Seats are estimated using distance bands (e.g., shorter routes mapped to A320neo 180 seats; longer routes mapped to A321neo 232 seats).
​

ASK is computed as: Flights × Seats × Distance (km).
​

Route operating cost is computed as: ASK × CASM (converted into INR Crores).
​

Profitability metrics
Gross Margin (INR Cr) = Revenue (INR Cr) − Cost (INR Cr).
​

Margin Percent = Gross Margin / Revenue × 100.
​

Per-flight revenue/cost/profit are derived by scaling route totals by flights.
​

Routes are ranked by profitability (gross margin) to generate a profit rank.
​

Outputs
The workflow prints route economics summaries and exports a consolidated dataset containing (typical fields): Route, Tier, Distance, Flights, Passengers, Revenue, Cost, Gross Margin, Margin %, and per-flight metrics.
​
One of the key exports in the notebook run is IndiGoRouteEconomicsAnalysis.csv (top 30 route economics).
​

Key findings (from the run in the notebook)
Most profitable route by gross margin: Mumbai-Bangalore (gross margin INR 3,820.74 Cr; margin 71.5%).
​

Least profitable route by gross margin: Kolkata-Mumbai (gross margin INR 510.59 Cr; margin 30.1%).
​

Tier performance ranking by average margin: Tier-3 highest, then Tier-2, then Tier-1.
​

Distance vs profitability: short-haul routes (<1000 km) show much higher average margin than long-haul routes (>1500 km).
​

How to run
Option A: Notebook (recommended)
Open notebooks/Indigo-Route-Level-Economic-Analysis.ipynb.
​

Run cells top-to-bottom to reproduce:

Data checks and distance enrichment

Revenue modeling

Cost modeling

Route economics summary and exports
​

Option B: Python script
If you want the repo to be runnable end-to-end via python src/indigo_project.py, the current script may need minor refactoring to:

Remove local machine paths and notebook-only assumptions

Accept data file paths as parameters

Write outputs into an outputs/ folder
​

Tell me your preferred execution style (Notebook-first vs CLI-first) and I’ll rewrite the repo so it runs cleanly.

Dependencies
The codebase uses standard data tooling such as pandas, numpy, scipy, plotly, and related utilities.
​
If you want, I can generate a clean requirements.txt based on your exact imports and versions.

Disclaimer
This project is intended for academic and educational purposes and does not constitute investment advice.
​
All modeling outputs depend on assumptions (yield, CASM, seat mapping, distance availability) and should be interpreted accordingly.

