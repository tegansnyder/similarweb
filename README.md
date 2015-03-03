# Similarweb
Python wrapper for the [SimilarWeb API](https://developer.similarweb.com/doc).

## Usage

Create a client object for the API you'd like to use:

#### Ready to go
* Traffic: `traffic_client = SimilarwebTrafficClient("your_api_key")`

#### In development
* Content: `content_client = SimilarwebContentClient("your_api_key")`
* Mobile: `mobile_client = SimilarwebMobileClient("your_api_key")`
* Sources: `sources_client = SimilarwebSourcesClient("your_api_key")`

## Traffic Client in Action

Let's set up the traffic object and some variables we'll be using throughout:

```python
>>> from similarweb import SimilarwebTrafficClient
>>> traffic_client = SimilarwebTraffiClient("my_api_key")
>>> url = "example.com"     # <~ no "www" or "http://"
>>> gr = "monthly"          # <~ or "weekly" or "daily"
>>> start_month = "11-2014" # <~ M-YYYY
>>> end_month = "12-2014"   # <~ M-YYYY
>>> md = False              # or True if you want main domain ONLY
```

##### Get the number of estimated visits for the requested domain on a monthly, weekly or daily basis:

```python
>>> traffic_client.visits(url, gr, start_month, end_month, md)
{"2014-11-01": 12897241, "2014-12-01": 13917811}
```

##### Get the global rank, country rank and traffic geography, traffic reach and traffic sources distribution:

```python
>>> traffic_client.traffic(url)
{
 "GlobalRank": 2,
 "CountryCode": 840,
 "CountryRank": 1,
 "TopCountryShares": {
  "840": 0.4321,
  "356": 0.3210,
  # ... many more country code-share pairs
  "876": 6.8674e-7,
  "10": 0
 },
 "TrafficReach": {
  "01/08/2014": 0.1734,
  "08/08/2014": 0.1649,
  # ... many more date-reach pairs
  "23/01/2015": 0.1631,
  "30/01/2015": 0.1681
 },
 "TrafficShares": {
  "Search": 0.1043,
  "Social": 0.0302,
  "Mail": 0.0041,
  "Paid Referrals": 0.0016,
  "Direct": 0.6771,
  "Referrals": 0.1826
 },
 "Date": "01/2015"
}
```

##### Get the average pageviews for the requested domain on a monthly, weekly or daily basis:

```python
>>> traffic_client.pageviews(url, gr, start_month, end_month, md)
{"2014-11-01": 14.7224, "2014-12-01": 14.2360}
```

##### Get the average visit duration at the requested domain on a monthly, weekly or daily basis:

```python
>>> traffic_client.visit_duration(url, gr, start_month, end_month, md)
{"2014-11-01": 971.0572, "2014-12-01": 961.5565}
```

##### Get the average bounce rate at the requested domain on a monthly, weekly or daily basis:

```python
>>> traffic_client.bounce_rate(url, gr, start_month, end_month, md)
{"2014-11-01": 0.2191, "2014-12-01": 0.2259}
```
