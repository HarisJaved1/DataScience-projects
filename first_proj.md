# First Project on Random User Data

### Objectives
> - Import & Explore
> - Clean the data
> - Visualize & Answer some questions


```python
# Import libraries
import pandas as pd
import numpy as np
import matplotlib.patches as mpatches
import matplotlib.pyplot as plt
import seaborn as sns 
```

### **Importing & Exploring**


```python
# Importing data 
df1 = pd.read_csv('Chilla_data2_for_plots.csv')
df1.head(3)
```





</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Gender</th>
      <th>Location</th>
      <th>Age</th>
      <th>Qualification_completed</th>
      <th>field_of_study</th>
      <th>Purpose_for_chilla</th>
      <th>What are you?</th>
      <th>Blood group</th>
      <th>Which mobile sim do you use</th>
      <th>Prepaid or Postpaid</th>
      <th>...</th>
      <th>Your favorite programming language?</th>
      <th>Marital Status?</th>
      <th>Are you Vaccinated?</th>
      <th>Where do you live?</th>
      <th>Research/Working experience (Float/Int) years</th>
      <th>Age (years)-Float/Int</th>
      <th>Your Weight in kg? (float)</th>
      <th>Height in cm? Freelancer- (Float)</th>
      <th>How many hours you code a day? (int) e.g: 5,4,3</th>
      <th>Light kitni der band hti hy? int</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Male</td>
      <td>Pakistan</td>
      <td>36-40</td>
      <td>Masters</td>
      <td>Natural Sciences</td>
      <td>to boost my skill set</td>
      <td>Unemplyed</td>
      <td>B+</td>
      <td>U-fone</td>
      <td>Prepaid</td>
      <td>...</td>
      <td>Python</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Urbun</td>
      <td>5</td>
      <td>38.00</td>
      <td>77.0</td>
      <td>179.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Male</td>
      <td>Pakistan</td>
      <td>26-30</td>
      <td>Bachelors</td>
      <td>CS/IT</td>
      <td>to boost my skill set</td>
      <td>Student</td>
      <td>B+</td>
      <td>U-fone</td>
      <td>Prepaid</td>
      <td>...</td>
      <td>Python</td>
      <td>No</td>
      <td>Yes</td>
      <td>Urbun</td>
      <td>1</td>
      <td>25.00</td>
      <td>53.6</td>
      <td>178.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Male</td>
      <td>Pakistan</td>
      <td>31-35</td>
      <td>Masters</td>
      <td>Enginnering</td>
      <td>Switch my field of study</td>
      <td>Employed</td>
      <td>B+</td>
      <td>Zong</td>
      <td>Prepaid</td>
      <td>...</td>
      <td>Python</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Urbun</td>
      <td>5.5</td>
      <td>31.34</td>
      <td>93.0</td>
      <td>173.0</td>
      <td>2.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 23 columns</p>
</div>




```python
# Shape of dataset
df1.shape
```




    (375, 23)




