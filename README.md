# Deep_Learning_Classification
In this competition, you are asked to solve the image classification problem for DL20 dataset we have prepared.

To evaluate the performance of your model, you should use the accuracy metric, which is widely used in image classification. However, high accuracy doesn't mean you will get a high score on this project. We will consider the novelty of your project, a poster presentation you will prepare, and many other factors during project period.

***

**추가사항** 
- Baseline.ipynb 파일을 추가했습니다. 노트북 파일이기 때문에 순석대로 하나하나 run하면 됩니다.
- 기존 train.py가 맘에 안들어서 제가 training하는 부분은 새로 작성했습니다. (한 epoch 돌때마다 validation accuracy를 측정해 bottleneck이 발생하더라구요...)
- 특별한 건 없고 early stopping 하나만 추가해 validation loss가 설정한 "patience"가 지나도 더이상 줄어들지 않으면 training을 종료합니다.
- 맨 마지막의 Test accuracy라고 써져 있는 부분은 validation set에 대한 accuracy입니다. Test set은 라벨링이 되어 있지 않기 때문에 Kaggle에서 돌려보지 않는 이상 모릅니다.

**유의사항**
- 기본적인 파라미터들은 조교님께서 주신 것들과 비슷하지만 batch_size와 learning rate만 살짝 바꿨습니다.
- **MultiEpochsDataLoader의 파라미터중 num_workers(코어 수)가 있는데 제가 3090으로 해서 64로 설정했습니다. 4, 8, 16 등으로 줄이셔야 할겁니다. 높을수록 training이 빨라지지만 본인의 코어 수를 넘기면 에러가 뜨기 때문에 에러가 나지 않는 선까지 올리시면 됩니다.**

**Todo**
- Kaggle에 제출하기 위해 test dataset을 classify해서 이미지/클래스 CSV파일 만들기 

***

## Dataset

* preparations:
  1. Prepare DL20 dataset.
  2. make the folder structure of the dataset as follows:
```
┌── README.md
├── data_loader.py
├── model.py
├── train.py
└── data
    └── DL20
        ├── train
        │   ├── cls0
        │   │   ├── 101.png
        │   │   ├── 134.png
        │   │   └── ...
        │   ├── cls1
        │   └── ...
        ├── valid
        │   ├── cls0
        │   │   ├── 6705.png
        │   │   ├── 6722.png
        │   │   └── ...
        │   ├── cls1
        │   └── ...
        └── test
            ├── 100011.png
            ├── 100196.png
            ├── 100334.png
            └── ...
```

# Quick Start

```bash
CUDA_VISIBLE_DEVICES=0 python3 train.py
```

# About Backbone Network

We provide a simple backbone network, Small-Resnet18. However, you can use any other backbone networks for your problem.
