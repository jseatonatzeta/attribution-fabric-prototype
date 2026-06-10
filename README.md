# Attribution Fabric Prototype

Interactive prototype demonstrating how a unified attribution surface would consume the proposed Zeta identity-fabric primitives — **Enterprise Events Log (EEL)**, **Lineage Logs**, and **SuperGraph Transition Logs** — to support multi-touch attribution, incrementality (including ZX-style propensity-decile stratified designs), and household projection from the same underlying data.

[**Open the prototype →**](https://jseatonatzeta.github.io/attribution-fabric-prototype/)

Companion to the Confluence design doc [**Identity Fabric for Unified Attribution**](https://zetaglobal.atlassian.net/wiki/spaces/PROD/pages/2010087583/Identity+Fabric+for+Unified+Attribution) (Zeta-only).

## What it shows

- **Controls** — switch attribution model (first / last / linear / time-decay / position-based), grouping (ZID, BSIN, customer ID, household), and view mode (MTA only / incrementality only / both).
- **Headline KPIs + run diagnostics** — first-pass match rate, second-pass rescue, placeholder-only conversions, audience-lineage parity, avg touchpoints per converter, freshness watermarks.
- **Athena insights** — narrative interpretation of the current view, driven by the same fabric outputs.
- **MTA section** — credited conversions by channel and top sources, with per-model deltas.
- **Incrementality section** — four-arm experiment (served / ghost / PSA / holdout) with three lift baselines (vs ghost as canonical, vs PSA, vs holdout) and per-channel incremental conversions.
- **Stratified test design** — per-decile breakdown, lift chart, allocation, and the propensity-score homogeneity-validation table that ZX-style decile-randomization designs publish.
- **Credited vs. Incremental by channel** — the calibration view that surfaces where the MTA model is over- or under-claiming.
- **Audiences & Waterfall** — campaign audiences, lineage-coverage status, and an editable per-run waterfall.
- **Data Inspector** — sample data for every fabric store (EEL exposures, EEL conversions, EEL identity events, Lineage Logs · Audience, SuperGraph Transition Logs) and the 11 canonical SQL joins the attribution engine runs.
- **Supported feature enhancements** — features the fabric already supports that an attribution UI could pick up without further infrastructure work.

## Design context

The prototype's data is illustrative. Several specific representations (notably the placement of `propensity_score` / `propensity_model_id` on EEL exposure rows) are flagged as open architectural decisions in the [Confluence design doc](https://zetaglobal.atlassian.net/wiki/spaces/PROD/pages/2010087583/Identity+Fabric+for+Unified+Attribution).

## Running locally

It is a single self-contained HTML file with React, ReactDOM, Chart.js, and Babel loaded from CDN. Open `index.html` in any modern browser, or:

```
cd attribution-fabric-prototype
python3 -m http.server 8000
# then visit http://localhost:8000/
```

No build step, no install.
