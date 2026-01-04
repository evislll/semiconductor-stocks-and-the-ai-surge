# **Semiconductor Stocks & the AI Surge**
### **Data Mining & Financial Trend Analysis**
Data mining analysis of semiconductor stock performance during the AI market surge using Python, Pandas, applying data preprocessing, visualization, and trend analysis to extract actionable insights.

## **Background**
There is a large amount of stock market data available, which is widely used to extract valuable market insights and is beneficial for traders, market analysts, and other financial professionals. **The purpose of this project is to explore how the AI boom has influenced the market capitalization and trading patterns of companies driving chip innovation**, supporting financial modeling and industry trend exploration.

To discover valuable insights, this data requires careful preparation and the application of relevant exploratory techniques.

## **Data Set**
The dataset used in this project is generated using the `yfinance` library from publicly available Yahoo Finance data. It is time-series historical daily stock market data for 152 semiconductor companies—including NVIDIA, AMD, Intel, and others—spanning from 2012 to 2024

For each: Company name ,Stock name, Date of the trading day (YYYY-MM-DD),
Opening price, Highest price of the day, Lowest price, Closing price and Volume

Available:[https://www.kaggle.com/datasets/farukece/semiconductor-stocks-and-the-ai-surge](url) “Semiconductor Stocks and the AI Surge”by F. Keçe, available on Kaggle.


## **Procedure**
1. Analyze how the top 10 performers over the last 3 years were affected, comparing trends from 2012 and from 2022
2. Verify results using **Risk/Return analysis** and a **K-means clustering model to see how the days can be grouped to analyze the current market condition** 
3. **Build a predictive model** for the best-performing company
4. **Improve the predictive mode** by adding rolling averages and new features, applying relevant techniques for time-series data

## **Features**
-Replacing **absolute** values that carry much less meaning compared to **ratios** - Provide contextual understanding of price dynamics beyond simple today/tommorow values comparisons, incorporate short, medium, and long-term indicators, that significanlty improved the model and balanced the decision-tree

## **Overview**

###**Semiconductor Companies performace**
<img width="1142" height="542" alt="Screenshot 2026-01-03 190507" src="https://github.com/user-attachments/assets/100b173d-a62a-4b8e-8d2f-aa8014bd0040" />
<img width="1128" height="551" alt="Screenshot 2026-01-03 190519" src="https://github.com/user-attachments/assets/2fe4d49d-922e-4149-91f4-55ec62fce479" />
**Overall Dominance:** 
NVIDIA 53,876% long-term return  
1,114%  AI Boom period 
**AI Boom Specialists:**
 Cambricon long-term return of 224%
highest return 1,113% 
**Strong Long-Term Performers:** 
Broadcom 13,791% long-term, 443% AI Boom 
Alchip 11,531% long-term, 355% AI Boom
HANMI  10,159% long-term, 689% AI Boom 
**Consistent Growth :** 
Credo 823% long-term return, 727% return during the AI Boom
# **Risk/Return Analysis Conclusions**
clear pattern that supports the idea that infrastructure outperforms speculation
**Aeluma , Credo Technology** delivers exceptionally high returns with moderate volatility efficient, sustainable growth, they are infrastructure-focused, They deliver strong long-term returns without the extreme risk we expect from speculative leaders
**NVIDIA**is not the most efficient performer here
Companies that build the underlying infrastructure like **Credo Technology, Broadcom, HANMI Semiconductor, Disco ---Corp., and Advantest**—show lower risk with  consistent returns.

<img width="1295" height="806" alt="Screenshot 2026-01-03 184634" src="https://github.com/user-attachments/assets/b534e109-24dd-4bf0-b199-d8b3ccb814d0" />

# **Predictive Model for the top Performer**
how  model makes predictions:
* It should give us improvement from the baseline model as we only compared today and tommorrow value before.

Train on new derived1 if tomorrow's close value is higher tha
0.48 - not a good precision score
improve it by training rolling averages
<img width="1576" height="993" alt="Screenshot 2026-01-03 190340" src="https://github.com/user-attachments/assets/9a836564-56da-49d3-896f-402d7db75820" />


# **Improving the model**

### **Increasing Confidence**
* Increase default threshhold to 0.7 - model return that the price will go up if there is a greater than a 70% chance that  price go up 

### **Changing predictors**
* **rolling averages** - add features, that are **Ratios**, **how much price today is greater/lesser, than it was last week, last month, last year**, replaced values of high, low, open, in the predictions
* **trend feature** - sum of the target for each day over the last given days

Now we will **give algorithm more information about those periods**:
  
 <img width="1254" height="140" alt="Screenshot 2026-01-03 205416" src="https://github.com/user-attachments/assets/6745dbfb-815b-47d5-a2e1-8c3fe5fd00f7" />

<img width="1879" height="1096" alt="Screenshot 2026-01-03 190418" src="https://github.com/user-attachments/assets/0e93cd11-c9a4-4148-bf8b-c6a9000277fa" />

 
 *Decision Logic*
* Each node in the tree represents a decision point based on one of added features.
*  **To identify patterns like** : if the price has been going up for the last 5 days (`Close_Ratio_5` > 0.7 ) and the long-term trend (`Trend_250`) is also positive, then predict an 'Up' day.

 *Leaves - Predictions** 
* leaf nodes (very bottom of the tree) show the final prediction (Up or Down)
* `samples` (number of data points that reached that leaf)
* `value` ( distribution of 'Up' vs 'Down' days in that leaf).




# **References:**
Dataset [27] F. Keçe. "Semiconductor Stocks and the AI Surge." Kaggle.com. Accessed: Oct 20, 2025
Online. Available: https://www.kaggle.com/datasets/farukece/semiconductor-stocks-and-the-ai-surge

Background Research: M. Intrator (CoreWeave CEO). "CoreWeave CEO pushes back against circular investment concerns." CNBC.com, Oct. 8, 2025. [Online]. Available: https://www.cnbc.com/2025/10/08/coreweave-ceo-pushes-back-against-circular-investment-concerns-.html

Report [28] Global Market Intelligence. "AI Infrastructure: Midyear 2025 Update and Future Technology Considerations." spglobal.com. October 2025. [Online]. Available: https://www.spglobal.com/market-intelligence/en/news-insights/research/2025/10/ai-infrastructure-midyear-2025-update-and-future-technology-considerations

Decision tree: V. Paruchuri. "S&P 500 Stock Market Forecasting" GitHub.com. Accessed: Nov 20, 2025,Online Available: https://github.com/dataquestio/projectwalkthroughs/blob/master/sp_500/market_prediction.ipynb

Time-series Analysis studies (ch 16), K-means clustering (ch 15) , idea on data partition (16.5):
Shmueli, Galit, et al. Data Mining for Business Analytics : Concepts, Techniques and Applications in Python, JohnWiley & Sons, Incorporated, 2019. ProQuest Ebook Central, http://ebookcentral.proquest.com/lib/senecac/detail.action?docID=5945647
