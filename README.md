# UD_North_Saami

Files:

* `sme-udep.xml`: Tree transformation rules for Giella-style dependency trees to UD-style.

Prerequisites:

* ```vislcg3``

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
