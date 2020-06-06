---
title: Deepnews.ai API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - php
  - javascript
  - go

toc_footers:
  - <a href='mailto:tech@deepnews.ai'>Support</a>

includes:
  - errors

search: false
---

# Introduction

Welcome to Deepnews.ai's API. Here, you'll be able to obtain a journalistic quality score for either a body of text or a URL containing a body of text.

It's very easy to get going. All you need is an API key and the ability to send that key in the headers of a POST request to:

`https://api.deepnews.ai/score`

The output will be in JSON...

# Scoring

## Articles by body text

```shell
wget --no-check-certificate --quiet \
  --method POST \
  --timeout=0 \
  --header 'Content-Type: application/json' \
  --body-data '{
	"key": "API_KEY",
	"body": ["Body text of first article", "Body text of second article"]
}' \
   'https://api.deepnews.ai/score'
```

```python
import requests

url = "https://api.deepnews.ai/score"

payload = "{\n\t\"key\": \"API_KEY\",\n\t\"body\": [\"Body text of first article\", \"Body text of second article\"]\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

```php
<?php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://api.deepnews.ai/score');
$request->setRequestMethod('POST');
$body = new http\Message\Body;
$body->append('{
	"key": "API_KEY",
	"body": ["Body text of first article", "Body text of second article"]
}');
$request->setBody($body);
$request->setOptions(array());
$request->setHeaders(array(
  'Content-Type' => 'application/json'
));
$client->enqueue($request)->send();
$response = $client->getResponse();
echo $response->getBody();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({"key":"API_KEY","body":["Body text of first article","Body text of second article"]});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.deepnews.ai/score", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.deepnews.ai/score"
  method := "POST"

  payload := strings.NewReader("{\n	\"key\": \"API_KEY\",\n	\"body\": [\"Body text of first article\", \"Body text of second article\"]\n}")

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Add("Content-Type", "application/json")

  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> The above code would return the following JSON output:

```json
{
    "conf_score": [
        0.0,
        0.0
    ],
    "entropy_of_results": [
        1.3620502948760986,
        1.3881547451019287
    ],
    "nb_articles": 2,
    "score": [
        1.9210876988957288,
        1.8359465908822323
    ],
    "score_features": [
        2.0112321749329567,
        1.9995275549590588
    ],
    "url": [
        0,
        1
    ]
}
```

To score one or more body texts, use this code.

## Articles by URL

```shell
wget --no-check-certificate --quiet \
  --method POST \
  --timeout=0 \
  --header 'Content-Type: application/json' \
  --body-data '{
	"key": "API_KEY",
	"url": ["https://www.nytimes.com/2020/06/05/us/defund-police-floyd-protests.html", "https://www.washingtonpost.com/national/protests-police-brutality-video/2020/06/05/a9e66568-a768-11ea-b473-04905b1af82b_story.html"]
}' \
   'https://api.deepnews.ai/score'
```

```python
import requests

url = "https://api.deepnews.ai/score"

payload = "{\n\t\"key\": \"API_KEY\",\n\t\"url\": [\"https://www.nytimes.com/2020/06/05/us/defund-police-floyd-protests.html\", \"https://www.washingtonpost.com/national/protests-police-brutality-video/2020/06/05/a9e66568-a768-11ea-b473-04905b1af82b_story.html\"]\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

```php
<?php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://api.deepnews.ai/score');
$request->setRequestMethod('POST');
$body = new http\Message\Body;
$body->append('{
	"key": "API_KEY",
	"url": ["https://www.nytimes.com/2020/06/05/us/defund-police-floyd-protests.html", "https://www.washingtonpost.com/national/protests-police-brutality-video/2020/06/05/a9e66568-a768-11ea-b473-04905b1af82b_story.html"]
}');
$request->setBody($body);
$request->setOptions(array());
$request->setHeaders(array(
  'Content-Type' => 'application/json'
));
$client->enqueue($request)->send();
$response = $client->getResponse();
echo $response->getBody();
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({"key":"API_KEY","url":["https://www.nytimes.com/2020/06/05/us/defund-police-floyd-protests.html","https://www.washingtonpost.com/national/protests-police-brutality-video/2020/06/05/a9e66568-a768-11ea-b473-04905b1af82b_story.html"]});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.deepnews.ai/score", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.deepnews.ai/score"
  method := "POST"

  payload := strings.NewReader("{\n	\"key\": \"API_KEY\",\n	\"url\": [\"https://www.nytimes.com/2020/06/05/us/defund-police-floyd-protests.html\", \"https://www.washingtonpost.com/national/protests-police-brutality-video/2020/06/05/a9e66568-a768-11ea-b473-04905b1af82b_story.html\"]\n}")

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Add("Content-Type", "application/json")

  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> The above code would return the following JSON output:

```json
{
    "conf_score": [
        0.20268878497899753,
        0.11293205282391551
    ],
    "entropy_of_results": [
        0.9082273542881012,
        1.0883015990257263
    ],
    "nb_articles": 2,
    "score": [
        2.7992293723965584,
        2.478889596037047
    ],
    "score_features": [
        0.9515315387398005,
        0.6575289871543646
    ],
    "url": [
        "https://www.nytimes.com/2020/06/05/us/defund-police-floyd-protests.html",
        "https://www.washingtonpost.com/national/protests-police-brutality-video/2020/06/05/a9e66568-a768-11ea-b473-04905b1af82b_story.html"
    ]
}
```

To score one or more online articles, use this code.