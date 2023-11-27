class: center, middle

# Longest Common Sequence

Andreas Madsack (mfa)

AX Semantics<br/>
2023-11-21

---

## Problem

- import banking statements csv into hledger files and into accounts
- Idea: find common substrings in the csv and have a lookup table for account names
- example strings:

```
- "# KAUFLAND | Kaufland Stuttgart//Stuttgart/DE 20 23-10-13T21:41:51 Folgenr.000 Verfa lld.2027-12"
- "# VISA KAUFLAND STUTTGART VAI | NR XXXX 1023 STUTTGART V KAUFUMSATZ 14.10 211231 ARN24xx3683288582881829xxx Google Pay"
```

- negatives:

```
- "# VISA ALDI SUED | NR XXXX 1023 STUTTGART KAUFUMSATZ 10.10 202540 ARN74xx0723283318365751xxx Google Pay"
- "# VISA LIDL DIENSTLEISTUNG | NR XXXX 1023 STUTTGART KAUFUMSATZ 18.10 121135 ARN74xx0723291314287015xxx Google Pay"
```


---

## Solution using core Python

- `difflib.SequenceMatcher` can find matching sequences in a pair of strings
- `itertools.combinations` pairs all elements of a list
- generate a set of strings that match all strings
- remove all that match a negative list of strings
- code for the implementation: <https://github.com/mfa/longest-common-sequence>
- deployed web version: <https://lcs.madflex.de/>

---

## Why not with machine learning?

- Initially I thought about training a character based LSTM to classify for different categories
- Or maybe clustering?
- But the biggest issue to start with was training data!
  I have quite few years of personal hledger data, but only for 1 year with csv as source -- before I was using HBCI.
  Aside from that there seems to be no Python package to parse ledger files with comments.


---


## Questions?

