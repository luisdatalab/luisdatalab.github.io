---
title: "Why I Built CLIMARISK AI"
description: "Why I chose climate data to build an end-to-end Analytics Engineering portfolio project with Microsoft Fabric, Power BI and a portable web experience."
date: 2026-09-29 10:30:00 -0300
categories: [Portfolio, Analytics Engineering]
tags: [microsoft-fabric, power-bi, analytics-engineering, data-engineering, climate-data, noaa]
author: Luis Correia
pin: false
image:
  path: /assets/img/posts/climarisk-ai/why-i-built-climarisk-ai.png
  alt: "CLIMARISK AI case study showing the path from NOAA RONI data to an analytical product"
---

I had one requirement for my next portfolio project: it could not end as just another dashboard.

I wanted to build something that would let me work through the full analytical cycle — from ingesting public data to defining business rules, validating the results and designing an experience that someone could understand without needing a technical explanation first.

That is how **CLIMARISK AI** started.

![CLIMARISK AI case study: from NOAA RONI data to a decision-ready analytical product](/assets/img/posts/climarisk-ai/why-i-built-climarisk-ai.png)
_The project follows the data from its public source to the analytical experience._

## Why climate data?

El Niño and La Niña affect discussions about agriculture, water availability, energy planning and supply chains. They are global phenomena, but the data used to monitor them is often presented in formats that are easier for specialists to interpret than for a broader audience to explore.

That made the subject a good fit for what I wanted to practice.

The technical challenge was not simply to display a historical line. It was to transform official observations into a structured analytical product while keeping the interpretation transparent.

For the first version, I chose the **Relative Oceanic Niño Index (RONI)** published by NOAA's Climate Prediction Center. The dataset provides a long historical series of overlapping three-month seasons, which creates useful questions for both data engineering and analytics:

- How should each seasonal observation be represented over time?
- How can warm, cold and neutral signals be classified consistently?
- When does a signal become a qualified episode?
- How can the result remain traceable to the original source?
- How should these rules be communicated visually?

## What I decided to build

The current scope covers **919 seasonal observations**, from July 1950 to July 2026, and identifies **44 qualified historical episodes** using an explicit persistence rule.

The solution was designed in layers:

1. Public NOAA data as the source.
2. Python notebooks for ingestion, transformation and validation.
3. Bronze, Silver and Gold layers in Microsoft Fabric.
4. An analytics-ready fact table with traceability fields.
5. A Power BI semantic model with reusable DAX measures.
6. Power BI and HTML experiences built from the same analytical dataset.

![CLIMARISK AI architecture preview showing NOAA, Python, Gold dataset, Power BI and HTML](/assets/img/posts/climarisk-ai/climarisk-ai-architecture-preview.png)
_One dataset supports two analytical experiences: Power BI for the semantic layer and HTML for a portable portfolio experience._

## A rule that changed the project

One of the most important decisions was separating a **signal** from a **qualified episode**.

A RONI value at or above `+0.5 °C` indicates a warm signal, while a value at or below `−0.5 °C` indicates a cold signal. But crossing a threshold once is not enough to qualify an episode in this project. The condition must persist for at least five consecutive overlapping seasons.

This distinction affected the pipeline, the data model, the measures and the interface. It also became a good example of something I value in Analytics Engineering: a metric is only useful when its definition is visible, consistent and testable.

## What I want this project to demonstrate

CLIMARISK AI is not an official NOAA forecasting product, and it does not attempt to predict regional impacts. Its current purpose is narrower and deliberate: monitor RONI observations, explore historical behavior and make the episode-classification logic clear.

As a portfolio project, it is also a way to connect several parts of my work that are sometimes presented separately:

- data ingestion and transformation;
- dimensional and semantic modeling;
- data-quality controls;
- reusable analytical measures;
- Power BI development;
- UX and information design;
- technical communication.

This is the first post in a series about the project. In the next one, I will show how the architecture was organized from the NOAA source through the Medallion layers and into the analytical experiences.

The interactive dashboard will be published later in the series, after I have shared the data structure and the main rules behind the numbers.

---

**Data source:** NOAA Climate Prediction Center — Relative Oceanic Niño Index (RONI).  
**Project status:** Portfolio case study in active development.  
**Author:** Luis Correia

