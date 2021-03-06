## 利用HMM进行中文词性标注
简介：通过给定的人工标注好词性的文件，进行有监督的一阶(二元)HMM(隐马尔科夫)模型训练；通过训练文件对分好词的文本进行词性标注。</br>

### 一、目录文件
```
./data/:
    train.conll: 训练集
    dev.conll: 测试集
./big-data/:
    train.conll: 大数据训练集
    dev.conll: 大数据开发集
    test.conll: 大数据测试集
根目录：
    train_HMM.py: 一阶隐马尔可夫模型的训练代码
    predict_HMM.py: 利用viterbi算法进行词性标注代码
    predict.txt: 预测结果
```
### 二、运行

#### 1.运行环境

​    python 3.6

#### 2.运行方法
（1）先运行train_HMM.py，得到四个训练参数文件tag.dict(词性及编号字典)，word.dict(分词及编号字典)，emission_matrix.txt(发射矩阵)，transition_matrix.txt(转移矩阵)</br>
（2）再运行predict_HMM.py，对人工分词的文件进行词性标注，并进行预测结果评价，输出预测文件predict.txt。


#### 3.参考结果
##### (1)小数据测试

注：可以修改不同的alpha比较准确率，训练集数据少结果正确率可能较低。

| 训练集    | ./data/train.conll |
| --------- | ------------------ |
| 测试集    | ./data/dev.conll   |
| 参数alpha | 0.1                |
| 准确率    | 74.7014%           |
| 预测时间  | 约16s              |


##### (2)大数据测试

| 训练集    | ./big-data/train.conll |
| --------- | ---------------------- |
| 测试集    | ./big-data/dev.conll   |
| 参数alpha | 0.01                    |
| 准确率    | 88.35%                 |
| 预测时间  | 约23s                  |

### 三、日志
#### 2018年8月25日
根据老师的建议完成了代码的优化，利用numpy中的矩阵进行模型参数存储并用数字编号代替分词，提高了标注效率。和其他同学的代码进行比对，得出了近乎相同的结果。</br>
#### 2018年7月14日
基于之前的训练模型得出的分词结果，和人工分词文件进行对比，得出了正确率为0.777（学姐的为0.764）。不排除是python版本不同而导致的概率精度不同,引起了正确率上的细微变化。</br>
接下来将根据老师的建议对HMM训练模型进行优化：调整矩阵存储形式(1.用numpy中的矩阵替代原来的嵌套字典形式;2.用数字编号替代原来的观测状态(分词))
#### 2018年6月13日
上传了两个代码：tarin_hmm.py是训练HMM(一阶)的代码，predict_hmm.py是用viterbi算法实现中文分词词性标注。</br>
由于时间仓促，目前还没有对模型及算法进行验证，代码也比较粗糙。加上最近要期末考试了，准备先放一放，7月份再继续完善。</br>
