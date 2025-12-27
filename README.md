
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
1. Bronze (Raw): Extracted raw JSON responses from the Spotify API for `Playlist#1` into initial staging tables.
2. Silver (Filtered): Cleaned, deduplicated, and normalized track data using PySpark and SparkSQL to handle nested structures.
3. Gold (Curated Star Schema): Engineered 6 final Delta Tables optimized for ACID compliance and performance.
4. Semantic Modeling: Integrated the Gold Layer into Power BI and engineered a Star Schema, managing all tracks with complex active/inactive relationships.

## Technical Highlights
- **Data Engineering**: Engineered a robust ETL pipeline in Azure Databricks using Python and Spark to automate data cleaning.
- **Behavioral DAX**: Authored a custom "Loyalty Score" metric using advanced logic to quantify user dedication to specific artists.
- **AI-Driven Insights**: Implemented an interactive Decomposition Tree for root-cause analysis from Artist popularity down to individual Track Duration.
- **UI/UX Design**: Built a sleek, "Floating Neon" Dark-Mode interface optimized for high-density reporting without visual noise.
- **Search Integration**: Enabled a search bar within the Artist Slicer for instant navigation through all the tracks in the playlist#1

## Data Model (ERD)
The backend architecture is a high-performance Star Schema consisting of 6 curated Gold Layer tables, engineered for granular drill-down and real-time responsiveness.
Central Fact Table:
  - _fact_track_breakdown_: The core engine containing individual stream counts, track durations, and popularity metrics.
Dimension Tables:
  - _dim_artist_stats_: Detailed artist-level metrics and metadata.
  - _dim_album_stats_: Album-level attributes for hierarchical analysis.
  - _dim_date_dimension_: Time-intelligence table for trend analysis across days, months, and years.
  - _dim_timeline_trends_: Specialized dimension for tracking historical listening behavior over time.
  - _dim_top_tier_tracks_: Filtered dimension identifying high-engagement tracks for focused reporting.
Dynamic Filtering:
  - The model supports seamless cross-filtering; for instance, selecting a specific node in the AI Decomposition Tree instantly updates the global "Total Tracks" KPI to reflect the current selection (e.g., from 147 down to 1).

## Dashboard Features
Loyalty Score Card: A glowing hero metric displaying user engagement.
Listening Trends: Line chart identifying peak listening periods by month/year.
Dual Top Artist Metrics: Comparative analysis of Top Artists by both Listening Minutes and Track Count.
Weekly Activity Pulse: Bar chart highlighting the most active days of the week.

_**Created with love for music and data 🎵**_
