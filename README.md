# Algorithmic Trading

- Algorithmic Trading is the use of algorithms in the financial market to make trading decisions. JP Morgan Chase & Co. is one of the businesses that use Algorithmic Trading for investment decisions.

# Performance of momentum strategies

- In a study in 1993 Narasimhan Jegadeesh and Sheridan Titman reported that this strategy give average returns of 1% per month for the following 3–12 months.[10] This finding has been confirmed by many other academic studies, some even going back to the 19th century,[11][12][13] though momentum strategies are associated with an increased risk of crashes and major losses.[5]

- Turnover tend to be high for momentum strategies, which could reduce the net returns of a momentum strategy. Some even claim that transaction costs wipe out momentum profits.[14] In their 2014 study 'fact, fiction, and momentum investing' Cliff Asness and his co-authors address 10 issues with regards to momentum investing, including transaction costs.[15]

- The performance of momentum comes with occasional large crashes. For example, in 2009, momentum experienced a crash of -73.42% in three months.[16] This downside risk of momentum can be reduced with a so called 'residual momentum' strategy in which only the stock specific part of momentum is used.[17]

- A momentum strategy can also be applied across industries and across markets

# Get Stock Price Data using Python

- Yahoo Finance is one of the most popular websites to collect stock price data. You need to visit the website, enter the company’s name or stock symbol, and you can easily download the dataset. But if you want to get the latest dataset every time you are running your code, you need to use the yfinance API. yfinance is an API provided by Yahoo Finance to collect the latest stock price data.

- To use this API, you need to install it by using the pip command in your terminal or command prompt as mentioned below:

  - pip install yfinance

- I hope you have easily installed this API. Now below is how you can get the latest stock price data using Python:


  - import pandas as pd
  
  - import yfinance as yf
  
  - import datetime
  
  - from datetime import date, timedelta
  
  - today = date.today()

  - d1 = today.strftime("%Y-%m-%d")
  
  - end_date = d1
  
  - d2 = date.today() - timedelta(days=360)
  
  - d2 = d2.strftime("%Y-%m-%d")
  
  - start_date = d2
  
  - data = yf.download('AAPL', 
                        start=start_date, 
                        end=end_date, 
                        progress=False)
                        
  - print(data.head())
 
### The above code will collect the stock price data from today to the last 360 days. In this dataset, Date is not a column, it’s the index of this dataset. To use this data for any data science task, we need to convert this index into a column. 

#### Below is how you can do that:

  - data["Date"] = data.index
  - data = data[["Date", "Open", "High", 
               "Low", "Close", "Adj Close", "Volume"]]
  - data.reset_index(drop=True, inplace=True)
  - print(data.head())
