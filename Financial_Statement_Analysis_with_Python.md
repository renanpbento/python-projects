```python
# Data 
revenue = [14574.49, 7606.46, 8611.41, 9175.41, 8058.65, 8105.44, 11496.28, 9766.09, 10305.32, 14379.96, 10713.97, 15433.50]
expenses = [12051.82, 5695.07, 12319.20, 12089.72, 8658.57, 840.20, 3285.73, 5821.12, 6976.93, 16618.61, 10054.37, 3803.96]
```

---

**Assessing the Financial Statement of Organization X**

---


```python
# First approach using Lists
# Calculating Profit
profit = list([])

for i in range (0, len(revenue)):
    profit.append(revenue[i] - expenses[i])
    
profit = [round(i,2) for i in profit]

profit
```




    [2522.67,
     1911.39,
     -3707.79,
     -2914.31,
     -599.92,
     7265.24,
     8210.55,
     3944.97,
     3328.39,
     -2238.65,
     659.6,
     11629.54]




```python
# Calculating Tax based on a tax rate of 30%

tax = [round(i * 0.30,2) for i in profit]

tax
```




    [756.8,
     573.42,
     -1112.34,
     -874.29,
     -179.98,
     2179.57,
     2463.17,
     1183.49,
     998.52,
     -671.6,
     197.88,
     3488.86]




```python
# Calculating Net Profit

net_profit = list([])

for i in range (0, len(profit)):
    net_profit.append(profit[i] - tax[i])

net_profit = [round(i,2) for i in net_profit]

net_profit
```




    [1765.87,
     1337.97,
     -2595.45,
     -2040.02,
     -419.94,
     5085.67,
     5747.38,
     2761.48,
     2329.87,
     -1567.05,
     461.72,
     8140.68]




```python
# Calculating the Net Profit Margin

net_profit_margin = list([])

for i in range (0,len(net_profit)):
    net_profit_margin.append(net_profit[i]/revenue[i])
    
net_profit_margin = [round((i*100),2) for i in net_profit_margin]

net_profit_margin
```




    [12.12,
     17.59,
     -30.14,
     -22.23,
     -5.21,
     62.74,
     49.99,
     28.28,
     22.61,
     -10.9,
     4.31,
     52.75]




```python
# Median of Net Profit along the period

import numpy as np

median_net_profit = np.median(net_profit)

median_net_profit
```




    1551.92




```python
# Classifying months above/below median

good_month = list([])

for i in range (0, len(profit)):
    good_month.append(net_profit[i] > median_net_profit)
    
good_month
```




    [True, False, False, False, False, True, True, True, True, False, False, True]




```python
bad_month = list([])

for i in range (0, len(profit)):
    bad_month.append(net_profit[i] < median_net_profit)
    
bad_month
```




    [False, True, True, True, True, False, False, False, False, True, True, False]



---


```python
# Second approach using Numpy
# Calculating Profit
import numpy as np

rev = np.array(revenue)
exp = np.array(expenses)
profit = rev - exp
    
profit
```




    array([ 2522.67,  1911.39, -3707.79, -2914.31,  -599.92,  7265.24,
            8210.55,  3944.97,  3328.39, -2238.65,   659.6 , 11629.54])




```python
# Calculating Tax based on a tax rate of 30%

taxes = profit * 0.3

taxes
```




    array([  756.801,   573.417, -1112.337,  -874.293,  -179.976,  2179.572,
            2463.165,  1183.491,   998.517,  -671.595,   197.88 ,  3488.862])




```python
# Calculating Net Profit

net_profit = profit-taxes

net_profit
```




    array([ 1765.869,  1337.973, -2595.453, -2040.017,  -419.944,  5085.668,
            5747.385,  2761.479,  2329.873, -1567.055,   461.72 ,  8140.678])



---


```python
Author: Renan Pereira Bento
```
