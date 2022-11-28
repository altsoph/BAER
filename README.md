# BAER

## TLDR
This repo contains supplemental materials accompanying the "[Actionable Entities Recognition Benchmark for Interactive Fiction](https://arxiv.org/abs/2109.13855)" paper, presented at  NILLI Workshop at EMNLP 2022.

## Data

We used 5K+ locations from 1K interactive text fiction games and extracted textual descriptions of locations and lists of actionable entities in them. 
The resulting [BAER dataset is available here](https://github.com/altsoph/BAER). You can find this [dataset here](https://github.com/altsoph/BAER/blob/main/BAER.txt).

## Benchmarking

We also trained an XLM-Roberta based language model fine-tuned for AER (Actionable Entities Recognition) -- recognition of entities that protagonists could interact with for further plot development.

## Example

The example of usage:
```py
from transformers import AutoModelForTokenClassification, AutoTokenizer, pipeline

MODEL_NAME = "altsoph/xlmr-AER"

text = """This bedroom is extremely spare, with dirty laundry scattered haphazardly all over the floor. Cleaner clothing can be found in the dresser.
A bathroom lies to the south, while a door to the east leads to the living room."""

model = AutoModelForTokenClassification.from_pretrained(MODEL_NAME)
tokenizer = AutoTokenizer.from_pretrained(MODEL_NAME)

pipe = pipeline("token-classification", model=model, tokenizer=tokenizer, aggregation_strategy="simple", ignore_labels=['O','PAD'])
entities = pipe(text)

print(entities)
```

## How to cite

If you use the model, please cite the following:

```
@inproceedings{Tikhonov-etal-2022-AER,
    title = "Actionable Entities Recognition Benchmark for Interactive Fiction",
    author = "Alexey Tikhonov and Ivan P. Yamshchikov",
    year = "2022",
}
```

## NILLI Workshop materials

* [Poster](https://github.com/altsoph/BAER/blob/main/AERBIF_poster_A0_v4.pdf)
