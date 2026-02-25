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
- Editable material quantities in dashboard
- Three views: Map, Dashboard, Compare Sources
- Per-source data tracking with `dataSources[]` array
- Fiber route classification (FTTH vs Backbone)
- Slack/waste buffer calculations
- Export functionality

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
