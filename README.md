# Daylily Data Science Portfolio

## Overview

This data science project analyzes over 100,000 daylily varieties from the American Daylily Society database to uncover breeding patterns, hybridizer career trajectories, and network relationships to facilitate data-driven plant breeding strategies.

## Project Objectives

### Primary Goal
**Data Preparation and Enrichment**: Transform the American Daylily Society's raw database into a comprehensive, analysis-ready dataset that enables future statistical breeding value calculations (BLUP, Bayesian methods).

### Specific Objectives
1. **Data Quality & Structure**: Clean and validate 100,000+ variety records for analytical reliability
2. **Relationship Mapping**: Extract and structure parent-child breeding relationships for pseudo-genetic analysis
3. **Geographic Enrichment**: Integrate hybridizer location data for regional breeding pattern analysis  
4. **Network Foundation**: Calculate centrality metrics as potential predictors for future breeding models
5. **Community Analysis**: Document declining hybridizer population trends (exploratory interest)

### Long-term Vision
Enable data-driven breeding decisions through statistical methods currently impossible due to data structure limitations.

---
## The Problem

With 100 years of intensive hybridization resulting in over 102,000 registered daylily varieties, collectors and hybridizers face an overwhelming selection challenge. Current breeding strategies range from:

- **Award-focused**: Selecting only award-winning varieties as parents
- **Trait-specific**: Choosing varieties with specific desired characteristics  
- **Performance-based**: Intensive screening for growth habit, disease, and pest resistance
- **Opportunistic**: Crossing available "pretty flowers" hoping for the best

**The Gap**: No data-driven techniques exist beyond simple filtering, leaving significant potential for improving breeding outcomes through statistical analysis and network-based insights.

### Why This Approach?
**The Solution**: This project creates the **first structured dataset** enabling statistical analysis of breeding success patterns - a necessary preprocessing step before implementing advanced genetic prediction models.

---
## Data Acquisition & Challenges

