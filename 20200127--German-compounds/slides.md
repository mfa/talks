class: center, middle

# German compounds - zusammengesetzte Wörter

Andreas Madsack (mfa)

datenobservatorium<br/>
2020-01-27

---

## Problem

- Geschlecht ist im Deutschen lexikalisiert -> viele Lexikoneinträge

--

- Der Kopf bestimmt das Geschlecht

--

z.B.
- Kunstleder - neutral
- Kunstledertasche - female
- Kunstlederkoffer - male

---

## Solution: Kopferkennung (mit charsplit)

- Kunstleder

```
0.4165885676205648      Kunst   Leder
-0.5776753308648312     Kunstle Der
-1.7192851824274014     Kunstl  Eder
-1.9277687556115966     Kun     Stleder
-1.9388189956940949     Kuns    Tleder
```

- Kunstledertasche

```
0.6167321981586269      Kunst   Ledertasche
-0.3936170212765957     Kunstleder      Tasche
-0.8394543546694648     Kunstledert     Asche
...
```

- Kunstlederkoffer

```
-0.5364372469635628     Kunstleder      Koffer
-0.7928571428571428     Kunstlederk     Offer
-0.9070773256508968     Kunst   Lederkoffer
...
```


---

## Wie funktioniert charsplit?

- verschiedene splits werden durchprobiert
- beste Prefix/Suffix probabilities +  niedrigste Infix probabilities werden genommen
- Fugen-s wird entfernt, wenn das Wort mit `ts`, `gs`, `ks`, `hls` oder `ns` endet


---

## weitere spannendere Beispiele

- Staubecken

```
0.6811588117086161      Staub   Ecken
0.5676378050229346      Stau    Becken
```

- Taschenmesserklinge

```
-0.5094339622641508     Taschenmesser   Klinge
-0.6214869864347374     Taschen Messerklinge
```

- Kuddelmuddel

```
-1.142400176483565      Kud     Delmuddel
-1.5325391572909772     Kuddelmud       Del
-2.027027027027027      Kuddel  Muddel
```
- Bettnässer

```
-1.3230399037497493     Bettnäs Ser
-1.4030454437306685     Bett    Nässer
```



---

## alternative Ideen

- direkt im Lexikon nachschauen -> mglw. zu langsam
- Modelle basierierend auf Silbengrenzen (hat Probleme mit z.B. Fugen-S)

---

## thanks

talk to me about

- python
- machine-learning
- computerlinguistics
