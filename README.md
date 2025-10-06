# Daylily Data Science Portfolio

## Overview

This data science project analyzes over 100,000 daylily varieties from the American Daylily Society database to uncover breeding patterns, hybridizer career trajectories, and network relationships through advanced pedigree reconstruction and statistical breeding value estimation.

**Project Evolution:** What began as database preprocessing has evolved into a analytical pipeline implementing Bayesian breeding value prediction - demonstrating data engineering, algorithm development, and statistical modeling capabilities.

**Repository Structure:** Core pipeline (01-05) and breeding value methodology (07) are public. Advanced pedigree reconstruction algorithms (06) and complete datasets remain private for intellectual property considerations.

---

## Table of Contents
- [Primary Goal](#primary-goal)
- [The Problem](#the-problem)
- [Technical Approach](#technical-approach)
- [Core Analysis Components](#core-analysis-components)
- [Key Findings](#key-findings)
- [Impact & Applications](#impact--applications)
- [Future Research Directions](#future-research-directions)
- [Project Setup](#project-setup)
- [Repository Structure & Access](#repository-structure--access)
- [Current Status & Limitations](#current-status--limitations)

---

## Primary Goal

Transform the American Daylily Society's dataset into a comprehensive, analysis-ready dataset that enables statistical breeding value calculations through Bayesian methods and hierarchical modeling.

### The Problem

With 100 years of intensive hybridization resulting in over 102,000 registered daylily varieties, collectors and hybridizers face an overwhelming selection challenge. Current breeding strategies range from award-focused selection to opportunistic crossing of "pretty flowers." 

**The Gap**: No data-driven techniques exist beyond simple filtering, leaving significant potential for improving breeding outcomes through statistical analysis and network-based insights.

### Why This Approach?

This project creates the first structured dataset enabling statistical analysis of breeding success patterns and implements quantitative genetic methods to estimate breeding values - moving beyond preprocessing to deliver actionable breeding intelligence.

---

## Technical Approach

### Data Acquisition

**Source**: American Daylily Society database (https://daylilies.org/)  
**Scale**: 101,718 unique varieties spanning 1763-2024  
**Completeness**: Varies by field (100% for core data, 1.07% for specialized traits)

Due to database access limitations, I developed a custom web scraping solution. The scraping was conducted ethically during nighttime hours with low bandwidth queries: 3-4 nights for text data, 3 additional nights for images (~4GB total). This approach produced a nearly complete and consistent dataset ready for analysis.

### Technical Stack

- **Languages**: Python, SQL
- **Core Libraries**: pandas, numpy, scipy, networkx, igraph
- **Statistical Modeling**: PyMC 5.x (Bayesian inference, MCMC sampling)
- **Visualization**: matplotlib, seaborn
- **Database**: SQLite for structured storage and joins
- **Environment**: Jupyter notebooks for reproducible analysis

### Data Pipeline

```
Raw Database → Cleaning → Relationship Extraction → Network Analysis → 
Geographic Enrichment → Master Dataset → Pedigree Reconstruction → Breeding Value Estimation
```

---

## Core Analysis Components

### Phase 1: Foundation Pipeline (Notebooks 01-05)

| Analysis Type | Method | Rationale | Key Limitations |
|---------------|--------|-----------|-----------------|
| **Data Cleaning** | IQR outlier detection, manual validation | Preserves integrity while removing impossible values | Some subjective decisions required |
| **Relationship Extraction** | Pattern matching on parentage strings | Only method available for unstructured text | Multiple parents complicate modeling |
| **Network Analysis** | Multiple centrality measures | Captures breeding influence from different perspectives | High density limits community detection |
| **Geographic Integration** | Region mapping via abbreviation codes | Enables climate/regional breeding analysis | Missing data for some hybridizers |

**Notebook Structure (Phase 1):**
1. **Data Exploration & Quality** (01): Statistical distributions, missing data analysis, database normalization
2. **Hybridizer Career Analysis** (02): Community trends and productivity patterns  
3. **Network Extraction & Analysis** (03): Parent-child relationship extraction and centrality calculations
4. **Regional Data Integration** (04): Geographic breeding pattern analysis
5. **Master Database Creation** (05): Comprehensive data fusion via SQL joins

---

### Phase 2: Advanced Analysis (Notebooks 06-07)

#### Notebook 06: Enhanced Pedigree Reconstruction (Private)

Addresses fundamental limitations of basic string matching through custom Abstract Syntax Tree (AST) parsing:

**Key Improvements:**
- **99.95% parsing success rate** across 101,446 varieties
- **Maternal/paternal differentiation**: Tracks pod vs. pollen parent roles for sex-specific lineage analysis
- **Multi-generational handling**: Resolves deeply nested crosses (e.g., `((A × B) × C) × (D × E)`)
- **Ambiguity resolution**: Distinct identity assignment for 13,042 unknown entries + 26,858 seedling entries to prevent network collapse
- **Network output**: 148,453 nodes, 200,583 directed edges with parental role attribution
- **Intermediate nodes**: Creates 20,836 synthetic cross nodes to preserve full pedigree hierarchy

**Why Private**: The parsing algorithms and data structures represent potential intellectual property for future applications. Implementation details remain private for IP considerations.

**Access**: Full implementation available to potential employers upon request during interview processes.

---

#### Notebook 07: Hierarchical Bayesian Breeding Value Estimation (Public)

Implements a Bayesian Animal Model using PyMC 5.x to estimate genetic merit (breeding values) across four horticultural traits: Scape Height, Bloom Size, Bud Count, and Branches.

**Model Architecture:**

$$Y = \mu + X\beta_{\text{environment}} + Za + \epsilon$$

- **Hierarchical Bayesian framework**: Decomposes phenotypic variation into genetic and environmental components
- **MCMC sampling**: Non-centered parameterization ensures efficient convergence (R-hat ≈ 1.00)
- **Fixed effects**: Accounts for Hybridizer (732 unique) and Region (36 unique) environmental influences
- **Genetic effects**: Simultaneous estimation of 3,627 unique parent breeding values
- **Sparse data handling**: Student-t likelihood for traits with <25% completeness to reduce outlier influence
- **Unknown Parent Groups (UPG)**: Temporal grouping by decade prevents artificial variance inflation from historical unknowns

**Quantitative Results:**

| Trait | Completeness | Heritability (h²) | Predictive R | Interpretation |
|-------|-------------|-------------------|--------------|----------------|
| **Bloom Size** | 82.9% | 0.538 ± 0.029 | 0.472 | Strong genetic control - selection highly effective |
| **Scape Height** | 99.7% | 0.345 ± 0.037 | 0.546 | Moderate heritability with strong predictability |
| **Branches** | 21.9% | 0.073 ± 0.094 | 0.497 | Unreliable - data sparsity limits inference |
| **Bud Count** | 22.1% | 0.106 ± 0.120 | 0.353 | Unreliable - data sparsity limits inference |

**Community Contribution:**
- Top 10 parents by breeding value published for each trait
- Example top performers: **Kindly Light** (Bloom Size BV: 8.54), **Lola Branham** (Scape Height BV: 36.38)
- Complete methodology documented for reproducibility

**Known Limitations:**
- Data sparsity for Bud Count/Branches reduces heritability estimate reliability
- A-matrix (additive relationship matrix) not yet implemented - would improve genetic covariance modeling
- Current implementation represents best-practice Bayesian methods given data constraints

---

## Key Findings

### Data Quality & Structure (Phase 1)

- **98%+ completeness** for core traits enables robust statistical analysis
- **Clean temporal span** (1763-2024) supports comprehensive trend analysis
- **Biological validation**: Branches and bud count correlation (0.61) confirms direct biological relationship

### Breeding Network Insights (Phase 1)

The analysis revealed that 1950s-1960s varieties dominate descendant counts not due to superior genetics, but because they represent the **foundation era** when systematic pedigree recording began. These early-recorded varieties had the longest time to infiltrate the breeding network, creating an artifact of documentation timing rather than genetic superiority.

**Network Structure:**
- Low density confirms strategic parent selection rather than random crossing
- Multiple centrality measures provide different perspectives on breeding influence
- Hierarchical breeding line structures with clear genetic connectors identified

### Community Evolution (Phase 1)

- **Peak Growth**: 2000s with 1,100+ new hybridizers
- **Current Decline**: 600 hybridizer net loss in 2020s  
- **Productivity Gains**: 22-24% efficiency increase among surviving hybridizers
- **Professionalization**: Transition from widespread hobby to specialized craft

### Regional Patterns (Phase 1)

Complete coverage across 15 ADS regions enables future climate adaptation and geographic breeding optimization studies.

---

### Pedigree Network Quality (Phase 2)

- **79,629 varieties** parsed into complete pedigree structures
- **Top genetic contributors** quantified: Ed Brown (489 offspring), Ida's Magic (466), J.T. Davis (368)
- **Gender-specific tracing**: Pod/pollen parent differentiation enables maternal vs. paternal lineage analysis
- **Complex cross resolution**: Multi-generational breeding strategies accurately captured

### Quantitative Genetics Analysis (Phase 2)

#### Heritability Estimates

The Bayesian Animal Model successfully partitioned genetic and environmental variance:
- **Bloom Size**: Highest heritability (h² = 0.54) confirms strong genetic control - selective breeding for this trait is highly effective
- **Scape Height**: Moderate heritability (h² = 0.35) with excellent predictive performance suggests both genetic and management factors contribute
- **Branches/Bud Count**: Low heritability estimates likely due to data sparsity rather than true biological patterns

#### Breeding Value Validation

Hold-out validation (2012+ varieties) demonstrates model predictive capability:
- Correlation between predicted and observed values ranges 0.35-0.55 across traits
- Strong performance despite sparse data confirms robust statistical framework
- Top-ranked parents identified with statistical confidence intervals

#### Methodological Insights

- **Unknown Parent Grouping**: Temporal UPG strategy successfully prevented genetic variance inflation
- **Student-t Likelihood**: Essential for sparse traits - stabilized variance estimates despite <25% data completeness
- **MCMC Convergence**: Non-centered parameterization achieved excellent diagnostics across 3,627 genetic parameters

---

## Impact & Applications

### For Data Scientists & Employers

- **Advanced Data Engineering**: Custom AST parser solving difficult data normalization challenges
- **Bayesian Statistical Modeling**: Hierarchical Animal Model with PyMC - demonstrates theoretical understanding and practical MCMC implementation
- **Sparse Data Techniques**: Student-t likelihood, Unknown Parent Grouping, non-centered parameterization
- **Quantitative Genetics**: Heritability estimation, breeding value prediction, variance decomposition
- **End-to-End Pipeline**: Data acquisition → cleaning → relationship extraction → statistical inference
- **Technical Rigor**: Honest limitation acknowledgment and validation frameworks

### For Plant Breeders & Geneticists

- **Breeding Value Rankings**: Top 10 parents by trait with statistical confidence intervals
- **Genetic vs. Environmental**: Quantified heritability reveals which traits respond to selection
- **Parent Selection Tool**: Breeding values enable prediction of offspring genetic potential
- **Evidence-Based Strategy**: Replace intuition with statistically rigorous genetic merit assessment

### For the Daylily Community

- **First Quantitative Genetic Analysis**: Pioneering application of Animal Models to ornamental horticulture
- **Actionable Results**: Top performers immediately usable for breeding decisions
- **Open Methodology**: Bayesian framework documented for community adoption and refinement
- **Data-Driven Culture**: Establishes foundation for evidence-based breeding practices

---

## Future Research Directions

### Statistical Model Enhancements

- **A-Matrix Integration**: Implement additive relationship matrix to properly model genetic covariance structure and improve breeding value accuracy
- **Multi-trait Models**: Simultaneous estimation across correlated traits for genetic correlation insights
- **Genomic Selection**: Integration with molecular marker data (future data collection)

### Data Quality Improvements

- **Trait Standardization**: Develop protocols for consistent measurement across regions
- **Dimensional Expansion**: Identify and document traits not previously recorded for genetic gain beyond current registration fields
- **Performance Metrics**: Systematic disease resistance and climate adaptation data collection
- **Validation Framework**: Field trial validation of breeding value predictions

### Analytical Extensions

- **Genetic Trend Analysis**: Quantify selection pressure and genetic gain over decades
- **Inbreeding Monitoring**: Pedigree-based inbreeding coefficients for diversity management  
- **Cross-Validation**: Regional hold-out sets to assess geographic generalization
- **Dominance Effects**: Expand from additive to additive + dominance genetic models (requires larger datasets)

---

## Project Setup

### Prerequisites

- Python 3.8+ 
- Jupyter Notebook/Lab
- SQLite3

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/drowsy-1/Daylily-Analytics.git
cd Daylily-Analytics
```

2. **Set up Python environment**  
It's recommended to use a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

### Running the Notebooks

After activating your virtual environment, start Jupyter:
```bash
jupyter notebook
```

Your browser will open automatically. If not, copy the URL shown in your terminal.

#### Notebook Execution Order

**Phase 1 (Complete Pipeline - Runnable):**
1. `01_data_exploration.ipynb` - Data quality assessment and cleaning
2. `02_hybridizer_analysis.ipynb` - Career trajectory and community trends
3. `03_network_analysis.ipynb` - Basic breeding relationship networks
4. `04_regional_data.ipynb` - Geographic pattern integration
5. `05_merge.ipynb` - Master database construction

**Phase 2 (Advanced Analysis):**
6. `06_pedigree_reconstruction` - Advanced AST parsing (not included in repository)
7. `07_breeding_values.ipynb` - Hierarchical Bayesian BV estimation ✓

**Important Notes:**
- Notebooks 01-05 can be run sequentially without dependencies on Phase 2
- Notebook 06 is a prerequisite for 07 but is not included in the public repository for IP considerations
- To run 07 independently, the enhanced pedigree network data from 06 is required
- Full codebase available to potential employers upon request

---

## Troubleshooting

If you encounter any issues:
- Ensure all dependencies are installed correctly: `pip install -r requirements.txt`
- Verify you're using Python 3.8+
- Try restarting the Jupyter kernel if you encounter memory issues
- Make sure to run all cells in each notebook in sequence
- For Phase 2 questions, note that Notebook 06 outputs are required for 07

---

## Repository Structure & Access

### Project Structure

```
Daylily-Analytics/
├── 01_data_exploration.ipynb      # EDA and data cleaning
├── 02_hybridizer_analysis.ipynb   # Career pattern analysis  
├── 03_network_analysis.ipynb      # Basic breeding networks
├── 04_regional_data.ipynb         # Geographic analysis
├── 05_merge.ipynb                 # Master database integration
├── 06_pedigree_reconstruction     # Advanced AST parsing (private)
├── 07_breeding_values.ipynb       # Bayesian BV estimation ✓
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

**Note:** Brackets indicate proprietary notebooks/data not included in public repository.

### Public Components

- **Data pipeline** (Notebooks 01-05): Complete data processing workflow from raw data to master database
- **Breeding value methodology** (Notebook 07): Bayesian implementation, model architecture, and top results
- **Documentation**: All analysis documentation and setup instructions
- **Database schema**: SQLite structure and table relationships

### Private Components

- **Advanced pedigree reconstruction algorithms** (Notebook 06)
- **Complete breeding value datasets**: Full parent rankings and predictions
- **Source data files**: Original scraped database and intermediate derivatives

**Rationale**: Advanced algorithms and complete datasets remain private for potential intellectual property considerations. Full codebase available to employers upon request during interview processes.

**Contact**: Available for discussion regarding employment opportunities or research collaboration.

---

## Current Status & Limitations

### Phase 1 (Complete)
- ✅ Data pipeline operational and documented
- ✅ Network analysis and regional integration complete
- ✅ Master database with 101,446 varieties ready for analysis

### Phase 2 (Functional with Known Limitations)
- ✅ Advanced pedigree reconstruction implemented (99.95% accuracy)
- ✅ Bayesian breeding value framework operational
- ⚠️ **Accuracy constraints**: Data sparsity limits prediction quality for some traits
- 📋 **Planned enhancement**: A-matrix integration to improve genetic covariance modeling

### Known Technical Limitations

**Data Quality:**
- Some traits have insufficient observations for robust prediction (Bud Count: 22.1%, Branches: 21.9%)
- Missing performance data for disease resistance and variety performance across regions
- Measurment protocols vary across time and between hybridizers 

**Statistical Model:**
- A-matrix (additive relationship matrix) not yet implemented
- Current BV estimates lack full genetic covariance structure correction
- Heritability estimates for sparse traits have wide confidence intervals

**Relationship Extraction:**
- 99.95% accuracy achieved, 53 edge cases remain unparsed
- Complex parentage (13+ parents) presents biological impossibilities requiring manual review

### Planned Improvements

- **A-Matrix Implementation**: Proper genetic covariance structure for improved BV accuracy (primary next step)
- **Data Collection Enhancement**: Expand trait coverage and measurement consistency
- **Validation Framework**: Cross-validation against field performance data
- **Multi-trait Models**: Correlated trait analysis for genetic correlations

---

## Data Structure

### Master Daylily Table (Post-Processing)

Total Records: 101,446

| Column Name | Data Type | Completeness | Description |
|-------------|-----------|--------------|-------------|
| url | string | 100.00% | ADS database URL |
| name | string | 100.00% | Variety name |
| hybridizer | string | 99.99% | Registrant/breeder |
| year | integer | 100.00% | Registration year |
| scape_height | float | 99.64% | Height in inches |
| bloom_size | float | 92.20% | Diameter in inches |
| bloom_season | string | 99.23% | Flowering period |
| ploidy | string | 98.27% | Diploid/Tetraploid |
| foliage_type | string | 97.73% | Evergreen/Dormant/Semi |
| bud_count | float | 52.37% | Buds per scape |
| branches | float | 52.47% | Branch count |
| parentage | string | 78.55% | Parent variety names |
| Region | float | 99.30% | ADS region code |
| Direct_Children | float | 74.97% | Immediate offspring count |
| Total_Descendants | float | 74.97% | All descendant count |
| PageRank | float | 74.97% | Network influence score |
| Betweenness_Centrality | float | 74.97% | Network bridging score |
| parents | string | 68.59% | Parsed parent list |
| children | string | 24.79% | Known offspring list |

---

## Recommendations

### For New Hybridizers
- Study foundation varieties from systematic pedigree recording era (1950s-1960s)
- Leverage breeding value rankings for strategic parent selection
- Focus on high-heritability traits (Bloom Size: h² = 0.54) for effective selection
- Plan for multi-year commitment with data-driven approaches from day one

### For Experienced Hybridizers  
- Identify underutilized high-value parents using breeding value estimates
- Evaluate long-term genetic contribution beyond immediate offspring success
- Consider transmitting ability (TA = BV/2) when planning crosses
- Integrate historical genetics with modern statistical methods

### For the Community
- Enhance database collection for specialized traits and performance metrics
- Implement collaborative breeding data sharing protocols
- Develop standardized measurement protocols across regions
- Support educational programs for statistical breeding methods
- Leverage multi-disipline insights to make more effective practices and outcomes

---

## Project Significance

This represents the first comprehensive quantitative genetic analysis of the American Daylily Society database. While ongoing enhancements (particularly A-matrix integration) will improve prediction accuracy, the current implementation provides actionable breeding intelligence through rigorous statistical methods.

**Key Contribution**: Transforms a horticultural database into a research-ready dataset with functioning breeding value prediction, demonstrating the power of combining modern data science techniques with traditional agricultural practices. The project provides a template for similar analyses in other plant breeding communities while advancing evidence-based breeding practices in ornamental horticulture.

---

## License

This project is available for portfolio review and educational purposes. Source code for public notebooks (01-05, 07) is provided under standard GitHub terms. Proprietary components (Notebook 06, complete datasets) are not included in this repository.

---

## Acknowledgments

- American Daylily Society for maintaining the comprehensive variety database
- The daylily breeding community for decades of meticulous record-keeping
- PyMC development team for excellent Bayesian modeling tools

---

**Author**: Trinity Love  
**Contact**: www.linkedin.com/in/trinity-love-a551011b3
**Repository**: https://github.com/drowsy-1/Daylily-Analytics