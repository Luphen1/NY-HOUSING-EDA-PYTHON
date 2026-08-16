# NY-HOUSING-EDA-PYTHON



Dataset contains prices of New York houses, providing valuable insights into the real estate market in the region. It includes field such as broker titles, house types, prices, number of bedrooms and bathrooms, property square footage, addresses, state, administrative and local areas, street names, and geographical coordinates.




### New York Housing Market — Exploratory Data Analysis(EDA)

Exploratory data analysis of the New York housing
market, examining price, size, and location patterns
across 4,587 property listings. Built as part of IU
International University of Applied Sciences'
DLBDSEDAV01 (Exploratory Data Analysis and
Visualization) coursework.


### Project Overview
This project explores what drives housing value in
New York City using statistical and visual EDA
techniques. The analysis covers:
Central tendency and spread (mean, median,
mode, variance, standard deviation) across price,
size, and room-count variables
Outlier detection and treatment using the IQR
method
Distribution shape and skewness, before and after
outlier treatment
Covariance and correlation between price,
property size, bedrooms, and bathrooms
A self-engineered 
PRICE_PER_SQFT
 feature to
normalize value across differently sized
properties
Geographic value concentration by sublocality


### Data Source
Dataset: New York Housing Market [https://www.kaggle.com/datasets/nelgiriyewithana/new-york-housing-market](kaggle)
Size: 4,801 listings (4,587 after removing 214
duplicates)
Key features:
PRICE 
, 
BEDS 
, 
TYPE 
, 
BATH 
, 
SUBLOCALITY 
, 
PROPERTYSQFT 
,
LOCALITY 
, 
LATITUDE 
,
LONGITUDE


### Tools
Language: Python
Libraries: Pandas, NumPy, Matplotlib, Seaborn
Environment: Jupyter Notebook


### Data Cleaning & Preparation
Removed 214 duplicate records
Verified no missing values across all columns
Identified outliers visually via boxplots, then
treated using the IQR method (values capped, not
deleted, at Q1 − 1.5×IQR and Q3 + 1.5×IQR)
Column
Values Capped
PRICE
BEDS
528
218
BATH
PROPERTYSQFT
108
374
Capping was chosen over deletion to preserve sample
size while limiting the influence of extreme values —
high-end listings represent a real market segment, not
noise, so removing them outright would discard
genuine information rather than simply moderating its
statistical influence.


### Key Insights
1. Price remains right-skewed even after treatment.
PRICE's mean ($1,144,499.90) sits well above its
median ($825,000), and skewness dropped from
65.35 (raw) to 1.06 (capped) — a >60-fold reduction
that confirms a small number of high-end listings
dominate the raw distribution.
2. Bathroom count predicts price more strongly than
square footage. Correlation with PRICE: BATH (0.630)
> PROPERTYSQFT (0.574) > BEDS (0.464). This is
counterintuitive — square footage is usually assumed
to dominate — and suggests bathroom count may act
as a proxy for build quality or property tier rather than
being purely a size signal.
3. Location drives per-square-foot value more than
any single structural feature. Manhattan
($1,220.58/sqft) and Dumbo ($1,200.54/sqft) lead the
market by a wide margin, with a clear drop-off to the
rest of the top 10 (roughly $530–$820/sqft) —
indicating concentrated, location-specific premiums
rather than a gradual citywide gradient.
4. Engineered features inherit — and can compound
—skew. The self-engineered 
PRICE_PER_SQFT
 metric
(mean $607.87, median $500.84) showed slightly
higher skewness (1.29) than PRICE itself (1.06), since
it's a ratio of two already right-skewed variables.



### Visualizations
Figure
Description
Boxplots
(before/after)
Distribution
histograms + KDE
Outlier presence and the
effect of IQR capping
Shape and skewness of
PRICE, PROPERTYSQFT,
BEDS, BATH,
PRICE_PER_SQFT
Figure
Description
Correlation heatmap
Pairplot
Relationship strength
across all five numeric
variables
Scatter:
PRICE_PER_SQFT vs.
BATH
House type /
bedroom / bathroom
distributions
Pairwise relationship
shapes beyond single
coefficients
Follow-up visualization on
the correlation finding
Categorical and count
based context
Sublocality bar chart
Top 10 areas by median
price per square foot


### Methodology Notes
Correlation over covariance for comparison:
covariance values aren't comparable across
variable pairs measured in different units (e.g.
PRICE in millions vs. BATH as a small count), so
correlation — which standardizes this — was used
for relationship-strength comparisons instead.
A caveat on 
PRICE_PER_SQFT correlations: since
this feature is mathematically derived from
PRICE
 and 
PROPERTYSQFT 
, its correlation with
those two columns partly reflects that built-in
relationship rather than an independent market
finding. Its correlations with 
BEDS
 and 
remain genuinely informative.


### References
BATH
Anscombe, F. J. (1973). Graphs in statistical
analysis. The American Statistician, 27(1), 17–21.
Cleveland, W. S., & McGill, R. (1984). Graphical
perception: Theory, experimentation, and
application to the development of graphical
methods. Journal of the American Statistical
Association, 79(387), 531–554.
Few, S. (2009). Now You See It: Simple
Visualization Techniques for Quantitative Analysis.
Analytics Press.
Healy, K. (2018). Data Visualization: A Practical
Introduction. Princeton University Press.
Nelgiriyewithana, N. (2024). New York Housing
Market [Data set]. Kaggle.
Tukey, J. W. (1977). Exploratory Data Analysis.
Addison-Wesley.

dataset
└── README.md                  # This file
