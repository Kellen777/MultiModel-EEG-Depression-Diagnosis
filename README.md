## EEG-based Depression Diagnosis

​        本项目旨在利用 EEG 信号和深度学习模型进行抑郁症诊断。项目中使用了来自 MODMA 数据集的 EEG 信号，通过多种数据预处理方法，包括将信号转化为适合自然语言处理的时间序列数据和频谱图数据，并使用不同的深度学习模型（包括 CNN、ResNet-18、Transformer 和 LSTM）进行模型训练和抑郁症识别。该项目的目标是为抑郁症的早期诊断提供一种高效的计算机辅助诊断方法。

## MODMA Dataset

​       MODMA 数据集由兰州大学可穿戴计算重点实验室所提供，包含了抑郁症患者和健康对照组的 EEG 信号。点击下面的链接可以获取该数据集详情 http://modma.lzu.edu.cn/data/index/

## Project Organization

```
EEG-based-Depression-Diagnosis/
│
├── data/                            # 数据文件夹
│   ├── Dataloader_1D/               # 1D时间序列数据加载器
│   └── Dataloader_2D/               # 2D频谱图数据加载器            
|   └── dataset_2Dimages/            # 2D频谱图
|   └── EEG_128channels_resting_lanzhou_2015 # 原始EEG数据
|   └── EEG_dataset                  # numpy数组格式数据
|   └── train_val_test_2Ddataset     # 2D频谱图训练集、验证集、测试集
│
├── data_preprocessing/              # 预处理数据并存储
│   ├── EEG_raw_preprocessing.ipynb  # 原始.mat格式数据转换成.npy格式
│   └── EEG_preprocessing_1D.ipynb   # 把数据集处理成时间序列数据并创建数据加载器
|   └── EEG_to2Dimages_Dataloader.ipynb # 把数据集处理成2D频谱图数据并创建数据加载器
│
├── Multiple_Models/                 # 模型训练和测试
│   ├── CNN.ipynb                    # CNN模型
│   ├── ResNet-18.ipynb              # ResNet-18 模型
│   ├── Transformer_model.ipynb      # Transformer 模型
│   └── LSTM.ipynb                   # LSTM 模型代码
│
│
└── README.md                        # 项目说明文件
```

## data_preprocessing

​        为了方便后续操作，首先将这些 `.mat` 文件转换为 numpy 数组，并保存为 `.npy` 文件，便于加载和处理。后续转换成了时间序列数据，用作LSTM、Transformer网络的数据集，以及2D频谱数据，用作CNN、ResNet-18网络的数据集。

## Multiple_Models

​        这一部分是模型的训练和测试，经过测试得出下列结论：

（1）CNN模型难以捕捉频谱图的特征，效果较差。

（2）ResNet-18网络可以较好得捕捉频谱图特征，经过一定轮次的训练，可以得到不错的识别准确率，但是模型训练的收敛速度较慢，需要花费较长的时间训练。

（3）LSTM和Transformer需要的训练时间很短，且已经达到了几乎百分百的准确率，通过EEG数据识别抑郁症有显著的优势。