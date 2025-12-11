# Dispatch & Shipment Analysis — Power BI Dashboard

**Project:** Dispatch & Shipment Analysis  
**Author:** Mayur Kanth  
**Last Updated:** 2025-12-04

## 🎯 Objective
Provide an interactive dashboard that summarizes dispatch history and logistics performance across delivery partners, products and regions to help stakeholders optimize courier allocation, inventory priorities and regional fulfillment planning.

## 📂 Repository Structure
- `pbix/` - Power BI `.pbix` file (if included)
- `data/` - sample, anonymized dataset used for the dashboard
- `docs/` - screenshots and design notes (data model, DAX)
- `README.md` - project overview and instructions

## Dataset
A cleaned and anonymized sample dataset is included in `data/sample_dispatch_data.csv`. Key columns:
- `OrderID`, `OrderDate`, `Delivery_Partner`, `ShipmentValue`, `Quantity`, `ProductName`, `Shipping_City`, `Shipping_State`

> **Security note:** This repository contains only anonymized sample data. Do NOT commit PII or production DB dumps.

## Data Modeling & Transformations
- Source transformed using Power Query (remove nulls, standardize partner names, convert data types).
- Star schema implemented: Fact = `DispatchData`; Dimensions = `Product`, `Location`, `DeliveryPartner`.

## Key DAX Measures (examples)
DAX
Total Orders = COUNTROWS('DispatchData')

Total Qty = SUM('DispatchData'[Quantity])

Total Shipment Value = SUM('DispatchData'[ShipmentValue])

AOV = DIVIDE([Total Shipment Value],[Total Orders])

Qty per Order = DIVIDE([Total Qty],[Total Orders])

% Share (Shipments) = DIVIDE([Total Orders], CALCULATE([Total Orders], ALL('DispatchData'[Delivery_Partner])))

Value % Share = DIVIDE([Total Shipment Value], CALCULATE([Total Shipment Value], ALL('DispatchData'[Delivery_Partner])))

## Key Insights 

Total Orders: 1,999

Total Qty: 5,071

Total Shipment Value: ₹5.2M

Top courier by volume & value: Ekart (~40%)

Top state: Maharashtra (473 orders)

Top products: Toothpaste, Bucket, Dinner Plate Set, Hand Wash, Mop



