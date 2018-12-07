
---
layout: post
title: "Data Basics with pandas"
subtitle: "From Personal notes on working with data"
date: 2018-11-17
author: Anders
category: data
tags: pandas, python
finished: false
---

## Data Basics

Part of the problem of working with data is to get the techniques in your
fingers. To simplify working with data, there are some great tools like pandas
and R, and a lot of the time in working with data is going to be manipulation
and exploration of data.

So lets get started and get our hands on the basics of working with data!

## Importing data

### CSV Imports

importing data from csv (stands for comma seperated values) files is very common when
working with data, and getting a hold of working with it is an essential data
skill.

Pretty easy in pandas, heres a useful example:

```
df = pd.reaf_csv(filepath, header=None,
    names=col_names, na_values={'column': ['-1']}
    parse_dates=[[0,1,2]])

df.to_csv('filename.csv')
```



### Other imports


