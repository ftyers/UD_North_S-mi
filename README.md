# UD_North_Saami

Files:

* `sme-udep.xml`: Tree transformation rules for Giella-style dependency trees to UD-style.

Prerequisites:

* ```vislcg3```
* ```matxin```
* ```ud-scripts```

Using this stuff:

The source corpus, which has been manually disambiguated morphologically and annotated
for syntactic function:

  http://victorio.uit.no/langtech/trunk/langs/sme/test/data/functionsCG.corr.txt

You will need the dependency parser from:

  http://victorio.uit.no/langtech/trunk/giella-shared/smi/src/syntax/dependency.cg3

Apply the dependency parser to the corpus:

```
   cat functionsCG.corr.txt | vislcg3 --grammar dependency.cg3 > functionsCG.dep.txt
```

You can compile the ```sme-udep.xml``` file using ```matxin-preprocess-transfer```:

```
  matxin-preprocess-transfer sme-udep.xml sme-udep.bin
```

Then convert the annotated corpus to Matxin XML:

```
  cat functionsCG.dep.txt | vislcg3-to-conllu.py | conllu-to-matxin.py > functionsCG.dep.xml
```

And apply the transformations:

```
  cat functionsCG.dep.xml | matxin-transfer sme-udep.bin > functionsCG.u-dep.xml
```

And then convert to CoNLL-U:

```
  cat functionsCG.u-dep.xml | matxin-to-conllu.py > sme-ud-train.conllu
```
