## working on weather dataset


import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns



wea=pd.read_csv(r'C:\Users\ANCHAL\Documents\Weather Data.csv' ,encoding ='latin-1')
wea

wea.columns #it shows the name of each columns

wea.shape # its shows the total no of rows and no.of colums of the dataframe

wea.head() #it shows the first N rows in the data (by default,N=5)

wea.index #this attribute provides the index of the dataframe

wea.dtypes #its shows the data type of each column

wea['Weather'].unique() #In a columns it shows all the unique values .it can be applied on a single column only,not on the whole dataframe.

wea.nunique() # it show the total no.of unique values in each column.it can be applied on a single column as well as on whole dataframe.

wea.count () #It shows the total no of non -null values in each in each column.it can be applied on a single as well as on whole dataframe


wea['Weather'].value_counts()

wea.info() #provides basic info about dataset 

## 1). Find all the unique 'wind speed' values in the data.

#wea.head(2) #filtering

wea[wea.Weather =='Clear']

wea.nunique()  #type1

wea['Wind Speed_km/h'].nunique()#type 2 find the unique

wea['Wind Speed_km/h'].unique()# unique value...

##  2).Find the number of times when the 'Weather is exactly clear'.

wea.head(3)

#value_count()
wea.Weather.value_counts()


# filterring
wea[wea.Weather =='Clear']

#groupby
wea.groupby('Weather').get_group('Clear')

##  3).Find the number of times when the 'whind seed was exactly 4km/h'.

#filtering
wea[wea['Wind Speed_km/h']==4]

## 4).Find out all the null values in the data

 wea.isnull().sum()

wea.notnull().sum()

## 5). Rename  the column nam 'weather of the dataframe to 'Weather condition'.

wea.rename(columns={'Weather':'Weather Condition'})#this code run for only temporieri  

wea.rename(columns={'Weather':'Weather Condition'},inplace=True)
wea.head()#its works for perment or rename the columns in  originaldata

## 6). what is the mean 'Visibility'?

wea.Visibility_km.median()

wea.Visibility_km.mean()

## 7). What is the standard  Deviation of 'Pressure' in the data?

wea.Press_kPa.std()

## 8).What is the variance of 'Relative Humidity'in this data? 

wea['Rel Hum_%'].var()

## 9). find all instance when 'Snow' was recorded.


#value_count()
#wea.head()
wea['Weather Condition'].value_counts()

#filtering
wea[wea['Weather Condition']=='Snow']

#str.contains
wea[wea['Weather Condition'].str.contains('Snow')]


## 10).find all instance when 'wind speed is above 24'and visibility is 25'

wea[(wea['Wind Speed_km/h']>24)&(wea['Visibility_km']==25)]

## 11). what is the mean value of each column against each 'Weather condition?

wea.groupby ('Weather Condition').mean()

## 12).what is the minimum values of each column agains each 'weather condition'?

wea.groupby ('Weather Condition').min()

wea.groupby ('Weather Condition').max()

## 13).show all the recored where weather condition is fog?

wea[wea['Weather Condition']=='Fog']

## 14).Find instance when 'weather is clear 'or 'visibility is above 40?

 wea[(wea['Weather Condition']=='Clear') | (wea['Visibility_km'] >40)]

## 15).Find all instance when

### A."Weather is clear' and 'relative humidity is greater than 50 or B. 'visibility is above 40'

wea[(wea['Weather Condition']=='clear') & (wea['Rel Hum_%']>50)|(wea['Visibility_km']>40)]









