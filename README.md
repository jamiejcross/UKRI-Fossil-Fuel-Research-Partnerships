**UKRI FOSSIL FUEL RESEACH PARTNERSHIPS DASHBOARD**

A Python search tool and interactive D3.js dashboard that identifies and visualises UKRI-funded research projects where fossil fuel companies are listed as project partners, collaborators, or participants.

**Data Collection**
Script: python/search_partners.py

Reads 310 coal, oil, and gas company names from an Excel directory (UoE _ EEI Global Companies Directory (Coal, Oil, Natural Gas).xlsx)
Searches the UKRI Gateway to Research (GTR) API for each company using fuzzy name matching (60% word overlap threshold)
For each matched organisation, fetches all linked projects via paginated API calls
Determines the company's role on each project: Project Partner (PP_ORG), Collaborator (COLLAB_ORG), or Participant (PARTICIPANT_ORG — Innovate UK model)
Enriches each record with: lead organisation, funder, grant value, dates, abstract, and grant category
Outputs a 14-column CSV: data/fossil_fuel_project_partners.csv
Results: 424 raw project-partner relationships across 46 matched companies and 326 unique projects, totalling £1.39B in grant funding (2006–2025).
After manual review, 12 organisations (52 records) were excluded as genuine false positives — organisations with no connection to the fossil fuel sector:

Libraries (CDN): D3.js v7, d3-sankey v0.12, Chart.js v4, PapaParse v5, Leaflet v1.9, jsPDF v2.5

**6 tabs**
1. Overview — KPIs (partnerships, funding, companies, universities, active projects), horizontal bar charts for research themes and funding by theme, top 20 universities and companies, donut charts for partnership role, funder, project status, and grant category, grant size distribution
2. Company-University Network — D3 force-directed graph. Companies as orange circles, universities as navy squares. Edge thickness = shared projects. Interactive slider to set minimum connection threshold. Drag and hover.
3, Relationship Flow — D3 Sankey diagram. Top 15 companies (left) → research themes (centre) → top 15 universities (right). Flow width = number of projects.
4. Geography — Leaflet map with ~40 UK university coordinates. Circle size = total funding. Click for popup with partner companies and project list.
5. Timeline — Stacked area chart (2006–2025) showing project count by theme per year. Clickable legend to toggle categories.
6. Project Table — All 372 records, sortable by any column, with colour-coded theme tags.

**Features**
- Active/All project filter toggle
- Export buttons on every chart (PNG/JPG/PDF)
- Client-side thematic tagging via regex (10 categories + Other)
- 10 research themes (auto-tagged):

**Themes**
- Energy Systems & Grids	#e65100	energy system, grid, power, smart grid, turbine
- Offshore & Marine	#00838f	offshore, marine, subsea, ocean, decommission
- Robotics & AI	#6a1b9a	robot, autonomous, AI, machine learning, sensor
- Decarbonisation & Net Zero	#2e7d32	decarbonisation, net zero, CCS, hydrogen
- Oil & Gas Upstream	#795548	petroleum, reservoir, drilling, seismic, hydrocarbon
- Materials & Manufacturing	#1565c0	materials, manufacturing, composite, polymer
- Environmental Science	#00897b	environment, ecology, biodiversity, pollution
- Nuclear & Storage	#c62828	nuclear, battery, energy storage, radioactive
- Training & Capacity	#f9a825	doctoral training, CDT, fellowship, KTP
- Infrastructure & Transport	#546e7a	infrastructure, construction, transport, vehicle

**Key Statistics (clean data)**

372 project-partner records
~330 unique projects
~38 fossil fuel companies
~80 lead universities
£1.3B+ total grant funding
Top companies: BP (74), Jacobs (31), ExxonMobil (27), Natural Resources Canada (23), Shell (20)
Top universities: Imperial College London (32), Cambridge (24), Heriot-Watt (20), Manchester (20)
Top funders: EPSRC (208), NERC (118), ISCF (35)
Roles: Collaborator (60%), Project Partner (30%), Participant (10%)
Peak year: 2017 (44 projects)
