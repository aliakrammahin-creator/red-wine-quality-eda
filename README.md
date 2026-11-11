# Red Wine Quality: Exploratory Data Analysis

I wanted to find out what actually separates a well-rated red wine from an average one, so I went through the classic Vinho Verde red wine dataset and looked at how its chemical properties relate to the quality score given by wine tasters.

This is one of my first data analysis projects. I'm learning Python and data analysis, and I wrote this up to practise the whole process: cleaning the data, exploring it, and explaining what I found.

## The question

**What physicochemical properties are associated with higher red wine quality?**

## The data

- **Source:** [UCI Machine Learning Repository, Wine Quality dataset](https://archive.ics.uci.edu/dataset/186/wine+quality) (Cortez et al., 2009)
- **Size:** 1,599 red wines and 12 columns. After removing 240 duplicate rows, 1,359 wines remain.
- **Inputs:** 11 lab measurements, including fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, sulfur dioxide, density, pH, sulphates and alcohol.
- **Output:** `quality`, a score from 0 to 10 given by tasters. In this data, scores range from 3 to 8.

There are no missing values, which made the cleaning step short.

## What I did

1. Checked the structure of the data, missing values and duplicates
2. Removed the 240 duplicate rows (they would have inflated counts and averages)
3. Checked how balanced the quality scores are
4. Looked at correlations between every feature and quality
5. Grouped wines into quality bands (poor, average, good) and alcohol bands (low, medium, high) to compare them
6. Plotted distributions and compared groups with box plots, a pair plot and scatter plots

## What I found

- **The data is imbalanced.** About 82% of wines are "average" (quality 5 or 6), 13.5% are "good" (7 and above) and only 4.6% are "poor" (4 and below). Only 10 wines scored a 3 and 17 scored an 8, so anything I say about the extremes rests on small samples.
- **Alcohol has the strongest link with quality** (correlation 0.48). Average alcohol rises from about 9.9% in quality 5 wines to about 11.5% in quality 7 wines.
- **Volatile acidity has the strongest negative link** (correlation -0.40). Its average falls steadily from 0.88 in quality 3 wines to 0.40 in quality 7 wines, so wines with more volatile acidity tend to score lower.
- **Sulphates (0.25) and citric acid (0.23)** have weaker positive relationships with quality.
- **Residual sugar and free sulfur dioxide** show almost no relationship with quality.

## Things to keep in mind

- Correlation is not causation. These patterns show association, not that changing one property will change the score.
- Quality is a taster's opinion, not a measured quantity.
- The correlations are modest (the strongest is 0.48), so no single feature predicts quality well on its own.
- I removed duplicates for simplicity. The lab measurements are rounded, so some of them may be genuinely different wines that happen to look identical.

## Next steps

- Check skew and outliers in columns like residual sugar and chlorides
- Try a simple model to predict quality, which would mean handling the class imbalance
- Repeat the analysis on the white wine dataset and compare

## Tools

Python, pandas, NumPy, Matplotlib, seaborn, Jupyter Notebook

## How to run it

1. Clone or download this repository
2. Install the libraries: `pip install pandas numpy matplotlib seaborn jupyter`
3. Open `red-wine-quality-eda.ipynb` in Jupyter and run the cells from top to bottom. The notebook loads the data straight from the UCI website, so you don't need to download it separately.

## Reference

Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). *Modeling wine preferences by data mining from physicochemical properties.* Decision Support Systems, 47(4), 547-553.

---

Feedback is welcome. If you spot something I got wrong or could explain better, please open an issue or message me.
