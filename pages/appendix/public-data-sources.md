---
layout: default
title: Public Data Sources
parent: Appendix
---

# Public Data Sources

This appendix documents the investigation into public and internal data sources for AI-driven communication processes, with specific focus on findings from Defra's AI agent prototypes.

**Public - Data Utilisation**: This investigation aimed to understand how different data types can be leveraged to enrich AI outputs and improve the relevance of communication lines through public and internal data sources.

## Parliamentary Questions Archive

In our prototypes, we heavily relied on the **official Parliamentary Questions API**, which provides structured access to all written and oral questions submitted to the UK Parliament. We elected to build our own set of scripts to pull data from the parliamentary questions API ourselves.

While the House of Commons Library also maintains an R package called `clquestions` for accessing this data, it has not seen recent updates.

**Technical Implementation:**
- **Approach**: Custom scripts built for Parliamentary Questions API
- **Data types**: Written questions, oral questions, ministerial statements
- **Access**: Free, structured API access
- **Update frequency**: Real-time
- **Licensing**: Parliamentary Copyright
- **Alternative**: `clquestions` R package (not actively maintained)

## Hansard Debate Transcripts

There is currently **no official API available** for accessing Hansard debate transcripts in the same way as Parliamentary Questions. However, an unofficial R package called `hansard` is available, which is designed to extract data from the Parliamentary archive datasets.

**Technical Challenges:**
- **Operational complexity**: Introduces dependency on R programming language, not commonly used within Defra
- **Bridge requirements**: R can be run via Python or JavaScript bridges, but adds maintenance overhead
- **Maintenance concerns**: Package appears no longer actively maintained
  - Last repository commit: Four years ago
  - Latest CRAN build: 2019
- **Reliability risks**: Structure changes to Parliamentary website could break scraping functionality
- **Repository**: [https://github.com/evanodell/hansard](https://github.com/evanodell/hansard)

**Practical outcome**: We may need to build a custom web scraper to ensure consistent data access.

**Current Status:**
- **Data types**: Debate transcripts, division lists, committee proceedings
- **Access**: Unofficial scraping via R package or custom implementation
- **Update frequency**: Same day for current proceedings
- **Licensing**: Parliamentary Copyright

## Policy and Legislative Documentation

The **GOV.UK Content API** provides structured data in JSON format, delivering access to policy pages, guidance, announcements, and other official publications.

**Technical Details:**
- **API Documentation**: [https://content-api.publishing.service.gov.uk/](https://content-api.publishing.service.gov.uk/)
- **Capabilities**: Automated content discovery, change tracking over time
- **Structure**: Designed around GOV.UK website layout
- **Status**: Beta (stability not guaranteed long-term)

**Implementation Requirements:**
- Prior knowledge of GOV.UK site structure required
- Robust mechanism needed for navigating content hierarchy
- API familiarity with human-facing webpage organisation

**Benefits:**
- Reduces need for scraping and manual data collection
- Structured and consistent data format
- Real-time access to policy updates

**Limitations:**
- Beta status may introduce breaking changes
- Requires understanding of site organisation
- Designed around webpage structure rather than data consumption

## Research Briefings

A **public API for Research Briefings** provides access to House of Commons Library publications, including briefing papers, debate packs, and POSTnotes.

**API Details:**
- **Endpoint**: `GET https://lda.data.parliament.uk/researchbriefings.json?_page=0&_view=all&_metadata=all`
- **Data types**: Briefing papers, debate packs, POSTnotes
- **Access**: Free, programmatic search and retrieval
- **Use case**: Integration of high-quality reference material into workflows

**Available Tools:**
- **R Package**: [https://github.com/houseofcommonslibrary/clbrief](https://github.com/houseofcommonslibrary/clbrief)
- **Status**: Not updated in several years
- **Recommendation**: Build lightweight custom integration for long-term reliability and compatibility

## UK Government Open Data

**GOV.UK Data Portal**
- URL: [data.gov.uk](https://data.gov.uk)
- Description: Central repository for UK government open data across all departments
- Data types: Statistics, geographical data, spending data, performance indicators
- Access: Free, API available, bulk downloads
- Update frequency: Varies by dataset (daily to annual)
- Licensing: Open Government Licence v3.0