```python
#Stats of the data
df1.describe() 
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
      <th>Age (years)-Float/Int</th>
      <th>Your Weight in kg? (float)</th>
      <th>Height in cm? Freelancer- (Float)</th>
      <th>How many hours you code a day? (int) e.g: 5,4,3</th>
      <th>Light kitni der band hti hy? int</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>375.000000</td>
      <td>375.000000</td>
      <td>375.000000</td>
      <td>375.000000</td>
      <td>375.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>27.576933</td>
      <td>69.321147</td>
      <td>162.679282</td>
      <td>2.976027</td>
      <td>3.618667</td>
    </tr>
    <tr>
      <th>std</th>
      <td>7.224460</td>
      <td>16.264434</td>
      <td>172.246844</td>
      <td>2.088115</td>
      <td>7.407986</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>7.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>24.000000</td>
      <td>58.050000</td>
      <td>158.000000</td>
      <td>2.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>27.000000</td>
      <td>68.300000</td>
      <td>169.000000</td>
      <td>3.000000</td>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>31.000000</td>
      <td>78.500000</td>
      <td>175.225000</td>
      <td>4.000000</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>90.000000</td>
      <td>161.000000</td>
      <td>1661.160000</td>
      <td>18.000000</td>
      <td>72.000000</td>
    </tr>
  </tbody>
</table>
</div>



### **Cleaning & Trimming**


```python
# Checking for null values
df1.isna().sum()
```




    Gender                                             0
    Location                                           0
    Age                                                0
    Qualification_completed                            0
    field_of_study                                     0
    Purpose_for_chilla                                 0
    What are you?                                      0
    Blood group                                        0
    Which mobile sim do you use                        0
    Prepaid or Postpaid                                0
    Which PC are you using?                            0
    Do you wear glasses?                               0
    When did you write your first line of code?        0
    Your favorite programming language?                0
    Marital Status?                                    0
    Are you Vaccinated?                                0
    Where do you live?                                 0
    Research/Working experience (Float/Int) years      0
    Age (years)-Float/Int                              0
    Your Weight in kg? (float)                         0
    Height in cm? Freelancer- (Float)                  0
    How many hours you code a day? (int) e.g: 5,4,3    0
    Light kitni der band hti hy? int                   0
    dtype: int64




```python
# Removing unnecessary Columns
clean_df = df1.drop(['Which mobile sim do you use', 'Prepaid or Postpaid' ,'Do you wear glasses?', 'Age'], axis=1)
clean_df.head(2)
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
      <th>Gender</th>
      <th>Location</th>
      <th>Qualification_completed</th>
      <th>field_of_study</th>
      <th>Purpose_for_chilla</th>
      <th>What are you?</th>
      <th>Blood group</th>
      <th>Which PC are you using?</th>
      <th>When did you write your first line of code?</th>
      <th>Your favorite programming language?</th>
      <th>Marital Status?</th>
      <th>Are you Vaccinated?</th>
      <th>Where do you live?</th>
      <th>Research/Working experience (Float/Int) years</th>
      <th>Age (years)-Float/Int</th>
      <th>Your Weight in kg? (float)</th>
      <th>Height in cm? Freelancer- (Float)</th>
      <th>How many hours you code a day? (int) e.g: 5,4,3</th>
      <th>Light kitni der band hti hy? int</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Male</td>
      <td>Pakistan</td>
      <td>Masters</td>
      <td>Natural Sciences</td>
      <td>to boost my skill set</td>
      <td>Unemplyed</td>
      <td>B+</td>
      <td>Apna Laptop</td>
      <td>&gt;3 years ago</td>
      <td>Python</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Urbun</td>
      <td>5</td>
      <td>38.0</td>
      <td>77.0</td>
      <td>179.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Male</td>
      <td>Pakistan</td>
      <td>Bachelors</td>
      <td>CS/IT</td>
      <td>to boost my skill set</td>
      <td>Student</td>
      <td>B+</td>
      <td>Apna Laptop</td>
      <td>&gt;3 years ago</td>
      <td>Python</td>
      <td>No</td>
      <td>Yes</td>
      <td>Urbun</td>
      <td>1</td>
      <td>25.0</td>
      <td>53.6</td>
      <td>178.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Renaming Big columns names
