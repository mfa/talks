class: center, middle

# Weather APIs

Andreas Madsack (mfa)

datenobservatorium<br/>
2020-05-04

---

## Problem

- darksky (former forecast.io) was bought by Apple and the API will be discontinued.
- what are the alternatives?

--

## Some alternatives

- Openweathermap
- met.no
- (a lot without API)

---

## 1. darksky

- no new registrations possible
- EOL will be end of 2021

---

## 1.1 darksky: API call

```python
import requests

KEY = "insert-key-here"
r = requests.get(f"https://api.darksky.net/forecast/{KEY}/48.7677,9.1719?units=si")
if r.status_code == 200:
    print(r.json())
```

- `units=si` is for non-imperial units (which is the default)

- returns `currently`, `hourly` and `daily` (all in one API call)

- example output: <a href="darksky-1588417820.json">darksky-1588417820.json</a>

---

## 1.2 darksky: Example output

```json
  "currently": {
    "time": 1588413601,
    "summary": "Partly Cloudy",
    "icon": "partly-cloudy-day",
    "precipIntensity": 0.0131,
    "precipProbability": 0.04,
    "precipType": "rain",
    "temperature": 13.47,
    "apparentTemperature": 13.47,
    "dewPoint": 4.52,
    "humidity": 0.55,
    "pressure": 1011,
    "windSpeed": 5.88,
    "windGust": 10.77,
    "windBearing": 247,
    "cloudCover": 0.38,
    "uvIndex": 4,
    "visibility": 16.093,
    "ozone": 372.6
```

---

## 2. openweathermap

- https://openweathermap.org/
- free for 1,000 calls/day
- max 60 calls/minute
- docs: https://openweathermap.org/api/one-call-api

- migration guide: https://openweathermap.org/darksky-openweather
- BUT most json keys are different.

---

## 2.1 openweathermap: API call

```python
import requests

params = {
    "lat": 48.7677,
    "lon": 9.1719,
    "appid": "inser-key-here",
    "units": "metric",
}

r = requests.get("https://api.openweathermap.org/data/2.5/onecall", params=params
)
```

- example output: <a href="openweathermap-1588417820.json">openweathermap-1588417820.json</a>

---

## 1.2 openweathermap: Example output

```json
  "current": {
    "dt": 1588417821,
    "sunrise": 1588392049,
    "sunset": 1588444774,
    "temp": 12.66,
    "feels_like": 7.47,
    "pressure": 1010,
    "humidity": 58,
    "dew_point": 4.62,
    "uvi": 5.34,
    "clouds": 75,
    "visibility": 10000,
    "wind_speed": 5.7,
    "wind_deg": 250,
    "weather": [
      {
        "id": 803,
        "main": "Clouds",
        "description": "broken clouds",
        "icon": "04d"
      }
    ]
  }
```

---

## 3. met.no

- https://api.met.no/weatherapi/locationforecast/1.9/documentation
- very old school - json that looks like XML
- no API-KEYs, no limits?

---

## 3.1 met.no: API call

```python
import requests

r = requests.get(f"https://api.met.no/weatherapi/locationforecast/1.9/.json?lat=48.7677&lon=9.1719")
if r.status_code == 200:
    print(r.json())
```

- example output: <a href="met.no-1588417820.json">met.no-1588417820.json</a>

---

## 3.2 met.no: Example output

```json
        "from": "2020-05-02T11:00:00Z",
        "location": {
          "cloudiness": {
            "percent": "70.3",
            "id": "NN"
          },
          "lowClouds": {
            "percent": "46.1",
            "id": "LOW"
          },
          "dewpointTemperature": {
            "id": "TD",
            "value": "4.2",
            "unit": "celsius"
          },
          "windDirection": {
            "id": "dd",
            "name": "W",
            "deg": "268.1"
          },
          "fog": {
            "percent": "0.0",
            "id": "FOG"
          },
          "mediumClouds": {
            "percent": "66.4",
            "id": "MEDIUM"
          },
          "pressure": {
            "id": "pr",
            "unit": "hPa",
            "value": "1011.3"
          },
          "longitude": "9.1719",
          "latitude": "48.7677",
          "humidity": {
            "value": "59.9",
            "unit": "percent"
          },
          "temperature": {
            "unit": "celsius",
            "value": "11.7",
            "id": "TTT"
          },
          "altitude": "337",
          "windSpeed": {
            "name": "Laber bris",
            "id": "ff",
            "mps": "6.0",
            "beaufort": "4"
```

---

## thanks
