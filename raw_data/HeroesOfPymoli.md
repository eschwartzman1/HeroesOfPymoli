
# Heroes of Pymoli
## Breaking down the company's purchasing data

-----

### Importing the dependencies

-----


```python
import pandas as pd
import numpy as np
```

### Reading the data
##### (and displaying the first five lines)

-----


```python
data = pd.read_json('purchase_data.json')

data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>



## Player Count

-----

- This is the total number of players, 573.




```python
data['SN'].nunique()
```




    573



## Purchasing Analysis (Total)

-----
- Number of Unique Items: 183


```python
num_unique_items = data['Item ID'].unique()
num_unique_items = len(num_unique_items)
num_unique_items
```




    183



-----

- Average Purchase Price: $2.93


```python
avg_purchase_price = data['Price'].mean()
avg_purchase_price = pd.to_numeric(avg_purchase_price)
avg_purchase_price
```




    2.931192307692303



-----

- Total Number of Purchases: 780


```python
purchase_count = data['Price'].count()
purchase_count
```




    780



-----

- Total Revenue: $2,286.33


```python
total_revenue = data['Price'].sum()
total_revenue
```




    2286.3299999999963




```python
data['Gender'].value_counts()
unique_players = data['Gender'].value_counts()[0] + data['Gender'].value_counts()[1]
data.count()
```




    Age          780
    Gender       780
    Item ID      780
    Item Name    780
    Price        780
    SN           780
    dtype: int64



## Gender breakdown of players:

-----


```python
gender_breakdown = data.groupby('Gender')['SN'].nunique().to_frame('Unique Player Count')
                                                                
gender_breakdown
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unique Player Count</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>100</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>465</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>8</td>
    </tr>
  </tbody>
</table>
</div>



-----

- Percentage of Male Players


```python
percent_male_players = (data['Gender'].value_counts()[0] / purchase_count) * 100
percent_male_players.round(decimals=2)
```




    81.150000000000006



-----

- Percentage of Female Players


```python
percent_female_players = (data['Gender'].value_counts()[1] / purchase_count) * 100
percent_female_players.round(decimals=2)
```




    17.440000000000001



-----

- Percentage of Other / Non-Disclosed Players: 1.41%


```python
percent_other_players = (data['Gender'].value_counts()[2] / purchase_count) * 100
percent_other_players.round(decimals=2)
```




    1.4099999999999999



## Analysis By Gender

-----

- Total Purchase Count:


```python
purchase_count = data.groupby('Gender')['Item ID'].count().to_frame('Total Purchase Count')
purchase_count
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Purchase Count</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>136</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>633</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>



-----

- Average Purchase Price:


```python

```

-----

- Total Purchase Value:


```python

```

-----

- Normalized Totals:


```python

```
