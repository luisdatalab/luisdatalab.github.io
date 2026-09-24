---
title: CLIMARISK
description: "An end-to-end climate and agricultural intelligence project combining data engineering, analytics engineering, BI, statistical analysis, and predictive modeling."
layout: page
permalink: /projetos/climarisk/
image:
  path: /assets/imagens/climarisk/part-01/climarisk-part-01-cover.png
  alt: "CLIMARISK project series"
---

![CLIMARISK project series](/assets/imagens/climarisk/part-01/climarisk-part-01-cover.png)

> **Project Series · In Progress**  
> Building a climate and agricultural intelligence product one layer at a time — from raw public data to analytics and, later, predictive models.

## Why I started this project

I live in Goiás, a Brazilian state where agriculture is part of the economic landscape. I had worked with data for years, but climate and agriculture were still domains I wanted to understand more deeply.

CLIMARISK became a way to learn that domain by building something real.

The project started with a simple question: **how can public climate, agricultural, and market data be transformed into information that is traceable, understandable, and useful for analysis?**

Instead of starting with a dashboard, I decided to build the project in layers. That choice turned CLIMARISK into a broader portfolio series covering data engineering, analytics engineering, data modeling, visualization, statistical analysis, and machine learning.

## Project scope

CLIMARISK is being developed as one product with complementary analytical modules:

- **Climate:** ENSO/RONI, climate anomalies, heat, precipitation, soil moisture, and historical context;
- **Agriculture:** production, productivity, crop estimates, crop progress, and territorial exposure;
- **Market:** international commodity price context;
- **Data Science:** temporal lag analysis, historical analogs, and future predictive models.

The goal is not to present agronomic recommendations or claim causal relationships from simple correlations. The project is designed to separate observed data, analytical indicators, historical associations, and predictive outputs.

## Current architecture

The engineering foundation uses a local Medallion architecture:

```text
Public Sources
     ↓
Bronze — immutable raw snapshots
     ↓
Silver — validated and standardized data
     ↓
Gold — analytics-ready datasets
     ↓
Semantic Model / Analytics
```

The pipeline also includes versioning, SHA-256 checksums, audit records, replay, rollback, publication controls, and stable `current/` datasets for analytical consumption.

## Data sources

The project currently works with or is preparing integration for public sources such as:

- NOAA — ENSO and RONI;
- NASA POWER — agroclimatology;
- IBGE PAM — annual agricultural production;
- IBGE LSPA — monthly crop estimates;
- CONAB — crop progress and seasonal context;
- World Bank — international commodity prices.

## Project series

The portfolio will document the project as it evolves. Each article represents a completed milestone rather than a summary written only after the final product is ready.

| Part | Topic | Status |
| --- | --- | --- |
| **01** | [Architecture & Data Engineering](/posts/climarisk-part-1-architecture-data-engineering/) | **Published / Ready** |
| **02** | Data Modeling | Planned |
| **03** | Climate Analytics | Planned |
| **04** | Agriculture Data Engineering | Planned |
| **05** | Integrated Climate & Agriculture Analytics | Planned |
| **06** | Data Science & Predictive Modeling | Planned |

## What is already implemented

- Medallion architecture with Bronze, Silver, and Gold layers;
- centralized `data/` structure organized by subject;
- immutable versioned datasets;
- `current/` publication pattern for stable consumption;
- auditing by layer and subject;
- SHA-256 verification;
- execution identifiers and lineage;
- replay from captured Bronze data;
- validation without publication;
- rollback during failed publication;
- concurrency lock;
- Windows scheduler entry points;
- automated tests for the architecture and transformation logic;
- initial ENSO and agricultural data pipelines.

## What comes next

The next milestones are intentionally incremental:

1. finalize source-specific extraction and transformation rules;
2. build the dimensional and semantic model;
3. publish the first climate analytics experience;
4. expand the agricultural analytical layer;
5. integrate climate, agriculture, and market context;
6. analyze ENSO-to-climate temporal lags;
7. build a historical analog engine;
8. introduce predictive agricultural models when spatial and agronomic coverage is sufficient.

## Interactive product

The interactive CLIMARISK experience will be added here once the analytical interface is ready. The final version is planned as a web-based experience so the visual design and interaction model are not constrained by a single BI tool.

**Interactive Dashboard:** _Coming in a future milestone._

---

### Latest article

[**Part 1 — Architecture & Data Engineering →**](/posts/climarisk-part-1-architecture-data-engineering/)
