# BTC_USDT_Trading_Model
Algorithmic Trading Model Development for BTC/USDT Crypto Market. Crafting models that outperform benchmarks, balancing returns and risk management in the dynamic BTC/USDT market and **generating 448% return along with the max drawdown of 6.28%**.

# Dataset:
The original data ```btc_4h``` used in this project is historical BTC/USDT 4hrs data (January 1, 2018 to January 31, 2022).
![newplot (2)](https://github.com/A-SOLO/BTC_USDT_Trading_Model/assets/78963312/9a71c8e9-edc4-4631-860d-ae054bf30025)

# Preprocessing:
- Feature Selection: The ‘opening price’ feature from the BTC/USDT dataset is used in training and testing the machine learning model.
- Sequence ceartion: Considering the last 10 observations and forecasting the single fututre observation for each sequence.
- Train-test split: Training Data :Jan 2018-Apr2021, Testing Data : Apr2021-Jan2022

# Model Training: Random Forest Regressor
![newplot (3)](https://github.com/A-SOLO/BTC_USDT_Trading_Model/assets/78963312/154b5915-ee14-4c38-a94f-4ce868259977)

# Strategy : Gap Trading Strategy
![Picture1](https://github.com/A-SOLO/BTC_USDT_Trading_Model/assets/78963312/17bb3f08-b2c1-4087-a77a-eefa6afb3aaf)

# Indicators:
### 1. Position:
position = 1: Represents a long trade, indicating that the algorithm has bought an asset or security.
position = 0: Denotes a neutral position, suggesting that there is no ongoing trade (neither buying nor
selling).
position = -1: Corresponds to a short trade, implying that the algorithm has sold an asset.

### 2. Action (The action suggested by the Gap trading strategy):
action = 1: Indicates a signal to buy or initiate a long trade or close a short trade.
action = 0: Represents a hold signal, advising to maintain the current position without taking any new
actions.
action = -1: Signifies a signal to sell or initiate a short trade.

# Logic:
### Long Trade (position P= 1 or 0):
1. If P = 0 and the action is 1 (Buy), it initiates a long trade. The algorithm purchases the asset.
2. If P = 1 and the action is -1 (Sell), it ends the long trade and initializes a short trade immediately.
3. If the action is 0, it means to maintain the current position without any new buying or selling.
4. If the price movement reaches a level that surpasses the stop-loss, the algorithm ends the long trade to minimize losses.

### Short Trade (position = -1):
1. If the action is 1 (Buy), it closes the short sell position and simultaneously initiates a new long trade.
2. If the action is 0, it means to maintain the current position without any new buying or selling.
3. If the action is -1, the model maintains the current position of short sell without any new buying or selling. As we use compounding, we don’t sell the stocks again.
4. If the price movement reaches a level that surpasses the stop-loss, the algorithm ends the short
trade and simultaneously initiates a new long trade.

# Key Risk Management Strategies:
### 1. Stop-Loss :
Set orders to limit potential losses. Automatically exits a trade if the market moves unfavorably.

### 3. Gap Strategy Threshold:
Adjusting this parameter allows users to customize the sensitivity of the strategy to price movements, catering to different preferences or market conditions.

# Backtesting Parameters :
1. ML model Parameters (Random Forest- see the code).
2. Gap-threshold-percentage = 0.85
3. Stop-loss-percentage = 0.30
4. Look-Back Window = 10 Obs.

# Random Forest Results:
Train Set Metrics:
- R2 Score: 0.9998820645527133
- Mean Squared Error: 14760.061048243917
- Mean Absolute Error: 54.92394429652503

Test Set Metrics:
- R2 Score: 0.9693747358366076
- Mean Squared Error: 2456163.9950162075
- Mean Absolute Error: 1038.8512681053812

# Conclusion:
* Used the Historical BTC/USDT 4hrs data from January 1, 2018 to January 31, 2022
* With the help of Random Forest , a simple yet powerful machine learning model and using a Gap Trading Strategy method.
* Generated 448% return along with the max drawdown of 6.28%.
