# Supervised OpenIE baseline and evaluation code

The ACoLi fork has been created as a point of reference for the OpenIE benchmark data in the `data/` folder, see attribution there. The remainder of the readme is about the *code*.

## Data

Data is created from [QASRL]{https://dada.cs.washington.edu/qasrl/} as described by Stanovsky and Dagan (2016):

    @inproceedings{stanovsky-dagan-2016-creating,
        title = "Creating a Large Benchmark for Open Information Extraction",
        author = "Stanovsky, Gabriel  and
          Dagan, Ido",
        booktitle = "Proceedings of the 2016 Conference on Empirical Methods in Natural Language Processing",
        month = nov,
        year = "2016",
        address = "Austin, Texas",
        publisher = "Association for Computational Linguistics",
        url = "https://aclanthology.org/D16-1252",
        doi = "10.18653/v1/D16-1252",
        pages = "2300--2305",
    }

## Code 

The maintenance of this project has moved to the [AllenNLP framework](https://allennlp.org/). <br>
Where you can use [the model and an online demo](http://demo.allennlp.org/open-information-extraction).
This [thin wrapper](https://github.com/gabrielStanovsky/supervised_oie_wrapper) may also be useful if you want to run the pretrained model.

Supervised OIE code for training a supervised Neural Open IE model, as described in a [NAACL2018 paper](https://gabrielstanovsky.github.io/assets/papers/naacl18long/paper.pdf).<br>

If you use this software, please cite:
```
@InProceedings{Stanovsky2018NAACL,
  author    = {Gabriel Stanovsky and Julian Michael and Luke Zettlemoyer and Ido Dagan},
  title     = {Supervised Open Information Extraction},
  booktitle = {Proceedings of The 16th Annual Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies (NAACL HLT)},
  month     = {June},
  year      = {2018},
  address   = {New Orleans, Louisiana},
  publisher = {Association for Computational Linguistics},
  pages     = {(to appear)},
}
```

Quickstart :hatching_chick:
-----------

1. Install requirements :bow:
```bash
pip install requirements.txt
```

2. Download embeddings :walking:
```bash
cd ./pretrained_word_embeddings/
./download_external.sh
```

3. Train model :running:
```bash
cd ./src
python  ./rnn/confidence_model.py  --train=../data/train.conll  --dev=../data/dev.conll  --test=../data/test.conll --load_hyperparams=../hyerparams/confidence.json```
```
***NOTE:*** Models are saved by default to the models dir, unless a "--saveto"
command line argument is passed. See [confidence_model.py](src/rnn/confidence_model.py) for more details. 

4. Predict with a trained model :clap:
```bash
python ./trained_oie_extractor.py \
    --model=path/to/model \
    --in=path/to/raw/sentences
    --out=path/to/output/file
    --conll
```

More scripts :bicyclist:
------------

See [src/scripts](src/scripts) for more handy scripts. Additional documentation coming soon!

