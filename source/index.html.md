---
title: Deepnews.ai API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php
  - python

toc_footers:
  - <a href='mailto:support@deepnews.ai'>Support</a>

includes:
  - errors

search: false
---

# Introduction

Welcome to Deepnews.ai's API. It's very easy to get going. All you need is an API Key and the ability to send that key in the headers of a GET request to:

`https://api.deepnews.ai/...`

You can choose an article and input either its URL or its body to get a score and confidence level. You can also input an array as your URL or body.

The output will be in JSON...

# Scoring

## Single article by URL

```python
import requests
import pandas as pd
import ast 

url = "http://34.76.135.168:9090/rank" 

# df = pd.read_csv("my_data.csv") 

data = {
    'url': ['https://www.deepnews.ai'],
    'body': ['Text to parse'],
    'key': 'XXX',
    'limit': 300,
    'multiplier': 2,
    'sort': True,
    'ascending': False
    }

req = requests.post(url, json=data)
res = ast.literal_eval(req.content.decode('utf-8'))
print("{} articles scored".format(res['number_articles']))
del res['number_articles']
pd.DataFrame.from_dict(res).to_csv("my_output_data.csv") 
```

> The above code would return the following JSON output:

```json
xxxx
```

This is how you would....

## Single article with body

```python
import requests
import pandas as pd
import ast 

url = "http://34.76.135.168:9090/rank" 

# df = pd.read_csv("my_data.csv") 

data = {
    'url': ['https://www.deepnews.ai'],
    'body': ['Text to parse'],
    'key': 'XXX',
    'limit': 300,
    'multiplier': 2,
    'sort': True,
    'ascending': False
    }

req = requests.post(url, json=data)
res = ast.literal_eval(req.content.decode('utf-8'))
print("{} articles scored".format(res['number_articles']))
del res['number_articles']
pd.DataFrame.from_dict(res).to_csv("my_output_data.csv") 
```

> The above code would return the following JSON output:

```json
...
```

Just put in the body...

## Multiple article URLs

```python
import requests
import pandas as pd
import ast 

url = "http://34.76.135.168:9090/rank" 

# df = pd.read_csv("my_data.csv") 

data = {
    'url': ['https://www.deepnews.ai'],
    'body': ['Text to parse'],
    'key': 'XXX',
    'limit': 300,
    'multiplier': 2,
    'sort': True,
    'ascending': False
    }

req = requests.post(url, json=data)
res = ast.literal_eval(req.content.decode('utf-8'))
print("{} articles scored".format(res['number_articles']))
del res['number_articles']
pd.DataFrame.from_dict(res).to_csv("my_output_data.csv") 
```

> The above code would return the following JSON output:

```json
...
```

An array of URLs

## Multiple article bodies

```python
import requests
import pandas as pd
import ast 

url = "http://34.76.135.168:9090/rank" 

# df = pd.read_csv("my_data.csv") 

data = {
    'url': ['https://www.deepnews.ai'],
    'body': ['Text to parse'],
    'key': 'XXX',
    'limit': 300,
    'multiplier': 2,
    'sort': True,
    'ascending': False
    }

req = requests.post(url, json=data)
res = ast.literal_eval(req.content.decode('utf-8'))
print("{} articles scored".format(res['number_articles']))
del res['number_articles']
pd.DataFrame.from_dict(res).to_csv("my_output_data.csv") 
```

> The above code would return the following JSON output:

```json
...
```

A bunch of article bodies