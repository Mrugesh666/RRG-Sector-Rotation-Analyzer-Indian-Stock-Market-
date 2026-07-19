# 📊 RRG Sector Rotation Analyzer (Indian Stock Market)

A professional **Relative Rotation Graph (RRG)** analyzer built using **HTML, JavaScript, Chart.js, and PapaParse** that helps traders and investors visualize **sector rotation** and analyze the relative strength of Indian stocks against the NIFTY benchmark.

The application calculates **RS Ratio**, **RS Momentum**, **Trend Score**, and a **Final Ranking Score** to determine where a stock or sector currently stands in the market cycle.

---

# Features

- Upload NSE stock master CSV
- Auto-complete stock search
- Relative Rotation Graph (RRG)
- Sector Rotation Analysis
- Compare stocks against NIFTY benchmark
- RS Ratio Calculation
- RS Momentum Calculation
- Trend Strength Analysis
- Final Composite Score
- Sector Filtering
- Interactive Zoom
- Local Browser Cache
- Top Performing Sector Ranking
- Market Quadrant Classification
- Responsive UI

---

# Screenshot

(Add your project screenshots here)

---

# Technologies Used

- HTML5
- CSS3
- JavaScript (ES6)
- Chart.js
- Chart.js Data Labels
- PapaParse
- Browser Local Storage

---

# Project Structure

```
Project
│
├── index.html
├── README.md
├── stock_master.csv
└── assets/
```

---

# How It Works

The application follows the standard Relative Rotation Graph (RRG) methodology.

## Step 1

Load stock price history.

↓

## Step 2

Load benchmark (NIFTY).

↓

## Step 3

Calculate Relative Strength.

↓

## Step 4

Normalize Relative Strength into RS Ratio.

↓

## Step 5

Calculate RS Momentum.

↓

## Step 6

Measure Trend Strength.

↓

## Step 7

Generate Final Composite Score.

↓

## Step 8

Plot Stock & Sector on RRG.

---

# Mathematical Methodology

## 1. Relative Strength (RS)

Measures how a stock performs compared to the benchmark.

\[
RS = \frac{StockPrice}{BenchmarkPrice} \times 100
\]

Where

- Higher RS = outperforming benchmark
- Lower RS = underperforming benchmark

---

## 2. Relative Strength Ratio (RS Ratio)

The raw Relative Strength values are standardized using a rolling mean and standard deviation.

### Step A

Rolling Average

\[
SMA_{RS} = \frac{\sum RS}{N}
\]

### Step B

Rolling Standard Deviation

\[
\sigma = \sqrt{\frac{\sum(RS-\mu)^2}{N}}
\]

### Step C

Normalized RS Ratio

\[
RSRatio = 100 + 2 \times \frac{RS-SMA}{StdDev}
\]

Interpretation

| RS Ratio | Meaning |
|-----------|----------|
| >100 | Strong Relative Strength |
| <100 | Weak Relative Strength |

---

## 3. RS Momentum

Measures how quickly RS Ratio is changing.

### Rate of Change

\[
ROC=\frac{RSRatio_{today}-RSRatio_{past}}{RSRatio_{past}}\times100
\]

Normalize ROC

\[
RSMomentum=100+2\times\frac{ROC-SMA(ROC)}{StdDev(ROC)}
\]

Interpretation

| Value | Meaning |
|---------|----------|
| >100 | Relative Strength is improving |
| <100 | Relative Strength is deteriorating |

---

## 4. Trend Strength

Trend Score combines two independent trend measurements.

### A. Linear Regression Slope

Measures overall direction of the trend.

Positive slope

→ Uptrend

Negative slope

→ Downtrend

---

### B. EMA Change

50-period Exponential Moving Average

EMA Formula

\[
EMA_t=(Price_t\times K)+(EMA_{t-1}\times(1-K))
\]

where

\[
K=\frac{2}{Period+1}
\]

EMA Percentage Change

\[
EMAChange=\frac{EMA_{Current}-EMA_{Previous}}{EMA_{Previous}}\times100
\]

---

### Final Trend Score

\[
TrendScore=(0.7\times Slope)+(0.3\times EMAChange)
\]

Reason for weighting:

- 70% Linear Regression Slope
- 30% EMA Trend

The slope represents the long-term trend, while EMA captures recent acceleration.

---

## 5. Final Composite Score

The application ranks every stock using three components.

\[
FinalScore=
0.4(RSRatio)+
0.3(RSMomentum)+
0.3(TrendScore)
\]

Weight Distribution

| Metric | Weight |
|---------|---------|
| RS Ratio | 40% |
| RS Momentum | 30% |
| Trend Score | 30% |

This weighting gives more importance to the current relative strength while still considering momentum and trend.

---

# RRG Quadrants

The graph is divided into four quadrants.

## 🟢 Leading

```
RS Ratio > 100
RS Momentum > 100
```

Characteristics

- Strong
- Improving
- Institutional buying
- Bullish

---

## 🔵 Improving

```
RS Ratio <100
RS Momentum >100
```

Characteristics

- Weak but improving
- Potential breakout
- Early trend reversal

---

## 🟡 Weakening

```
RS Ratio >100
RS Momentum <100
```

Characteristics

- Still strong
- Momentum slowing
- Profit booking likely

---

## 🔴 Lagging

```
RS Ratio <100
RS Momentum <100
```

Characteristics

- Weak
- Underperforming
- Avoid unless reversal appears

---

# Scoring Logic

```
Relative Strength
        │
        ▼
RS Ratio
        │
        ▼
RS Momentum
        │
        ▼
Trend Score
        │
        ▼
Final Score
        │
        ▼
Quadrant Classification
```

---

# Performance Optimizations

The application includes:

- Browser caching
- Stock cache
- Sector cache
- Lazy loading
- CSV parsing
- Auto-complete search
- Interactive chart rendering

---

# Future Improvements

- Live NSE Data
- Yahoo Finance API Integration
- Multiple Benchmark Support
- Volume Confirmation
- ADX Trend Strength
- Relative Volume
- Sector Heatmap
- Export Reports
- Watchlist
- Portfolio Tracking
- Historical Backtesting
- Multi-Timeframe RRG
- AI-Based Stock Ranking

---

# Disclaimer

This project is built purely for **educational and research purposes**.

The calculations are based on Relative Rotation Graph concepts and should **not be considered financial advice**.

Always perform your own research before making investment decisions.

---

# Author

**Mrugesh Bhatia**

Portfolio Manager | Quantitative Research | Financial Modeling | Relative Rotation Graph (RRG)

GitHub: *(Add your GitHub URL)*

LinkedIn: *(Add your LinkedIn URL)*

---

# License

This project is released under the MIT License.
