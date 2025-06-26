# Small_businesses_owners_in_US

*The primary objective of this assignment is to focus on business owners in the United States. It aims to achieve this by:*
  1-Examining some demographic characteristics of business owners, such as their age, income category, and the relationship between their debt and home value.
  2-Selecting high-variance features from the dataset relevant to this group.
  3-Creating a clustering model to segment these small business owners into distinct subgroups.
  4-Developing visualizations to highlight and communicate the differences observed between these identified subgroups.



1-Prepare Data - Import:
The initial step involves loading the SCFP2019.csv.gz dataset into a DataFrame df (supplied by WorldQuant university). This dataset originates from the Survey of Consumer Finances (SCF), which tracks financial, demographic, and opinion information about families in the U.S.


2-Prepare Data - Explore:
Identify Business Owners: The analysis begins by calculating the proportion of respondents in the df DataFrame who are business owners (identified using the "HBUS" column).
Income Distribution: A side-by-side bar chart is generated to compare the normalized frequency of income categories ("INCCAT") between business owners and non-business owners.
Home Value vs. Household Debt: A scatter plot is used to visualize the relationship between "HOUSES" (home value) and "DEBT" (household debt), with data points differentiated by business ownership. This allows for a comparison of this financial relationship between business owners and non-business owners.
Age Distribution: A histogram of the "AGE" column is created specifically for the subset of small business owners (df_small_biz) to analyze their age distribution, drawing a parallel to the age analysis of credit-fearful individuals in a previous section.
High Variance Features: To prepare for clustering, the trimmed variance (excluding the top and bottom 10% of observations to mitigate outlier effects) is calculated for features within the df_small_biz DataFrame. A horizontal bar chart is then created to visualize the top 10 features with the largest trimmed variance.

3-Prepare Data - Split:
A feature matrix X is constructed, comprising the five columns that exhibited the highest trimmed variance from the df_small_biz DataFrame. This matrix will serve as the input for the clustering model.


4-Build Model - Iterate:
K-Means Model Training: A for loop iterates to build and train multiple K-Means models, experimenting with n_clusters (number of clusters) ranging from 2 to 12.
Standardization: Each model is configured to include a StandardScaler, which standardizes the features so they all have a mean of 0 and a standard deviation of 1, crucial for effective clustering when features have different scales.
Performance Metrics: For each trained model, inertia and silhouette score are calculated. These metrics help evaluate the quality of the clustering. The random_state is set to 42 for reproducibility.
Optimal Cluster Determination:
An "elbow plot" (line plot of inertia vs. number of clusters) is generated. The goal is to identify the point where the decrease in inertia becomes less dramatic and the line flattens out, suggesting an optimal number of clusters.
A line plot of silhouette score vs. number of clusters is also created. A higher silhouette score indicates better-defined and separated clusters, helping to confirm the optimal number of clusters.


5-Communicate:
Final Model & Cluster Means: A final K-Means model is built and trained using the optimal number of clusters determined in the iteration phase. A DataFrame xgb is then created to contain the mean values of the selected features for each of the clusters.
Mean Feature Visualization: A side-by-side bar chart is generated from xgb, displaying the mean values of the features for each cluster. This visualization helps to understand the distinct characteristics and financial profiles of each subgroup of small business owners
