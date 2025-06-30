# Daylily Breeding Analysis - Simplified 4-Week Plan

## Goal: Identify varieties with highest breeding values for trait improvement

**Trait Weighting:** Branches (40%) > Height (30%) > Bloom Size (20%) > Bud Count (10%)

---

## **WEEK 1: Foundation**

### Notebook 1: Data Exploration & Visualization (`01_data_exploration.ipynb`)
**Since cleaning/database is complete, focus on:**

- [ ] Load cleaned data and explore basic statistics
- [ ] Create trait distribution visualizations
- [ ] Make correlation heatmap between all 4 traits
- [ ] Plot trait completeness by year/hybridizer
- [ ] Generate summary statistics tables
- [ ] Identify data quality issues or patterns

### Notebook 2: Hybridizer Career Analysis (`02_hybridizer_analysis.ipynb`)

- [ ] Extract hybridizer career spans (first/last introduction years)
- [ ] Calculate varieties per hybridizer over time
- [ ] Plot hybridizer productivity trends by decade
- [ ] Identify most prolific hybridizers
- [ ] Analyze trait improvement patterns by era

**Week 1 Output:** Clean data understanding + hybridizer insights

---

## **WEEK 2: Breeding Values (CORE DELIVERABLE)**

### Notebook 3: Statistical Breeding Values (`03_breeding_values.ipynb`)

- [ ] Build parent-child relationship dataframe
- [ ] Calculate population means for each trait
- [ ] For each parent: measure offspring trait improvement(change) vs. population/+ parent
- [ ] Calculate breeding values using regression methods (build on your existing work)
- [ ] Apply custom trait weights (40% branches, 30% height, 20% bloom, 10% buds) - (for my specific goals)
- [ ] Create composite breeding value ranking
- [ ] Export ranked list of varieties for breeding recommendations

### Notebook 4: Network Analysis (`04_network_analysis.ipynb`)

- [ ] Create network graph object from parent-child relationships
- [ ] Calculate centrality measures (PageRank, betweenness, degree, katz)
- [ ] Combine network influence with breeding values?
- [ ] **[STRETCH]** Add PCA analysis of trait relationships
- [ ] Identify "bridge varieties" connecting breeding lines

**Week 2 Output:** Ranked list of best breeding varieties

---

## **WEEK 3: Analysis & Recommendations**

### Notebook 5: Breeding Recommendations (`05_recommendations.ipynb`)

- [ ] Create final ranked breeding lists:
  - Top 25 overall varieties (composite breeding value)
  - Top 10 for each individual trait
  - "Sleeper" varieties (high breeding value, low use)
- [ ] Generate actionable breeding advice
- [ ] **[STRETCH]** Simple cross recommendations (high × high value pairings)

### Required Visualizations (3 different types):
- [ ] **Scatter plot:** Breeding value vs. network centrality
- [ ] **Heatmap:** Trait correlations or breeding value matrix
- [ ] **Network plot:** Key breeding varieties and connections

**Week 3 Output:** Final breeding recommendations

---

## **WEEK 4: Integration & Polish**

### Notebook 6: Database Integration (`06_database_integration.ipynb`)

- [ ] Join breeding values back to main varieties table
- [ ] Create final master dataset with all metrics
- [ ] Demonstrate SQL joins between tables (capstone requirement)
- [ ] Export final breeding database

### Project Polish

- [ ] Clean up all notebook code and add documentation
- [ ] Create comprehensive README with setup instructions
- [ ] Add requirements.txt file
- [ ] Write project summary and insights
- [ ] **[STRETCH]** Create simple interactive dashboard

**Week 4 Output:** Complete, professional project

---

## **Core Functions to Build (Capstone Requirements)**

```python
def calculate_breeding_value(parent_name: str, trait: str, offspring_df: pd.DataFrame) -> float:
    """Calculate breeding value for a parent-trait combination"""

def create_composite_index(breeding_values: dict, weights: dict) -> float:
    """Combine trait breeding values using custom weights"""

def extract_parent_relationships(parentage_series: pd.Series) -> pd.DataFrame:
    """Parse parentage strings into parent-child relationships"""
```

---

## **Stretch Goals (If Time Permits)**

### **Week 2 Additions:**
- [ ] PCA analysis of variety relationships
- [ ] Community detection in breeding networks

### **Week 3 Additions:**
- [ ] Advanced cross recommendations
- [ ] Heterosis prediction analysis

### **Week 4 Additions:**
- [ ] Public interactive dashboard
- [ ] Additional visualizations (3D plots, interactive networks)

---

## **Success Checklist**

### **Minimum Viable Project (Capstone Requirements):**
- [ ] atleast 3 unique graphs and visualizations 
- [ ] SQLite database with multiple tables 
- [ ] SQL joins between tables
- [ ] 3 different visualization types
- [ ] 3+ custom functions with type hints and docstrings
- [ ] Feature engineering (breeding values)
- [ ] Clean, organized code structure

### **Career Portfolio Goals:**
- [ ] Actionable breeding variety rankings
- [ ] Novel insights not available elsewhere
- [ ] Professional documentation and presentation
- [ ] Demonstrates advanced statistical methods

### **Community Value:**
- [ ] Breeding recommendations any daylily enthusiast can use
- [ ] Methodology others can replicate and extend
- [ ] Queryable database for future breeding decisions

---

## **Daily Workflow**
- **Days 1-2:** Complete Week 1 notebooks
- **Days 3-5:** Core breeding value analysis (Week 2)
- **Days 6-8:** Network analysis and recommendations (Week 2-3)
- **Days 9-11:** Final recommendations and visualizations (Week 3)
- **Days 12-14:** Integration and polish (Week 4)
- **Days 15-21:** Buffer week for stretch goals and refinement
