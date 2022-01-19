class: center, middle

# Overfitting

Andreas Madsack (mfa)

AX Semantics<br/>
2022-01-18

---

## Agenda

1. What is overfitting?

2. How can I detect overfitting?

3. How can I prevent overfitting?

4. Examples


---

## What is overfitting?

The model corresponds to closely to the training data and cannot generalize for new data.

If your new data is very similar to your training data, because the problem is very narrow, overfitting may be no problem at all.

But being aware of overfitting may help building better/smaller models.

---

## How can I detect overfitting?

The training loss reaches 0 very fast (a few epochs) and the validation loss increases.

With a small amount of training data this can be a overfitting problem.

---

## How can I prevent overfitting?

Train with more data and/or augment your data if possible.

Simplify the model can help -- or even better start with a simpler model and increase complexity if needed.

Add dropout (random threshold for setting data to 0). A good starting point is a dropout of `0.5`.

---

## Example

(Modified) MNIST example from **machine learning workshop part 1** in 2 weeks.

The modification is a decrease of training data to 3x 128 samples instead of 55000 samples.

Model/Training: [http://localhost:8888/notebooks/overfitting.ipynb#](http://localhost:8888/notebooks/overfitting.ipynb#)

Report: [http://localhost:8000/w_and_b__report.pdf](http://localhost:8000/w_and_b__report.pdf)

<br/>
<br/>
<br/>

``FIXME: set both links to github repo``

---

## Questions?



