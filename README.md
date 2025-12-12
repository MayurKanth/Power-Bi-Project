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
Total Orders = CALCULATE(COUNTROWS(DISTINCT(ecommerce_orders_100k_with_state_and_products[Order_ID])))

Total Qty = SUM(ecommerce_orders_100k_with_state_and_products[Item_Quantity])

Value of the shipment = SUM(ecommerce_orders_100k_with_state_and_products[Selling_Price])

AOV (Average Order Value ) = DIVIDE([Value of the shipment],[Total Orders])

Qty/Order = DIVIDE([Total Qty],[Total Orders])


## Key Insights 

Total Orders: 1,999

Total Qty: 5,071

Total Shipment Value: ₹5.2M

Top courier by volume & value: Ekart (~40%)

Top state by orders: Maharashtra (473 orders)

Top selling products: Toothpaste, Bucket, Dinner Plate Set, Hand Wash, Mop

<img width="2135" height="1246" alt="image" src="https://github.com/user-attachments/assets/311156ce-5614-4632-81c6-78aa20b1d890" />




