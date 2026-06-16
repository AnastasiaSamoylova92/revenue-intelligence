# Synthetic Revenue Intelligence Dataset – Data Dictionary

## Datenmodell
Relationales Star-/Snowflake-Modell für Revenue Intelligence, Business Analytics, Forecasting, PVM, Executive Reporting und Machine Learning.

## Tabellen

### factSales
Grain: eine Transaktionszeile je Bestellung, Datum, Kunde, Produkt, Region und Sales Rep.

Spalten:
- sales_id
- order_id
- date_id
- date
- year_month
- customer_id
- product_id
- region_id
- sales_rep_id
- units
- asp_eur
- discount_pct
- revenue_eur
- revenue_local_currency
- currency
- unit_cost_eur
- gross_profit_eur
- gross_margin_pct
- is_outlier_order

Beschreibung:
- Enthält alle Umsatztransaktionen.
- Grundlage für Revenue-, Margin-, ASP- und PVM-Analysen.
- Enthält bewusst Missing Values und Ausreißer.

---

### dimCustomer

Beschreibung:
Kundenstammdaten mit Segmentierung, Churn-Risiko und Größenklassifizierung.

Spalten:
- customer_id
- customer_code
- customer_segment
- industry
- region_id
- customer_since
- customer_size_score
- base_churn_probability

Businesslogik:
- Enterprise-Kunden bestellen größere Mengen.
- SMB-Kunden churnen häufiger.
- Distributor-Kunden haben hohe Volumen und höhere Discounts.

---

### dimProduct

Beschreibung:
Produktstammdaten inklusive Lifecycle und Margenlogik.

Spalten:
- product_id
- sku
- product_family
- product_group
- product_name
- launch_year
- lifecycle_stage
- base_list_price_eur
- base_unit_cost_eur
- target_margin_pct
- product_growth_factor

Lifecycle Stages:
- New
- Growth
- Mature
- Decline

Businesslogik:
- Neue Produkte wachsen schneller.
- Legacy-Produkte verlieren Marktanteile.
- Unterschiedliche Produktgruppen besitzen unterschiedliche Margen.

---

### dimDate

Beschreibung:
Kalendertabelle von 2021-01-01 bis 2025-12-31.

Spalten:
- date
- date_id
- year
- quarter
- month
- month_name
- year_month
- day_of_week
- week_of_year
- is_month_end
- is_quarter_end

Nutzung:
- Zeitreihenanalysen
- Forecasting
- YoY / MoM Berechnungen
- Rolling Windows

---

### dimRegion

Beschreibung:
Regionen-, Länder- und Währungsinformationen.

Spalten:
- region_id
- country
- region
- currency
- fx_to_eur
- market_growth_factor
- margin_factor

Businesslogik:
- Regionen entwickeln sich unterschiedlich.
- Unterschiedliche Währungen simulieren FX-Effekte.
- Regionen besitzen unterschiedliche Profitabilität.
---

### dimSalesRep

Beschreibung:
Sales-Repräsentanten mit Region und Quota.

Spalten:
- sales_rep_id
- sales_rep_code
- region_id
- seniority
- annual_quota_eur

Seniority Levels:
- Junior
- Professional
- Senior
- Key Account

---

### factForecast

Beschreibung:
Forecast-Daten für Revenue- und Units-Planung.

Spalten:
- forecast_id
- year_month
- product_id
- region_id
- forecast_version
- forecast_units
- forecast_revenue_eur
- actual_units
- actual_revenue_eur

Forecast Versionen:
- Budget
- Rolling Forecast
- Latest Estimate

Businesslogik:
- Forecasts enthalten Bias und Forecast Error.
- Geeignet für Forecast Accuracy und Bias Analysen.

---

### factInventory

Beschreibung:
Bestands- und Lagerdaten.

Spalten:
- inventory_id
- year_month
- product_id
- region_id
- opening_stock_units
- production_units
- ending_stock_units
- stockout_flag
- inventory_value_eur

Businesslogik:
- Ermöglicht Inventory Turnover Analysen.
- Enthält simulierte Stockouts.

---

### factCosts

Beschreibung:
Historische Produktkosten je Monat.

Spalten:
- cost_id
- year_month
- product_id
- standard_unit_cost_eur
- actual_unit_cost_eur

Businesslogik:
- Kosten steigen über die Jahre leicht durch Inflation.
- Standard- und Istkosten unterscheiden sich.

---

### factCRMActivities

Beschreibung:
CRM- und Sales-Aktivitäten.

Spalten:
- activity_id
- date_id
- date
- customer_id
- sales_rep_id
- activity_type
- activity_minutes
- sentiment_score
- customer_health_score

Activity Types:
- Call
- Email
- Demo
- Visit
- Business Review
- Training

Businesslogik:
- Customer Health Scores korrelieren mit Sentiment.
- Geeignet für Churn-Modelle und Customer Analytics.

---

### factReturns

Beschreibung:
Retouren und Reklamationen.

Spalten:
- return_id
- sales_id
- date_id
- date
- customer_id
- product_id
- region_id
- return_units
- return_value_eur
- return_reason

Return Reasons:
- Defect
- Wrong Configuration
- Customer Cancellation
- Shipping Damage
- Other

---

### factPipeline

Beschreibung:
Sales Pipeline und Opportunity Funnel.

Spalten:
- opportunity_id
- created_date
- customer_id
- product_group
- sales_rep_id
- stage
- expected_value_eur
- win_probability
- expected_close_date
- created_date_id
- weighted_pipeline_eur

Stages:
- Lead
- Qualified
- Proposal
- Negotiation
- Closed Won
- Closed Lost

Businesslogik:
- Simuliert realistische Funnel Conversion.
- Weighted Pipeline = Expected Value × Win Probability.

---

# Zentrale Businesslogik

## Zeitliche Dynamiken
- Mehrjährige Zeitreihe 2021–2025
- Q4-Saisonpeak
- Sommerdip
- Inflationseffekte
- Wachstumsraten pro Region

## Produktdynamiken
- Neue Produkte wachsen langsam an
- Mature-Produkte stabilisieren sich
- Decline-Produkte verlieren Umsatz

## Kundendynamiken
- Enterprise stabiler
- SMB volatiler
- Unterschiedliche Churn-Risiken

## Finanzlogik
- ASP steigt leicht jährlich
- Kosten steigen über Zeit
- Margen unterscheiden sich je Produktgruppe

## Datenrealismus
- Missing Values
- Ausreißerorders
- Forecast Errors
- Währungsumrechnung
- Unterschiedliche Marktperformance