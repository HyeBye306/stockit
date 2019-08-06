# stockit

stockit is a python class that aids in easy prediction and alaysis of stocks

stockit_class_sklearn.py is a class that has many of the tools needed for analysis and prediction such as polynomial regression and a moving average graph creation tool
 
stockit_realtime.py takes real time data from yahoo and with a theoretical $50k and buys as much theoretical stock as it can with it 

it will the use that live data from yahoo finance to allow it to calculate a potential climb or fall in stock price and then make appropriate actions on that information


# Change Log

<i>Wednesday, July 24 12:45 am (ADT)</i>
over the past two days ive implemented a few boring general optimizations, things like variables that only need to be definded once and not in a for loop and the relatively resource intensive sklearn linearregression() class running twice for no reason 

after these fixes i implemented the very popular moving average analysis technique with a method called moving_avg()
this method takes in the inputs of self and index

self is used to get the data 
index i used to tell the program how far back you want each moving average window to go 

# USAGE:

get stock data with Close/close column from a csv or other file as a pandas dataframe
```python
import pandas as pd 
data = pd.read('example.csv')
```
import the stockit class from stockit_class_sklearn.py
```python
from stockit_class_sklearn import stockit_class
```

then lets create an object out of stockit_class, passing it our pandas dataframe

```python

stockit = stockit_class(data)

```

from here we can do a few things 

1. we can use the polynomial regression feature 
2. we can use the newly added (as of july 24 2019) moving average feature 

Polynomial Regressor
```python
 #next day that we will predict the price of 
 next = len(data)+1
 #create the polynomial with stockit.train()
 #we can specify the degree of the polynomial and the index
 #the index is just how far back from the end of the data we generate the polynomial from
 #the lower this number the more relevant it is, higher numbers may give you a better picture, dont specify or pass 0 for the entire set
 stockit.train(degree = 10, index = 300)
 
 #make prediction on the next day 
 print(stockit.predict(next))

```

moving average
```python

 #simply call the moving_avg() method of stockit
 #index specifies the length of each window, lower = more relevant, higher = bigger picture, your choice
 stockit.moving_avg(index = 35)
 
```