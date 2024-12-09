# KLUE-NER SNRoberta

This project implements Named Entity Recognition for the KLUE (Korean Language Understanding Evaluation) benchmark using an ensemble of RoBERTa models. The project includes multi-GPU training automation and ensemble evaluation with Stochastic Weight Averaging (SWA).

## Project Structure
```
.
├── README.md
├── environment.yaml
├── main_SWA_NER.py
├── eval_across_architecture.py
├── run_parallel_experiments-epochs=10_SWA_ensemble.sh
├── eval.sh
├── src/
│   ├── __init__.py
│   ├── datasets.py
│   └── utils.py
└── data/
    └── klue-ner/
```

## Installation

1. Clone the repository:
```bash
git clone https://github.com/jhpark-kaist/KLUE-NER-SNRoberta
cd KLUE-NER-SNRoberta
```

2. Install required packages:
```bash
conda env create -f environment.yaml
conda activate kllm-fairness
```

## Usage

### Training
```bash
chmod +x run_parallel_experiments-epochs=10_SWA_ensemble.sh
./run_parallel_experiments-epochs=10_SWA_ensemble.sh
```

### Evaluation
```bash
chmod +x eval.sh
./eval.sh
```

## Results

### Model Performance Across Seeds

| Seed | Model                                                                  | Entity F1  | Char F1    | Status |
|------|------------------------------------------------------------------------|------------|------------|---------|
| 1    | roberta-base_seed=1_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa   | 89.33      | 93.81      | OK      |
| 1    | roberta-large_seed=1_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa  | 88.70      | 93.71      | OK      |
| 1    | **ENSEMBLE**                                                           | **89.34**  | **93.91**  | **OK**  |
| 2    | roberta-base_seed=2_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa   | 89.04      | 93.58      | OK      |
| 2    | roberta-large_seed=2_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa  | 89.68      | 94.01      | OK      |
| 2    | **ENSEMBLE**                                                           | **89.80**  | **94.06**  | **OK**  |
| 3    | roberta-base_seed=3_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa   | 88.79      | 93.64      | OK      |
| 3    | roberta-large_seed=3_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa  | 89.19      | 93.58      | OK      |
| 3    | **ENSEMBLE**                                                           | **89.41**  | **93.95**  | **OK**  |
| 4    | roberta-base_seed=4_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa   | 89.28      | 93.71      | OK      |
| 4    | roberta-large_seed=4_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa  | 89.05      | 93.61      | OK      |
| 4    | **ENSEMBLE**                                                           | **89.55**  | **93.93**  | **OK**  |
| 5    | roberta-base_seed=5_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa   | 88.91      | 93.62      | OK      |
| 5    | roberta-large_seed=5_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa  | 89.47      | 93.88      | OK      |
| 5    | **ENSEMBLE**                                                           | **89.79**  | **94.10**  | **OK**  |
| 6    | roberta-base_seed=6_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa   | 88.63      | 93.75      | OK      |
| 6    | roberta-large_seed=6_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa  | 88.98      | 93.86      | OK      |
| 6    | **ENSEMBLE**                                                           | **89.23**  | **94.02**  | **OK**  |
| 7    | roberta-base_seed=7_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa   | 89.09      | 93.78      | OK      |
| 7    | roberta-large_seed=7_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa  | 89.05      | 93.83      | OK      |
| 7    | **ENSEMBLE**                                                           | **89.53**  | **94.03**  | **OK**  |
| 8    | roberta-base_seed=8_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa   | 88.77      | 93.72      | OK      |
| 8    | roberta-large_seed=8_lr=5e-05_batch=32_outweight=1.0_freeze=False_swa  | 89.46      | 93.86      | OK      |
| 8    | **ENSEMBLE**                                                           | **89.43**  | **94.03**  | **OK**  |

### Average Ensemble Performance
**Entity F1: 89.51 ± 0.19**  
**Char F1: 94.00 ± 0.06**
