# **Course 3 Automatidata project**
**Course 3 - Go Beyond the Numbers: Translate Data into Insights**

You are the newest data professional in a fictional data consulting firm: Automatidata. The team is still early into the project, having only just completed an initial plan of action and some early Python coding work. 

Luana Rodriquez, the senior data analyst at Automatidata, is pleased with the work you have already completed and requests your assistance with some EDA and data visualization work for the New York City Taxi and Limousine Commission project (New York City TLC) to get a general understanding of what taxi ridership looks like. The management team is asking for a Python notebook showing data structuring and cleaning, as well as any matplotlib/seaborn visualizations plotted to help understand the data. At the very least, include a box plot of the ride durations and some time series plots, like a breakdown by quarter or month. 

Additionally, the management team has recently asked all EDA to include Tableau visualizations. For this taxi data, create a Tableau dashboard showing a New York City map of taxi/limo trips by month. Make sure it is easy to understand to someone who isn’t data savvy, and remember that the assistant director at the New York City TLC is a person with visual impairments.

A notebook was structured and prepared to help you in this project. Please complete the following questions.

# Course 3 End-of-course project: Exploratory data analysis

In this activity, you will examine data provided and prepare it for analysis. You will also design a professional data visualization that tells a story, and will help data-driven decisions for business needs. 

Please note that the Tableau visualization activity is optional, and will not affect your completion of the course. Completing the Tableau activity will help you practice planning out and plotting a data visualization based on a specific business need. The structure of this activity is designed to emulate the proposals you will likely be assigned in your career as a data professional. Completing this activity will help prepare you for those career moments.

**The purpose** of this project is to conduct exploratory data analysis on a provided data set. Your mission is to continue the investigation you began in C2 and perform further EDA on this data with the aim of learning more about the variables. 
  
**The goal** is to clean data set and create a visualization.
<br/>  
*This activity has 4 parts:*

**Part 1:** Imports, links, and loading

**Part 2:** Data Exploration
*   Data cleaning


**Part 3:** Building visualizations

**Part 4:** Evaluate and share results

<br/> 
Follow the instructions and answer the questions below to complete the activity. Then, you will complete an Executive Summary using the questions listed on the PACE Strategy Document.

Be sure to complete this activity before moving on. The next course item will provide you with a completed exemplar to compare to your own work. 



# **Visualize a story in Tableau and Python**

# **PACE stages** 