clean_df.rename(columns = {'Which PC are you using?': 'your device', 'When did you write your first line of code?' : 'first code', 'Your favorite programming language?' : 'favrt language', 'How many hours you code a day? (int) e.g: 5,4,3': 'hours coding', 'Height in cm? Freelancer- (Float)':'height(cm)', 'Your Weight in kg? (float)':'weight(kg)', 'Research/Working experience (Float/Int) years' : 'experience', 'Where do you live?' : 'location','Light kitni der band hti hy? int': 'light off','Age (years)-Float/Int': 'age' },inplace=True)
clean_df.head(2)
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
      <th>Gender</th>
      <th>Location</th>
      <th>Qualification_completed</th>
      <th>field_of_study</th>
      <th>Purpose_for_chilla</th>
      <th>What are you?</th>
      <th>Blood group</th>
      <th>your device</th>
      <th>first code</th>
      <th>favrt language</th>
      <th>Marital Status?</th>
      <th>Are you Vaccinated?</th>
      <th>location</th>
      <th>experience</th>
      <th>age</th>
      <th>weight(kg)</th>
      <th>height(cm)</th>
      <th>hours coding</th>
      <th>light off</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Male</td>
      <td>Pakistan</td>
      <td>Masters</td>
      <td>Natural Sciences</td>
      <td>to boost my skill set</td>
      <td>Unemplyed</td>
      <td>B+</td>
      <td>Apna Laptop</td>
      <td>&gt;3 years ago</td>
      <td>Python</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Urbun</td>
      <td>5</td>
      <td>38.0</td>
      <td>77.0</td>
      <td>179.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Male</td>
      <td>Pakistan</td>
      <td>Bachelors</td>
      <td>CS/IT</td>
      <td>to boost my skill set</td>
      <td>Student</td>
      <td>B+</td>
      <td>Apna Laptop</td>
      <td>&gt;3 years ago</td>
      <td>Python</td>
      <td>No</td>
      <td>Yes</td>
      <td>Urbun</td>
      <td>1</td>
      <td>25.0</td>
      <td>53.6</td>
      <td>178.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Checkig for outliers in height column
sns.boxplot(y='height(cm)', data=clean_df)
```




    <AxesSubplot:ylabel='height(cm)'>




    
![png](output_11_1.png)
    



```python
# Removing Outliers
df_outlier = clean_df[clean_df['height(cm)'] >= 300]
clean_df = clean_df.drop(df_outlier.index, axis=0)

```


```python
# After removing outliers
sns.boxplot(x='height(cm)', data=clean_df)
```




    <AxesSubplot:xlabel='height(cm)'>




    
![png](output_13_1.png)
    


> Here i found that the data in height was incorrect. Meaning some data was in **CM** and some was in **FEET** \
> The dataset was already small so i did not remove more rows instead i remove the columns.


```python
# Removing Height and Weight column
clean_df = clean_df.drop(['height(cm)','weight(kg)'], axis=1)

```


```python
clean_df.columns

```




    Index(['Gender', 'Location', 'Qualification_completed', 'field_of_study',
           'Purpose_for_chilla', 'What are you?', 'Blood group ', 'your device',
           'first code', 'favrt language', 'Marital Status?',
           'Are you Vaccinated?', 'location', 'experience', 'age', 'hours coding',
           'light off'],
          dtype='object')



### **Visualization & Answering questions**


```python
# Which Gender does more coding(in this dataset)
sns.barplot(x='Gender', y='hours coding', data = clean_df, errorbar=None)
plt.title('Which Gender does more coding')
```




    Text(0.5, 1.0, 'Which Gender does more coding')




    
![png](output_18_1.png)
    



```python
# Most used language by People in this dataset
sns.countplot(x='favrt language', data=clean_df)
plt.title("The Most Used programming language")
```




    Text(0.5, 1.0, 'The Most Used programming language')




    
![png](output_19_1.png)
    



```python
# Which area does have more electricity outage
sns.barplot(x='location', y='light off', data=clean_df, errorbar=None)
plt.title('Most Light off in which area')
```




    Text(0.5, 1.0, 'Most Light off in which area')




    
![png](output_20_1.png)
    



```python
# Which Field want to with this chilla (Chilla Means Course)
sns.histplot(x='field_of_study', hue='Purpose_for_chilla' , data=clean_df, alpha=0.4)
plt.xticks(rotation=90)
```




    ([0, 1, 2, 3, 4, 5, 6, 7, 8],
     [Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, '')])




    
![png](output_21_1.png)
    



```python
clean_df.columns
```




    Index(['Gender', 'Location', 'Qualification_completed', 'field_of_study',
           'Purpose_for_chilla', 'What are you?', 'Blood group ', 'your device',
           'first code', 'favrt language', 'Marital Status?',
           'Are you Vaccinated?', 'location', 'experience', 'age', 'hours coding',
           'light off'],
          dtype='object')




```python
# Which age of people are from which area
sns.barplot(y='age', x='location', data=clean_df, errorbar=None)
plt.title("Which age of people are from which area")
```




    Text(0.5, 1.0, 'Which age of people are from which area')




    
![png](output_23_1.png)
    



```python

```
