
# 🎧 Spotify Advanced Analytics Command Center
An end-to-end ETL pipeline that transforms raw Spotify API data into an interactive Power BI dashboard. It uses Azure Databricks (Python/PySpark/SQL) to clean and structure data into a professional Star Schema, featuring custom metrics and AI-driven insights to analyze listening habits

## Tech Stack
- **Cloud**: Azure Databricks
- **Processing**: Python, PySpark, SparkSQL
- **API**: Spotify API
- **Storage**: Delta Lake (Bronze/Silver/Gold). All 6 tables are stored as ACID compliant Delta tables in the default Databricks SQL database, ensuring data integrity and high-speed retrieval for Power BI.
- **BI & Modeling**: Power BI Desktop (Star Schema / DAX)

## System Architecture & Pipeline
This project follows a modern data stack pipeline, moving from raw ingestion to a structured Semantic Layer.
```mermaid
graph TD
    A[Spotify API / Raw JSON] -->|Python Extraction| B(Bronze: Raw Ingestion)
    B -->|PySpark / SparkSQL| C(Silver: Cleaned & Normalized)
    C -->|Gold: Star Schema| D{Delta Lake Storage}
    D -->|Import Mode| E[Power BI Semantic Model]
    E -->|Advanced DAX| F[Loyalty Score & KPI Cards]
    E -->|AI Engine| G[Decomposition Tree]
    G -->|User Interaction| H[Floating Neon Dashboard]
  ```
  
## 🔄 The Medallion Data Pipeline
1. _**Bronze (Raw)**_: Extracted raw JSON responses from the Spotify API for `Playlist#1` into initial staging tables.
2. _**Silver (Filtered)**_: Cleaned, deduplicated, and normalized track data using PySpark and SparkSQL to handle nested structures.
3. _**Gold (Curated Star Schema)**_: Engineered 6 final Delta Tables optimized for ACID compliance and performance.
4. _**Semantic Modeling**_: Integrated the Gold Layer into Power BI and engineered a Star Schema, managing all tracks with complex active/inactive relationships.

## Technical Highlights
- **Data Engineering**: Engineered a robust ETL pipeline in Azure Databricks using Python and Spark to automate data cleaning.
- **Behavioral DAX**: Authored a custom "Loyalty Score" metric using advanced logic to quantify user dedication to specific artists.
- **AI-Driven Insights**: Implemented an interactive Decomposition Tree for root-cause analysis from Artist popularity down to individual Track Duration.
- **UI/UX Design**: Built a sleek, "Floating Neon" Dark-Mode interface optimized for high-density reporting without visual noise.
- **Search Integration**: Enabled a search bar within the Artist Slicer for instant navigation through all the tracks in the playlist#1

## Data Model (ERD)
High-performance Star Schema with 6 Gold Layer tables:
Central Fact: _fact_track_breakdown_ (streams, durations, popularity)
Dimensions: 
➜ _dim_artist_stats_
➜ _dim_album_stats_  
➜ _dim_date_dimension_
➜ _dim_timeline_trends_
➜ _dim_top_tier_tracks_
Dynamic cross-filtering: AI Tree selection updates "Total Tracks" KPI (147 → 1)

## Star Schema Data Model

![Star Schema Model](analytics-visuals/star-schema-model.png)

*Power BI semantic model with fact_track_breakdown and 6 Delta tables relationships.*


## Dashboard Features
| Feature               | Description                                                           |
| --------------------- | --------------------------------------------------------------------- |
| Loyalty Score         | A glowing hero metric displaying user engagement.                     |
| Decomposition Tree    | AI drill-down: Artist → Album → Track → Duration.                     |
| Listening Trends      | Line chart: Peak periods by month/year                                |
| Dual Artist Metrics   | Listening Minutes vs Track Count comparison (Engagement vs Volume)    |
| Weekly Activity Pulse | Bar chart: Most active days of week                                   |

## PowerBI Dashboard
![Dashboard Overview](analytics-visuals/dashboard-spotify-command-center.png)
![Spotify Command Center](analytics-visuals/dashboard-spotify-command-center.gif)

*Interactive "Floating Neon" dashboard with 8 synchronized visuals and filtering.*

---

_**Created with love for music and data 🎵**_
