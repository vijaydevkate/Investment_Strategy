# Comparison of Investment Strategies using Modern Portfolio Theory

## Objective:

* The Objective of this project is to create a portfolio of stocks that appropriately balances the conflicting risk and profit and compare different investment strategies such as Buy and hold and Momentum Trading for stocks based on Modern Portfolio Theory (MPT).
* We choose the assets (stocks) from the sectors such as:
  1. Consumer Discretionary
  2. Technology Sector
  3. Industrial Sector

## Modern Portfolio Theory:

* In MPT, the goal is to allocate money into stocks to maximize the expected return while accounting for your risk tolerance, which is measured by volatility.  
* Unfortunately, you cannot optimize two conflicting quantities (profit and risk) simultaneously. 
* Instead, you will take a piecewise approach: for each given risk tolerance ceiling (the max amount of risk you are willing to take on), you will maximize profit for that given risk level. So you will calculate one optimal mix of allocation of stocks that maximizes profit for each risk level.
* For example, if you evaluate 100 different risk levels, you will have 100 (potentially distinct) allocations. Low-risk levels will have well-balanced and diversified portfolios, but you will probably make less money. High-risk levels will have very skewed/narrow portfolio mixes (like only buying Tesla in your portfolio!), but this can be highly volatile. 
* The goal is to show the range of profit outcomes you could achieve for all risk levels (the efficient frontier).

## The Stocks that we chose for our analysis:

![image](https://user-images.githubusercontent.com/48169929/226130243-70a35d77-e509-4830-b31a-79da9f35b2e9.png)

## Optimization Model: Portfolio Allocation
### Optimal Stock Allocation:
* We used Pyomo to build our Portfolio Allocation Model
* Towards the lefthand side, we have lower risk and higher diversity.
* Towards the righthand side, we have higher risk and lower diversity.
* We have the optimal allocation of stocks corresponding to each risk level. 
* For our analysis, we would be considering the risk value of 0.000205 and the corresponding stocks chosen are McDonald's, Autodesk and Verisk. 
* This risk value has been chosen as these 3 stocks belong to 3 different sectors and their allocation proportion sums to 1 approximately.
![image](https://user-images.githubusercontent.com/48169929/226142316-629c4ff7-18e6-4159-a3c8-c0422dc69d0d.png)

### The Efficient Frontier:
* We have plotted the efficient frontier, that is, risk (X) vs. return (Y).
* After a certain point, taking on more risk doesn't increase your returns! This occurs at ~Risk = *0.00055* which achieves a maximum return of around *0.132% (0.00132)*.
* Any point on the efficient frontier represents an optimal allocation based on your risk tolerance.
* From the Selected Portfolio Allocation, we can see that we have allocated 0.272% of the Portfolio to McDonald's Stock , 0.328% of the Portfolio to Autodesk Stock, and 0.40% of the Portfolio to Verisk Stock.
![image](https://user-images.githubusercontent.com/48169929/226142435-51226b45-feba-4ca8-84a1-10a4306558d4.png)


## Momentum Trading:

* The MT strategy is based on the crossing points of the moving averages. 
* For example if we considered the moving averages of 9 days and 21 days, buy operations are triggered when the 9-day moving average becomes larger than the 21-day moving average, and sell operations are triggered when the 21-day moving average becomes larger than the 9-day moving average. 
* The goal is to identify good parameters for a momentum trading strategy tailored for a portfolio identified by the MPT model. 
* We have considered 5 different pairs of moving averages for the selected portfolio:

  1. 9-Day/21-Day Moving Average Strategy
  2. 5-Day/13-Day Moving Average Strategy
  3. 50-Day/200-Day Moving Average Strategy for Long Term Investors
  4. 21-Day/55-Day Moving Average Strategy
  5. 15-Day/30-Day Moving Average Strategy
* Choosing the best Strategy of the 5 for each stock:

  1. For McDonald's, the highest return is for the 21-Day/55-Day strategy.
  2. For Autodesk, the highest return is for the 5-Day/13-Day strategy.
  3. For Verisk, the highest return is for the 15-Day/30-Day strategy.
## Analysis:
* If we had USD 100,000 to invest , the amount invested in McDonald's would be USD 27,168.5 , the amount invested in Autodesk would be USD 32,814.4 and the amount invested in Verisk would be USD 40,017.1
### Buy and Hold Strategy:
![image](https://user-images.githubusercontent.com/48169929/226143210-df701481-2110-4fdd-be58-bf2ef272e3aa.png)
### Momentum Trading:
#### 1. McDonald's (21-Day/55-Day Strategy - for 2022)
   ![image](https://user-images.githubusercontent.com/48169929/226143298-c2fd7e70-0ba9-4ea6-b9d6-d817e45cfb7b.png)   
#### 2. Autodesk (5-Day/13-Day Strategy - for 2022)
   ![image](https://user-images.githubusercontent.com/48169929/226143327-d07c88de-c2c4-4333-b6f7-887962cc40c7.png)
#### 3. Verisk (15-Day/30-Day Strategy - for 2022)
   ![image](https://user-images.githubusercontent.com/48169929/226143360-1b813f3f-cdb3-47fa-a178-d0622453a962.png)
#### Value of Each Position & Aggregate Value at the Beginning of Each Month (Momentum Trading Strategy)
![image](https://user-images.githubusercontent.com/48169929/226143386-0de6a792-2758-4943-b0ee-ab24d3130755.png)
## Comparing the stratagies:
* For the Buy_and_Hold strategy, the Aggregate Value of the investment on November 1st 2022 was **$93,253.**
* For the Momentum Trading strategy, the Aggregate Value of the investment on November 1st 2022 was **$88,033.**
* If we invested in S&P 500 index, the Aggregate Value of the investment on November 1st 2022 was **$90,356.**
* Therefore, if we used the 'Buy & Hold Strategy' or the 'Momentum Trading Strategy' based on the chosen portfolio allocation, we would be losing money. If we invest in S&P 500 index, we would be losing about $10,000 approx.
* So we can conclude that Buy_and_Hold strategy helps to retain the maximum value for investment of the 3 strategies.
![image](https://user-images.githubusercontent.com/48169929/226146538-fbd1ded5-a195-464d-8766-c2032ea49eb7.png)
## Conclusion:
* For the Portfolio Allocation Model, we have used binary constraints to ensure that we select one and only one stock from each sector.
* Decreasing the max limit for risk and reducing the step size gave us good results as the data collected is on a daily basis (for 5 years). Using the parameter analysis, the optimal risk was chosen, and was used for further analysis.
* We considered 5 different pairs of values of moving averages to determine the best Momentum Trading Strategy for each stock. The best strategy for each stock was decided based on the system return value for all the combinations.
* Based on the analysis for 2022, we got to know that 'Buy and Hold' strategy worked better for the chosen portfolio on the whole when compared to Momentum Trading strategy.
* Coming to the Individual stocks, for Verisk, the Momentum Trading Strategy worked better than Buy and Hold Strategy. For the other two stocks (McDonald's & Autodesk), Buy and Hold strategy worked better than Momentum Trading Strategy.
* During the course of this project, we got to learn more about various terms in the stock market and how a strategy could be used to an investor's advantage.
* Investment strategies play a vital role for investors; they can be goal-oriented and hence can help the investors make investment decisions based on their goals. The best investing strategies are the ones that have higher returns & lower risks. However, there is always a trade-off.
* The obtained strategy may vary on several factors, including but not limited to, one’s investment goals such as short term or long term, asset sector considered, the timeframe considered, and the risk ceiling considered. 
