# specimen-ner

Code and data in this repository support an ongoing project to analyze specimen references in natural history collections [under development]. The goals of this project are to:
1. develop a named entity recognition (NER) model to detect references to specimen in text
2. apply the model to extract references to specimen across various natural history collection
3. analyze specimen citations and co-citations to demonstrate the impact of collections

## /data
Articles from the bibliographies of natural history collections. PDFs are parsed with [GROBID](https://github.com/kermitt2/grobid) software.
* `bibliography_ummz_json`: 461 articles from the [University of Michigan Museum of Zoology](https://lsa.umich.edu/ummz) bibliography
* `bibliography_ummz_json`: 46 articles from the [University of Texas Works Progress Administration](https://www.jsg.utexas.edu/vpl/collections/the-works-progress-administration-wpa-collection) bibliography

## /notebooks
Demonstration of NER model applied to each bibliography.
* `UMMZ_results.ipynb`: notebook for detecting references to specimens in the UMMZ bibliography
* `WPA_results.ipynb`: notebook for detecting references to specimens in the WPA bibliography

## /output
Best performing Named Entity Recognition (NER) model trained and evaluated in a [spaCy](https://spacy.io/) pipeline.
* /model-best: recall (96.4); precision (91.1); F-score (93.7)

## /results
Collection-level reports on the frequency of specimen references in articles, specimen predictions, unique specimens references per paper, and total specimen counts.

## /train
Sentences with labeled entities from UMMZ, WPA bibliographies. 1,010 sentences split into 80% training (train.spacy) and 20% test (dev.spacy)
* config.cfg: Configuration settings for training model in spaCy


