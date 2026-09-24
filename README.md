## Confounding-aware rectified weakly supervised learning for EGFR genotyping via tumor CT images
A preliminary implementation of CR-MIL.


## ⚙️ Environmental Requirements
To run the codes, the following dependencies are required:
+ python 3.9
+ PyTorch 1.12.0
+ cuda 11.3
+ torchvision 0.13.0
+ torchnet 0.0.4
+ pandas 2.2.3
+ numpy 1.26.4

## 📁 File Descriptions

The main files and directories are organized as follows:

```text
CR-MIL/
├── train_te.py
├── datasets.py
├── utils.py
├── README.md
├── models/
│   ├── __init__.py
│   ├── CR_MIL.py
│   ├── MSA_relative_instance_input.py
│   └── relative_position_encoding.py
└── Figs/
```

- `train_te.py`: Model training, validation, testing, and result saving.
- `datasets.py`: Dataset loading, CT normalization, patch extraction, and data splitting.
- `utils.py`: Loss functions.
- `models/CR_MIL.py`: Main CR-MIL model implementation.
- `models/MSA_relative_instance_input.py`: Vision Transformer and attention modules.
- `models/relative_position_encoding.py`: Relative position encoding implementation.


## 🚀 Training

Before training, please update the dataset paths and GPU configuration in:

- `train_te.py`
- `datasets.py`

Then run:

```bash
python train_te.py
```

The default training configuration is:

| Parameter | Value |
| --- | --- |
| Batch size | 16 |
| Epochs | 100 |
| Learning rate | 0.0001 |
| Optimizer | Adam |
| Number of task-relevant patches | 75 |

The code performs five-fold training using the following split settings:

```python
['12345', '23451', '34512', '45123', '51234']
```

For each split, four folds are used for training and the remaining fold is used for validation.