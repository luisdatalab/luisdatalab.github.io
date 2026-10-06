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

## Current milestone: ENSO analytical layer

The second completed milestone turns NOAA RONI data into three analytical products:

```text
fact_enso_observation
dim_enso_episode
fact_enso_signal_run
```

The module separates signal, sequence, and qualified episode; distinguishes point-in-time qualification from retrospective episode membership; tracks recent-data revision status; and publishes its own Bronze, Silver, Gold, and audit artifacts without rewriting the agricultural pipeline.

The validated implementation reconstructed **919 historical observations**, **44 qualified episodes**, and **58 Warm/Cold signal runs**, while the complete automated suite reached **61 passing tests with no identified regressions**.

## Data sources

The project currently works with or is preparing integration for public sources such as:

- NOAA — ENSO and RONI;
- NASA POWER — agroclimatology;
- IBGE PAM — annual agricultural production;
- IBGE LSPA — monthly crop estimates;
- CONAB — crop progress and seasonal context;
- World Bank — international commodity prices.

## Project series

Each article represents a completed milestone rather than a retrospective summary written only after the final product is ready.

| Part | Topic | Status |
| --- | --- | --- |
| **01** | [Architecture & Data Engineering](/posts/climarisk-part-1-architecture-data-engineering/) | Published |
| **02** | [Engineering the ENSO Layer](/posts/climarisk-part-2-engineering-the-enso-layer/) | **Latest** |
| **03** | Data Modeling | Planned |
| **04** | Climate Analytics | Planned |
| **05** | Agriculture Data Engineering | Planned |
| **06** | Integrated Climate & Agriculture Analytics | Planned |
| **07** | Data Science & Predictive Modeling | Planned |

## What is already implemented

- Medallion architecture with Bronze, Silver, and Gold layers;
- centralized `data/` structure organized by subject;
- immutable versioned datasets and stable `current/` publication paths;
- auditing by layer, subject, and analytical dataset;
- SHA-256 verification, execution identifiers, and lineage;
- replay from captured Bronze data;
- validation without publication and rollback during failed publication;
- concurrency locks and observable Windows launchers;
- automated testing of transformation and orchestration rules;
- independent ENSO pipeline using NOAA RONI data;
- temporal modeling of ENSO signals, runs, and qualified episodes;
- point-in-time correctness for episode qualification;
- explicit separation between recent provisional observations and historical context.

## What comes next

The next milestone is **analytical and semantic modeling**: dimensions, relationships, measures, and a consumption model for the first climate dashboard.

After that, the roadmap continues with climate analytics, the agricultural module, integrated climate/agriculture analysis, ENSO-to-climate lag analysis, historical analogs, and predictive agricultural models when the data coverage is sufficient.

## Interactive product

The interactive CLIMARISK experience will be added here once the analytical interface is ready. The final version is planned as a web-based experience so the visual design and interaction model are not constrained by a single BI tool.

**Interactive Dashboard:** _Coming in a future milestone._

---

### Latest article

[**Part 2 — Engineering the ENSO Layer →**](/posts/climarisk-part-2-engineering-the-enso-layer/)
