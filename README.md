# Ames Housing Dataset: Exploratory Data Analysis
<img src="https://cdn.prod.website-files.com/62d64ff33158a9a2aba96531/63e22d9d29cb7279ce51bdae_Real%20Estate%20Data%20Analytics%20Thumbnail%20(1).svg" width="600"/>

## Project Overview
This repository contains a comprehensive exploratory data analysis (EDA) of the Ames Housing dataset. The analysis examines residential property characteristics in Ames, Iowa, to uncover patterns, relationships, and insights about factors influencing home values.

## Dataset Description
The Ames Housing dataset provides detailed information on residential properties in Ames, Iowa:
- 1,460 observations (properties)
- 81 explanatory variables (features)
- Mix of categorical, ordinal, and numerical data types

### Key Feature Categories:
- **Property Characteristics**: Living area, lot size, neighborhood, zoning, building style  
- **Quality Metrics**: Overall quality and condition ratings (scale 1–10)  
- **Interior Features**: Bedrooms, bathrooms, kitchen quality, basement details  
- **Exterior Characteristics**: Exterior materials, roof style, masonry veneer, porches  
- **Garage Information**: Type, size, quality, capacity  
- **Land Attributes**: Lot configuration, shape, topography  
- **Temporal Data**: Year built, remodeled, and sold  

### Target Variable:
- **SalePrice**: The property's sale price in dollars  

## Exploratory Data Analysis

### 1. Data Understanding
<img src="https://images.ctfassets.net/lzny33ho1g45/5FH7fLMZABa2N5O25hniRV/e980968e81b8bcda2bebffc98736e47a/Data_analysis_hero.jpg?w=1520&fm=jpg&q=31&fit=thumb&h=760" width="600"/>

- Dataset structure and composition  
- Feature types and distributions  
- Summary statistics for numerical variables  
- Frequency distributions for categorical variables  

### 2. Boxplot of Top 6 Correlated Features
<img src="https://github.com/Shivadzn/eda-house-price-prediction/blob/main/Eda_analysis/Images/Boxplot%20of%20top%206%20correlated%20features.png?raw=true" width="600"/>

- **OverallQual**: Concentrated at higher values (median ~7); few lower outliers  
- **GrLivArea**: Right-skewed; median around 1500 sq ft; several large outliers  
- **GarageCars**: Median 2 cars; concentrated at 1, 2, and 3; few 0 and 4  
- **GarageArea**: Right-skewed; median ~480 sq ft; several large outliers  
- **TotalBsmtSF**: Right-skewed; many with 0 sq ft; median ~850 sq ft for those with basements; large outliers  
- **1stFlrSF**: Right-skewed; median ~1100 sq ft; large outliers  

### 3. Missing Value Analysis
<img src="Eda_analysis/Images/missing_values.png" width="600"/>

- **PoolQC**, **MiscFeature**, **Alley**, and **Fence** have >80% missing values  
- **MasVnrType** and **FireplaceQu** have significant missing values  
- **LotFrontage**, **GarageYrBlt**, and **BsmtExposure** have partial missing data  
- **Electrical** and **MasVnrArea** have minimal to no missing values  

### 4. Distribution of SalePrice After Normalization
<img src="https://github.com/Shivadzn/eda-house-price-prediction/blob/main/Eda_analysis/Images/Distribution%20of%20saleprice%20vs%20distribution%20of%20log%20transformed%20saleprice.png?raw=true" width="600"/>

- Original SalePrice is right-skewed  
- Log-transformed SalePrice approximates normal distribution  
- Transformation improves linear model assumptions and performance  

### 5. Correlation Analysis
<img src="https://github.com/Shivadzn/eda-house-price-prediction/blob/main/Eda_analysis/Images/Correlation%20heatmap%20of%20top%20features.png?raw=true" width="600"/>

- **SalePrice** has high correlation with:  
  - **OverallQual** (0.79)  
  - **GrLivArea** (0.71)  
  - **GarageCars** (0.64)  
  - **GarageArea** (0.62)  
  - **TotalBsmtSF** (0.61)  
  - **1stFlrSF** (0.61)  
  - **FullBath** (0.56)  
  - **TotRmsAbvGrd** (0.53)  
  - **YearBuilt** (0.52)  
  - **YearRemodAdd** (0.51)  
- High multicollinearity detected between:  
  - **GarageCars** and **GarageArea** (0.88)  
  - **TotalBsmtSF** and **1stFlrSF** (0.82)  

### 6. SalePrice vs Top 9 Correlated Features
<img src="https://github.com/Shivadzn/eda-house-price-prediction/blob/main/Eda_analysis/Images/SalePrice%20vs%20top%209%20correlated%20features.png?raw=true" width="600"/>

- **OverallQual**: Strong positive trend; stepwise due to discrete quality ratings  
- **GrLivArea**: Linear increase in SalePrice with larger living area  
- **GarageCars**: Distinct bands; SalePrice rises with garage capacity  
- **GarageArea**: Positive trend; more scattered than GarageCars  
- **TotalBsmtSF**: Larger basements generally lead to higher SalePrice  
- **1stFlrSF**: Positive linear relationship  
- **FullBath**: SalePrice increases with number of full baths  
- **TotRmsAbvGrd**: More rooms above ground → higher SalePrice  
- **YearBuilt**: Newer homes tend to sell for more  

### 7. Key Insights and Findings
- Identified strongest predictors of SalePrice  
- Found pricing anomalies and outliers  
- Detected importance of quality and living area  
- Suggested features for transformation and selection  

## Key EDA Findings
- **High correlation** of quality, area, and garage metrics with price  
- **Log transformation** necessary for normalized SalePrice  
- **Missing data** requires tailored imputation strategies  
- **Temporal trends** show steady increase in home values  
- **Neighborhood-level variation** significantly impacts price  

## Technologies Used
- **Python Libraries**:  
  - `pandas`, `numpy` – data wrangling  
  - `matplotlib`, `seaborn` – visualization  
  - `scipy` – statistical tests
    
## Repository Structure
```
├── data/
│   └── ames_housing.csv
├── notebooks/
│   └── ames_housing_eda.ipynb 
├── images/                
│   ├── correlation_heatmap.png
│   ├── price_distribution.png
│   └── ...
├── README.md         
└── requirements.txt     
```

## Getting Started

### Prerequisites
- Python 3.8+
- Required packages: pandas, numpy, matplotlib, seaborn

### Installation
1. Clone this repository
```bash
https://github.com/Shivadzn/eda-house-price-prediction.git
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Run the Jupyter notebook
```bash
jupyter notebook notebooks/ames_housing_eda.ipynb
```

## Insights for Future Modeling
The EDA reveals several key considerations for subsequent predictive modeling:
- Logarithmic transformation recommended for the target variable
- Feature engineering opportunities identified for several variables
- Potential feature selection strategy based on correlation analysis
- Data preprocessing steps needed before modeling

## Contact
- **Name**: [Shiva]
- **Email**: [shivajaiswaldzn@gmail.com]
- **GitHub**: [https://github.com/Shivadzn]
