class: center, middle

# Datasette

Andreas Madsack (mfa)

datenobservatorium<br/>
2020-01-13

---

## Datasette

- A tool for exploring and publishing data

- https://github.com/simonw/datasette

- in Python

- data is filebased (sqlite) - less complex hosting


---

## Some Examples

- https://fivethirtyeight.datasettes.com/fivethirtyeight

- https://fivethirtyeight.datasettes.com/fivethirtyeight/forecast-methodology%2Fhistorical-senate-predictions

- https://global-power-plants.datasettes.com/global-power-plants/global-power-plants?country_long=Germany


---

## Growing Ecosystem

- https://datasette.readthedocs.io/en/stable/ecosystem.html#the-datasette-ecosystem

- sqlite-utils

- csvs/db/markdown/yml to sqlite

- plugins for different outputs: https://datasette.readthedocs.io/en/stable/ecosystem.html#datasette-plugins


---

## Why I started to look into Datasette?

- https://meinsack.click/

- explore ways for simpler (less maintenance) hosting

- example: http://localhost:8001/meinsack/pickupdate_street?street__exact=Marienstra%C3%9Fe&zipcode__exact=70178


---

## next

- host on https://data.meinsack.click

- create sqlite-db using a manage command in current Django code (and not manually)

- ical plugin


---

## thanks

talk to me about

- python
- machine-learning
