# Stock Liquidity & Bid-Ask Spread Analysis

## Project Overview

This project analyzes the determinants of bid-ask spreads across U.S. stocks and ETFs using Python-based regression analysis. The goal is to understand how stock price, trading volume, and market capitalization affect market liquidity and transaction costs.

The analysis focuses on whether average bid-ask spreads and relative spreads are better explained by price levels, trading volume, and market capitalization. The project also compares individual stocks with ETFs to evaluate which asset type has more stable liquidity characteristics.

---

## Research Questions

1. How does stock price affect average bid-ask spreads?
2. Does price explain relative spreads after normalizing by stock price?
3. How does trading volume affect liquidity and transaction costs?
4. Does market capitalization add explanatory power beyond trading volume?
5. Are ETF spreads more stable than individual stock spreads?

---

## Dataset

The original stock dataset contained 5,611 securities. After removing missing values and extreme outliers, the final cleaned stock dataset contained 5,521 securities.

Key variables used in the analysis:

| Variable | Description |
|---|---|
| `price` | Security price |
| `avg_sp` | Average bid-ask spread |
| `rel_sp` | Relative spread, calculated as spread divided by price |
| `adv` | Average daily trading volume |
| `adv_lvl` | Trading volume category: Low, Medium, High |
| `p_lvl` | Price category: LL, L, M, H, HH |
| `market_cap` | Market capitalization |

---

## Methodology

The project uses cross-sectional regression analysis to study the relationship between liquidity measures and explanatory variables.

Main regression models:

```text
avg_sp ~ price
rel_sp ~ price
avg_sp ~ p_lvl
avg_sp ~ adv_lvl - 1
rel_sp ~ adv_lvl - 1
avg_sp ~ adv_lvl + market_cap
```

The `-1` specification removes the intercept, allowing each volume-category coefficient to be interpreted directly as the average spread for that category.

---

## Regression Output Highlights

### Average Spread vs Stock Price

![Average Spread vs Price Regression](figures/regression_avg_sp_price.png)

Price explains approximately 57.3% of the variation in average bid-ask spreads. Higher-priced stocks generally have wider dollar spreads.

### Relative Spread vs Stock Price

![Relative Spread vs Price Regression](figures/regression_rel_sp_price.png)

After normalizing spread by price, the explanatory power of stock price falls sharply. This suggests relative spread is a cleaner liquidity measure across securities with different price levels.

### Average Spread by Trading Volume Level

![Average Spread by Volume Level](figures/regression_volume_levels.png)

Low-volume stocks have significantly wider spreads than high-volume stocks. This confirms that liquidity is a major determinant of transaction costs.

### Market Capitalization Model

![Volume and Market Cap Regression](figures/regression_marketcap.png)

Adding market capitalization only increases R² from 0.370 to 0.371, and the market cap coefficient is statistically insignificant. Trading volume remains the dominant explanatory variable.

---

## Key Findings

### 1. Stock Price Strongly Explains Absolute Spreads

The regression of average spread on price produced an R² of 0.573. This means price explains about 57.3% of the variation in average bid-ask spreads.

### 2. Relative Spread Removes Most Price Effects

The regression of relative spread on price produced an R² of only 0.012. After adjusting spreads by price, price has very little economic explanatory power.

### 3. Volume Is a Strong Predictor of Liquidity

For low-priced stocks, high-volume securities had the lowest average spreads, while low-volume securities had the highest average spreads.

| Volume Level | Average Spread |
|---|---:|
| High | $0.0117 |
| Medium | $0.0236 |
| Low | $0.0619 |

Low-volume stocks had spreads more than five times larger than high-volume stocks.

### 4. Market Capitalization Adds Minimal Value

Adding market capitalization to the volume model barely improved R² and produced an insignificant market-cap coefficient. This suggests market cap does not meaningfully improve the explanation of bid-ask spreads beyond trading volume.

### 5. ETFs Have More Stable Liquidity

ETFs showed tighter and more stable spreads than individual stocks. Individual stock spreads were more sensitive to changes in volume, while ETF spreads were less volatile across liquidity groups.

---

## Business Implications

### For Portfolio Managers

- High-volume securities help reduce execution costs.
- Liquidity should be considered when selecting securities for large trades.
- ETFs may provide more stable liquidity exposure than individual stocks.

### For Traders

- Low-volume securities can create significant hidden trading costs.
- Bid-ask spreads should be considered before entering large positions.
- Relative spread is a better comparison tool across different price levels.

### For Asset Managers

- Transaction cost analysis can improve portfolio construction and trade execution.
- Liquidity risk should be incorporated into security selection.
- ETFs may be more efficient vehicles when liquidity stability is important.

---

## Key Skills Demonstrated

### Financial Analysis

- Market microstructure analysis
- Liquidity measurement
- Bid-ask spread modeling
- Transaction cost analysis
- ETF vs equity market comparison

### Quantitative Methods

- Linear regression
- Cross-sectional analysis
- Statistical inference
- Hypothesis testing
- Model evaluation using R², F-statistics, and p-values

### Data Analytics

- Data cleaning
- Outlier detection
- Feature engineering
- Quantile-based categorization
- Exploratory data analysis

### Programming

- Python
- Pandas
- NumPy
- Statsmodels
- Matplotlib
- Jupyter Notebook

### Portfolio Management Applications

- Liquidity risk assessment
- Trading cost estimation
- Execution cost analysis
- Asset selection considerations

---

## Trading Cost Example

For a trade of 1,000,000 shares of a high-volume stock with an estimated average spread of $0.0117 per share:

```text
1,000,000 × $0.0117 = $11,700
```

This represents a lower-bound estimate of transaction costs before commissions, market impact, and price movement during execution.

---

## Repository Structure

```text
├── README.md
├── Project_4_Group_10_Chang_Wesley.ipynb
└── figures/
    ├── regression_avg_sp_price.png
    ├── regression_rel_sp_price.png
    ├── regression_volume_levels.png
    └── regression_marketcap.png
```

---

## How to Run

Install the required Python packages:

```bash
pip install pandas numpy matplotlib statsmodels jupyter
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
Project_4_Group_10_Chang_Wesley.ipynb
```

Run all cells to reproduce the analysis.

---

## Conclusion

The analysis shows that trading volume is a major determinant of liquidity and transaction costs. Stock price strongly explains absolute spreads, but relative spreads remove most of the price effect and provide a cleaner liquidity measure. Market capitalization adds little explanatory power once volume is considered. Compared with individual stocks, ETFs generally maintain tighter and more stable spreads.

Overall, this project demonstrates how regression analysis can be used to evaluate market liquidity, estimate trading costs, and support portfolio management decisions.

---

## Authors

- Wesley Chang
- Devansh Patel
- Anabella Orellana

Fordham University  
Master of Science in Finance
