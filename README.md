# Specimen Citations

This repository supports an ongoing project to surface and analyze specimen citations in natural history collections. The goals of this project are to:
1. develop a computational model to detect references to specimen in text
2. apply the model to extract specimen references in academic literature
3. analyze specimen citations to demonstrate the impact of collections

Resources:
- [University of Michigan Museum of Zoology](https://lsa.umich.edu/ummz/mammals/publications.html) bibliography
- [GROBID](https://github.com/kermitt2/grobid) software
- [Prodigy](https://prodi.gy/docs) software
- [spaCy](https://spacy.io/usage/training) software
- [GPT](https://platform.openai.com/docs/models) API

## /data
* `bibliography_ummz_json`: 461 papers from from the University of Michigan Museum of Zoology bibliography parsed with with GROBID software
* `formal_collection_acronym`: list of mammal collections
* `specimen_truth_deck`: labeled sentences from UMMZ papers for model validation
* `ummz_bib`: full list of papers from the UMMZ bibliography as of fall 2022
* `ummz_pattern_matching`: sentences extracted from UMMZ papers labeled in Prodigy software for NER training

## /notebooks
* `gpt_specimens` : search for specimens using GPT-3
* `ner_specimens` : train a custom NER model with spaCy to search for specimen codes
* `regex_specimens` : search for specimens using regular expression pattern matching on mammal collection codes
* `truth_deck`: compare truth deck sentences (n=374) to RegEx; NER; and GPT using Jaro-Winkler similarity score
* `ummz_results`: run custom NER model on all available papers in the UMMZ bibliography

## /output
* `/model-best`: best performing Named Entity Recognition (NER) model trained and evaluated in a [spaCy](https://spacy.io/) pipeline with recall (96.4); precision (91.1); F-score (93.7)

## /results
* `frequency_ummz`: count of specimens extracted with NER model
* `predictions_ummz`: row level specimen predictions from NER model
* `specimens_per_paper_ummz`: grouped specimen predictions per paper from NER model
* `ummz_specimen_count`: plot of specimen frequencies across available papers in the UMMZ bibliography

## /train
* `labels`: input labels for training NER model (1,010 sentences)
* `config`: configuration settings for NER training in spaCy
* `dev.spacy`: labels held out for evaluating NER model (20%)
* `train.spacy`: labels used in training NER model (80%)