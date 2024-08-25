# STPA - Step 1 - Dataset

## Introduction
This dataset contains textual sentences generated and used during the first step of the ***System-Theoretic Process Analysis*** (STPA) hazard analysis technique, called "defining the purpose of the analysis".
In this step, three security aspects of the system are defined:
- ***Losses*** are something of value which a loss is unacceptable to stakeholders, such as human life, equipment or mission;
- ***System-Level Hazards*** are system states or conditions that, together with a set of worst-case environmental conditions, will lead to a loss;
- ***Sustem-Level Constraints*** are the system's conditions or behaviors that need to be satisfied to prevent hazards.

## Dataset Creation
This dataset was created by extracting sentences found in presentations from the [*Annual MIT STAMP Workshop*](https://psas.scripts.mit.edu/home/).
The presentations are from 2012 to 2023.

### How to Use
The dataset is a ".csv" file.
For Python programming language, the use of Pandas library is recommended:
```python
import pandas as pd
df = pd.read_csv(r'/[PATH]/stpa-step1-dataset.csv')
```

## Dataset Columns
This dataset has 8 columns that organize the collected data.
1. "sentence": The extracted textual sentence;
2. "label": The classification label related to the sentence;
3. "domain": The presentation domain;
4. "year": The year of presentation;
5. "title": The presentation title;
6. "url": The presentation URL;
7. "slide": The slide number where the sentence was extracted;
8. "obs": If the presentation is not explicitly about STPA, then the type of presentation.

## Class distribution
The sentences extracted are from slides that explicitly show the type of sentence (for example a table explaining which are the system losses and hazards), that automatically represents the corresponding label to be filled in the dataset. However, the presentations containing different amounts of examples lead to an unbalanced dataset.
| Class  | Sentences |
| :---     |        ---: |
| loss  | 254  |
| hazard  | 408  |
| constraint  | 316  |
| exloss  | 47  |
| hazard  | 34  |
| constraint  | 19  |
| Total  | 1078  |

In this dataset, there are few sentences with ambiguous meanings, or lack of information or context. Some sentences might be too different from what is recommended by the STPA Handbook. Instead of completely removing these sentences from the dataset, the sentences which may impact classification performance were grouped into a new label, named “excluded” sentences. In order to keep the original label information, a combination of both labels is used, resulting in new "exloss", "exhazard" and "exconstraint" labels.

The criteria for separation are as follows:

For Losses:
1. The sentence should contain a Loss-related keyword (such as “loss”, “damage”, “injury”);
2. The sentence should involve something of value to stakeholders.

For Hazards:
1. The sentence should mention a <system> and an <unsafe condition>;
2. The sentence should be a state or condition that, together with a set of worst-case environmental conditions, will lead to a loss.

For Constraints:
1. The sentence should mention a <system> and <condition to enforce> (using a modal verb, such as “must”, ”shall”, “should”);
2. The sentence can also define how to minimize losses in case a hazard occurs.

## Classification Experiments
In this repository is available a Python Notebook to demonstrate the use of this dataset. There are two experiments that use traditional machine learning classification algorithms, called Support Vector Machines (SVM) and Naïve Bayes (NB).

Experiment 1: Classification of sentences only using the “loss”, “hazard” and “constraint” labels, without the “excluded” sentences. This aims to investigate the dataset in a clean state, with sentences closer to what is recommended by the Handbook.

Experiment 2: Classification of sentences with the “excluded” sentences reverted and added back into their original classes (“exloss”, “exhazard” and “exconstraint” added back into “loss”, “hazard” and “constraint”, respectively). This aims to investigate the dataset by including possible noise from excluded sentences, and to compare the dataset in different levels of quality.

## About the Author
This dataset was created by the Computing and Communication Systems graduate student *Andrey Toshiro Okamura*, from the State University of Campinas (UNICAMP)'s School of Technology.
