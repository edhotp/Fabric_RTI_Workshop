# Fabric Real-Time Intelligence (RTI) Workshop

A hands-on, end-to-end tutorial series for **Real-Time Intelligence in Microsoft Fabric**. Learn how to extract insights and visualize streaming data in motion through event-driven scenarios, streaming data ingestion, and log analysis.

## Overview

Real-Time Intelligence (RTI) is a powerful capability in Microsoft Fabric that enables organizations to act on data in motion. This workshop walks you through a complete real-time analytics pipeline — from ingesting live bicycle rental data, to transforming and querying it, to building interactive dashboards and maps with anomaly detection.

By the end of this workshop, you will have built a fully functional real-time analytics solution using Microsoft Fabric's core RTI components: **Real-Time Hub**, **Eventstream**, **Eventhouse (KQL Database)**, **Real-Time Dashboard**, and **Activator Alerts**.

## Scenario

The sample dataset used throughout this tutorial is a set of **bicycle rental data** from London, including bike IDs, docking station locations (latitude/longitude), timestamps, and availability metrics. You will ingest this data in real time and progressively build layers of analytics on top of it.

## Tutorial Series

| # | Tutorial | Description |
|---|---------|-------------|
| 0 | [Introduction](tutorial-introduction.md) | Overview of the tutorial series, learning objectives, and prerequisites. |
| 1 | [Set Up Resources](tutorial-1-resources.md) | Create an Eventhouse and its child KQL database to store streaming data. |
| 2 | [Get Real-Time Events](tutorial-2-get-real-time-events.md) | Browse the Real-Time Hub, create an eventstream with sample bicycle data, add timestamp transformations, and publish to a KQL database destination. |
| 3 | [Set an Alert](tutorial-3-set-alert.md) | Configure an Activator alert on the eventstream to send Teams notifications when bike availability drops below a threshold. |
| 4 | [Transform Data in KQL Database](tutorial-4-transform-kql-database.md) | Build a Bronze/Silver/Gold medallion architecture using stored functions and update policies to automatically transform raw ingested data. |
| 5 | [Query Streaming Data](tutorial-5-query-data.md) | Write KQL queries, create time charts and materialized views, query with T-SQL, convert SQL to KQL, and generate queries using Copilot. |
| 6 | [Create a Real-Time Dashboard](tutorial-6-create-dashboard.md) | Build an interactive Real-Time Dashboard with multiple visualization tiles, set alerts on dashboard queries, and share with your team. |
| 7 | [Detect Anomalies](tutorial-7-create-anomaly-detection.md) | Enable the anomaly detection feature on Eventhouse tables to automatically identify unusual patterns in bike dock availability. |
| 8 | [Create a Geospatial Map](tutorial-8-create-map.md) | Visualize bike station locations on an interactive map with bubble markers and GeoJSON overlays (borough boundaries and road data). |
| 9 | [Clean Up Resources](tutorial-9-clean-up-resources.md) | Delete all resources created during the workshop by removing the workspace. |

## What You'll Learn

- Set up an **Eventhouse** and KQL database in Microsoft Fabric
- Ingest real-time streaming data via the **Real-Time Hub** and **Eventstream**
- Transform raw data using **update policies** (medallion architecture)
- Write analytical queries in **KQL** and **T-SQL**
- Use **Copilot** to generate KQL queries from natural language
- Build interactive **Real-Time Dashboards** with multiple visualizations
- Configure **Activator alerts** for real-time monitoring and notifications
- Detect data **anomalies** automatically on streaming tables
- Create **geospatial map visualizations** with latitude/longitude data

## Prerequisites

- A [Microsoft Fabric workspace](https://learn.microsoft.com/fabric/fundamentals/create-workspaces) with a Fabric-enabled capacity
- Tenant admin must enable the **Maps** and **Anomaly Detector** preview settings in the admin portal

## Repository Structure

```
├── tutorial-introduction.md          # Series introduction & prerequisites
├── tutorial-1-resources.md           # Part 1: Set up Eventhouse
├── tutorial-2-get-real-time-events.md # Part 2: Ingest real-time data
├── tutorial-3-set-alert.md           # Part 3: Configure alerts
├── tutorial-4-transform-kql-database.md # Part 4: Data transformation
├── tutorial-5-query-data.md          # Part 5: KQL & T-SQL queries
├── tutorial-6-create-dashboard.md    # Part 6: Real-Time Dashboard
├── tutorial-7-create-anomaly-detection.md # Part 7: Anomaly detection
├── tutorial-8-create-map.md          # Part 8: Geospatial maps
├── tutorial-9-clean-up-resources.md  # Part 9: Clean up
└── media/tutorial/                   # Screenshots and images
```

## Getting Started

Start with the [Introduction](tutorial-introduction.md) to understand the scenario, then proceed sequentially through each tutorial part. Each section builds on the previous one.

## License

This workshop content is based on official [Microsoft Fabric documentation](https://learn.microsoft.com/fabric/real-time-intelligence/).
