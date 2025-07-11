# Finacial_Investments_Analysis

# Algorithmic Trading & Portfolio Optimization

## Project Overview

In this project, undertaken for a Financial Information Systems course, I constructed and optimized a diversified investment portfolio. The primary objective was to build a portfolio of 8 instruments—spanning equities, fixed income, commodities, and currencies—that achieves a **Sharpe Ratio greater than 1.0** and a **Portfolio Beta less than or equal to 0.5** relative to the S&P 500 (SPY).

The analysis leverages technical trading strategies, including **Moving Average (MA) Crossovers** and **Bollinger Bands (BB)**, to enhance risk-adjusted returns. The final portfolio weights were determined using Mean-Variance Optimization (MVO) through a Monte Carlo simulation to identify the efficient frontier.

## Key Features

-   **Strategy Implementation:** Python functions for MA Crossover (with flat and short signals) and Bollinger Band trading strategies.
-   **Data Analysis:** Analysis of historical price data for 12 different financial instruments from December 31, 1999, to December 31, 2018.
-   **Sensitivity Analysis:** Determination of optimal lookback parameters (`fastWindow`, `slowWindow`, `bbWindow`) to maximize strategy effectiveness.
-   **Portfolio Construction:** Strategic selection of 8 instruments and their corresponding trading strategies based on performance and correlation.
-   **Mean-Variance Optimization:** Monte Carlo simulation (5,000 portfolios) to identify the Minimum Volatility and Maximum Sharpe Ratio portfolios.
-   **Performance & Risk Analysis:** In-depth evaluation of the final portfolio's Sharpe Ratio, Beta, Max Drawdown, and comparison against benchmark portfolios.

## Methodology & Workflow

1.  **Strategy Implementation:** A wrapper function, `runMovingAverageAndBB`, was created to apply MA and BB strategies to any given instrument's price data.
2.  **Data Loading & Preparation:** The `PricesForProject.csv` dataset, containing daily prices for 12 instruments, was loaded and prepared for analysis.
3.  **Parameter & Strategy Selection:**
    -   A sensitivity analysis was performed to find the optimal parameters that work best across the selected instruments.
        -   **Fast MA Window:** 87 days
        -   **Slow MA Window:** 130 days
        -   **Bollinger Band Window:** 45 days
        -   **Bollinger Band Stdev:** 2.0
    -   Based on individual Sharpe Ratios and diversification potential, the following 8 strategies were chosen for the portfolio:
        - `AAPL-MAFlat`
        - `EXC-BMK-MA`
        - `FBNDX-MAShort`
        - `GBP-MAShort`
        - `GE-MAShort`
        - `INTC-BB`
        - `PFE-BB`
        - `SPGSCI-MAFlat`
4.  **Correlation Analysis:** The correlation matrix of the chosen strategies was computed to ensure the portfolio benefits from diversification. The matrix confirmed a low-to-moderate correlation structure, justifying the strategy selection.
5.  **Mean-Variance Optimization (MVO):** A 5,000-step Monte Carlo simulation was run to plot the efficient frontier and identify the optimal portfolio weights for both Minimum Volatility and Maximum Sharpe Ratio.

## Core Findings & Results

The optimization process successfully produced a portfolio that met all project constraints.

**Maximum Sharpe Ratio Portfolio Performance:**
| Metric | Value |
| :--- | :--- |
| **Sharpe Ratio** | **1.45** |
| **Beta (vs. SPY)** | **0.057** |
| Annualized Return | 6.26% |
| Annualized Risk (Volatility)| 4.31% |
| Max Drawdown | -7.23% |

**Optimal Portfolio Weights (Maximum Sharpe):**
| Instrument | Weight |
| :--- | :--- |
| FBNDX-MAShort | 43.06% |
| GBP-MAShort | 16.01% |
| INTC-BB | 13.11% |
| PFE-BB | 12.26% |
| AAPL-MAFlat | 8.54% |
| EXC-BMK-MA | 2.39% |
| GE-MAShort | 2.36% |
| SPGSCI-MAFlat | 2.27% |

The final portfolio significantly outperforms an equal-weighted portfolio (Sharpe: 1.27) and all variant benchmark portfolios (BMK-only, MAFlat-only, BB-only), showcasing the power of combining optimized strategies with MVO. The extremely low Beta of 0.057 indicates that the portfolio's returns have a very weak correlation with the broader market, making it resilient to market-wide fluctuations.

## Visualizations

The Jupyter notebook generates two key visualizations:

1.  **Correlation Matrix:** A heatmap illustrating the correlation between all potential trading strategies.
2.  **Efficient Frontier:** A scatter plot of the 5,000 simulated portfolios, highlighting the risk-return trade-off and marking the Minimum Volatility and Maximum Sharpe Ratio portfolios.

## Technical Stack

-   **Python 3**
-   **Libraries:**
    -   `pandas`
    -   `numpy`
    -   `matplotlib`
    -   `seaborn`
    -   `scipy`
    -   `itertools`
