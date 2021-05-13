**Retrieving economic events from Investing.com**

Quickly pulling data from an economic calendar comes in handy when someone is performing a macroeconomic analysis. In this example, I'm interested about the interest rate decision meetings from the Brazilian Central Bank that ocurred this year (2021).

---


```python
#Importing the investpy package and retrieving the complete calendar for 2021 until today (13/05)

import investpy

data = investpy.news.economic_calendar(
    time_zone=None, 
    time_filter='time_only', 
    countries=None, 
    importances=None, 
    categories=None, 
    from_date='01/01/2021', 
    to_date='13/05/2021')


data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>time</th>
      <th>zone</th>
      <th>currency</th>
      <th>importance</th>
      <th>event</th>
      <th>actual</th>
      <th>forecast</th>
      <th>previous</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9</td>
      <td>01/01/2021</td>
      <td>All Day</td>
      <td>united states</td>
      <td>None</td>
      <td>None</td>
      <td>United States - New Year's Day</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9</td>
      <td>01/01/2021</td>
      <td>All Day</td>
      <td>united kingdom</td>
      <td>None</td>
      <td>None</td>
      <td>United Kingdom - New Year's Day</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9</td>
      <td>01/01/2021</td>
      <td>All Day</td>
      <td>germany</td>
      <td>None</td>
      <td>None</td>
      <td>Germany - New Year's Day</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9</td>
      <td>01/01/2021</td>
      <td>All Day</td>
      <td>switzerland</td>
      <td>None</td>
      <td>None</td>
      <td>Switzerland - New Year's Day</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>4</th>
      <td>9</td>
      <td>01/01/2021</td>
      <td>All Day</td>
      <td>italy</td>
      <td>None</td>
      <td>None</td>
      <td>Italy - New Year's Day</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>




```python
#It seems like it worked out. Now it's time to select only the monetary policy meetings from the Central Bank of Brazil during this period

bacen_2021 = data.loc[(data['zone'] == 'brazil') & (data['event'] == 'Interest Rate Decision')]

bacen_2021
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>time</th>
      <th>zone</th>
      <th>currency</th>
      <th>importance</th>
      <th>event</th>
      <th>actual</th>
      <th>forecast</th>
      <th>previous</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1553</th>
      <td>420816</td>
      <td>20/01/2021</td>
      <td>17:00</td>
      <td>brazil</td>
      <td>BRL</td>
      <td>medium</td>
      <td>Interest Rate Decision</td>
      <td>2.00%</td>
      <td>2.00%</td>
      <td>2.00%</td>
    </tr>
    <tr>
      <th>7748</th>
      <td>423145</td>
      <td>17/03/2021</td>
      <td>17:00</td>
      <td>brazil</td>
      <td>BRL</td>
      <td>medium</td>
      <td>Interest Rate Decision</td>
      <td>2.75%</td>
      <td>2.50%</td>
      <td>2.00%</td>
    </tr>
    <tr>
      <th>14852</th>
      <td>428260</td>
      <td>05/05/2021</td>
      <td>17:00</td>
      <td>brazil</td>
      <td>BRL</td>
      <td>medium</td>
      <td>Interest Rate Decision</td>
      <td>3.50%</td>
      <td>3.50%</td>
      <td>2.75%</td>
    </tr>
  </tbody>
</table>
</div>



---

In 2021, the Brazilian Central Bank started a partial normalization of monetary policy due to inflationary pressures. In january, the committee maintained interest rate at 2.00%, but in the subsequent meetings promoted two hikes of 75 bps. The SELIC is currently at 3.50% and may go higher.
