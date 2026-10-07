# Warning to Action — Bangladesh Early-Warning Research Prototype

**[Open the live prototype](https://aitullalimon.github.io/bangladesh-early-warning-prototype/)**

A people-centered early-warning demonstrator by **Aitulla Labib Limon**, Research Student at KCGI, Kyoto, Japan. It explores how warning information can become understandable guidance, citizen action, and structured feedback for human support teams.

> **Research simulation only.** All warnings, rainfall values, assistance requests and evaluation records are demo data. This application does not forecast hazards, issue official warnings, dispatch assistance or provide an emergency monitoring service.

## What works

- Full Bangladesh interactive map with 64 district polygons and linked selectors for 8 divisions and 64 districts.
- CARTO Voyager basemap, pan/zoom, district labels, simulated rainfall colors and legend.
- District side panel with selected location, illustrative rainfall and available research scenarios.
- Flood and thunderstorm/lightning scenarios in Kurigram, with different available action times.
- Clearly separated authority-information and communication-guidance layers.
- Household acknowledgement and preparedness/protective-action checklists.
- Simulated assistance requests and a support-team inbox with review status and filters.
- Eight-step presentation mode for a 5–7-minute professor walkthrough.
- Condition A/B evaluation: comprehension, action choice, relevance, perceived risk, intention, trust, usability and response time.
- Local JSON export and demo reset.

## Professor demonstration

1. Open the site and select **Flood — Kurigram**.
2. Show the synthetic warning and its FFWC/BWDB source reference.
3. Click **Explain this warning** and show the predefined guidance.
4. Click **Prepare / Act**, acknowledge understanding, complete the checklist and save.
5. Click **Need Assistance**, use fictional details, and submit the simulated request.
6. Open **Support-Team Dashboard** and show the response and request.
7. Explain: “This demonstrates the two-way communication component of my framework.”
8. Switch to **Thunderstorm / Lightning** and show why rapid shelter guidance replaces longer-term preparation.
9. Open **Research Evaluation** and compare **Condition A vs Condition B**.

Click **Presentation mode** for guided navigation. The guide changes views but never invents citizen responses or completes checklists on your behalf.

## Run locally (optional)

```bash
git clone https://github.com/aitullalimon/bangladesh-early-warning-prototype.git
cd bangladesh-early-warning-prototype
python3 -m http.server 8000 
```

While this server is running on your computer, visit http://localhost:8000. For ordinary access, use the live link at the top.

No package installation or build is needed. The interface, district boundaries and Leaflet code are included in the repository; internet access is required for background map tiles. District polygons remain usable when tile requests fail.

## Validation

With Node.js 18 or later:

```bash
node --check app.js
node check.cjs
```

Checks cover scenario isolation, checklist completion, assistance submission, dashboard visibility, evaluation scoring, text escaping, the 8/64 administrative list, linked selectors, presentation controls, rainfall classes, district-name mapping and map initialization wiring. These are logic checks with a lightweight DOM stub; they do not replace visual or real-browser testing.

## Architecture and storage

Buildless HTML/CSS/JavaScript. Leaflet handles maps. All demo responses are stored in the current browser's `localStorage` under `warning-action-demo-v1`; there is no backend, central database, authentication or multi-user service. Citizen and support-team views are two views of the same local research session. Tabs on the same origin synchronize through the storage event. Different browsers, devices and hosting origins do not share records.

**AI Stage A:** predefined hazard-specific guidance templates; no LLM API is called. A future Stage B would require a controlled knowledge base, grounded generation, output validation, failure handling and expert review. This repository does not claim those features are implemented.

The A/B instrument is manually selected demonstration mode, not randomized experimental software. Repeated responses are not independent participants. No causal improvement, statistical significance or real-world preparedness benefit is claimed.

## Sources and attribution

- [Bangladesh National Portal](https://bangladesh.gov.bd/views/district-list/District-List/): administrative hierarchy.
- [FFWC / BWDB](https://ffwc.gov.bd/): flood authority reference; the warning text is synthetic, not an issued bulletin.
- [BMD lightning warning](https://www.bmd.gov.bd/web/en/p/Lightning-Warning): weather authority reference; no live warning feed.
- [National Weather Service safety guidance](https://www.weather.gov/safety/): guidance reference; local expert validation is required before field use.
- [geoBoundaries BGD ADM2](https://www.geoboundaries.org/api/current/gbOpen/BGD/ADM2/): BBS/OCHA ROAP district boundaries, geometry representing 2020, CC BY 3.0 IGO. Display names are mapped to current district names.
- [Leaflet 1.9.4](https://leafletjs.com/): BSD-2-Clause.
- [CARTO](https://carto.com/attributions) Voyager tiles and [OpenStreetMap contributors](https://www.openstreetmap.org/copyright): basemap attribution displayed on the map.

Weather symbols are district-label decorations at approximate bounding-box centers, not monitoring stations. Rainfall totals are illustrative 24-hour values, not observations or forecasts, and do not generate warnings. The repository uses the verified public Voyager tile endpoint without embedding the personal key supplied during development.

## Deployment

GitHub Actions runs the logic checks and packages the website assets in `_site/` and publishes them to GitHub Pages on each push to `main`. In repository **Settings → Pages**, select **GitHub Actions** as the source. Manual redeployment is available from **Actions → Deploy research prototype → Run workflow**.

## Project files

| Path | Purpose |
| --- | --- |
| `index.html` | Application shell |
| `style.css` | Responsive interface and map styles |
| `app.js` | Scenarios, citizen flow, dashboard, evaluation and map behavior |
| `districts-data.js` | 64 district geometries and normalized names |
| `leaflet.js`, `leaflet.css` | Vendored map library |
| `map-source.txt` | Map attribution and simulation notes |
| `check.cjs` | Local logic checks |
| `.github/workflows/pages.yml` | Checks and automatic Pages deployment |
| `RESEARCH_NOTES.md` | Research boundaries and future work |
| `THIRD_PARTY_NOTICES.md` | Third-party licensing and attribution |

## Research scope and future work

This prototype demonstrates communication feasibility. Future work includes official data integration, expert-reviewed Bengali guidance, controlled AI generation, consent and ethics procedures, randomized assignment, validated measurement instruments, secure multi-user storage and field evaluation. These are planned capabilities, not completed results.

[Academic portfolio](https://aitullalimon.github.io/academic-portfolio/) · [GitHub profile](https://github.com/aitullalimon)
