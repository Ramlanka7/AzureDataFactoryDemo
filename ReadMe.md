
---

## 🧱 Database Structure

### **Staging**
| Table | Purpose |
|--------|----------|
| `[Staging].[W_Sales_2010_2024]` | Raw loaded data from CSV |

### **Dimension**
| Table | Description |
|--------|-------------|
| `DimDate` | Calendar reference |
| `DimModel` | Car model details |
| `DimPowertrain` | Fuel type, engine, transmission |
| `DimGeo` | Region & Country |
| `FactSales` | Aggregated sales data |

---

## 💾 Stored Procedure: `etl.usp_Load_From_Staging`
- Reads data from staging.
- Cleans and aggregates data into a temp table.
- Populates all dimension tables with `MERGE`.
- Inserts or updates sales facts.
- Validates row counts by year.

### Key benefits:
- Idempotent (safe to run repeatedly).
- Uses set-based SQL (efficient).
- Fully automated from ADF pipeline.

---

## 🔄 Deployment & Git Integration

### **GitHub Integration**
This Data Factory is linked to GitHub for version control.

| Item | Description |
|-------|-------------|
| **Repository** | `github.com/<your-org>/BmwSalesDataFactory` |
| **Collaboration branch** | `main` |
| **Publish branch** | `adf_publish` |
| **Root folder** | `/adf` |

### **Typical Dev Workflow**
1. Edit pipeline in ADF Studio.
2. **Commit** → saves changes to GitHub.
3. **Publish** → generates ARM templates in `adf_publish` for deployment.

---

## ⚡ Technologies Used
- **Azure Data Factory**
- **Azure Blob Storage**
- **Azure SQL Database / SQL Server**
- **Self-hosted Integration Runtime**
- **GitHub Source Control**
- **T-SQL (ELT transformations)**

---

## 🧠 Lessons Learned
- Copy Activity is ideal for ingestion (simple, fast, low-cost).
- Transformations are best handled in SQL (via stored procedures) for complex business rules.
- GitHub integration provides versioning and CI/CD capability.
- Using Self-hosted IR allows secure access to on-prem SQL instances.

---

## ✅ Next Steps
- Implement **CI/CD deployment** from `adf_publish` branch to Test/Prod Data Factories.
- Add **data quality checks** or **email alerts** for pipeline runs.
- Parameterize pipeline for dynamic file names or incremental loads.

---

## 👨‍💻 Author
**Ram**  
Software Engineer (.NET, C#, Azure)  
Data Engineering & Cloud Enthusiast 🚀

---
