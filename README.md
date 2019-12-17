## Is BERT good at low resource Neural Machine Translation?

This repository contains the code for fine-tuning and analyzing BERT for resource constrained neural translation task. The resource constrained language chosen for our experiments is Latin. 

Google recently added versions of BERT that have [multilingual support](https://github.com/google-research/bert/blob/master/multilingual.md)
  
For our experiments we used the `bert-base-multilingual-uncased` model.


### Package Requirements and Installation

* [PyTorch](http://pytorch.org/) version >= 1.0.0
* Python version >= 3.5

```
git clone https://github.com/shreyapandit/bert-nmt-latin
pip install --editable .
```

## How to run

### Data Preprocessing
 First, prepare the Latin dataset by executing prepare_dataset_dec6.ipynb

### Prepare data for BERT and fine-tune BERT:
Run the BERT-latin-v2.ipynb

### Generate translations and evaluation of BLEU score
Replace file paths as appropriate.

```
python generate.py  --quiet --bert-model-name bert-base-multilingual-uncased \
                    --path /content/drive/My\ Drive/shreya_bert_on_collab/checkpoints_bert_lat_multilingual_2/checkpoint_best.pt \
                    examples/translation/iwslt14.tokenized.lat-en \
                    | tee -a /content/drive/My\ Drive/shreya_bert_on_collab/checkpoints_bert_lat_multilingual_2/generate.log

```

Some of the code has been inspired/re-used from [this](https://github.com/bert-nmt/bert-nmt) implementation of BERT for NMT

### Major contributions:
 - Preparing a classical latin dataset to make it usable for downstream tasks such as NMT using BERT
 - Experiments to analyze performance of BERT for Latin, a low resource language (We acheived a BLEU Score of 20.23)
