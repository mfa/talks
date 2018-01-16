# Deep Learning Dependency Parsers

Andreas Madsack (mfa)

mlugs<br/>
2018-01-16

---

## What is a dependency parser?

Syntax analysis/tree of a sentence.  
The verb is always the root.

<img src="https://github.com/tensorflow/models/raw/master/research/syntaxnet/g3doc/images/sawman.png" width="80%" style="background-color:white;">

---

### Why do we need a depenency parser?

The AX Semantics text generation applies grammatical agreement between all (marked) constituents.

For example:
```sh
1 microUSB port is available.
2 microUSB ports are available.
[number] microUSB [G:noun=port] [G:verb=be]
```

---

### Verb agreement

```sh
Hans sieht Maria mit dem Fernglas.
```

```
sehen <nsubj> <dobj> <pobj:mit>
```

<img src="/images/hans_sieht_maria.png" width="80%">


---

## Syntaxnet / Parsey McParseface

- for non English: Parsey Universal
- Part of Tensorflow (now in models repository)
- pre trained for lots of languages (from Google;  
  Data based on Universal Dependencies)

- https://github.com/tensorflow/models/blob/master/research/syntaxnet/g3doc/syntaxnet-tutorial.md
- https://github.com/tensorflow/models/blob/master/research/syntaxnet/g3doc/universal.md

---

#### Demo

```sh
docker run --rm -ti tensorflow/syntaxnet bash
curl -O http://download.tensorflow.org/models/parsey_universal/German.zip
unzip German.zip
echo "Die Ärmel der Strickjacke haben am Armabschluss ein Bündchen."  \
| syntaxnet/models/parsey_universal/parse.sh `pwd`/German
```

---

#### Tradeoffs

- the parsey_universal folder/model was removed from models repository -- no support anymore?
- everything still Python 2.7
- the German model (and maybe all other models too) doesn't have features (i.e. case, number, tense, ...)
- no real python api. all is called via bazel


---

## DRAGNN

- successor of SyntaxNet
- seems more complex. but this time it has a Python api
- https://github.com/tensorflow/models/blob/master/research/syntaxnet/g3doc/DRAGNN.md

---

#### (no) Demo

Installed: https://github.com/tensorflow/models/blob/master/research/syntaxnet/README.md#ubuntu-1610-binary-installation

And failed running `bazel` based evaluation code.

No docker with pretrained models.

---

#### Tradeoffs

- too complicated
- really bad documented
- clearly research and not production ready  
  (for non Google)

---

## CoreNLP

- https://stanfordnlp.github.io/CoreNLP/
- https://stanfordnlp.github.io/CoreNLP/images/Xi-Jinping.png
- models for: Arabic, Chinese, English, French, German, Spanish

---

#### Demo

```sh
git clone https://github.com/mfa/corenlp-german
cd corenlp-german
docker build --tag corenlp .
docker run -p 8080:9000 --name=corenlp corenlp

curl --data 'Die Ärmel der Strickjacke haben am Armabschluss ein Bündchen.' \
'http://localhost:8080/?properties={%22pipelineLanguage%22%3A%22de%22%2C%22annotators%22%3A%22tokenize%2Cssplit%2Cpos%2Cdepparse%22%2C%22outputFormat%22%3A%22conll%22}' -o -
```


---

#### Tradeoffs

- docker container needs 4gb of memory
- model doesn't have features (case, number, ...)

---


## Spacy

- https://spacy.io/
- DP models for: English, German, Spanish, Portuguese, French, Italian, Dutch

---

### Demo

```sh
# run webserver
docker run -p "80:80" jgontrum/spacyapi:de_v2
```

```sh
# show UI in browser
http://34.251.60.217/ui/?text=Die%20%C3%84rmel%20der%20Strickjacke%20haben%20am%20Armabschluss%20ein%20B%C3%BCndchen.&model=de_dep_news_sm&cpu=0&cph=0
```

```sh
# get json data via curl
curl -s http://34.251.60.217/dep -d '{"text":"Die Ärmel der Strickjacke haben am Armabschluss ein Bündchen.", "model":"de_dep_news_sm"}'
```

---

### Tradeoffs

- no ConLL format natively - but json is fine
- limited number of languages: EN, DE, ES, FR
  https://github.com/jgontrum/spacy-api-docker#images


---

## Google Cloud

- commercial API from google for syntax, sentiment and NER.

---

### Demo

not really. it is an API.

<img src="/images/hans_sieht_maria.png" width="80%">

<a href="/google-cloud-output.json">example json response</a>

---

### Tradeoffs

- costs money (not that much; 1000 requests - 0.50$)
- limited number of languages: Chinese, English, French, German, Italian, Japanese, Korean, Portuguese, Spanish

---

Vielen Dank für eure Aufmerksamkeit!
