# Trader Performance vs Market Sentiment  
Primetrade.ai – Data Science Intern Round 0 Assignment  

## Objective

This project analyzes how Bitcoin market sentiment (Fear/Greed regimes) relates to trader behavior and performance on Hyperliquid.

The goal is to:
- Identify regime-level performance patterns
- Analyze behavioral shifts across sentiment regimes
- Segment traders based on structural characteristics
- Propose actionable strategy rules

---

## Datasets

1. **Bitcoin Fear & Greed Index**
   - Date
   - Classification (Extreme Fear, Fear, Neutral, Greed, Extreme Greed)

2. **Historical Trader Data (Hyperliquid)**
   - Account
   - Timestamp IST
   - Size USD
   - Closed PnL
   - Trade metadata

Trades were aggregated at daily level and aligned with sentiment classification.

---

## Methodology

### 1. Data Preparation
- Converted timestamps to daily level
- Removed duplicates and invalid rows
- Merged trade data with sentiment regime on date

### 2. Feature Engineering
- Daily cumulative PnL
- Win rate
- Volatility (PnL standard deviation)
- Drawdown proxy
- Trade frequency per account
- Risk-adjusted return (mean / std)

### 3. Regime-Level Analysis
For each sentiment regime:
- Mean and median PnL
- Volatility
- Win rate
- Average position size
- Risk-adjusted return

### 4. Trader Segmentation
Traders were segmented into:
- Frequent vs Infrequent traders
- High vs Low average PnL traders
- Consistent vs Inconsistent traders (based on volatility)

Performance was compared across sentiment regimes for each segment.

### 5. Predictive Modeling (Exploratory)
A Random Forest classifier was trained using:
- Position size
- Sentiment indicator

The model evaluates short-term predictive power of sentiment and exposure.

---

## Key Findings

1. **Extreme Greed exhibits the highest risk-adjusted return**, indicating superior reward efficiency relative to volatility.

2. **Infrequent traders materially outperform frequent traders**, particularly during Fear regimes, suggesting overtrading reduces performance.

3. **Position size increases during Fear regimes**, indicating elevated exposure during uncertainty.

4. Profitability appears driven more by volatility tolerance than strict consistency, as inconsistent traders generate higher mean returns.

---

## Strategy Recommendations

1. Limit trade frequency during Fear regimes, as infrequent traders demonstrate superior performance.

2. Allocate incremental capital during Extreme Greed regimes where risk-adjusted return is highest, while enforcing volatility controls.

3. Monitor position sizing during Fear periods to prevent excessive risk concentration.

---

## Model Results

- Accuracy: ~60%
- Feature importance indicates position size is a stronger predictor than sentiment alone.
- Results suggest structural behavior plays a larger role than short-term sentiment signals.

---

## How to Run

1. Place both CSV files in the root directory:
   - `fear_greed_index.csv`
   - `historical_data.csv`

2. Open the notebook:
