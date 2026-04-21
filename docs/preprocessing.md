# Preprocessing the data

The first step of the pipeline is to preprocess the data.
During this step, we will format the inputs of each methods accordingly.

Additionnaly, we will retrieve the LDSC results.

```bash
sh run_preprocessing.sh
```

## Method specific filtering

### FactorGo

Variants were selected based on the following filters:

* MAF > 0.01 (Done in JASS preprocessing)
* Outside of HLA locus (Chr 6: 28510120-33480577)
* p < 5e-8 in at least two study
* LD pruning with kb = 250 and r2 < 0.3

### GFA

Variants were selected based on the following filters:

* MAF > 0.01 (Done in JASS preprocessing)
* Differ by less than 10% from the median sample size
* LD pruning with kb = 1000, r2 < 0.01 and p < 0.05

### GLEANR

Variants were selected based on the following filters:

* MAF > 0.01 (Done in JASS preprocessing)
* Outside of HLA locus (Chr 6: 28510120-33480577)
* p < 10e-5 in at least one study
* LD based on pleiotropy score with kb = 250 and r2 < 0.2 (detailed in [Note S3](https://ars.els-cdn.com/content/image/1-s2.0-S0002929725002733-mmc1.pdf))