<img src="images/Pace.png" width="100" height="100" align=left>

   *        [Plan](#scrollTo=psz51YkZVwtN&line=3&uniqifier=1)
   *        [Analyze](#scrollTo=mA7Mz_SnI8km&line=4&uniqifier=1)
   *        [Construct](#scrollTo=Lca9c8XON8lc&line=2&uniqifier=1)
   *        [Execute](#scrollTo=401PgchTPr4E&line=2&uniqifier=1)

Throughout these project notebooks, you'll see references to the problem-solving framework PACE. The following notebook components are labeled with the respective PACE stage: Plan, Analyze, Construct, and Execute.

<img src="images/Plan.png" width="100" height="100" align=left>


## PACE: Plan 

In this stage, consider the following questions where applicable to complete your code response:
1. Identify any outliers: 


*   What methods are best for identifying outliers?
*   How do you make the decision to keep or exclude outliers from any future models?



==> ENTER YOUR RESPONSE HERE

### Task 1. Imports, links, and loading
Go to Tableau Public
The following link will help you complete this activity. Keep Tableau Public open as you proceed to the next steps. 

Link to supporting materials: 
Tableau Public: https://public.tableau.com/s/ 

For EDA of the data, import the data and packages that would be most helpful, such as pandas, numpy and matplotlib. 



```python
# Import packages and libraries
#==> ENTER YOUR CODE HERE

import numpy as np
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns
from plotly import express as px


```

**Note:** As shown in this cell, the dataset has been automatically loaded in for you. You do not need to download the .csv file, or provide more code, in order to access the dataset and proceed with this lab. Please continue with this activity by completing the following instructions.


```python
# Load dataset into dataframe
df = pd.read_csv('2017_Yellow_Taxi_Trip_Data.csv')
```

<img src="images/Analyze.png" width="100" height="100" align=left>

## PACE: Analyze 

Consider the questions in your PACE Strategy Document to reflect on the Analyze stage.

### Task 2a. Data exploration and cleaning

Decide which columns are applicable

The first step is to assess your data. Check the Data Source page on Tableau Public to get a sense of the size, shape and makeup of the data set. Then answer these questions to yourself: 

Given our scenario, which data columns are most applicable? 
Which data columns can I eliminate, knowing they won’t solve our problem scenario? 

Consider functions that help you understand and structure the data. 

*    head()
*    describe()
*    info()
*    groupby()
*    sortby()

What do you do about missing data (if any)? 

Are there data outliers? What are they and how might you handle them? 

What do the distributions of your variables tell you about the question you're asking or the problem you're trying to solve?




==> ENTER YOUR RESPONSE HERE

Start by discovering, using head and size. 


```python
#==> ENTER YOUR CODE HERE
df.head()
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
      <th>Unnamed: 0</th>
      <th>VendorID</th>
      <th>tpep_pickup_datetime</th>
      <th>tpep_dropoff_datetime</th>
      <th>passenger_count</th>
      <th>trip_distance</th>
      <th>RatecodeID</th>
      <th>store_and_fwd_flag</th>
      <th>PULocationID</th>
      <th>DOLocationID</th>
      <th>payment_type</th>
      <th>fare_amount</th>
      <th>extra</th>
      <th>mta_tax</th>
      <th>tip_amount</th>
      <th>tolls_amount</th>
      <th>improvement_surcharge</th>
      <th>total_amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>24870114</td>
      <td>2</td>
      <td>03/25/2017 8:55:43 AM</td>
      <td>03/25/2017 9:09:47 AM</td>
      <td>6</td>
      <td>3.34</td>
      <td>1</td>
      <td>N</td>
      <td>100</td>
      <td>231</td>
      <td>1</td>
      <td>13.0</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>2.76</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>16.56</td>
    </tr>
    <tr>
      <th>1</th>
      <td>35634249</td>
      <td>1</td>
      <td>04/11/2017 2:53:28 PM</td>
      <td>04/11/2017 3:19:58 PM</td>
      <td>1</td>
      <td>1.80</td>
      <td>1</td>
      <td>N</td>
      <td>186</td>
      <td>43</td>
      <td>1</td>
      <td>16.0</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>4.00</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>20.80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>106203690</td>
      <td>1</td>
      <td>12/15/2017 7:26:56 AM</td>
      <td>12/15/2017 7:34:08 AM</td>
      <td>1</td>
      <td>1.00</td>
      <td>1</td>
      <td>N</td>
      <td>262</td>
      <td>236</td>
      <td>1</td>
      <td>6.5</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>1.45</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>8.75</td>
    </tr>
    <tr>
      <th>3</th>
      <td>38942136</td>
      <td>2</td>
      <td>05/07/2017 1:17:59 PM</td>
      <td>05/07/2017 1:48:14 PM</td>
      <td>1</td>
      <td>3.70</td>
      <td>1</td>
      <td>N</td>
      <td>188</td>
      <td>97</td>
      <td>1</td>
      <td>20.5</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>6.39</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>27.69</td>
    </tr>
    <tr>
      <th>4</th>
      <td>30841670</td>
      <td>2</td>
      <td>04/15/2017 11:32:20 PM</td>
      <td>04/15/2017 11:49:03 PM</td>
      <td>1</td>
      <td>4.37</td>
      <td>1</td>
      <td>N</td>
      <td>4</td>
      <td>112</td>
      <td>2</td>
      <td>16.5</td>
      <td>0.5</td>
      <td>0.5</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>17.80</td>
    </tr>
  </tbody>
</table>
</div>




```python
#==> ENTER YOUR CODE HERE
df.size
```




    408582




```python
df.shape
```




    (22699, 18)



Use describe... 


```python
#==> ENTER YOUR CODE HERE
df.describe()

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
      <th>Unnamed: 0</th>
      <th>VendorID</th>
      <th>passenger_count</th>
      <th>trip_distance</th>
      <th>RatecodeID</th>
      <th>PULocationID</th>
      <th>DOLocationID</th>
      <th>payment_type</th>
      <th>fare_amount</th>
      <th>extra</th>
      <th>mta_tax</th>
      <th>tip_amount</th>
      <th>tolls_amount</th>
      <th>improvement_surcharge</th>
      <th>total_amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>2.269900e+04</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
      <td>22699.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.675849e+07</td>
      <td>1.556236</td>
      <td>1.642319</td>
      <td>2.913313</td>
      <td>1.043394</td>
      <td>162.412353</td>
      <td>161.527997</td>
      <td>1.336887</td>
      <td>13.026629</td>
      <td>0.333275</td>
      <td>0.497445</td>
      <td>1.835781</td>
      <td>0.312542</td>
      <td>0.299551</td>
      <td>16.310502</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.274493e+07</td>
      <td>0.496838</td>
      <td>1.285231</td>
      <td>3.653171</td>
      <td>0.708391</td>
      <td>66.633373</td>
      <td>70.139691</td>
      <td>0.496211</td>
      <td>13.243791</td>
      <td>0.463097</td>
      <td>0.039465</td>
      <td>2.800626</td>
      <td>1.399212</td>
      <td>0.015673</td>
      <td>16.097295</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.212700e+04</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>-120.000000</td>
      <td>-1.000000</td>
      <td>-0.500000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>-0.300000</td>
      <td>-120.300000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.852056e+07</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.990000</td>
      <td>1.000000</td>
      <td>114.000000</td>
      <td>112.000000</td>
      <td>1.000000</td>
      <td>6.500000</td>
      <td>0.000000</td>
      <td>0.500000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>8.750000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>5.673150e+07</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.610000</td>
      <td>1.000000</td>
      <td>162.000000</td>
      <td>162.000000</td>
      <td>1.000000</td>
      <td>9.500000</td>
      <td>0.000000</td>
      <td>0.500000</td>
      <td>1.350000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>11.800000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>8.537452e+07</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>3.060000</td>
      <td>1.000000</td>
      <td>233.000000</td>
      <td>233.000000</td>
      <td>2.000000</td>
      <td>14.500000</td>
      <td>0.500000</td>
      <td>0.500000</td>
      <td>2.450000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>17.800000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.134863e+08</td>
      <td>2.000000</td>
      <td>6.000000</td>
      <td>33.960000</td>
      <td>99.000000</td>
      <td>265.000000</td>
      <td>265.000000</td>
      <td>4.000000</td>
      <td>999.990000</td>
      <td>4.500000</td>
      <td>0.500000</td>
      <td>200.000000</td>
      <td>19.100000</td>
      <td>0.300000</td>
      <td>1200.290000</td>
    </tr>
  </tbody>
</table>
</div>



**I noticed that the min fareamount is -120... this is very strange (is it a refund?)**

**RateCodeID has a max of 99 but there are only 6 possible RateCodeID values - is this an error?**

**payment_type has a max of 4 but there are 6 possible RateCodeID values - are unknown and voided trips intetionally excluded??**

And info. 


```python
df = df[df["fare_amount"] >= 0] 
df.describe()
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
      <th>Unnamed: 0</th>
      <th>VendorID</th>
      <th>passenger_count</th>
      <th>trip_distance</th>
      <th>RatecodeID</th>
      <th>PULocationID</th>
      <th>DOLocationID</th>
      <th>payment_type</th>
      <th>fare_amount</th>
      <th>extra</th>
      <th>mta_tax</th>
      <th>tip_amount</th>
      <th>tolls_amount</th>
      <th>improvement_surcharge</th>
      <th>total_amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>2.268500e+04</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
      <td>22685.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.675861e+07</td>
      <td>1.555962</td>
      <td>1.642231</td>
      <td>2.914952</td>
      <td>1.043244</td>
      <td>162.421732</td>
      <td>161.544545</td>
      <td>1.335552</td>
      <td>13.041876</td>
      <td>0.333723</td>
      <td>0.498038</td>
      <td>1.836914</td>
      <td>0.312734</td>
      <td>0.299921</td>
      <td>16.328490</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.274427e+07</td>
      <td>0.496869</td>
      <td>1.285034</td>
      <td>3.653698</td>
      <td>0.708122</td>
      <td>66.632736</td>
      <td>70.136002</td>
      <td>0.493288</td>
      <td>13.212569</td>
      <td>0.462812</td>
      <td>0.031257</td>
      <td>2.801119</td>
      <td>1.399622</td>
      <td>0.004878</td>
      <td>16.068902</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.212700e+04</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.852087e+07</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.990000</td>
      <td>1.000000</td>
      <td>114.000000</td>
      <td>112.000000</td>
      <td>1.000000</td>
      <td>6.500000</td>
      <td>0.000000</td>
      <td>0.500000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>8.750000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>5.673150e+07</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.610000</td>
      <td>1.000000</td>
      <td>162.000000</td>
      <td>162.000000</td>
      <td>1.000000</td>
      <td>9.500000</td>
      <td>0.000000</td>
      <td>0.500000</td>
      <td>1.350000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>11.800000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>8.537404e+07</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>3.070000</td>
      <td>1.000000</td>
      <td>233.000000</td>
      <td>233.000000</td>
      <td>2.000000</td>
      <td>14.500000</td>
      <td>0.500000</td>
      <td>0.500000</td>
      <td>2.450000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>17.800000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.134863e+08</td>
      <td>2.000000</td>
      <td>6.000000</td>
      <td>33.960000</td>
      <td>99.000000</td>
      <td>265.000000</td>
      <td>265.000000</td>
      <td>4.000000</td>
      <td>999.990000</td>
      <td>4.500000</td>
      <td>0.500000</td>
      <td>200.000000</td>
      <td>19.100000</td>
      <td>0.300000</td>
      <td>1200.290000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = df[df["RatecodeID"] <= 6]
df.describe()
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
      <th>Unnamed: 0</th>
      <th>VendorID</th>
      <th>passenger_count</th>
      <th>trip_distance</th>
      <th>RatecodeID</th>
      <th>PULocationID</th>
      <th>DOLocationID</th>
      <th>payment_type</th>
      <th>fare_amount</th>
      <th>extra</th>
      <th>mta_tax</th>
      <th>tip_amount</th>
      <th>tolls_amount</th>
      <th>improvement_surcharge</th>
      <th>total_amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>2.268400e+04</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
      <td>22684.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.675971e+07</td>
      <td>1.555987</td>
      <td>1.642303</td>
      <td>2.915080</td>
      <td>1.038926</td>
      <td>162.417254</td>
      <td>161.540028</td>
      <td>1.335567</td>
      <td>13.039048</td>
      <td>0.333737</td>
      <td>0.498038</td>
      <td>1.836995</td>
      <td>0.312748</td>
      <td>0.299921</td>
      <td>16.325771</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.274457e+07</td>
      <td>0.496867</td>
      <td>1.285016</td>
      <td>3.653728</td>
      <td>0.280022</td>
      <td>66.630791</td>
      <td>70.134248</td>
      <td>0.493294</td>
      <td>13.205991</td>
      <td>0.462817</td>
      <td>0.031258</td>
      <td>2.801154</td>
      <td>1.399651</td>
      <td>0.004879</td>
      <td>16.064038</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.212700e+04</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.852071e+07</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.990000</td>
      <td>1.000000</td>
      <td>114.000000</td>
      <td>112.000000</td>
      <td>1.000000</td>
      <td>6.500000</td>
      <td>0.000000</td>
      <td>0.500000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>8.750000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>5.673222e+07</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.610000</td>
      <td>1.000000</td>
      <td>162.000000</td>
      <td>162.000000</td>
      <td>1.000000</td>
      <td>9.500000</td>
      <td>0.000000</td>
      <td>0.500000</td>
      <td>1.350000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>11.800000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>8.537428e+07</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>3.070000</td>
      <td>1.000000</td>
      <td>233.000000</td>
      <td>233.000000</td>
      <td>2.000000</td>
      <td>14.500000</td>
      <td>0.500000</td>
      <td>0.500000</td>
      <td>2.450000</td>
      <td>0.000000</td>
      <td>0.300000</td>
      <td>17.800000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.134863e+08</td>
      <td>2.000000</td>
      <td>6.000000</td>
      <td>33.960000</td>
      <td>5.000000</td>
      <td>265.000000</td>
      <td>265.000000</td>
      <td>4.000000</td>
      <td>999.990000</td>
      <td>4.500000</td>
      <td>0.500000</td>
      <td>200.000000</td>
      <td>19.100000</td>
      <td>0.300000</td>
      <td>1200.290000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#==> ENTER YOUR CODE HERE
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 22684 entries, 0 to 22698
    Data columns (total 18 columns):
     #   Column                 Non-Null Count  Dtype  
    ---  ------                 --------------  -----  
     0   Unnamed: 0             22684 non-null  int64  
     1   VendorID               22684 non-null  int64  
     2   tpep_pickup_datetime   22684 non-null  object 
     3   tpep_dropoff_datetime  22684 non-null  object 
     4   passenger_count        22684 non-null  int64  
     5   trip_distance          22684 non-null  float64
     6   RatecodeID             22684 non-null  int64  
     7   store_and_fwd_flag     22684 non-null  object 
     8   PULocationID           22684 non-null  int64  
     9   DOLocationID           22684 non-null  int64  
     10  payment_type           22684 non-null  int64  
     11  fare_amount            22684 non-null  float64
     12  extra                  22684 non-null  float64
     13  mta_tax                22684 non-null  float64
     14  tip_amount             22684 non-null  float64
     15  tolls_amount           22684 non-null  float64
     16  improvement_surcharge  22684 non-null  float64
     17  total_amount           22684 non-null  float64
    dtypes: float64(8), int64(7), object(3)
    memory usage: 3.3+ MB


**tpep_pickup_datetime is an object type, it needs to be converted to datetime**

**tpep_dropoff_datetime is an object type, it needs to be converted to datetime**

**store_and_fwd_flag is an object type, it needs to be converted to boolean**

### Task 2b. Assess whether dimensions and measures are correct

On the data source page in Tableau, double check the data types for the applicable columns you selected on the previous step. Pay close attention to the dimensions and measures to assure they are correct. 

In Python, consider the data types of the columns. *Consider:* Do they make sense? 

Review the link provided in the previous activity instructions to create the required Tableau visualization. 

### Task 2c. Select visualization type(s)

Select data visualization types that will help you understand and explain the data.

Now that you know which data columns you’ll use, it is time to decide which data visualization makes the most sense for EDA of the TLC dataset. What type of data visualization(s) would be most helpful? 

* Line graph
* Bar chart
* Box plot
* Histogram
* Heat map
* Scatter plot
* A geographic map


Box plot, scatterplot histograms, heatmap, and bar charts

<img src="images/Construct.png" width="100" height="100" align=left>

## PACE: Construct 

Consider the questions in your PACE Strategy Document to reflect on the Construct stage.

### Task 3. Data visualization

You’ve assessed your data, and decided on which data variables are most applicable. It’s time to plot your visualization(s)!


### Boxplots

Perform a check for outliers on relevant columns such as trip distance and trip duration. Remember, some of the best ways to identify the presence of outliers in data are box plots and histograms. 

**Note:** Remember to convert your date columns to datetime in order to derive total trip duration.  


```python
# Convert data columns to datetime
#==> ENTER YOUR CODE HERE
df["tpep_pickup_datetime"] = pd.to_datetime(df["tpep_pickup_datetime"])
df["tpep_dropoff_datetime"] = pd.to_datetime(df["tpep_dropoff_datetime"])
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 22684 entries, 0 to 22698
    Data columns (total 18 columns):
     #   Column                 Non-Null Count  Dtype         
    ---  ------                 --------------  -----         
     0   Unnamed: 0             22684 non-null  int64         
     1   VendorID               22684 non-null  int64         
     2   tpep_pickup_datetime   22684 non-null  datetime64[ns]
     3   tpep_dropoff_datetime  22684 non-null  datetime64[ns]
     4   passenger_count        22684 non-null  int64         
     5   trip_distance          22684 non-null  float64       
     6   RatecodeID             22684 non-null  int64         
     7   store_and_fwd_flag     22684 non-null  object        
     8   PULocationID           22684 non-null  int64         
     9   DOLocationID           22684 non-null  int64         
     10  payment_type           22684 non-null  int64         
     11  fare_amount            22684 non-null  float64       
     12  extra                  22684 non-null  float64       
     13  mta_tax                22684 non-null  float64       
     14  tip_amount             22684 non-null  float64       
     15  tolls_amount           22684 non-null  float64       
     16  improvement_surcharge  22684 non-null  float64       
     17  total_amount           22684 non-null  float64       
    dtypes: datetime64[ns](2), float64(8), int64(7), object(1)
    memory usage: 3.3+ MB


**trip distance**


```python
# Create box plot of trip_distance

sns.boxplot(data = df,
            x = 'trip_distance')
plt.xlabel('trip Distance')
plt.title('Trip Distance Box Plot')
```




    Text(0.5, 1.0, 'Trip Distance Box Plot')




![png](output_38_1.png)



```python
# Create histogram of trip_distance
#==> ENTER YOUR CODE HERE

sns.histplot(data = df, 
             x = 'trip_distance',
            binrange = (0, 25),
            binwidth = 1)
plt.title("Trip Distance Histogram")
plt.show
```




    <function matplotlib.pyplot.show(*args, **kw)>




![png](output_39_1.png)


**total amount**


```python
# Create box plot of total_amount
#==> ENTER YOUR CODE HERE

sns.boxplot(data = df, 
           x = 'total_amount')
plt.xlabel("Total Amount")
plt.title("Total Amount Box Plot")
```




    Text(0.5, 1.0, 'Total Amount Box Plot')




![png](output_41_1.png)



```python
# Create histogram of total_amount
#==> ENTER YOUR CODE HERE
sns.histplot(data = df,
            x = "total_amount",
            binrange = (0, 100),
            binwidth = 5,
            alpha = 1)
plt.xlabel("Total Amount")
plt.title("Total Amount Histogram")
```




    Text(0.5, 1.0, 'Total Amount Histogram')




![png](output_42_1.png)


**tip amount**


```python
# Create box plot of tip_amount
#==> ENTER YOUR CODE HERE
sns.boxplot(data = df,
           x = "tip_amount")
plt.xlabel("Tip Amount")
plt.title("Tip Amount Box Plot")
```




    Text(0.5, 1.0, 'Tip Amount Box Plot')




![png](output_44_1.png)



```python
# Create histogram of tip_amount
#==> ENTER YOUR CODE HERE
sns.histplot(data = df,
            x = "tip_amount",
            binrange = (0, 15),
            binwidth = 1)
plt.xlabel("Tip Amount")
plt.title("Tip Amount Histogram")
```




    Text(0.5, 1.0, 'Tip Amount Histogram')




![png](output_45_1.png)


**tip_amount by vendor**


```python
# Create histogram of tip_amount by vendor
#==> ENTER YOUR CODE HERE

sns.histplot(data = df,
            x = "tip_amount",
            hue = "VendorID",
            multiple = "dodge",
            palette = ["red", "green"],
            binrange = (0, 20),
            binwidth = 2)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7cd0221fb290>




![png](output_47_1.png)


Next, zoom in on the upper end of the range of tips to check whether vendor one gets noticeably more of the most generous tips.


```python
# Create histogram of tip_amount by vendor for tips > $10 
#==> ENTER YOUR CODE HERE
sns.histplot(data = df[df["tip_amount"] > 10],
            x = "tip_amount",
            hue = "VendorID",
            multiple = "stack",
            palette = ["red", "green"],
            binrange = (10, 60),
            binwidth = 2.5)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7cd022121510>




![png](output_49_1.png)


**Mean tips by passenger count**

Examine the unique values in the `passenger_count` column.


```python
#==> ENTER YOUR CODE HERE
df["passenger_count"].unique()
```




    array([6, 1, 2, 4, 5, 3, 0])




```python
# Calculate mean tips by passenger_count
#==> ENTER YOUR CODE HERE
mean_tips_by_passenger_count = pd.DataFrame(df.groupby("passenger_count"
                                         ).mean()["tip_amount"])
mean_tips_by_passenger_count['index_col'] = mean_tips_by_passenger_count.index
mean_tips_by_passenger_count.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 7 entries, 0 to 6
    Data columns (total 2 columns):
     #   Column      Non-Null Count  Dtype  
    ---  ------      --------------  -----  
     0   tip_amount  7 non-null      float64
     1   index_col   7 non-null      int64  
    dtypes: float64(1), int64(1)
    memory usage: 168.0 bytes



```python
# Create bar plot for mean tips by passenger count
#==> ENTER YOUR CODE HERE
sns.barplot(data = mean_tips_by_passenger_count,
            x = "index_col",
            y = "tip_amount")
plt.axhline(df['tip_amount'].mean(), ls='--', color='red', label='global mean')
plt.xlabel("Passenger Count")
plt.ylabel("Mean Tips")
plt.title("bar plot for mean tips by passenger count")
```




    Text(0.5, 1.0, 'bar plot for mean tips by passenger count')




![png](output_53_1.png)


**Create month and day columns**


```python
# Create a month column
#==> ENTER YOUR CODE HERE

df["month"] = df["tpep_pickup_datetime"].dt.month_name().str.slice(stop = 3)

# Create a day column
#==> ENTER YOUR CODE HERE

df["weekday"] = df["tpep_pickup_datetime"
              ].dt.day_name().str.slice(stop = 3)
df.head()

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
      <th>Unnamed: 0</th>
      <th>VendorID</th>
      <th>tpep_pickup_datetime</th>
      <th>tpep_dropoff_datetime</th>
      <th>passenger_count</th>
      <th>trip_distance</th>
      <th>RatecodeID</th>
      <th>store_and_fwd_flag</th>
      <th>PULocationID</th>
      <th>DOLocationID</th>
      <th>payment_type</th>
      <th>fare_amount</th>
      <th>extra</th>
      <th>mta_tax</th>
      <th>tip_amount</th>
      <th>tolls_amount</th>
      <th>improvement_surcharge</th>
      <th>total_amount</th>
      <th>month</th>
      <th>weekday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>24870114</td>
      <td>2</td>
      <td>2017-03-25 08:55:43</td>
      <td>2017-03-25 09:09:47</td>
      <td>6</td>
      <td>3.34</td>
      <td>1</td>
      <td>N</td>
      <td>100</td>
      <td>231</td>
      <td>1</td>
      <td>13.0</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>2.76</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>16.56</td>
      <td>Mar</td>
      <td>Sat</td>
    </tr>
    <tr>
      <th>1</th>
      <td>35634249</td>
      <td>1</td>
      <td>2017-04-11 14:53:28</td>
      <td>2017-04-11 15:19:58</td>
      <td>1</td>
      <td>1.80</td>
      <td>1</td>
      <td>N</td>
      <td>186</td>
      <td>43</td>
      <td>1</td>
      <td>16.0</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>4.00</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>20.80</td>
      <td>Apr</td>
      <td>Tue</td>
    </tr>
    <tr>
      <th>2</th>
      <td>106203690</td>
      <td>1</td>
      <td>2017-12-15 07:26:56</td>
      <td>2017-12-15 07:34:08</td>
      <td>1</td>
      <td>1.00</td>
      <td>1</td>
      <td>N</td>
      <td>262</td>
      <td>236</td>
      <td>1</td>
      <td>6.5</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>1.45</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>8.75</td>
      <td>Dec</td>
      <td>Fri</td>
    </tr>
    <tr>
      <th>3</th>
      <td>38942136</td>
      <td>2</td>
      <td>2017-05-07 13:17:59</td>
      <td>2017-05-07 13:48:14</td>
      <td>1</td>
      <td>3.70</td>
      <td>1</td>
      <td>N</td>
      <td>188</td>
      <td>97</td>
      <td>1</td>
      <td>20.5</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>6.39</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>27.69</td>
      <td>May</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>4</th>
      <td>30841670</td>
      <td>2</td>
      <td>2017-04-15 23:32:20</td>
      <td>2017-04-15 23:49:03</td>
      <td>1</td>
      <td>4.37</td>
      <td>1</td>
      <td>N</td>
      <td>4</td>
      <td>112</td>
      <td>2</td>
      <td>16.5</td>
      <td>0.5</td>
      <td>0.5</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.3</td>
      <td>17.80</td>
      <td>Apr</td>
      <td>Sat</td>
    </tr>
  </tbody>
</table>
</div>



**Plot total ride count by month**

Begin by calculating total ride count by month.


```python
# Get total number of rides for each month
#==> ENTER YOUR CODE HERE

df["month"] = pd.Categorical(df["month"]
                             , categories = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]
                             , ordered = True)

rides_per_month = pd.DataFrame(df.groupby("month")
                               .count()
                               .reset_index()).rename(columns = {"Unnamed: 0":"number of rides"}
                                                     )[["month", "number of rides"]]
rides_per_month
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
      <th>month</th>
      <th>number of rides</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jan</td>
      <td>1996</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Feb</td>
      <td>1768</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Mar</td>
      <td>2048</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apr</td>
      <td>2016</td>
    </tr>
    <tr>
      <th>4</th>
      <td>May</td>
      <td>2012</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Jun</td>
      <td>1963</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jul</td>
      <td>1695</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Aug</td>
      <td>1724</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Sep</td>
      <td>1733</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Oct</td>
      <td>2026</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Nov</td>
      <td>1842</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Dec</td>
      <td>1861</td>
    </tr>
  </tbody>
</table>
</div>



Reorder the results to put the months in calendar order.


```python
# Create a bar plot of total rides per month
#==> ENTER YOUR CODE HERE
sns.barplot(data = rides_per_month, x = "month", y = "number of rides")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x75f063ff3b90>




![png](output_59_1.png)


**Plot total ride count by day**

Repeat the above process, but now calculate the total rides by day of the week.


```python
# Repeat the above process, this time for rides by day
#==> ENTER YOUR CODE HERE

df["weekday"] = pd.Categorical(df["weekday"]
                               , categories = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
                               , ordered = True)

rides_per_day = pd.DataFrame(df.groupby("weekday")
                             .count()
                             .reset_index()).rename(columns = {"Unnamed: 0" : "rides per day"})[["weekday", "rides per day"]]

rides_per_day
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
      <th>weekday</th>
      <th>rides per day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mon</td>
      <td>2929</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tue</td>
      <td>3196</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Wed</td>
      <td>3388</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Thu</td>
      <td>3400</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Fri</td>
      <td>3411</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sat</td>
      <td>3364</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Sun</td>
      <td>2996</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create bar plot for ride count by day
#==> ENTER YOUR CODE HERE

sns.barplot(data = rides_per_day
            , x = "weekday"
            , y = "rides per day")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x75f0642adb50>




![png](output_62_1.png)


**Plot total revenue by day of the week**

Repeat the above process, but now calculate the total revenue by day of the week.


```python
# Repeat the process, this time for total revenue by day
#==> ENTER YOUR CODE HERE

total_revenue_by_day = pd.DataFrame(df
                                    .groupby("weekday")
                                    .agg({"total_amount": "sum"})
                                    .reset_index()).rename(columns = {"total_amount" : "total revenue"})

total_revenue_by_day
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
      <th>weekday</th>
      <th>total revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mon</td>
      <td>49582.47</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tue</td>
      <td>52452.94</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Wed</td>
      <td>55317.57</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Thu</td>
      <td>57190.51</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Fri</td>
      <td>55830.34</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sat</td>
      <td>51325.30</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Sun</td>
      <td>48634.66</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create bar plot of total revenue by day
#==> ENTER YOUR CODE HERE

sns.barplot(data = total_revenue_by_day
           , x = "weekday"
           , y = "total revenue")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x75f06429aa90>




![png](output_65_1.png)


**Plot total revenue by month**


```python
# Repeat the process, this time for total revenue by month
#==> ENTER YOUR CODE HERE

total_revenue_by_month = pd.DataFrame(df
                                    .groupby("month")
                                    .agg({"total_amount": "sum"})
                                    .reset_index()).rename(columns = {"total_amount" : "total revenue"})

total_revenue_by_month
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
      <th>month</th>
      <th>total revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jan</td>
      <td>31739.05</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Feb</td>
      <td>28943.69</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Mar</td>
      <td>33091.69</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apr</td>
      <td>32059.14</td>
    </tr>
    <tr>
      <th>4</th>
      <td>May</td>
      <td>33832.38</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Jun</td>
      <td>32924.82</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jul</td>
      <td>26626.24</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Aug</td>
      <td>27759.56</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Sep</td>
      <td>28211.18</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Oct</td>
      <td>33070.63</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Nov</td>
      <td>30804.74</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Dec</td>
      <td>31270.67</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a bar plot of total revenue by month
#==> ENTER YOUR CODE HERE

sns.barplot(data = total_revenue_by_month
           , x = "month"
           , y = "total revenue")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x75f064c7af90>




![png](output_68_1.png)


#### Scatter plot

You can create a scatterplot in Tableau Public, which can be easier to manipulate and present. If you'd like step by step instructions, you can review the following link. Those instructions create a scatterplot showing the relationship between total_amount and trip_distance. Consider adding the Tableau visualization to your executive summary, and adding key insights from your findings on those two variables.

[Tableau visualization guidelines](https://docs.google.com/document/d/1pcfUlttD2Y_a9A4VrKPzikZWCAfFLsBAhuKuomjcUjA/template/preview)

**Plot mean trip distance by drop-off location**


```python
# Get number of unique drop-off location IDs
#==> ENTER YOUR CODE HERE

print("There are "
      , df["DOLocationID"].nunique()
      , "unique drop-off location IDs")

```

    There are  216 unique drop-off location IDs



```python
# Calculate the mean trip distance for each drop-off location
#==> ENTER YOUR CODE HERE

mean_trip_distance_by_DOLocationID = df.groupby("DOLocationID"
                                               ).agg({"trip_distance" : "mean"}
                                                    ).reset_index().rename(columns = {"trip_distance": "mean trip distance"}
                                                                          ).sort_values(by = "mean trip distance"
                                                                                        , ascending = True)
mean_trip_distance_by_DOLocationID
# Sort the results in descending order by mean trip distance
#==> ENTER YOUR CODE HERE

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
      <th>DOLocationID</th>
      <th>mean trip distance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>164</th>
      <td>207</td>
      <td>1.200000</td>
    </tr>
    <tr>
      <th>154</th>
      <td>193</td>
      <td>1.390556</td>
    </tr>
    <tr>
      <th>192</th>
      <td>237</td>
      <td>1.558983</td>
    </tr>
    <tr>
      <th>189</th>
      <td>234</td>
      <td>1.727806</td>
    </tr>
    <tr>
      <th>109</th>
      <td>137</td>
      <td>1.818852</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>40</th>
      <td>51</td>
      <td>17.310000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>11</td>
      <td>17.945000</td>
    </tr>
    <tr>
      <th>167</th>
      <td>210</td>
      <td>20.500000</td>
    </tr>
    <tr>
      <th>21</th>
      <td>29</td>
      <td>21.650000</td>
    </tr>
    <tr>
      <th>16</th>
      <td>23</td>
      <td>24.275000</td>
    </tr>
  </tbody>
</table>
<p>216 rows × 2 columns</p>
</div>




```python
# Create a bar plot of mean trip distances by drop-off location in ascending order by distance
#==> ENTER YOUR CODE HERE
sns.barplot(data = mean_trip_distance_by_DOLocationID
            , x = "DOLocationID"
            , y = "mean trip distance"
            )
```




    <matplotlib.axes._subplots.AxesSubplot at 0x75f0642edad0>




![png](output_75_1.png)


## BONUS CONTENT

To confirm your conclusion, consider the following experiment:
1. Create a sample of coordinates from a normal distribution&mdash;in this case 1,500 pairs of points from a normal distribution with a mean of 10 and a standard deviation of 5
2. Calculate the distance between each pair of coordinates 
3. Group the coordinates by endpoint and calculate the mean distance between that endpoint and all other points it was paired with
4. Plot the mean distance for each unique endpoint


```python
#BONUS CONTENT

#1. Generate random points on a 2D plane from a normal distribution
#==> ENTER YOUR CODE HERE

# 2. Calculate Euclidean distances between points in first half and second half of array
#==> ENTER YOUR CODE HERE

# 3. Group the coordinates by "drop-off location", compute mean distance
#==> ENTER YOUR CODE HERE

# 4. Plot the mean distance between each endpoint ("drop-off location") and all points it connected to
#==> ENTER YOUR CODE HERE
```

**Histogram of rides by drop-off location**

First, check to whether the drop-off locations IDs are consecutively numbered. For instance, does it go 1, 2, 3, 4..., or are some numbers missing (e.g., 1, 3, 4...). If numbers aren't all consecutive, the histogram will look like some locations have very few or no rides when in reality there's no bar because there's no location. 


```python
# Check if all drop-off locations are consecutively numbered
#==> ENTER YOUR CODE HERE
```

To eliminate the spaces in the historgram that these missing numbers would create, sort the unique drop-off location values, then convert them to strings. This will make the histplot function display all bars directly next to each other. 


```python
#==> ENTER YOUR CODE HERE
# DOLocationID column is numeric, so sort in ascending order
#==> ENTER YOUR CODE HERE

# Convert to string
#==> ENTER YOUR CODE HERE

# Plot
#==> ENTER YOUR CODE HERE
```

<img src="images/Execute.png" width="100" height="100" align=left>

## PACE: Execute 

Consider the questions in your PACE Strategy Document to reflect on the Execute stage.

### Task 4a. Results and evaluation

Having built visualizations in Tableau and in Python, what have you learned about the dataset? What other questions have your visualizations uncovered that you should pursue? 

***Pro tip:*** Put yourself in your client's perspective, what would they want to know? 

Use the following code fields to pursue any additional EDA based on the visualizations you've already plotted. Also use the space to make sure your visualizations are clean, easily understandable, and accessible. 

***Ask yourself:*** Did you consider color, contrast, emphasis, and labeling?



==> ENTER YOUR RESPONSE HERE

I have learned .... 

My other questions are .... 

My client would likely want to know ... 



```python
#==> ENTER YOUR CODE HERE
```


```python
#==> ENTER YOUR CODE HERE
```

### Task 4b. Conclusion
*Make it professional and presentable*

You have visualized the data you need to share with the director now. Remember, the goal of a data visualization is for an audience member to glean the information on the chart in mere seconds.

*Questions to ask yourself for reflection:*
Why is it important to conduct Exploratory Data Analysis? Why are the data visualizations provided in this notebook useful?



EDA is important because ... 
==> ENTER YOUR RESPONSE HERE


Visualizations helped me understand ..
==> ENTER YOUR RESPONSE HERE


You’ve now completed professional data visualizations according to a business need. Well done! 

**Congratulations!** You've completed this lab. However, you may not notice a green check mark next to this item on Coursera's platform. Please continue your progress regardless of the check mark. Just click on the "save" icon at the top of this notebook to ensure your work has been logged.
