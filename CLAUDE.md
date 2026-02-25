# Fiber - FTTX Materials Analyzer Template

## Project Overview
Single-page HTML application for analyzing and comparing fiber optic materials from multiple data sources (KMZ, Excel, CSV, PDF, Smartsheet). Deployed as a static site on Vercel with auto-deploy from GitHub.

## Architecture
- **Single file app**: `index.html` — all HTML, CSS, and JS in one file (no build step, no package.json)
- **Libraries** (loaded via CDN):
  - Leaflet.js — interactive mapping with multiple tile layers (Esri World Topo, OSM, Esri Satellite, OpenTopoMap)
  - JSZip — KMZ/KML file parsing
  - SheetJS (XLSX) — Excel/Smartsheet parsing
  - PDF.js — PDF text extraction
  - Inter font from Google Fonts

## Key Features
- Light theme with CSS variables for easy theming
- Multi-file upload queue (batch files before processing)
- **Comprehensive materials catalog**: 150+ pre-loaded FTTX materials across 10 categories
- Editable quantities AND unit costs in dashboard — extended costs auto-calculate
- Category subtotals and grand total budget
- "Hide zero-quantity items" toggle to focus on active materials
- Collapsible category sections
- Three views: Map, Dashboard, Compare Sources
- Per-source data tracking with `dataSources[]` array
- Smart material mapping: file-detected materials auto-map to catalog via `MATERIAL_ALIASES`
- Unmapped materials from uploads go to a dynamic overflow category
- Fiber route classification (FTTH vs Backbone)
- Slack/waste buffer calculations
- JSON export with full catalog data

## Materials Catalog Categories
1. **Fiber Cable** — 2F-864F aerial & underground, drop cable variants
2. **Conduit / Microduct** — 5-18mm microduct, 1-24 way, HDPE 1"-4", innerduct
3. **Structures / Enclosures** — Handholes Tier 1-6, vaults, FDH cabinets, splice enclosures
4. **Splice Components** — Closures, trays, mechanical/fusion splices
5. **Connectors / Terminals** — SC/LC/MPO connectors, drop terminals, MSTs, NAPs
6. **Drop Materials** — Pre-cut drops, NIDs, ONT units, hardware
7. **Aerial / Pole Hardware** — Strand, lashing, clamps, guys, brackets
8. **Underground / Boring** — Bore, plow, trench, encasement, tape/wire
9. **Testing / Passive** — Splitters 1x2-1x128, patch panels, WDM, attenuators
10. **Restoration / Misc** — Ground rods, markers, permits, easements

## Key Data Structures
- `DEFAULT_MATERIALS` — immutable catalog constant with all items
- `projectMaterials` — mutable runtime copy (deep clone of defaults)
- `MATERIAL_ALIASES` — maps file-detected keys (e.g. "24F") to catalog IDs
- `resolveToMaterialId(rawKey)` — fuzzy matching function for uploads
- `mergeMaterialsIntoCatalog()` — merges all dataSources into projectMaterials

## Deployment
- **Live URL**: https://generic-materials-analyzer.vercel.app
- **Vercel Project**: `generic-materials-analyzer` (prj_AVHWhJ6vrpntQTSFmX2wz4QTWX5Q)
- **Vercel Team**: Sprocket-Networks (team_oDZmCn2oPMUHtWOlsWOGBlOm)
- **Auto-deploy**: Connected to GitHub — push to `main` triggers automatic deployment
- **GitHub Repo**: https://github.com/Sprocket-Networks/Generic-fiber-materials-analyzer
- **Production Branch**: `main`

## Local Development
- No npm/node required for development (it's a static HTML file)
- Preview locally with: `python3 -m http.server 8080 --directory /Users/kgmacbookpro15/Projects/sprocket-materials-analyzer`
- Then open: http://localhost:8080
- Node.js portable (for Vercel CLI if needed): `/tmp/node-v20.11.1-darwin-arm64/bin/`
  - Note: this is in /tmp and may not persist across reboots — re-download if needed

## Manual Deploy (if needed)
```bash
export PATH="/tmp/node-v20.11.1-darwin-arm64/bin:$PATH"
npx vercel --prod --yes
```
Usually NOT needed since auto-deploy from GitHub is active.

## GitHub Org: Sprocket-Networks
- **Owners**: Timothy Valis (timvalis), wgibson13 (Will Gibson, CEO)
- **Members**: kgibson13 (current user), Alex Lynn (awlynn68), patch (patchy-ai)
- User (kgibson13) has repo admin access but is org-level Member
- Org owner approval required for org-wide GitHub App installations

## Related Projects
- `/Users/kgmacbookpro15/Projects/sprocket-collin-county-demo/` — Collin County FTTH demo (more specific, with real data)
- Vercel also hosts: collin-county-ftth, fwf-materials-analyzer, fiber-build-analyzer

## Workflow
1. Make code changes to `index.html`
2. `git add index.html && git commit -m "description" && git push origin main`
3. Vercel auto-deploys in ~15-20 seconds
4. Live at https://generic-materials-analyzer.vercel.app
