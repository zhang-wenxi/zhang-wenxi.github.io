---
layout: posts
title: "Data Sources That Matter in Power BI"
author_profile: false
date:   2026-05-24 00:00:00 +0800
excerpt: "Multi-system data dynamics and the prominent sources powering modern analytics."
categories: [writing]
header:
  overlay_image: "https://media.istockphoto.com/id/1194112917/photo/concept-of-file-sharing.jpg?s=2048x2048&w=is&k=20&c=jqJk1tRdzOf5eAKyhAfcYsqEpKMQCdiiYk0uOIHcrqQ="
  overlay_color: "transparent"
  teaser: "https://media.istockphoto.com/id/1194112917/photo/concept-of-file-sharing.jpg?s=2048x2048&w=is&k=20&c=jqJk1tRdzOf5eAKyhAfcYsqEpKMQCdiiYk0uOIHcrqQ="
  caption: "Photo credit: [iStock: fatido](https://www.istockphoto.com/portfolio/fatido?mediatype=photography)"
tags: ["Power BI", "Data Engineering", "Microsoft Fabric"]
tagline: "Data Engineering"
highlight_home: true
---

Today, data does not come from one place. Orders sit in SAP. Customer records live in Salesforce. Finance runs on a separate SQL warehouse. The business still wants one dashboard. Complex questions require pulling across multiple systems at once. Power BI's Get Data is where this begins.

The connector you pick is not just a technical setting. It determines data latency, query performance, available features, and governance. The right way to think about it is this: what is the source, what path does the data take, and what does the report actually require. That framing drives every good connector decision.

## Microsoft Fabric: The Modern Data Stack

![Microsoft Fabric Get Data sources](/assets/images/articles/powerbi/image2.png)

Microsoft Fabric unifies what was previously a collection of separate Azure services into a single capacity licence with a shared storage layer called [OneLake](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview). This changes how data platforms are built in Microsoft environments.

Within Fabric, Dataflows Gen 2 is the transformation layer. It ingests from source systems, applies Power Query transformations, and lands results directly into Fabric data stores. No pipeline code required. Lakehouses store data in open Delta format on OneLake. They serve as the central landing zone that multiple reports and semantic models can share. Warehouses provide a SQL endpoint for structured analytical workloads. KQL Databases handle real-time event streams.

In a mature Fabric setup, Power BI does not connect to source systems directly at report time. It connects to governed Lakehouse or Warehouse tables that Dataflows Gen 2 has already prepared. The [Fabric well-architected guidance](https://learn.microsoft.com/en-us/fabric/well-architected/) is explicit on this point. The Get Data connector is the last step, not the first.

## Databases: The Relational Workhorses

![Database Get Data sources](/assets/images/articles/powerbi/image3.png)

SQL Server, PostgreSQL, MySQL, Oracle, IBM Db2, and Amazon Redshift cover the most widely deployed data sources in enterprise environments. These are well-understood sources with predictable query behaviour. They support both Import and DirectQuery connection modes. For many organisations that have not yet moved to cloud-native architecture, these remain the primary layer feeding Power BI reports.

SAP HANA deserves specific mention. In SAP environments, ABAP developers write [CDS views](https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/ee6ff9b281d8448f96b4fe6c89f2bdc8/4ed1f2e06e391014adc9fffe4e204223.html), Core Data Services, directly on the HANA layer. A well-built CDS view handles joins, client filters, currency conversion, and authorisation checks. It presents a clean, business-ready data model without exposing raw SAP tables. Power BI connects to SAP HANA using DirectQuery, reading the CDS view live at query time. No import copy is maintained. The business logic stays in the SAP layer, maintained and versioned by the SAP team.

Pure DirectQuery on SAP HANA has [known limits](https://learn.microsoft.com/en-us/power-bi/connect-data/desktop-directquery-about#limitations-and-considerations). Cross-source joins are not supported unless Composite Mode is used. Some time intelligence DAX functions do not push down to the HANA engine. High-cardinality columns can degrade query performance. The practical solution is [Composite Mode](https://learn.microsoft.com/en-us/power-bi/transform-model/desktop-composite-models): import small reference and dimension tables, keep large fact tables on DirectQuery against HANA. This preserves data freshness where it matters while maintaining report performance.

## Azure: Cloud-Native Sources

![Azure Get Data sources](/assets/images/articles/powerbi/image1.png)

Azure SQL Database and Azure Synapse Analytics SQL are the primary cloud relational sources. Synapse handles large-scale analytical workloads. Azure Data Lake Storage Gen2 connects to raw data zones. Azure Blob Storage covers unstructured file storage. Azure Cosmos DB supports NoSQL document workloads. Azure Data Explorer serves time-series and log analytics scenarios.

In hybrid environments where some workloads remain on-premise and others sit in Azure, these connectors bridge the two. Power BI developers are often the end consumers of Azure infrastructure that data engineering teams have already built. Knowing what sits behind a connector, and what it means for performance and data freshness, is what allows a practitioner to participate in architecture conversations meaningfully.

## The DirectQuery Effect on Page Refresh

![Power BI Page Refresh settings](/assets/images/articles/powerbi/image4.png)

Every connector in Power BI delivers data through one of two modes. This is not a minor detail. It determines which features are available and how the report behaves in production.

Import mode copies a snapshot of source data into Power BI's in-memory VertiPaq engine. Visuals render against this local copy. The data is only as current as the last [scheduled refresh](https://learn.microsoft.com/en-us/power-bi/connect-data/refresh-scheduled-refresh). Scheduled refresh is an Import mode concept. It runs on a defined interval in the Power BI Service and updates the snapshot.

DirectQuery sends a live query to the source system every time a visual renders or a filter is applied. There is no data copy. The data is always current. Scheduled refresh does not exist in DirectQuery because there is no snapshot to update. What you manage instead is query performance, caching strategy, and query reduction settings.

The [automatic page refresh](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-automatic-page-refresh) feature visible in the Format Page panel follows this same rule. It only appears when the report uses DirectQuery. It allows the report to re-query the source on a set interval, independent of the manual refresh button. For Import mode reports, the option is simply not present. This is not a gap. It is the expected consequence of the connection mode chosen at design time.

For SAP HANA via CDS views, DirectQuery with Composite Mode is typically the right architecture. The HANA engine handles live queries efficiently and the business requires current data. For large historical datasets in a relational database or Fabric Warehouse, Import mode with a well-scheduled refresh delivers better report performance and broader feature support. The decision is made at design time. Not after the report is built.
