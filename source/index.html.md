---
title: Deepnews API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - php

toc_footers:
  - <a href='mailto:tech@deepnews.ai'>Support</a>

includes:
  # - errors

search: false
---

# Introduction

Welcome to Deepnews's API. Here, you'll be able to obtain a journalistic quality score for either a body of text or a URL containing a body of text.

It's very easy to get going. All you need is an API key and the ability to send that key in the headers of a POST request to:

`https://api.deepnews.ai/score`

The output will be in JSON.

# Scoring

## Article by body text

```shell
wget --no-check-certificate --quiet \
  --method POST \
  --timeout=0 \
  --header '' \
   'https://api.deepnews.ai/score?key=API_KEY&body=BODY'
```

```python
import requests

url = "https://api.deepnews.ai/score?key=API_KEY&body=BODY"

response = requests.request("POST", url)

print(response.text)
```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.deepnews.ai/score?key=API_KEY&body=BODY',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

> The above code would return the following JSON output:

```json
[
    {
        "confidence": CONFIDENCE,
        "score": SCORE
    }
]
```

To score an article when you already have its body, use this code.

## Article by URL

```shell
wget --no-check-certificate --quiet \
  --method POST \
  --timeout=0 \
  --header '' \
   'https://api.deepnews.ai/score?key=API_KEY&url=URL'
```

```python
import requests

url = "https://api.deepnews.ai/score?key=API_KEY&url=URL"

response = requests.request("POST", url)

print(response.text)
```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.deepnews.ai/score?key=API_KEY&url=URL',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

> The above code would return the following JSON output:

```json
[
    {
        "confidence": CONFIDENCE,
        "score": SCORE
    }
]
```

To score an article given only its URL, use this code.