# 朴素贝叶斯分类器项目

## 数据集介绍
该数据集包含165封邮件，具体分布如下：
- 前126篇为垃圾邮件
- 127-149为正常邮件
- 第150到155为未知邮件
- 156到165共10篇邮件，对应的分类如下：
  - ham
  - spam
  - spam
  - spam
  - spam
  - ham
  - spam
  - spam
  - ham
  - spam

## 项目实现

### 1. 数据预处理
- 使用jieba进行中文分词
- 加载停用词表（cn_stopwords.txt）
- 去除停用词和空白字符
- 将分词结果用空格连接

### 2. 特征提取
- 使用TF-IDF向量化器
  - max_df=0.8：去掉出现在80%以上文档中的词
  - min_df=3：去掉在3个以下文档中出现的词
  - max_features=1500：控制维度，防止稀疏性
  - ngram_range=(1, 2)：使用1-2元组（unigram+bigram）

### 3. 模型训练
- 使用MultinomialNB（多项式朴素贝叶斯）分类器
- 训练集：前150封邮件
  - 标签：前127为垃圾邮件（1），其余为正常邮件（0）

### 4. 预测与评估
- 对150-165号邮件进行预测
- 输出每封邮件的预测结果（垃圾邮件/正常邮件）

## 文件结构
- `data/`：存放邮件数据（.txt文件）
- `cn_stopwords.txt`：中文停用词表
- `NBC.ipynb`：基础实现版本
- `NBC-Improvements.ipynb`：改进版本（使用TF-IDF）

## 依赖库
- jieba
- scikit-learn
- numpy