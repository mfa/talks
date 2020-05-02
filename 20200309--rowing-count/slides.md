class: center, middle

# Count Rows on a rowing machine

Andreas Madsack (mfa)

datenobservatorium<br/>
2020-03-09

---

## Problem

- Count rows on a completly mechanical rowing machine
- <https://www.google.com/search?q=Hanseatic+Rowing+Machine&source=lnms&tbm=isch>

---

## Sensor

- MMA7455 accelerometer
- raspberry pi zero

<img src="https://madflex.de/images/rowing_sensor.png" height="400px" align="top">

---

## Recording

 - python script started with systemd on boot

 - code: https://github.com/mfa/rowing-count/blob/master/record.py

---

## Evaluation

Here we see 1 row, 2 rows and 5 rows:

<img src="https://madflex.de/images/rowing_all_axes.png" height="400px" align="top">

---

## Evaluation

And only the 5 rows zoomed in:

<img src="https://madflex.de/images/rowing_all_axes_5.png" height="400px" align="top">


---

## Evaluation

Only x axis of the 5 rows:

<img src="https://madflex.de/images/rowing_5x.png" height="400px" align="top">


---

## Evaluation

Peak finding is easier if the peaks are on top -- negate axis

<img src="https://madflex.de/images/rowing_5x_neg.png" height="400px" align="top">


---

## Evaluation

Filter using scipy [savgol filter](https://docs.scipy.org/doc/scipy-1.4.1/reference/generated/scipy.signal.savgol_filter.html):

<img src="https://madflex.de/images/rowing_5x_neg_savgol.png" height="400px" align="top">

---

## Evaluation

[find_peaks](https://docs.scipy.org/doc/scipy-1.4.1/reference/generated/scipy.signal.find_peaks.html)

<img src="https://madflex.de/images/rowing_5.png" height="400px" align="top">

---

## Evaluation

[find_peaks](https://docs.scipy.org/doc/scipy-1.4.1/reference/generated/scipy.signal.find_peaks.html)

The (orange) line is the prominence. This value is used to filter too small peaks

<img src="https://madflex.de/images/rowing_5.png" height="400px" align="top">

---

## Evaluation

```python
def get_peaks(x):
   _ = np.negative(x)
   _ = scipy.signal.savgol_filter(_, 51, 3)
   peaks, properties = scipy.signal.find_peaks(_, prominence=5, width=40)
   return sum(map(lambda i: i>12, properties["prominences"]))
```

last line sums only peaks with prominence higher 12.

---

## Evaluation

with 100 rows:

<img src="https://madflex.de/images/rowing_100.png" height="400px" align="top">

---

## Links

- The full code: https://github.com/mfa/rowing-count/

- Blogpost: https://madflex.de/posts/count-rows-on-an-old-rowing-machine/

---

## thanks

talk to me about

- python
- machine-learning
- computerlinguistics
