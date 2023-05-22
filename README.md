# Specimen Citations

This repository supports an ongoing project to surface and analyze specimen citations in natural history collections. The goals of this project are to:
1. develop a computational model to detect references to museum specimens in text
2. compare this model to other methods of detecting references to mseum specimens in text (RegEx, ChatGPT)
3. apply the model to extract specimen references in academic literature
4. analyze specimen citations to demonstrate the impact of collections

Our initial corpus comes from:
- the University of Michgan Museum of Zoology's Google Scholar page, which has been compiled by Cody Thompson and others at UMMZ. This bibliography includes papers _by_ researchers associated with the divorse, and papers that _use_ specimens from the collection. 
- an internally curated bibliography from the Smithsonian 

# Findings so far
- Custom NER model and RegEx outperform ChatGPT. 
- Custom NER model was more flexible and generalized well with edge cases, whereas RegEx was less flexible and often missed examples such as code ranges (e.g. "LACM 10203-10207")
- Specimen citation metrics are lower overall than we expected, but further work is needed to figure out why. Our corpora may simply be too small to capture a holistic picture of a collection's specimen use. This should be a consideration in any future infrastructure or metrics development for tracking specimen citation
- We suspect ChatGPT performance could be improved with better prompt engineering, but this is a nascent area. A focused study on the perfromance of ChatGPT with different tasks is needed.

# Resources:
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
