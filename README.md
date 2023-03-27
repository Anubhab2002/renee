# Renee: End-to-end training of extreme classification models

Official PyTorch implementation for the paper: "Renee: End-to-end training of extreme classification models" accepted at MLSys 2023.

## Abstract

The goal of Extreme Multi-label Classification (XC) is to learn representations that enable mapping input texts to the most relevant subset of labels selected from an extremely large label set, potentially in hundreds of millions.

We identify challenges in the end-to-end training of XC models and devise novel optimizations that improve training speed over an order of magnitude, making end-to-end XC model training practical. Renee delivers state-of-the-art accuracy in a wide variety of XC benchmark datasets.

## Requirements

Run the below command, this will create a new conda environment with all the dependencies required to run Renee.

```bash
bash install1.sh
```

## Training sripts

Train Renee on LF-AmazonTitles-131K dataset, you can use the following command (make sure you modify `data-dir`, `use-ngame-encoder` accordingly)
```bash
python main.py \
--epochs 100 \
--batch-size 32 \
--lr1 0.05 \
--lr2 1e-5 \
--warmup 5000 \
--data-dir xc/Datasets/LF-AmazonTitles-131K-Aug \
--maxlen 32 \
--tf sentence-transformers/msmarco-distilbert-base-v4 \
--dropout 0.85 \
--pre-tok \
--wd1 1e-4 \
--noloss \
--fp16xfc \
--use-ngame-encoder xc/ngame_pretrained_models/LF-AmazonTitles-131K/state_dict.pt \
--expname debug
```
To change hyperparameters, you can refer to the various arguments provided in `main.py` file or you can do `python main.py --help` to list out the all the arguments.

## Citation

If you find our work/code useful in your research, please cite the following:

```bibtex
@article{Renee2023,
  title={Renee: End-to-end training of extreme classification models},
  author={Jain, Vidit and Prakash, Jatin and Saini, Deepak and Jiao, Jain and Ramjee, Ramachandran and Varma, Manik},
  journal={Proceedings of Machine Learning and Systems},
  year={2023}
}
```

## References