### Data Source
- **Primary**: American Daylily Society database (https://daylilies.org/)
- **Scale**: 101,718 unique varieties spanning 1763-2025
- **Completeness**: Varies by field (100% for core data, 1.07% for specialized traits)

### Technical Approach
Due to database access limitations, I developed a custom web scraping solution:
- **Methodology**: Iterative scraping using Python requests module
- **Ethics**: Nighttime execution (off-peak) with low bandwidth queries
- **Scope**: 3-4 nights for text data, 3 nights for images (~4GB)
- **Output**: Clean, consistent dataset ready for cleaning

### Analysis Method Selection Rationale
```python
| Analysis Type | Method Chosen | Why Selected | Limitations Discovered |
|---------------|---------------|--------------|----------------------|
| **Data Cleaning** | IQR outlier detection, manual validation | Preserves data integrity while removing impossible values | Some subjective decisions required |
| **Relationship Extraction** | Pattern matching on parentage strings | Only available method for unstructured text data | Multiple parents (up to 13) complicate genetic modeling |
| **Network Analysis** | Multiple centrality measures | Captures breeding influence from different perspectives | High density (25k nodes) limits community detection |
| **Geographic Integration** | Region mapping via abbreviation codes | Enables climate/regional breeding analysis | Missing data for some hybridizers |
| **Career Analysis** | Temporal productivity tracking | Documents concerning community decline | Not directly related to breeding values |
```
### Technical Architecture

**Data Pipeline:**
```
Raw Database → Cleaning → Relationship Extraction → Network Analysis → Geographic Enrichment → Master Dataset
```

**Technologies Used:**
- **Python**: pandas, numpy, scipy, networkx, igraph
- **Database**: SQLite for structured storage and SQL joins
- **Visualization**: matplotlib, seaborn
- **Environment**: Jupyter notebooks for reproducible analysis

---
## Core Analysis Components

### 1. Data Exploration & Quality (Notebook 01)
**Purpose**: Establish baseline data quality and identify analytical opportunities
**Methods**: 
- Statistical distributions and correlations
- Missing data analysis  
- Outlier detection using IQR methods
- Database normalization

**Key Finding**: Branches and bud count correlation (0.61) suggests direct biological relationship 

### 2. Hybridizer Career Analysis (Notebook 02)  
**Purpose**: Document community trends and identify productivity patterns
**Methods**:
- Hyrbidizer community entry and exit measurement
- Temporal productivity analysis
- Modern vs. historical efficiency comparison

**Key Finding**: 600-hybridizer decline in 2020s, but 22-24% productivity increase in survivors

### 3. Network Relationship Extraction & Analysis (Notebooks 03_0, 03)
**Purpose**: Create structured breeding relationships for future genetic modeling
**Methods**:
- Pattern matching for parent-child extraction
- Graph theory centrality calculations (PageRank, Betweenness, Degree)
- Multi-generational descendant tracking

**Key Limitation**: High network density prevented meaningful community detection
**Key Discovery**: 1950s-1960s varieties dominate descendant counts due to early pedigree recording

### 4. Regional Data Integration (Notebook 04)
**Purpose**: Enable geographic breeding pattern analysis
**Methods**:
- ADS region mapping (16 regions)
- State/province standardization
- Database integration via hybridizer codes

**Future Application**: Regional performance optimization and climate adaptation studies

### 5. Master Database Creation (Notebook 05)
**Purpose**: Combine all analyses into single queryable dataset
**Methods**:
- SQL joins across multiple tables
- Relationship parsing into parent/child columns
- Data export for future analysis

**Output**: 101,446 varieties with 38 analytical dimensions

## Data Overview

### Dataset Characteristics
- **Total Varieties**: 101,718 unique entries
- **Time Span**: 262 years (1763-2025)
- **Attributes**: 21 different characteristics tracked

#### Numerical Characteristics Distribution
| Trait            |   Mean | Median | Std Dev | Range  |
|------------------|--------|--------|---------|--------|
| **Bloom Size**   | 5.75"  | 6.00"  | 1.29"   | 1-14"  |
| **Scape Height** | 29.26" | 28.00" | 6.82"   | 2-73"  |
| **Branching**    | 3.51   | 3.00   | 1.06    | 1-9    |
| **Bud Count**    | 19.79  | 19.00  | 7.40    | 1-68   |

---
## Key Discoveries & Implications

### Data Quality Insights
- **98%+ completeness** for core breeding traits
- **Strong biological correlations** support future modeling
- **Clean temporal span** (1763-2024) enables trend analysis

### Network Structure Revelations  
- **"Golden Age" Genetics**: 1950s-1960s varieties dominate not due to superior genetics, but because they were recorded early and had longest time to infiltrate the breeding network
- **Selective Breeding Patterns**: Low network density confirms strategic parent selection rather than random crossing
- **Centrality as Predictor**: Multiple centrality measures provide different perspectives on breeding influence

### Community Evolution
- **Professionalization**: Declining hobbyist participation but increased individual productivity
- **Modern Efficiency**: Contemporary hybridizers achieve higher early-career output
- **Knowledge Transfer**: Historical analysis informs modern breeding strategies
  **Peak Growth**: 2000s with 1,100+ new hybridizers
- **Current Decline**: 600 hybridizer net loss in 2020s  
- **Peak Activity**: 485 active hybridizers (2011)
- **Trend**: Transition from widespread and growing hobby to specialized craft

### Hybridizer Success Indicators
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
- **Bridge Varieties**: Certain cultivars serve as genetic connectors between groups
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

## Future Research Enabled

### Immediate Applications (Current Dataset)
1. **Regional Performance Analysis**: Geographic breeding success patterns
2. **Naive Trait Inheritance Modeling**: Parent-offspring characteristic transfer
3. **Breeding Line Analysis**: Analyze cross line mixing and identifcation of program keystone varieties

### Advanced Statistical Methods (Requires Enhanced Data)
1. **BLUP Models**: Best Linear Unbiased Prediction for breeding values
2. **Bayesian Analysis**: Probabilistic breeding outcome prediction  
3. **Genomic Selection**: Integration with genetic marker data

### Data Enhancement Needs
- **Robust Relationship Extraction**: Handle complex parentage (13+ parents)
- **Performance Metrics**: Disease resistance, regional adaptation data

---
## Impact 

### For Data Scientists
- **Methodology Template**: Reproducible approach for agricultural genetic databases
- **Network Analysis**: Novel application of graph theory to plant breeding
- **Data Integration**: Complex multi-source database construction

### For Plant Breeders
- **Historical Perspective**: Evidence-based understanding of breeding trends
- **Parent Selection**: Network-informed breeding stock identification
- **Regional Optimization**: Geographic breeding advantage recognition

### For Daylily Community
- **First Comprehensive Analysis**: No prior analytical work exists on this scale
- **Evidence-Based Insights**: Replace intuition with data-driven understanding
- **Preservation Priority**: Identify historically significant genetic material

---
## Recommendations

### For New Hybridizers
1. **Study Golden Age Genetics**: Focus and understand foundation varieties and their modern effects
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
3. **Breeding Cooperatives**: Use network analysis for collaborative breeding, and sharing of offspring data
4. **Education Programs**: Teach statistical breeding methods to newcomers

### Possible Future Research Directions
1. **Trait Inheritance Modeling**: Predict characteristic expression patterns
2. **Climate Adaptation Analysis**: Regional performance optimization
3. **Disease Resistance Mapping**: Network analysis of disease resistant varieties
4. **BLUP and Bayesian Methods**: Models to reliably predict best parents for improved breeding efficiency 

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
- **Deduplication**: Duplicate detection and removal
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
## Known Limitations & Future Improvements

### Current Constraints
1. **Relationship Extraction**: Pattern matching introduces some errors
2. **Missing Genetic Data**: No DNA/marker information available
3. **Performance Metrics**: Limited disease/climate resistance data
4. **Complex Parentage**: Some varieties have 13+ parents (biologically impossible)

### Planned Enhancements
1. **Improved Parsing**: Machine learning for parentage extraction
2. **Performance Integration**: Disease resistance enrichment
---

*The project showcases the power of combining modern data science techniques with traditional horticultural & agricultural practices, to unlock insights that were previously impossible to discover, providing a template for similar analyses in other plant breeding communities.*

## Project Significance

This represents the **first data science analysis** of the American Daylily Society database. While not providing final breeding recommendations, it establishes the analytical foundation necessary for advanced statistical breeding methods.

**Key Contribution**: Transforms an horticultural database into a research-ready dataset, enabling future application of modern genetic analysis techniques to improve breeding outcomes.

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