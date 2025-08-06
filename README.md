# Daylily Data Science Portfolio

## Project Overview

This comprehensive data science project analyzes over 100,000 daylily varieties from the American Daylily Society database to uncover breeding patterns, hybridizer career trajectories, and network relationships that could revolutionize data-driven plant breeding strategies.

### Workflow
**Problem → Data → EDA → Network Analysis → Regional Analysis → Integration → Insights & Recommendations**

---

## The Problem

With 100 years of intensive hybridization resulting in over 102,000 registered daylily varieties, collectors and hybridizers face an overwhelming selection challenge. Current breeding strategies range from:

- **Award-focused**: Selecting only award-winning varieties as parents
- **Trait-specific**: Choosing varieties with specific desired characteristics  
- **Performance-based**: Intensive screening for growth habit, disease, and pest resistance
- **Opportunistic**: Crossing available "pretty flowers" hoping for the best

**The Gap**: No data-driven techniques exist beyond simple filtering, leaving significant potential for improving breeding outcomes through statistical analysis and network-based insights.

**The Solution**: This project provides the first comprehensive data-driven analysis of daylily breeding patterns, offering actionable insights for both novice and experienced hybridizers.

---

## Data Acquisition & Challenges

### Data Source
- **Primary**: American Daylily Society database (https://daylilies.org/)
- **Scale**: 101,718 unique varieties spanning 1763-2025
- **Completeness**: Varies by field (100% for core data, 1.07% for specialized traits)

### Technical Approach
Due to database access limitations, I developed a custom web scraping solution:
- **Methodology**: Iterative scraping using Python requests module
- **Ethics**: Nighttime execution (off-peak), 10 entries per request, proxy rotation
- **Scope**: 3-4 nights for text data, 3 nights for images (~4GB)
- **Output**: Clean, consistent dataset ready for analysis

---

## Exploratory Data Analysis

### Dataset Characteristics
- **Total Varieties**: 101,718 unique entries
- **Time Span**: 262 years (1763-2025)
- **Attributes**: 21 different characteristics tracked
- **Data Quality**: Comprehensive cleaning and validation implemented

### Key Statistical Insights

#### Physical Characteristics Distribution
| Trait            |   Mean | Median | Std Dev | Range  | Skewness |
|------------------|--------|--------|---------|--------|----------|
| **Bloom Size**   | 5.75"  | 6.00"  | 1.29"   | 1-14"  | 0.39     |
| **Scape Height** | 29.26" | 28.00" | 6.82"   | 2-73"  | 0.72     |
| **Branching**    | 3.51   | 3.00   | 1.06    | 1-9    | 0.83     |
| **Bud Count**    | 19.79  | 19.00  | 7.40    | 1-68   | 0.88     |

#### Critical Correlations
- **Branches ↔ Bud Count**: 0.61 (strongest positive correlation)
- **Insight**: More branches reliably predict higher bud counts

### Data Completeness Analysis
- **Complete Fields**: Name, Year, Hybridizer (100%)
- **Specialized Fields**: Sculpting (1.07%), Form (12.72%), Rebloom (45.33%)
- **Moderate Fields**: Image URLs (67.54%), Parentage (96.14%)

---

## Hybridizer Career Analysis

### Community Demographics & Trends

#### Historical Growth Patterns
- **Peak Growth**: 2000s with 1,100+ new hybridizers
- **Current Decline**: 600 hybridizer net loss in 2020s  
- **Peak Activity**: 485 active hybridizers (2011)
- **Trend**: Transition from widespread and growing hobby to specialized craft

#### Career Achievement Patterns
- **Elite Status**: Only 4.1% have introduced 100+ varieties
- **Top Performer**: Wild (1,837 varieties over 73 years)
- **Single-Year Record**: Krekler (395 introductions in 1987)
- **Median Career**: 1 year (50% are brief careers)

#### Modern vs Historical Efficiency
- **Early Career Boost**: Modern hybridizers show 22% higher initial productivity
- **Peak Performance**: 24% increase in maximum output compared to historical
- **Experience Correlation**: Peak performance typically achieved after 15-20 years

### Success Indicators
1. **Persistence**: Survival beyond first year is crucial
2. **Long-term Commitment**: 15+ years for peak performance
3. **Continuous Learning**: Modern techniques increase efficiency
4. **Quality Focus**: Fewer hybridizers but higher individual output

---

## Network Analysis & Breeding Relationships

### Network Construction
- **Technical Implementation**: Sophisticated matching algorithm
- **Data Processing**: Chunked processing
- **Relationship Extraction**: Parent-child breeding connections
- **Storage**: Both CSV and SQLite database formats

### Network Structure Insights

#### Centrality Measures Applied
- **PageRank**: Overall network influence
- **In/Out-Degree**: Parent/offspring connections  
- **Katz Centrality**: Extended network reach
- **Betweenness**: Bridge variety identification

#### Golden Age Discoveries (1950s-1960s)
The analysis identified a "Golden Age" of breeding with exceptional long-term influence:

| Variety         | Year | Total Descendants | Breeding Impact                          |
|-----------------|------|-------------------|------------------------------------------|
| **Frances Fay** | 1957 | 32,478            | Exceptional multi-generational influence |
| **Crestwood**   | 1961 | 30,914            | Sustained breeding success               |
| **Dorcas**      | 1958 | 30,505            | Long-term genetic contribution           |

#### Key Network Findings
- **Selective Breeding**: Low network density indicates strategic parent selection
- **Hierarchical Structure**: Clear breeding line hierarchies identified
- **Bridge Varieties**: Certain cultivars serve as crucial genetic connectors
- **Success Pattern**: High direct offspring ≠ long-term influence

---

## Regional Analysis

### Geographic Distribution
Analysis across 15 ADS regions covering US and Canadian territories:

#### Regional Organization
- **Region Coverage**: Complete US/Canada territorial mapping
- **Data Integration**: Hybridizer locations linked to breeding activity
- **Cross-border Handling**: US-Canada region management

#### Technical Implementation
- **Database Structure**: SQLite integration with location_data table
- **Data Validation**: Comprehensive state/province to region mapping
- **Error Handling**: Missing data management

---

## Master Database Integration

### Comprehensive Data Fusion
The project culminates in a master database combining:

#### Integrated Data Dimensions
1. **Basic Variety Information**: Names, years, physical characteristics
2. **Geographic Context**: Regional distribution and hybridizer locations  
3. **Network Metrics**: Breeding influence and relationship statistics
4. **Family Relationships**: Parent-child breeding connections
5. **Career Analytics**: Hybridizer performance and trends

#### Technical Excellence
- **Modular Integration**: Systematic data enrichment process
- **Quality Preservation**: LEFT JOINs maintain data integrity
- **Export Ready**: CSV format for accessibility
- **Relationship Mapping**: Comma-separated parent/child lists

---

## Key Insights & Discoveries

### 1. Breeding Strategy Optimization
- **Golden Age Genetics**: 1950s-1960s varieties show exceptional long-term influence
- **Modern Efficiency**: Contemporary hybridizers achieve 22-24% higher productivity
- **Network Power**: Understanding breeding relationships reveals hidden genetic value

### 2. Career Development Patterns  
- **Persistence Premium**: First-year survival predicts long-term success
- **Experience Advantage**: Peak performance requires 15+ year commitment
- **Quality Evolution**: Industry shifting toward more specialized, efficient breeding

### 3. Data-Driven Breeding Potential
- **Predictive Modeling**: Network analysis enables future parent selection optimization
- **Hidden Gems**: Statistical analysis reveals undervalued breeding stock
- **Success Patterns**: Quantifiable traits help predict breeding outcomes

### 4. Industry Evolution
- **Professional Transition**: From hobby to a more specialized niche
- **Efficiency Gains**: Fewer participants but higher individual impact
- **Knowledge Transfer**: Historical analysis informs modern strategy

---

## Recommendations

### For New Hybridizers
1. **Study Golden Age Genetics**: Focus and understand 1950s-1960s foundation varieties and their modern effects
2. **Leverage Network Analysis**: Use breeding relationship data for parent selection
3. **Modern Techniques**: Adopt data-driven approaches from day one to esnure quality outcomes
4. **Persistence Strategy**: Plan for multi-year commitment with gradual scaling

### For Experienced Hybridizers  
1. **Network Optimization**: Identify underutilized high-value parents in your collection
2. **Regional Specialization**: Leverage geographic breeding advantages
3. **Descendant Analysis**: Evaluate long-term genetic contribution of your varieties
4. **Cross-Era Integration**: Combine historical genetics with modern efficiency

### For the Daylily Community
1. **Database Enhancement**: Improve data collection for specialized traits
2. **Knowledge Sharing**: Implement data-driven decision support tools  
3. **Breeding Cooperatives**: Use network analysis for collaborative breeding
4. **Education Programs**: Teach statistical breeding methods to newcomers

### Possible Future Research Directions
1. **Trait Inheritance Modeling**: Predict characteristic expression patterns
2. **Climate Adaptation Analysis**: Regional performance optimization
3. **Disease Resistance Mapping**: Network analysis of disease resistant varieties
4. **Market Value Prediction**: Economic modeling of variety success
5. **BLUP and Bayesian Methods**: Models to reliably predict best parents for improved breeding efficiency 

---

## Technical Implementation

### Tools & Technologies
- **Languages**: Python, SQL
- **Libraries**: pandas, numpy, scipy, networkx, sqlite3
- **Analysis**: Statistical modeling, network analysis, data visualization
- **Storage**: SQLite database with CSV export capabilities
- **Web Scraping**: Custom requests-based solution with ethical constraints

### Data Quality Measures
- **Validation**: Multi-stage data cleaning and verification
- **Deduplication**: Advanced duplicate detection and removal
- **Outlier Management**: IQR-based outlier detection with trait-specific handling
- **Missing Data**: Strategic imputation and completeness analysis

### Reproducibility
- **Database Schema**: Documented table structures and relationships
- **Processing Pipeline**: Modular notebook approach with clear dependencies
- **Export Formats**: Multiple output formats (CSV, JSON, SQLite)
- **Documentation**: Comprehensive analysis documentation and insights

---

## Project Structure

```python

├── 01_data_exploration.ipynb      # EDA and data cleaning
├── 02_hybridizer_analysis.ipynb   # Career pattern analysis  
├── 03_0 netowrk_extraction.ipynb  # Indentifies Parent-Child relationships (not included)
├── 03_network_analysis.ipynb      # Breeding relationship networks
├── 04_regional_data.ipynb         # Geographic analysis
├── 05_merge.ipynb                 # Master database integration
├── daylilies.db/                  # SQLite database
│   ├── master_daylily             # Final integrated dataset
│   ├── daylilies                  
|   ├── location_data
|   ├── network_influences_metrics
│   └── parent_child_relationships
├── README.md                      # This documentation
├── regional_data.xlsx             # ADS regional information
└── requirements.txt               # Project dependancies 
```

---

## Data Structure

```python

============================================================
DATA: COLUMN TYPES AND COMPLETENESS
============================================================


RAW DAYLILIES.JSONL ANALYSIS (before cleaning)
Total Records: 102,611
--------------------------------------------------
+-------------------+-------------+----------------+
| Column Name       | Data Type   | Completeness   |
+===================+=============+================+
| url               | string      | 100.00%        |
+-------------------+-------------+----------------+
| scraped_at        | string      | 100.00%        |
+-------------------+-------------+----------------+
| name              | string      | 100.00%        |
+-------------------+-------------+----------------+
| hybridizer        | string      | 100.00%        |
+-------------------+-------------+----------------+
| year              | string      | 100.00%        |
+-------------------+-------------+----------------+
| scape_height      | string      | 99.66%         |
+-------------------+-------------+----------------+
| bloom_size        | string      | 92.24%         |
+-------------------+-------------+----------------+
| bloom_season      | string      | 99.28%         |
+-------------------+-------------+----------------+
| ploidy            | string      | 98.27%         |
+-------------------+-------------+----------------+
| foliage_type      | string      | 97.74%         |
+-------------------+-------------+----------------+
| fragrance         | string      | 32.67%         |
+-------------------+-------------+----------------+
| bloom_habit       | string      | 94.22%         |
+-------------------+-------------+----------------+
| bud_count         | string      | 52.62%         |
+-------------------+-------------+----------------+
| branches          | string      | 52.75%         |
+-------------------+-------------+----------------+
| seedling_#        | string      | 86.14%         |
+-------------------+-------------+----------------+
| color_description | string      | 99.95%         |
+-------------------+-------------+----------------+
| parentage         | string      | 96.17%         |
+-------------------+-------------+----------------+
| image_url         | string      | 67.56%         |
+-------------------+-------------+----------------+
| form              | string      | 12.72%         |
+-------------------+-------------+----------------+
| sculpting         | string      | 1.08%          |
+-------------------+-------------+----------------+
| notes             | string      | 3.12%          |
+-------------------+-------------+----------------+

REGIONAL FILE ANALYSIS
NAME: Hemerocallis-Hybridizer-Registrant-List_Through-2024.xlsx
Total Records: 5,562
--------------------------------------------------
+-------------------+-------------+----------------+
| Column Name       | Data Type   | Completeness   |
+===================+=============+================+
| ABBREVIATION CODE | string      | 100.00%        |
+-------------------+-------------+----------------+
| Garden Name       | string      | 43.20%         |
+-------------------+-------------+----------------+
| Region            | float       | 99.84%         |
+-------------------+-------------+----------------+
| Name              | string      | 99.98%         |
+-------------------+-------------+----------------+
| Deceased          | string      | 88.21%         |
+-------------------+-------------+----------------+
| Address           | string      | 99.82%         |
+-------------------+-------------+----------------+
| City              | string      | 99.80%         |
+-------------------+-------------+----------------+
| State             | string      | 93.98%         |
+-------------------+-------------+----------------+
| Country           | string      | 11.27%         |
+-------------------+-------------+----------------+
| Zip               | string      | 86.91%         |
+-------------------+-------------+----------------+
| Region.1          | string      | 24.06%         |
+-------------------+-------------+----------------+
| Name.1            | string      | 24.38%         |
+-------------------+-------------+----------------+
| Deceased.1        | string      | 9.64%          |
+-------------------+-------------+----------------+
| Address.1         | string      | 24.34%         |
+-------------------+-------------+----------------+
| City.1            | string      | 24.07%         |
+-------------------+-------------+----------------+
| State.1           | string      | 22.96%         |
+-------------------+-------------+----------------+
| Country.1         | string      | 2.05%          |
+-------------------+-------------+----------------+
| Zip.1             | string      | 22.01%         |
+-------------------+-------------+----------------+
| Date              | string      | 16.85%         |
+-------------------+-------------+----------------+
| Notes             | string      | 24.33%         |
+-------------------+-------------+----------------+
| Unnamed: 20       | string      | 0.04%          |
+-------------------+-------------+----------------+
| Unnamed: 21       | string      | 0.02%          |
+-------------------+-------------+----------------+
| Unnamed: 22       | string      | 0.02%          |
+-------------------+-------------+----------------+
| Unnamed: 23       | string      | 0.02%          |
+-------------------+-------------+----------------+
| Unnamed: 24       | string      | 0.02%          |
+-------------------+-------------+----------------+
| Unnamed: 25       | string      | 0.02%          |
+-------------------+-------------+----------------+


FINAL MASTER DAYLILY TABLE
Total Records: 101,446
--------------------------------------------------
+-------------------------+-------------+----------------+
| Column Name             | Data Type   | Completeness   |
+=========================+=============+================+
| url                     | string      | 100.00%        |
+-------------------------+-------------+----------------+
| name                    | string      | 100.00%        |
+-------------------------+-------------+----------------+
| hybridizer              | string      | 99.99%         |
+-------------------------+-------------+----------------+
| year                    | integer     | 100.00%        |
+-------------------------+-------------+----------------+
| scape_height            | float       | 99.64%         |
+-------------------------+-------------+----------------+
| bloom_size              | float       | 92.20%         |
+-------------------------+-------------+----------------+
| bloom_season            | string      | 99.23%         |
+-------------------------+-------------+----------------+
| ploidy                  | string      | 98.27%         |
+-------------------------+-------------+----------------+
| foliage_type            | string      | 97.73%         |
+-------------------------+-------------+----------------+
| fragrance               | string      | 32.78%         |
+-------------------------+-------------+----------------+
| bloom_habit             | string      | 94.20%         |
+-------------------------+-------------+----------------+
| bud_count               | float       | 52.37%         |
+-------------------------+-------------+----------------+
| branches                | float       | 52.47%         |
+-------------------------+-------------+----------------+
| seedling_num            | string      | 86.00%         |
+-------------------------+-------------+----------------+
| color_description       | string      | 99.95%         |
+-------------------------+-------------+----------------+
| parentage               | string      | 78.55%         |
+-------------------------+-------------+----------------+
| image_url               | string      | 67.43%         |
+-------------------------+-------------+----------------+
| form                    | string      | 12.72%         |
+-------------------------+-------------+----------------+
| sculpting               | string      | 1.07%          |
+-------------------------+-------------+----------------+
| notes                   | string      | 3.14%          |
+-------------------------+-------------+----------------+
| rebloom                 | integer     | 100.00%        |
+-------------------------+-------------+----------------+
| Region                  | float       | 99.30%         |
+-------------------------+-------------+----------------+
| primary_hybridizer      | string      | 99.30%         |
+-------------------------+-------------+----------------+
| City                    | string      | 99.26%         |
+-------------------------+-------------+----------------+
| State                   | string      | 94.33%         |
+-------------------------+-------------+----------------+
| Country                 | string      | 99.29%         |
+-------------------------+-------------+----------------+
| Direct_Children         | float       | 74.97%         |
+-------------------------+-------------+----------------+
| Total_Descendants       | float       | 74.97%         |
+-------------------------+-------------+----------------+
| Avg_Generation_Impact   | float       | 74.97%         |
+-------------------------+-------------+----------------+
| Descendant_Success_Rate | float       | 74.97%         |
+-------------------------+-------------+----------------+
| Breeding_Span           | float       | 74.97%         |
+-------------------------+-------------+----------------+
| Yearly_Impact           | float       | 74.97%         |
+-------------------------+-------------+----------------+
| In_Degree_Centrality    | float       | 74.97%         |
+-------------------------+-------------+----------------+
| Out_Degree_Centrality   | float       | 74.97%         |
+-------------------------+-------------+----------------+
| PageRank                | float       | 74.97%         |
+-------------------------+-------------+----------------+
| Katz_Centrality         | float       | 74.97%         |
+-------------------------+-------------+----------------+
| Betweenness_Centrality  | float       | 74.97%         |
+-------------------------+-------------+----------------+
| parents                 | string      | 68.59%         |
+-------------------------+-------------+----------------+
| children                | string      | 24.79%         |
+-------------------------+-------------+----------------+

```

---

## Impact & Applications

This analysis represents the first data-driven approach to daylily breeding optimization. The insights provide:

- **Strategic Breeding**: Data-backed parent selection methodology
- **Career Guidance**: Evidence-based development paths for hybridizers  
- **Industry Intelligence**: Market and community trend analysis
- **Genetic Preservation**: Identification of historically valuable genetics
- **Innovation Foundation**: Platform for advanced breeding technologies

*The project showcases the power of combining modern data science techniques with traditional horticultural & agricultural practices, to unlock insights that were previously impossible to discover, providing a template for similar analyses in other plant breeding communities.*

---

# Project Setup Instructions

## Repository Setup

1. Clone the repository
```bash
git clone https://github.com/drowsy-1/Daylily-Analytics.git
cd Daylily-Analytics
```

2. Set up Python environment
It's recommended to use a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

## Notebook Structure

This repository contains a series of Jupyter notebooks numbered from 01 to 05. There is also an additional notebook (03_0) which is a supplementary notebook to notebook 03.

The notebooks should be run in numerical order:
- 01_data_exploration.ipynb
- 02_hybridizer_analysis.ipynb
- 03_0_network_extraction.ipynb (supplementary to notebook 03 not included)
- 03_network_analysis.ipynb
- 04_regional_data.ipynb
- 05_merge.ipynb

## Running the Notebooks

1. After activating your virtual environment, start Jupyter:
```bash
jupyter notebook
```

2. Your browser will open automatically. If not, copy the URL shown in your terminal.

3. Navigate through the notebooks in order, running each cell sequentially. (01 -> 05)

## Important Notes

- Make sure to run the notebooks in the specified order as they have dependencies on previous notebooks
- Notebook 03_0 is essential to notebook 03 and must be run before notebook 03
- Each notebook should indicate any specific prerequisites at its beginning in the imports

## Troubleshooting

If you encounter any issues:
1. Ensure all dependencies are installed correctly
2. Verify that you're using the correct Python version
3. Try restarting the Jupyter kernel if you encounter any memory issues
4. Make sure to run all cells in each notebook in sequence