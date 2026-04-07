# 🍔 BurgerMetrics Dataset

Ein umfangreicher Fast-Food-Analyse-Datensatz mit Sales-, Kunden-, Produkt- und Wetterdaten für Business Intelligence und Data Analytics Übungen.

## 📊 Dataset Übersicht

Dieser Datensatz enthält **326 MB** an strukturierten Daten eines fiktiven Fast-Food-Unternehmens und ist ideal für:
- Business Intelligence Analysen
- SQL-Übungen (Joins, Aggregationen, Window Functions)
- Data Warehouse Modellierung (Star Schema)
- Datenvisualisierung und Dashboard-Entwicklung
- Predictive Analytics und Machine Learning

## 📁 Enthaltene Dateien

### Dimensionstabellen (Star Schema)

| Datei | Größe | Beschreibung |
|-------|-------|--------------|
| `dim_branch.csv` | 1.2 KB | Filialen mit Standort, Größe und Eröffnungsdatum |
| `dim_customer.csv` | 1.2 MB | Kundenstammdaten (Demografie, Präferenzen) |
| `dim_date.csv` | 251 KB | Datumsdimension mit Kalenderinformationen |
| `dim_employee.csv` | 6.6 KB | Mitarbeiterdaten |
| `dim_payment_method.csv` | 179 B | Zahlungsmethoden |
| `dim_product.csv` | 4.5 KB | Produktkatalog mit Kategorien und Preisen |
| `dim_promotion.csv` | 441 B | Marketing-Aktionen und Rabatte |
| `dim_supplier.csv` | 515 B | Lieferanten-Informationen |
| `dim_time_slot.csv` | 233 B | Tageszeit-Segmente (Frühstück, Lunch, Dinner) |
| `dim_weather.csv` | 103 KB | Wetterdaten (Temperatur, Niederschlag) |

### Faktentabellen

| Datei | Größe | Beschreibung |
|-------|-------|--------------|
| `fact_orders.csv` | 51 MB | Bestellungen mit Zeitstempel, Filiale, Kunde, Summe |
| `fact_order_items.csv` | 83 MB | Einzelne Bestellpositionen (Produkte pro Order) |
| `obt_orders.csv` | 176 MB | **One Big Table** – denormalisierte Vollansicht aller Bestellungen |

## 🎯 Mögliche Analysen

- **Sales Performance:** Umsatz nach Filiale, Produkt, Zeitraum
- **Customer Behavior:** Kaufmuster, Frequency, Lifetime Value
- **Weather Impact:** Korrelation zwischen Wetter und Verkaufszahlen
- **Time Series:** Trends, Seasonality, Peak Hours
- **Product Analytics:** Bestseller, Warenkorb-Analysen, Cross-Selling
- **Employee Performance:** Verkaufsleistung pro Mitarbeiter

## 🚀 Quick Start

### 1. Repository klonen
```bash
git clone https://github.com/swrobuts/burger.git
cd burger
```

### 2. Git LFS installieren (für große Dateien)
```bash
# macOS
brew install git-lfs
git lfs install

# Dateien herunterladen
git lfs pull
```

### 3. Daten laden (Beispiel mit Python/Pandas)
```python
import pandas as pd

# Dimensionstabellen
products = pd.read_csv('dim_product.csv')
branches = pd.read_csv('dim_branch.csv')
customers = pd.read_csv('dim_customer.csv')

# Faktentabellen
orders = pd.read_csv('fact_orders.csv')
order_items = pd.read_csv('fact_order_items.csv')

# One Big Table (OBT) für schnelle Ad-hoc Analysen
obt = pd.read_csv('obt_orders.csv')
```

### 4. SQL-Analyse (DuckDB)
```bash
# DuckDB installieren
brew install duckdb

# Direkt SQL auf CSV ausführen
duckdb -c "SELECT * FROM 'fact_orders.csv' LIMIT 10"
```

## 📈 Schema Diagramm

```
┌─────────────────┐
│  dim_customer   │
└────────┬────────┘
         │
         ▼
┌─────────────────┐       ┌─────────────────┐
│  fact_orders    │◄─────►│  dim_branch     │
└────────┬────────┘       └─────────────────┘
         │
         │  1:N          ┌─────────────────┐
         ├──────────────►│ fact_order_items│
         │               └────────┬────────┘
         │                        │
         ▼                        ▼
┌─────────────────┐       ┌─────────────────┐
│   dim_date      │       │  dim_product    │
└─────────────────┘       └─────────────────┘
```

## 🛠️ Tech Stack Kompatibilität

- **Python:** Pandas, Polars, DuckDB
- **SQL:** PostgreSQL, MySQL, SQLite, BigQuery
- **BI-Tools:** Tableau, Power BI, Looker, Metabase
- **Visualisierung:** Plotly, Matplotlib, Seaborn, D3.js
- **Cloud:** AWS S3, Google Cloud Storage, Azure Blob

## 📚 Lernziele (für Studenten)

1. **Data Warehousing:** Star Schema Design verstehen
2. **SQL:** Komplexe Joins, Aggregationen, Subqueries
3. **ETL:** Daten laden, transformieren, validieren
4. **Analytics:** KPIs definieren und berechnen
5. **Visualisierung:** Dashboards und Reports erstellen

## 📝 Lizenz

Dieses Dataset ist für **Bildungszwecke** frei verfügbar.

## 🏫 Verwendung

Erstellt für die **THWS Business School** im Rahmen der Veranstaltung **Business Intelligence & Data Analytics** (Sommersemester 2026).

---

**Erstellt mit:** Python, Faker, NumPy  
**Dozent:** Prof. Dr. Robert Butscher  
**Hochschule:** Technische Hochschule Würzburg-Schweinfurt
