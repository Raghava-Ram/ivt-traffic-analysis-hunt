# IVT Traffic Analysis - Hunt Digital Media

A comprehensive data analytics project to detect and analyze Invalid Traffic (IVT) in mobile ad datasets. This project analyzes ad request traffic for 6 mobile apps (3 valid, 3 invalid) for the period September 11-15, 2025, identifying fraud patterns and key differentiators between valid and invalid traffic.

## 📓 Notebook Structure

The Jupyter notebook (`ivt-traffic-analysis-hunt.ipynb`) contains **14 cells** organized as follows:

- **Cell 0-1**: Introduction, data loading, and parsing from Excel files
- **Cell 2**: Key metric definitions
- **Cell 3-4**: Daily IVT timeline visualization with threshold marking
- **Cell 5-6**: Key metric bar comparisons (IVT, IDFA-to-UA, Requests per IDFA)
- **Cell 7-8**: Scatter plot analysis of IVT vs IDFA-to-UA ratio
- **Cell 9-10**: Heatmap visualization of IVT transition period
- **Cell 11-12**: Final summary table with comprehensive findings
- **Cell 13**: Key insights and recommendations

## 📁 Project Contents

- **`ivt-traffic-analysis-hunt.ipynb`** - Interactive Jupyter notebook with complete analysis
- **`ivt-traffic-analysis-notebook.md`** - Markdown documentation of the analysis
- **`IVT-Analysis.docx`** - Comprehensive report document
- **`Data-Analytics-Assignment.xlsx`** - Source data file (required for running the notebook)

## 🔍 Key Metrics Analyzed

- **IVT (Invalid Traffic)**: Invalid traffic ratio indicator
- **IDFA-to-UA Ratio**: Unique devices per User-Agent string (primary fraud indicator)
- **IDFA-to-IP Ratio**: Unique devices per IP address
- **Requests per IDFA**: Request volume per device
- **Impressions**: Total delivered ads
- **User-Agent Diversity**: Unique UA strings

## 📊 Key Findings

### Critical Differentiator
- **IDFA-to-UA Ratio**: Valid apps show ~7,455 (15x higher), while invalid apps average ~495
- This metric is the **strongest fraud signal** for detecting UA spoofing

### IVT Levels
- **Valid Apps**: Average 2.23% (range: 0.39% - 5.84%)
- **Invalid Apps**: Average 72.23% (range: 55.87% - 85.31%)
- **32.3x higher** in invalid traffic

### Additional Fraud Signals
- Sudden IVT spikes mark detection points
- High UA diversity (invalid apps show 262-1,232 unique UAs)
- High IVT volatility (31x higher std dev in invalid apps)
- Zero impression delivery (all blocked before delivery)

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

### Running the Notebook
1. Ensure `Data-Analytics-Assignment.xlsx` is in the project directory
2. Open `ivt-traffic-analysis-hunt.ipynb` in Jupyter
3. Run all cells sequentially

### Data Format
The Excel file should contain 6 sheets:
- **Valid 1, Valid 2, Valid 3** - Legitimate traffic apps
- **Invalid 1, Invalid 2, Invalid 3** - Fraudulent traffic apps

Each sheet contains three sections:
- **Total Data**: Aggregate metrics for the entire period
- **Daily Data**: Daily breakdown by date
- **Hourly Data**: Hourly breakdown for detailed analysis

Key columns processed:
- `unique_idfas`, `unique_ips`, `unique_uas`
- `total_requests`, `requests_per_idfa`
- `impressions`, `impressions_per_idfa`
- `idfa_ip_ratio`, `idfa_ua_ratio`
- `IVT` (Invalid Traffic ratio)

### Notebook Details
The notebook includes:
- **Excel Data Parsing**: Custom function to extract Total, Daily, and Hourly data from 6 sheets
- **Data Processing**: Converts dates and numeric columns, handles missing values
- **Visualizations**: Timeline plots, bar charts, scatter plots, and heatmaps using matplotlib and seaborn
- **Key Threshold**: IVT=0.5 marking threshold for fraud detection
- **Transition Analysis**: Focus on Sept 11-13 period when invalid apps were detected

## 📈 Analysis Sections

### Cell 0-1: Data Loading & Parsing
```python
# Parses 6 Excel sheets (Valid 1-3, Invalid 1-3)
# Extracts: Total Data, Daily Data, Hourly Data
# Processes: Dates, numeric conversions, missing value handling
```

### Cell 2: Key Metric Definitions
- IVT (Invalid Traffic ratio)
- IDFA-to-UA ratio (Unique devices per User-Agent)
- IDFA-to-IP ratio
- Requests per IDFA
- Impressions per IDFA

### Cell 3-4: Daily IVT Comparison
- Timeline visualization for all 6 apps
- IVT=0.5 threshold line
- Color coding: Green (Valid), Red (Invalid)

### Cell 5-6: Metric Bar Comparisons
- Average Daily IVT by App (bar chart)
- IDFA-to-UA Ratio (log scale bar chart)
- Requests per IDFA (bar chart)

### Cell 7-8: Scatter Analysis
- IVT vs IDFA-to-UA Ratio (log scale)
- Clear separation between valid/invalid apps
- Markers: Circle (Valid), Triangle (Invalid)

### Cell 9-10: Heatmap Visualization
- Transition period: Sept 11-13, 2025
- Shows IVT levels when apps got marked as invalid
- Uses seaborn heatmap with RdYlGn_r colormap

### Cell 11-12: Summary Table
Displays comprehensive comparison table with 10 key metrics

### Cell 13: Insights & Recommendations
Key takeaways and actionable monitoring strategies

## 💡 Key Insights

From the analysis in Cell 13:

- **Sudden IVT spikes** mark IVT detection points
- **IDFA-to-UA ratio** is the strongest fraud signal—low ratios flag UA spoofing
- High UA diversity, zero impressions, and IVT volatility are supporting signals

## 📊 Recommendations

- Track IDFA-to-UA ratios and UA diversity hourly
- Monitor for IVT spikes and rising UA diversity
- Use impression delivery failure as a supporting red flag

## 📝 Outputs

The notebook generates visual outputs:
- Timeline plots showing IVT evolution
- Bar charts comparing key metrics
- Scatter plot showing IVT vs IDFA-to-UA relationship
- Heatmap of IVT transition period
- Summary table with comprehensive findings

**Note**: This notebook focuses on visualizations and insights. No CSV files are exported.

## 🎯 Use Cases

- Ad fraud detection in mobile advertising
- Traffic quality assessment
- Real-time monitoring system development
- Forensic analysis of suspicious traffic patterns

## 📄 License

See LICENSE file for details.
