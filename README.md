# PREM-GAD Reproduction and Extended Experiments

This repository contains my reproduction of the paper  
**“PREM: A Simple Yet Effective Approach for Node-Level Graph Anomaly Detection”**  
and my additional experiments on new datasets.

Original implementation:  
https://github.com/CampanulaBells/PREM-GAD  
(The original README is preserved under `/original_README/`.)

---

##  Project Overview

This work aims to:

1. Reproduce the original PREM-GAD results on classic benchmark datasets (Cora, Citeseer, PubMed, ACM, Flickr)

2. Extend the experiments to new datasets such as BlogCatalog, and perform anomaly injection following the strategy introduced in Ding et al. (SDM 2019).

---

##  Environment Setup

My experiments were conducted in **Google Colab(T4 GPU)** with the following environment:

| Library | Version |
|--------|---------|
| Python | 3.12.12 |
| DGL | 2.4.0 + cu124 |
| PyTorch | 2.4.0 + cu121 |
| TorchVision | 0.19.0 + cu121 |
| Torchaudio| 2.4.0 + cu121 |

Since DGL must match the installed PyTorch version, please install PyTorch **first**, then install DGL:

```
!pip install torch==2.4.0 torchvision==0.19.0 torchaudio==2.4.0 \
    --index-url https://download.pytorch.org/whl/cu121 -q

!pip install dgl -f https://data.dgl.ai/wheels/torch-2.4/cu124/repo.html
```

##  Dataset Sources and Anomaly Injection

The additional dataset used in my extended experiments (BlogCatalog) was obtained from a public GitHub repository referenced in a related work.  
Since the original dataset does not contain ground-truth anomaly labels, I follow the anomaly injection strategy described in:

Ding et al., 2019 — “Deep Anomaly Detection on Attributed Networks” (SDM 2019)

This procedure injects approximately 300 synthetic anomalies into the graph, consisting of:

&nbsp;&nbsp;&nbsp;&nbsp;•Attributive anomalies: replacing node features with those from distant nodes
&nbsp;&nbsp;&nbsp;&nbsp;•Structural anomalies: rewiring selected nodes into fully connected subgraphs


##  Running Experiments on New Datasets

To reproduce the result of new dataset(Blogcatalog) , run 

```
python run.py –dataset blogcatalog --lr 0.0005 --alpha 0.1 --gamma 0.9 --num_epoch 1500
```


##  Citation

This project is based on the official PREM-GAD implementation.  
If you use PREM-GAD in your research, please cite the original paper:

```bibtex
@inproceedings{pan2023prem,
  title={PREM: A Simple Yet Effective Approach for Node-Level Graph Anomaly Detection},
  author={Pan, Junjun and Liu, Yixin and Zheng, Yizhen and Pan, Shirui},
  booktitle={2023 IEEE International Conference on Data Mining (ICDM)},
  pages={1253--1258},
  year={2023},
  organization={IEEE}
}

