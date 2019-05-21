class: center, middle

# Lightning Talk: Encoder-Decoder-Networks

Andreas Madsack (mfa)

datenobservatorium<br/>
2019-05-20

---

## Sequences Networks

![](http://karpathy.github.io/assets/rnn/diags.jpeg)

(img src: http://karpathy.github.io/2015/05/21/rnn-effectiveness/ )

---

## Many to Many

other names:

- Sequence to Sequence
- Encoder-Decoder

---

## Examples for Encoder-Decoder

- Translation

--

- Named Entity Recognition

--

- POS tagging

--

- Speech Recognition

--

- Morphological Inflection (Talk tomorrow at mlugs)

--

- ⋯

---

## Encoder-Decoder

![](https://cdn-images-1.medium.com/max/800/0*VwQyyHLPDgEWSD-2.)

(img src: https://medium.com/syncedreview/a-brief-overview-of-attention-mechanism-13c578ba9129 )

---

## Important to understand

![](https://github.com/bentrevett/pytorch-seq2seq/raw/61157fe51246a68db40dbff69adcd839abcaee05/assets/seq2seq1.png)

- The last *hidden-state* of the **encoder** is part of the *input* of the **decoder**!

(img src: https://github.com/bentrevett/pytorch-seq2seq/ )

---

## Cells

RNN  | GRU  | LSTM
---- | ---- | -----
![](https://cdn-images-1.medium.com/max/400/1*28XR1ajfW1WuTOkjpOc9xA.png) | ![](https://cdn-images-1.medium.com/max/400/1*GSZ0ZQZPvcWmTVatAeOiIw.png) | ![](https://cdn-images-1.medium.com/max/600/1*ZX2mVCwMIOhftEaf4FTOYQ.png)

(img src https://medium.com/@saurabh.rathor092/simple-rnn-vs-gru-vs-lstm-difference-lies-in-more-flexible-control-5f33e07b1e57 )

---

## Attention (is all you need)

<img src="https://cdn-images-1.medium.com/max/800/0*VrRTrruwf2BtW4t5." width="50%">

(img src: https://medium.com/syncedreview/a-brief-overview-of-attention-mechanism-13c578ba9129 )

---

## Attention helps you visualize!

![](https://bastings.github.io/annotated_encoder_decoder/images/output_66_1.png)

(img src: https://bastings.github.io/annotated_encoder_decoder/)


---

## BUT everything comes with a price.

--

- More hidden states -> more parameters to train

--

- More complex Cells (LSTM instead of RNN) -> more parameters to train

--

- Using attention -> more parameters to train

--

- More complex attention algorithm -> more parameters to train

--

⇨ you need more data to train all these parameters!


---

## Thanks!

### tomorrow

*Machine Learning UserGroup Stuttgart*:
**"Morphological Inflection using Encoder-Decoder-Networks"**

(in German!)
