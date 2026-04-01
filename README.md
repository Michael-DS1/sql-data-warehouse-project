# sql-data-warehouse-project
Building a mordern data warehouse with SQL server, including ETL processes, data modellling and analytics

# Data Warehouse Project

## 📖 Overview

A brief description of the project — what business problem it solves, what data it handles, and what value it delivers.

> **Example:** This project implements a modern data warehouse using SQL Server to consolidate sales, inventory, and customer data from multiple source systems. It supports analytical reporting and business intelligence across the organization.

---

## 🏗️ Architecture

```
┌─────────────────┐     ┌──────────────┐     ┌─────────────────┐
│   Source Systems │────▶│  ETL Process │────▶│  Data Warehouse │
│  (CRM, ERP, etc) │     │  (SSIS / SQL)│     │  (SQL Server)   │
└─────────────────┘     └──────────────┘     └─────────────────┘
                                                       │
                                              ┌────────▼────────┐
                                              │  Analytics Layer│
                                              │ (Reports / BI)  │
                                              └─────────────────┘
```

**Layers:**
- **Bronze (Raw)** — Raw ingested data, unmodified from source systems
- **Silver (Cleansed)** — Cleaned, validated, and standardized data
- **Gold (Curated)** — Business-ready data models for analytics and reporting

---

## 🗂️ Repository Structure

```
sql-data-warehouse-project/
│
├── datasets/                   # Raw source data files (CSV, Excel, etc.)
│
├── docs/                       # Documentation and architecture diagrams
│   ├── architecture.drawio
│   ├── data_dictionary.md
│   └── naming_conventions.md
│
├── scripts/
│   ├── init_database.sql       # Database and schema setup
│   ├── bronze/                 # Raw layer DDL and load scripts
│   ├── silver/                 # Cleansing and transformation scripts
│   └── gold/                   # Analytical model scripts (facts & dims)
│
├── tests/                      # Data quality and validation scripts
│
├── .gitignore
└── README.md
```

---

## ⚙️ Tech Stack

| Component        | Technology          |
|-----------------|---------------------|
| Database         | SQL Server 20xx     |
| ETL              | SSIS / T-SQL        |
| Data Modelling   | Star Schema         |
| Version Control  | Git / GitHub        |
| Reporting        | Power BI / SSRS     |

---

## 🚀 Getting Started

### Prerequisites

- [ ] SQL Server (version XX or later) installed
- [ ] SQL Server Management Studio (SSMS)
- [ ] Git

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/sql-data-warehouse-project.git
   cd sql-data-warehouse-project
   ```

2. **Initialize the database**
   ```sql
   -- Run in SSMS
   scripts/init_database.sql
   ```

3. **Load Bronze layer**
   ```sql
   scripts/bronze/load_bronze.sql
   ```

4. **Run Silver transformations**
   ```sql
   scripts/silver/transform_silver.sql
   ```

5. **Build Gold models**
   ```sql
   scripts/gold/build_gold.sql
   ```

---

## 📊 Data Models

### Star Schema — [Subject Area, e.g., Sales]

```
              ┌──────────────┐
              │  Fact_Sales  │
              └──────┬───────┘
          ┌──────────┼──────────┐
          ▼          ▼          ▼
   ┌────────────┐ ┌────────┐ ┌──────────┐
   │ Dim_Customer│ │Dim_Date│ │Dim_Product│
   └────────────┘ └────────┘ └──────────┘
```

> See `/docs/data_dictionary.md` for full column definitions and business rules.

---

## 🔄 ETL Process

| Step    | Description                                  | Schedule     |
|---------|----------------------------------------------|--------------|
| Extract | Pull raw data from source systems            | Daily 02:00  |
| Load    | Stage raw data into Bronze layer             | Daily 02:30  |
| Transform | Cleanse and validate into Silver layer     | Daily 03:00  |
| Model   | Build fact/dimension tables in Gold layer    | Daily 04:00  |

---

## 🧪 Data Quality Checks

Quality validations are located in `/tests/`. Checks include:

- Null / missing value detection
- Referential integrity between facts and dimensions
- Duplicate record identification
- Row count reconciliation between source and target

---

## 📜 Naming Conventions

| Object       | Convention         | Example              |
|-------------|---------------------|----------------------|
| Tables       | `snake_case`       | `fact_sales`         |
| Columns      | `snake_case`       | `customer_id`        |
| Stored Procs | `sp_<layer>_<name>`| `sp_silver_cleanse`  |
| Views        | `vw_<name>`        | `vw_monthly_revenue` |

> Full conventions documented in `/docs/naming_conventions.md`.

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add: your feature description'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 👤 Author

**Your Name**
- GitHub: [@your-username](https://github.com/your-username)
- LinkedIn: [your-profile](https://linkedin.com/in/your-profile)

---

> ⭐ If you find this project useful, consider giving it a star on GitHub!
