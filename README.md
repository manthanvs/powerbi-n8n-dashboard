# 🏍️ Honda Two-Wheeler Sales Pipeline & Dashboard

Welcome to the **Honda Two-Wheeler Analytics Project**! This repository demonstrates an end-to-end data pipeline: from capturing unstructured sales data via email, automating ingestion into a PostgreSQL database, to visualizing the key KPI metrics in an interactive Power BI dashboard.

<div align="center">
  <img src="images/images/honda-png-22028.png" width="300" alt="Honda Logo"/>
</div>

---

## 📊 Project Overview

This architecture is built around three core components:

### 1. Data Ingestion & Automation (n8n Workflow)
We utilize **n8n** to automate the tedious data entry process. The `My-n8n-workflow.json` acts as the backbone:
- **IMAP Email Trigger**: Listens for incoming emails containing Honda Sales Datasets.
- **Data Validation**: Checks logic conditions (e.g., verifying if the attachment is a valid `.csv`).
- **Data Transformation**: Extracts CSV fields and rigorously formats dynamic dates into a strict database-friendly structure.
- **Database Upsert**: Loads pristine data directly into a **PostgreSQL** database table (`sales_data`).
- **Notification System**: Triggers an automated Gmail alert to administrators informing them that new regional data has arrived.

### 2. Honda Sales Dataset
The repository includes high-fidelity data records inside `Honda All Dataset.csv` (1,500+ rows) and city-specific breakdowns (Mumbai, Bangalore, NCR, etc.). The features include:
- **Vehicles:** `Bike_Model` (e.g. Activa 6G, Hornet 2.0, CB350, SP 125, Unicorn)
- **Logistics:** `Dealership & Region` (City, State, Dealer Name)
- **Financials:** `On-Road Price`, `Discount`, `Insurance`, `Accessories`, `Net Sales Amount`, `Gross Profit`
- **Customers:** `Age`, `Gender`, `Delivery Days`, `Payment Mode`, and `Ratings`.

### 3. Business Intelligence Dashboard (Power BI)
The `PowerBIDashboard.pbix` file connects to the ingested data and transforms raw rows into actionable business intelligence. It visualizes:
- **Sales & Revenue**: Best performing two-wheeler segments (Scooter vs Commuter vs Sports vs Premium).
- **Regional Analysis**: Geographical heatmaps driving sales volume.
- **Profit Margins**: Deep-dives into exact net sales versus base costs.

---

## 🚀 Getting Started

### Setting up the Automation (n8n)
1. Ensure your [n8n](https://n8n.io/) instance is running.
2. In your n8n workspace, go to the top right and select **Import from File**. Upload `My-n8n-workflow.json`.
3. Add your unique credentials into the configured nodes (`IMAP Account`, `PostgreSQL Account`, and `Gmail OAuth2`).
4. Activate the workflow!

### Setting up Power BI
1. Download Microsoft Power BI Desktop.
2. Open `PowerBIDashboard.pbix`.
3. If necessary, navigate to **Transform Data** > **Data Source Settings** to point it to your identical Postgres configuration or to the local CSV files included right here.

---

## 📂 Repository Structure

```text
├── Honda All Dataset.csv        # Aggregated Master Database
├── Honda_*.csv                  # City-wise split raw datasets (Ahmedabad, Pune, etc.)
├── PowerBIDashboard.pbix        # Interactive Analytical BI Dashboard
├── My-n8n-workflow.json         # Automated Pipeline JSON blueprint
├── images/                      # Media assets & Icons for Dashboard
└── README.md                    # Project Documentation
```

*Developed by Manthan Vijay Sankpal*
