---
title: Executive Sentiment API Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

search: true

code_clipboard: true
---

# Introduction

Welcome to Executive Sentiment API! You can use our API to access stock’s fundamental data, including company reviews and company executive analysis.

We have language bindings in Shell, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

Base URL: `/v1/`


# Authentication

> To authorize, use this code:

```python
import sentiment

api = sentiment.authorize('YOUR API KEY')
```

```shell
# With shell, you can just pass the correct header with each request
curl https://api.executivesentiment.com/v1/ \
  -H "YOUR API KEY"
```

```javascript
const sentiment = require('sentiment');

let api = sentiment.authorize('YOUR API KEY');
```

The Executive Sentiment API uses API Keys to authenticate requests. You can view and manage your API keys in the Dashboard. 

Your API keys carry many privileges, so be sure to keep them secure! Do not share your secret API keys in publicly accessible areas such as GitHub, client-side code, and so forth.

`Authorization: YOUR API KEY`

# Company Profile

```python
import requests

r = requests.get('https://api.executivesentiment.com/v1/stock/profile?symbol=AAPL')
```

```shell
curl 'https://api.executivesentiment.com/v1/stock/profile?symbol=AAPL' \
  -H "YOUR API KEY"
```

```javascript
const request = require('request');

request('https://api.executivesentiment.com/api/v1/stock/profile?symbol=AAPL', { json: true }, (err, res, body) => {
  if (err) { return console.log(err); }
  console.log(body.url);
  console.log(body.explanation);
});
```

> The above command returns JSON structured like this:

```json
{
    "name": "Apple Inc",
    "description": "Apple Inc. is an American multinational technology company headquartered in Cupertino, California, that designs, develops, and sells consumer electronics, computer software, and online services. It is considered one of the Big Four technology companies, alongside Amazon, Google, and Microsoft. The company's hardware products include the iPhone smartphone, the iPad tablet computer, the Mac personal computer, the iPod portable media player, the Apple Watch smartwatch, the Apple TV digital media player, the AirPods wireless earbuds and the HomePod smart speaker. Apple's software includes the macOS, iOS, iPadOS, watchOS, and tvOS operating systems, the iTunes media player, the Safari web browser, the Shazam acoustic fingerprint utility, and the iLife and iWork creativity and productivity suites, as well as professional applications like Final Cut Pro, Logic Pro, and Xcode. Its online services include the iTunes Store, the iOS App Store, Mac App Store, Apple Music, Apple TV+, iMessage, and iCloud. Other services include Apple Store, Genius Bar, AppleCare, Apple Pay, Apple Pay Cash, and Apple Card.",
}
```

Get general information of a company. 

### Example

`/stock/profile?symbol=AAPL`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
symbol | None | Symbol of the company: e.g. AAPL

### Response Attributes

Parameter | Description
--------- | -----------
name | Company name
description | Company business summary

# Company Executive

```python
import requests

r = requests.get('https://api.executivesentiment.com/v1/stock/executive?symbol=AAPL')
```

```shell
curl 'https://api.executivesentiment.com/v1/stock/executive?symbol=AAPL' \
  -H "YOUR API KEY"
```

```javascript
const request = require('request');

request('https://api.executivesentiment.com/api/v1/stock/executive?symbol=AAPL', { json: true }, (err, res, body) => {
  if (err) { return console.log(err); }
  console.log(body.url);
  console.log(body.explanation);
});
```

> The above command returns JSON structured like this:

```json
{
  "executive": [
    {
      "name": "Luca Maestri",
      "position": "Senior Vice President",
      "since": "2014",
      "compensation": "25209637",
      "currency": "USD"
    },
    {
      "name": "Apple Inc",
      "position": "Director and Chief Executive Officer",
      "since": "2011",
      "compensation": "11555466",
      "currency": "USD"
    }
  ]
}
  

```

Get a list of company's executives and members of the Board. 

### Example

`/stock/executive?symbol=AAPL`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
symbol | None | Symbol of the company: e.g. AAPL

