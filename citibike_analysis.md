

```python
import pandas as pd
```


```python
df_list = []
```


```python
# 2015
df_list.append(pd.read_csv("2015/JC-201509-citibike-tripdata.csv"))
df_list.append(pd.read_csv("2015/JC-201510-citibike-tripdata.csv"))
df_list.append(pd.read_csv("2015/JC-201511-citibike-tripdata.csv"))
```


```python
#2016
for x in range(1,13):
    df_list.append(pd.read_csv(f"2016/JC-2016{x:02}-citibike-tripdata.csv"))
```


```python
#2017
for x in range(1,13):
    df_list.append(pd.read_csv(f"2017/JC-2017{x:02}-citibike-tripdata.csv"))
```


```python
# 2018 below here:
df_list.append(pd.read_csv("2018/201801_citibikejc_tripdata.csv"))
df_list.append(pd.read_csv("2018/201802_citibikejc_tripdata.csv"))
df_list.append(pd.read_csv("2018/201803_citibikejc_tripdata.csv"))
df_list.append(pd.read_csv("2018/JC-201804-citibike-tripdata.csv"))
```


```python
# Fix the inconsistent names in the columns:
dfs_list = []
for x in df_list:
    dfs_list.append(x.rename(index=str, columns={"Bike ID": "bikeid", "End Station ID": "end station id", "End Station Latitude": "end station latitude",
                             "Start Station Longitude": "start station longitude", "End Station Name": "end station name", "Start Station Name" :"start station name", "Gender" : "gender", 
                             "Start Time": "starttime", "Stop Time": "stoptime", "Trip Duration": "tripduration", "User Type": "usertype", "Birth Year" : "birth year", "Start Station ID": "start station id", "Start Station Latitude": "start station latitude", "End Station Longitude": "end station longitude"}))
```


```python
mother_load = pd.concat(dfs_list)
```


```python
mother_load = mother_load.drop("name_localizedValue0", axis=1)
```


```python
mother_load.to_csv("201701-201801_citibike_tripdata.csv")
```


```python
mother_load.count()
```




    bikeid                     652081
    birth year                 605684
    end station id             652081
    end station latitude       652081
    end station longitude      652081
    end station name           652081
    gender                     652081
    start station id           652081
    start station latitude     652081
    start station longitude    652081
    start station name         652081
    starttime                  652081
    stoptime                   652081
    tripduration               652081
    usertype                   651584
    dtype: int64


