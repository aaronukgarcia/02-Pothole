# PotholeWatch: An Open Data Commons for Road-Surface Health

*A concept paper*

## What is PotholeWatch?

PotholeWatch proposes an open data commons for road-surface condition: a neutral pool where any device — a fleet vehicle's telematics, a phone running a detection app, a citizen with a web form — can contribute a tiny anonymous defect report, and where the aggregated clusters are published under an open licence that any council, researcher, or routing app can use.

The report model is deliberately minimal: a timestamp, a WGS84 location, a source class, an optional bump intensity. Roughly 120 bytes. No names, no number plates, no images required.

## Why it doesn't already exist

Every layer of this idea exists in some closed, static, or single-jurisdiction form — and the paper surveys them honestly:

- **FixMyStreet / Open311** — citizen reporting, human-only, per-jurisdiction
- **Pothole Patrol (2008), Nericell (2008), Mednis (2011)** — proved phones and vehicles detect defects; study-bounded datasets
- **Street Bump (Boston, 2011)** — the canonical equity-bias warning every crowdsourced system inherits
- **Waymo + Waze (April 2026)** — machine-detected potholes fed to cities, in closed, single-fleet form
- **OpenStreetMap surface tags** — open but static; no defect events, no freshness

No system combines machine ingestion from any source, defect-level events with freshness, open licensing, and cross-jurisdiction scope. That combination is the proposal.

## What the paper does and doesn't claim

This is a concept paper, not a specification, and nothing in it is built. The hard problems are stated as open questions with candidate approaches, tagged as hypotheses:

- **Trust versus privacy** — the central tension: device accountability creates linkable movement trails; candidate mitigations (Privacy Pass-style rotating credentials, aggregate-only publication) are untested
- **Equity** — refuse-collection fleets visit every street regardless of neighbourhood income; whether that defeats the Street Bump bias is an empirical question
- **Cold start and funding** — unsolved; the adoption path argued is institutional (procurement data-sharing clauses), not volunteer

## The proposed first test

One borough, one refuse fleet: accelerometer loggers on a council's own bin lorries, open defect clusters for one collection area, ground-truthed against the council's inspections for one season — with defined success criteria and a go/no-go decision at the end.

## Documentation

See [`PotholeWatch_v11.0.pdf`](PotholeWatch_v11.0.pdf) for the full concept paper.

*Note: this v11 concept paper replaces the earlier v8 technical white paper, which was withdrawn for overstating the maturity of unbuilt components.*

## Call for Contributors

The concept needs adversaries before it needs code: geospatial and distributed-systems engineers, privacy engineers, council asset-management practitioners, fleet operators, and open-data governance specialists.

## License

MIT License — see [LICENSE](LICENSE). The proposed commons dataset itself would use an ODbL-style open database licence.

## Contact

Aaron Garcia
aaron@garcia.ltd
