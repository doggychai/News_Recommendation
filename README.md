# 新闻推荐系统

基于多路召回和LightGBM排序的新闻推荐系统，采用协同过滤、双塔网络和Word2Vec等多种召回策略，结合丰富的特征工程，实现精准的个性化新闻推荐。

## 项目概述

本项目实现了一个完整的新闻推荐系统，包含以下核心功能：

### 召回阶段
- **ItemCF召回** (recall_itemcf.py): 基于物品协同过滤的召回策略，考虑用户历史点击序列的位置信息权重
- **Bi-Network召回** (recall_binetwork.py): 基于双塔网络的召回策略，通过用户-物品和物品-用户的双向关系计算相似度
- **Word2Vec召回** (recall_w2v.py): 基于Word2Vec的物品向量召回，使用AnnoyIndex加速向量相似度计算

### 排序阶段
- **特征工程** (rank_feature.py): 构建丰富的用户、文章和交互特征
- **LightGBM排序** (rank_lgb.py): 使用LightGBM二分类模型进行精排

### 数据处理
- **数据预处理** (data.py): 处理训练和测试数据，划分验证集
- **召回合并** (recall.py): 合并多路召回结果，进行归一化和加权

## 环境依赖
```
pandas==0.25.3
numpy==1.19.2
lightgbm==3.0.0
scikit_learn==0.24.0
gensim==3.8.3
annoy==1.17.0
joblib==0.17.0
tqdm==4.50.2
pandarallel==1.5.1
multitasking==0.0.9
```

## 项目结构

```
News_recommend/
├── code/                      # 源代码目录
│   ├── data.py               # 数据预处理
│   ├── recall.py             # 召回结果合并
│   ├── recall_itemcf.py      # ItemCF召回
│   ├── recall_binetwork.py   # Bi-Network召回
│   ├── recall_w2v.py         # Word2Vec召回
│   ├── rank_feature.py       # 特征工程
│   ├── rank_lgb.py           # LightGBM排序模型
│   ├── utils.py              # 工具函数
│   ├── test.sh               # 离线验证脚本
│   └── online.sh             # 线上测试脚本
├── user_data/                # 用户数据目录
│   ├── data/                 # 处理后的数据
│   ├── log/                  # 日志文件
│   ├── model/                # 模型文件
│   ├── sim/                  # 相似度矩阵
│   └── tmp/                  # 临时文件
├── prediction_result/         # 预测结果
│   └── result.csv            # 最终提交结果
├── requirements.txt          # 依赖包列表
└── README.md                 # 项目说明文档
```

# 离线验证
```bash
bash test.sh
``` 

# 线上测试
bash online.sh
```