### Response Attributes

Parameter | Description
--------- | -----------
name | Executive name
position | Executive position
since | Year appointed
compensation | Total compensation
currency | Compensation currency

# Executive Sentiment


```python
import requests

r = requests.get('https://api.executivesentiment.com/v1/executivesentiment?symbol=AAPL')
```

```shell
curl 'https://api.executivesentiment.com/v1/executivesentiment?symbol=AAPL' \
  -H "YOUR API KEY"
```

```javascript
const request = require('request');

request('https://api.executivesentiment.com/api/v1/executivesentiment?symbol=AAPL', { json: true }, (err, res, body) => {
  if (err) { return console.log(err); }
  console.log(body.url);
  console.log(body.explanation);
});
```

> The above command returns JSON structured like this:

```json
{
    "executiveForwardStatement": [
      {
        "date": "2020-02-17",
        "headline": "Investor update on quarterly guidance",
        "url": "https://www.apple.com/newsroom/2020/02/investor-update-on-quarterly-guidance/"
      },
      {
        "date": "2020-10-29",
        "headline": "Apple Reports Fourth Quarter Results",
        "url": "https://www.apple.com/newsroom/2020/10/apple-reports-fourth-quarter-results/"
      },
    ],
    "executiveSentimentScore": "0.86"
}
```

Get official statements by the company and sentiment analysis score on these statements. 

### Example

`/executivesentiment?symbol=AAPL`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
symbol | None | Symbol of the company: e.g. AAPL

### Response Attributes

Parameter | Description
--------- | -----------
executiveForwardStatement | Array of forward statements by the company
date | Statement date
headline | Headline of the statement
executiveSentimentScore | Sentiment score for all statements. Positive score means positive sentiment and vice versa.

# Company Review

```python
import requests

r = requests.get('https://api.executivesentiment.com/v1/reviews?symbol=AAPL')
```

```shell
curl 'https://api.executivesentiment.com/v1/reviews?symbol=AAPL' \
  -H "YOUR API KEY"
```

```javascript
const request = require('request');

request('https://api.executivesentiment.com/api/v1/reviews?symbol=AAPL', { json: true }, (err, res, body) => {
  if (err) { return console.log(err); }
  console.log(body.url);
  console.log(body.explanation);
});
```

> The above command returns JSON structured like this:

```json
{
    "reviews": {
        "pros": [
          "Apple has great benefits for students even as a part-time employee",
          "nice place to work great people around you"
        ],
        "cons": [
          "Long hours tend to make one tired",
          "Retail hours are not fun at all"
        ]
      }
}
```

Get employees' reviews of the company.

### Example

`/reviews?symbol=AAPL`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
symbol | None | Symbol of the company: e.g. AAPL

### Response Attributes

Parameter | Description
--------- | -----------
reviews | Reviews by employees
pros | Array of positive reviews
cons | Array of negative reviews

# Review Sentiment

```python
import requests

r = requests.get('https://api.executivesentiment.com/v1/reviews-sentiment?symbol=AAPL')
```

```shell
curl 'https://api.executivesentiment.com/v1/reviews-sentiment?symbol=AAPL' \
  -H "YOUR API KEY"
```

```javascript
const request = require('request');

request('https://api.executivesentiment.com/api/v1/reviews-sentiment?symbol=AAPL', { json: true }, (err, res, body) => {
  if (err) { return console.log(err); }
  console.log(body.url);
  console.log(body.explanation);
});
```

> The above command returns JSON structured like this:

```json
{
    "companySentimentScore": "0.768",
    "reviewSentimentScore": "0.891",
}
```

Get sentiment analysis score of reviews and news of the company.

### Example

`/reviews-sentiment?symbol=AAPL`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
symbol | None | Symbol of the company: e.g. AAPL

### Response Attributes

Parameter | Description
--------- | -----------
companySentimentScore | Sentiment score from news and articles regarding the company
companyReviewScore | Sentiment score from employees' reviews
