# Daylily Breeding Analysis - Simplified 4-Week Plan

## Goal: Identify varieties with highest breeding values for trait improvement

**Trait Weighting:** Branches (40%) > Height (30%) > Bloom Size (20%) > Bud Count (10%)

---

## **PART 1: Foundation**

### Notebook 1: Data Exploration & Visualization (`01_data_exploration.ipynb`)

- [x] Load cleaned data and explore basic statistics
- [x] Identify data quality issues or patterns (attempted to rectify data issues in cleaning)
- [x] Create trait distribution visualizations
- [x] Make correlation heatmap between all 4 traits
- [X] Generate summary statistics tables


### Notebook 2: Hybridizer Career Analysis (`02_hybridizer_analysis.ipynb`)

- [x] Extract hybridizer career spans (first/last introduction years)
- [x] Calculate varieties per hybridizer over time
- [x] Plot hybridizer productivity trends by decade
- [x] Identify most prolific hybridizers
- [x] Measure number of unique hybridizers by year
- [x] Identify most prolific hybridizer by num of intros per year
- [x] Meausure average number of introduction per hybridizer by year and decade

### Notebook 2.5 **[STRETCH]** : Visualize Trait values Over Time (`02_5_visualize_traits.ipynb`)

- [ ] Visulaize trait distributions over time 

**Part 1 Output:** Clean data understanding + hybridizer insights


---

## **Part 2: Breeding Values (CORE DELIVERABLE)**

### Notebook 3.0: Network Extraction (`03_0_network_extraction.ipynb`)

- [x] extract parent-child relationships(not published)

### Notebook 3: Network Analysis (`03_network_analysis.ipynb`)

- [x] Calculate centrality measures (PageRank, betweenness, degree, katz)
- [0] Combine network influence with breeding values?
- [ ] **[STRETCH]** Add PCA analysis of trait relationships
- [0] Identify "bridge varieties" connecting breeding lines (decided community detection wasn't as useful given structure and inbreeding)

### Notebook 4: Regional Data (`04_regional_data.ipynb`)

- [x] import and read in regional data for hybridizers

### Notebook 5: Merging Data (`05_Merge.ipynb`)

- [x] Combine all generated tables into a master table
- [x] Use 3 SQL merges
- [x] Parse Parent Child Relationships table to add parents and offspring columns
- [x] Save and export master table 

### Project Polish

- [ ] Clean up all notebook code and add documentation
- [ ] Create comprehensive README with setup instructions
- [ ] Add requirements.txt file
- [ ] Write project summary and insights
- [ ] **[STRETCH]** Create simple interactive dashboard

--- **END OF CURRENT PROGRESS** ---

### Notebook 8: Statistical Breeding Values (`08_breeding_values.ipynb`)

- [ ] Calculate population means for each trait
- [ ] For each parent: measure offspring trait improvement(change) vs. population/+ parent
- [ ] Calculate breeding values using regression methods (build on your existing work)
- [ ] Apply custom trait weights (40% branches, 30% height, 20% bloom, 10% buds) - (for my specific goals)
- [ ] Create composite breeding value ranking
- [ ] Export ranked list of varieties for breeding recommendations
- [ ] Combine network influence with breeding values?


**Part 2 Output:** Ranked list of best breeding varieties

---

## **PART 3: Analysis & Recommendations**

### Notebook 5: Breeding Recommendations (`09_recommendations.ipynb`)

- [ ] Create final ranked breeding lists:
  - Top 25 overall varieties (composite breeding value)
  - Top 10 for each individual trait
  - "Sleeper" varieties (high breeding value, low use)
- [ ] Generate actionable breeding advice
- [ ] **[STRETCH]** Simple cross recommendations (high × high value pairings)

**Part 3 Output:** Final breeding recommendations

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
- [x] atleast 3 unique graphs and visualizations 
- [x] SQLite database with multiple tables 
- [x] SQL joins between tables
- [x] 3 different visualization types
- [ ] 3+ custom functions with type hints and docstrings
- [x] Feature engineering (breeding values) (went with centrality)
- [x] Clean, organized code structure

### **Career Portfolio Goals:**
- [ ] Actionable breeding variety rankings
- [x] Novel insights not available elsewhere
- [ ] Professional documentation and presentation
- [ ] Demonstrates advanced statistical methods

### **Community Value:**
- [ ] Breeding recommendations any daylily enthusiast can use
- [ ] Methodology others can replicate and extend
- [ ] Queryable database for future breeding decisions

---
