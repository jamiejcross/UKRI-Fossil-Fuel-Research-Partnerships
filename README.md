A Python search tool and interactive D3.js dashboard that identifies and visualises UKRI-funded research projects where fossil fuel companies are listed as project partners, collaborators, or participants.

Data Collection
Script: python/search_partners.py

Reads 310 coal, oil, and gas company names from an Excel directory (UoE _ EEI Global Companies Directory (Coal, Oil, Natural Gas).xlsx)
Searches the UKRI Gateway to Research (GTR) API for each company using fuzzy name matching (60% word overlap threshold)
For each matched organisation, fetches all linked projects via paginated API calls
Determines the company's role on each project: Project Partner (PP_ORG), Collaborator (COLLAB_ORG), or Participant (PARTICIPANT_ORG — Innovate UK model)
Enriches each record with: lead organisation, funder, grant value, dates, abstract, and grant category
Outputs a 14-column CSV: data/fossil_fuel_project_partners.csv
Results: 424 raw project-partner relationships across 46 matched companies and 326 unique projects, totalling £1.39B in grant funding (2006–2025).

False Positive Cleaning
Fuzzy matching produced spurious results. After manual review, 12 organisations (52 records) were excluded as genuine false positives — organisations with no connection to the fossil fuel sector:
