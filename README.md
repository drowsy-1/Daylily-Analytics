# Daylily Data Science Portfolio

## Overview

This data science project analyzes over 100,000 daylily varieties from the American Daylily Society database to uncover breeding patterns, hybridizer career trajectories, and network relationships to facilitate data-driven plant breeding strategies.

### Primary Goal
Transform the American Daylily Society's raw database into a comprehensive, analysis-ready dataset that enables future statistical breeding value calculations (BLUP, Bayesian methods).

### The Problem
With 100 years of intensive hybridization resulting in over 102,000 registered daylily varieties, collectors and hybridizers face an overwhelming selection challenge. Current breeding strategies range from award-focused selection to opportunistic crossing of "pretty flowers." **The Gap**: No data-driven techniques exist beyond simple filtering, leaving significant potential for improving breeding outcomes through statistical analysis and network-based insights.

### Why This Approach?
This project creates the first structured dataset enabling statistical analysis of breeding success patterns - a necessary preprocessing step before implementing advanced genetic prediction models.

## Technical Approach

### Data Acquisition
**Source**: American Daylily Society database (https://daylilies.org/)  
**Scale**: 101,718 unique varieties spanning 1763-2024  
**Completeness**: Varies by field (100% for core data, 1.07% for specialized traits)

Due to database access limitations, I developed a custom web scraping solution. The scraping was conducted ethically during nighttime hours with low bandwidth queries: 3-4 nights for text data, 3 additional nights for images (~4GB total). This approach produced a consistent dataset ready for analysis.

### Technical Stack
- **Languages**: Python, SQL
- **Libraries**: pandas, numpy, scipy, networkx, igraph, matplotlib, seaborn
- **Database**: SQLite for structured storage and joins
- **Environment**: Jupyter notebooks for reproducible analysis

### Data Pipeline
Raw Database → Cleaning → Relationship Extraction → Network Analysis → Geographic Enrichment → Master Dataset

## Core Analysis Components
```
| Analysis Type                                           |
| Method                                                  |
| Rationale                                               | 
| Key Limitation                                          |
|---------------------------------------------------------|

 **Data Cleaning** 
| IQR outlier detection, manual validation                |
| Preserves integrity while removing impossible values    | 
| Some subjective decisions required                      |

 **Relationship Extraction** 
| Pattern matching on parentage strings                   | 
| Only method available for unstructured text             | 
| Multiple parents complicate modeling                    |

 **Network Analysis** 
| Multiple centrality measures                            |
| Captures breeding influence from different perspectives |
| High density limits community detection                 |

**Geographic Integration** 
| Region mapping via abbreviation codes                   | 
| Enables climate/regional breeding analysis              | 
| Missing data for some hybridizers                       |

```

### Notebook Structure
1. **Data Exploration & Quality** (01): Statistical distributions, missing data analysis, database normalization
2. **Hybridizer Career Analysis** (02): Community trends and productivity patterns  
3. **Network Extraction & Analysis** (03_0, 03): Parent-child relationship extraction and centrality calculations
4. **Regional Data Integration** (04): Geographic breeding pattern analysis
5. **Master Database Creation** (05): Comprehensive data fusion via SQL joins

## Key Findings

### Data Quality & Structure
- 98%+ completeness for core traits
- Clean temporal span (1763-2024) enables comprehensive trend analysis
- Branches and bud count correlation (0.61) confirms direct biological relationship

### Breeding Network Insights
The analysis revealed that 1950s-1960s varieties dominate descendant counts not due to superior genetics, but because they represent the **foundation era** when systematic pedigree recording began. These early-recorded varieties had the longest time to infiltrate the breeding network, creating an artifact of documentation timing rather than genetic superiority.

**Network Structure**:
- Low density confirms strategic parent selection rather than random crossing
- Multiple centrality measures provide different perspectives on breeding influence
- Hierarchical breeding line structures with clear genetic connectors identified

### Community Evolution
- **Peak Growth**: 2000s with 1,100+ new hybridizers
- **Current Decline**: 600 hybridizer net loss in 2020s  
- **Productivity Gains**: 22-24% efficiency increase among surviving hybridizers
- **Professionalization**: Transition from widespread hobby to specialized craft

### Regional Patterns
Complete coverage across 15 ADS regions enables future climate adaptation and geographic breeding optimization studies.

## Impact & Applications

### For Data Scientists
- **Methodology Template**: Reproducible approach for agricultural genetic databases
- **Novel Network Application**: Graph theory applied to plant breeding relationships
- **Complex Integration**: Multi-source database construction techniques

### For Plant Breeders
- **Historical Perspective**: Evidence-based understanding of breeding trends
- **Parent Selection**: Network-informed breeding stock identification  
- **Regional Optimization**: Geographic breeding advantage recognition

### for Daylily Community
- **First Comprehensive Analysis**: No prior analytical work exists on this scale
- **Evidence-Based Insights**: Replace intuition with data-driven understanding
- **Preservation Priority**: Identify historically significant genetic material

## Future Research Directions

### Immediate Applications (Current Dataset)
- **Regional Performance Analysis**: Geographic breeding success patterns
- **Trait Inheritance Modeling**: Parent-offspring characteristic transfer patterns
- **Breeding Line Analysis**: Cross-line mixing and keystone variety identification

### Advanced Statistical Methods (Enhanced Data Required)
- **BLUP Models**: Best Linear Unbiased Prediction for breeding values - requires expanded data collection and standardized performance metrics
- **Bayesian Analysis**: Probabilistic breeding outcome prediction - needs prior distribution establishment from historical success rates
- **Genomic Selection**: Integration with genetic marker data - requires DNA analysis of key varieties

### Critical Data Enhancement Needs
- **Robust Relationship Extraction**: Machine learning approaches for complex parentage (13+ parents)
- **Performance Metrics**: Disease resistance, regional adaptation, and longevity data
- **Standardized Evaluation**: Consistent trait measurement protocols across regions

## Recommendations

### For New Hybridizers
- Study foundation varieties from systematic pedigree recording era (1950s-1960s)
- Leverage network analysis for strategic parent selection
- Plan for multi-year commitment with data-driven approaches from day one

### For Experienced Hybridizers  
- Identify underutilized high-value parents using centrality metrics
- Evaluate long-term genetic contribution beyond immediate offspring success
- Integrate historical genetics with modern efficiency techniques

### For the Community
- Enhance database collection for specialized traits and performance metrics
- Implement collaborative breeding data sharing protocols
- Develop educational programs for statistical breeding methods

## Known Limitations & Future Improvements

### Current Constraints
- **Relationship Extraction**: Pattern matching introduces parsing errors
- **Missing Performance Data**: Limited disease/climate resistance information  
- **Complex Parentage**: Biological impossibilities in recorded lineages (13+ parents)
- **Geographic Gaps**: Missing location data for some hybridizers

### Planned Enhancements
- **Improved Parsing**: Machine learning or improved algorithm for parentage extraction accuracy
- **Performance Integration**: Disease resistance and adaptation metrics
- **Validation Systems**: Cross-reference breeding records with physical plant characteristics

## Project Significance

This represents the first comprehensive data science analysis of the American Daylily Society database. While not providing final breeding recommendations, it establishes the analytical foundation necessary for advanced statistical breeding methods.

**Key Contribution**: Transforms a horticultural database into a research-ready dataset, enabling future application of modern genetic analysis techniques to improve breeding outcomes. The project showcases the power of combining modern data science techniques with traditional agricultural practices, providing a template for similar analyses in other plant breeding communities.

---

## Data Structure

### RAW DAYLILIES.JSONL ANALYSIS (before cleaning)
Total Records: 102,611

| Column Name       | Data Type | Completeness |
|-------------------|-----------|--------------|
| url               | string    | 100.00%      |
| scraped_at        | string    | 100.00%      |
| name              | string    | 100.00%      |
| hybridizer        | string    | 100.00%      |
| year              | string    | 100.00%      |
| scape_height      | string    | 99.66%       |
| bloom_size        | string    | 92.24%       |
| bloom_season      | string    | 99.28%       |
| ploidy            | string    | 98.27%       |
| foliage_type      | string    | 97.74%       |
| fragrance         | string    | 32.67%       |
| bloom_habit       | string    | 94.22%       |
| bud_count         | string    | 52.62%       |
| branches          | string    | 52.75%       |
| seedling_#        | string    | 86.14%       |
| color_description | string    | 99.95%       |
| parentage         | string    | 96.17%       |
| image_url         | string    | 67.56%       |
| form              | string    | 12.72%       |
| sculpting         | string    | 1.08%        |
| notes             | string    | 3.12%        |

### REGIONAL FILE ANALYSIS
**Name**: Hemerocallis-Hybridizer-Registrant-List_Through-2024.xlsx  
Total Records: 5,562

| Column Name       | Data Type | Completeness |
|-------------------|-----------|--------------|
| ABBREVIATION CODE | string    | 100.00%      |
| Garden Name       | string    | 43.20%       |
| Region            | float     | 99.84%       |
| Name              | string    | 99.98%       |
| Deceased          | string    | 88.21%       |
| Address           | string    | 99.82%       |
| City              | string    | 99.80%       |
| State             | string    | 93.98%       |
| Country           | string    | 11.27%       |
| Zip               | string    | 86.91%       |
| Region.1          | string    | 24.06%       |
| Name.1            | string    | 24.38%       |
| Deceased.1        | string    | 9.64%        |
| Address.1         | string    | 24.34%       |
| City.1            | string    | 24.07%       |
| State.1           | string    | 22.96%       |
| Country.1         | string    | 2.05%        |
| Zip.1             | string    | 22.01%       |
| Date              | string    | 16.85%       |
| Notes             | string    | 24.33%       |
| Unnamed: 20       | string    | 0.04%        |
| Unnamed: 21       | string    | 0.02%        |
| Unnamed: 22       | string    | 0.02%        |
| Unnamed: 23       | string    | 0.02%        |
| Unnamed: 24       | string    | 0.02%        |
| Unnamed: 25       | string    | 0.02%        |

### FINAL MASTER DAYLILY TABLE
Total Records: 101,446

| Column Name             | Data Type | Completeness |
|-------------------------|-----------|--------------|
| url                     | string    | 100.00%      |
| name                    | string    | 100.00%      |
| hybridizer              | string    | 99.99%       |
| year                    | integer   | 100.00%      |
| scape_height            | float     | 99.64%       |
| bloom_size              | float     | 92.20%       |
| bloom_season            | string    | 99.23%       |
| ploidy                  | string    | 98.27%       |
| foliage_type            | string    | 97.73%       |
| fragrance               | string    | 32.78%       |
| bloom_habit             | string    | 94.20%       |
| bud_count               | float     | 52.37%       |
| branches                | float     | 52.47%       |
| seedling_num            | string    | 86.00%       |
| color_description       | string    | 99.95%       |
| parentage               | string    | 78.55%       |
| image_url               | string    | 67.43%       |
| form                    | string    | 12.72%       |
| sculpting               | string    | 1.07%        |
| notes                   | string    | 3.14%        |
| rebloom                 | integer   | 100.00%      |
| Region                  | float     | 99.30%       |
| primary_hybridizer      | string    | 99.30%       |
| City                    | string    | 99.26%       |
| State                   | string    | 94.33%       |
| Country                 | string    | 99.29%       |
| Direct_Children         | float     | 74.97%       |
| Total_Descendants       | float     | 74.97%       |
| Avg_Generation_Impact   | float     | 74.97%       |
| Descendant_Success_Rate | float     | 74.97%       |
| Breeding_Span           | float     | 74.97%       |
| Yearly_Impact           | float     | 74.97%       |
| In_Degree_Centrality    | float     | 74.97%       |
| Out_Degree_Centrality   | float     | 74.97%       |
| PageRank                | float     | 74.97%       |
| Katz_Centrality         | float     | 74.97%       |
| Betweenness_Centrality  | float     | 74.97%       |
| parents                 | string    | 68.59%       |
| children                | string    | 24.79%       |

## Project Setup Instructions

### Repository Setup

1. **Clone the repository**
```bash
git clone https://github.com/drowsy-1/Daylily-Analytics.git
cd Daylily-Analytics
```

2. **Set up Python environment**  
It's recommended to use a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

### Notebook Structure

This repository contains a series of Jupyter notebooks numbered from 01 to 05. There is also an additional notebook (03_0) which is a prerequisite to notebook 03.

The notebooks should be run in numerical order:

1. `01_data_exploration.ipynb`
2. `02_hybridizer_analysis.ipynb`
3. `03_0_network_extraction.ipynb` (not included)
4. `03_network_analysis.ipynb`
5. `04_regional_data.ipynb`
6. `05_merge.ipynb`

### Running the Notebooks

After activating your virtual environment, start Jupyter:
```bash
jupyter notebook
```

Your browser will open automatically. If not, copy the URL shown in your terminal.

Navigate through the notebooks in order, running each cell sequentially. (01 → 05)

### Project Structure
```
├── 01_data_exploration.ipynb      # EDA and data cleaning
├── 02_hybridizer_analysis.ipynb   # Career pattern analysis  
├── 03_0_network_extraction.ipynb  # Identifies Parent-Child relationships (not included)
├── 03_network_analysis.ipynb      # Breeding relationship networks
├── 04_regional_data.ipynb         # Geographic analysis
├── 05_merge.ipynb                 # Master database integration
├── daylilies.db/                  # SQLite database
│   ├── master_daylily             # Final integrated dataset
│   ├── daylilies                  
│   ├── location_data
│   ├── network_influences_metrics
│   └── parent_child_relationships
├── README.md                      # This documentation
├── regional_data.xlsx             # ADS regional information
└── requirements.txt               # Project dependencies 
```

### Important Notes
- Make sure to run the notebooks in the specified order as they have dependencies on previous notebooks
- Notebook 03_0 is essential to notebook 03 and must be run before notebook 03
- Each notebook indicates any specific prerequisites at its beginning in the imports

### Troubleshooting
If you encounter any issues:
- Ensure all dependencies are installed correctly
- Verify that you're using the correct Python version
- Try restarting the Jupyter kernel if you encounter any memory issues
- Make sure to run all cells in each notebook in sequence
