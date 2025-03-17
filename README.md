

# Algo_Backtrader

## Overview

Algo_Backtrader is a backtesting system using the **Backtrader** library with **mean-variance optimization** for portfolio rebalancing.

## Steps to Run

1. **Import Required Libraries**

   ```python
   import backtrader as bt
   import pandas as pd
   import numpy as np
   from cvxopt import matrix, solvers
   from datetime import datetime
   ```

2. **Define Strategy** (`MyStrategy`)

   - Implements **mean-variance optimization** using **CVXOPT**.
   - **Key Methods:**
     - `calculate_weights()`: Computes portfolio weights.
     - `reweight()`: Updates portfolio based on calculated weights.
     - `reweight_monthly()`: Rebalances on the 1st of each month.
     - `next()`: Calls `reweight_monthly()` and executes trades.

3. **Load Data**

   - Read stock price data:
     ```python
     df = pd.read_csv("data.csv", parse_dates=["date"])
     ```
   - Convert to Backtrader data feeds and add to `cerebro`.

4. **Set Up & Run Backtest**

   ```python
   cerebro = bt.Cerebro()
   cerebro.addstrategy(MyStrategy)
   cerebro.broker.setcash(1000000)
   cerebro.run()
   print("Final Portfolio Value:", cerebro.broker.getvalue())
   ```

5. **(Optional) Analyze & Plot**
   - Use `bt.analyzers` for performance metrics.
   - Generate strategy visualizations.

## Requirements

- Install dependencies:
  ```bash
  pip install backtrader cvxopt pandas numpy
  ```

---


