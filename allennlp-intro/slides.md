class: center, middle

# AllenNLP Intro

Andreas Madsack (mfa)

mlugs<br/>
2019-03-19

---

## Agenda

1. About

2. Pro/Contra AllenNLP

3. Example 1: Tagger from AllenNLP Tutorial

4. Example 2: NMT as code and as config

5. Example 3: Transfer PyTorch to AllenNLP

6. Conclusion

---

## About

(copied from https://allenai.github.io/allennlp-docs/)

Built on **PyTorch**, AllenNLP makes it easy to design and evaluate new deep learning models for nearly any NLP problem, along with the infrastructure to easily run them in the cloud or on your laptop.

AllenNLP was designed with the following principles:

- Hyper-modular and lightweight. Use the parts which you like seamlessly with PyTorch.
- Extensively tested and easy to extend. Test coverage is above 90% and the example models provide a template for contributions.
- Take padding and masking seriously, making it easy to implement correct models without the pain.
- Experiment friendly. Run reproducible experiments from a json specification with comprehensive logging.


---

## Pro/Contra AllenNLP

### Pro

- abstraction on top of PyTorch

- a lot of standard components in NLP are already implemented: Transformer, BERT, ...

- CUDA just works (because of PyTorch)

- Python 3.6+

- lots of tests and typing

### Contra:

- may not have enough traction

- far too little documentation

---

## Example 1: AllenNLP Tutorial

see https://allennlp.org/tutorials

Good example with lots of annotation.

But without resonable training data :(

---

## Example 2: NMT as code and as config

NMT example for English to Chinese:

http://www.realworldnlpbook.com/blog/building-seq2seq-machine-translation-models-using-allennlp.html

Same example but as AllenNLP config (NMT for English to German):

https://madflex.de/posts/allennlp--machine-translation-using-configuration/

---

## Example 3: Transfer PyTorch to AllenNLP

Addition using sequences

Code in PyTorch + Ignite: https://github.com/mfa/addition_seq2seq/

Code in AllenNLP: https://github.com/mfa/addition_seq2seq_allennlp/

Essentials:

- library/data.py
- addition.jsonnet

---

### Example 3: training loss comparision

.left-column[
PyTorch only:

<img src="https://paste.madflex.de/p4xQGPA9/+inline?" height="400px">

https://www.floydhub.com/mfandreas/projects/addition_seq2seq/6
]
.right-column[
AllenNLP:

<img src="https://paste.madflex.de/yuWRrQjZ/+inline?" height="400px">
]

---

## Conclusion

AllenNLP is a best practices first NLP framework.

You may need more time to get startet, but imho it's worth it.
