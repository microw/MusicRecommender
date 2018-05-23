## 音乐推荐
简介：  
基于用户的播放次数，给用户推荐乐队，  
用户播放乐队的歌曲次数代表了用户对这个乐队的喜爱程度  
采用User_CF,Item_CF,LFM,BPR,ALS_WR模型算法进行求解比较  
衡量标准采用：准确率，召回率，覆盖率，多样性  
- 数据集(两份数据): 
  1. lastfm-360K(small_data.csv)取最活跃的10000个用户，最受欢迎的1000首歌
  2. u.data,lable编码后的小数据集
#### 1.基于用户的协同过滤  
        计算用户的相似度，两个用户对冷门物品产生行为，则这两个用户应该具有较高的相似度
#### 2.基于物品的协同过滤  
        计算物品的相似度，活跃用户对物品的相似度贡献应该小于不活跃用户
#### 3.隐语义模型（LFM）
        通过隐含特征联系用户和物品
        参数：隐特征的个数
              学习速率alpha
              正则化项系数lamba
#### 4.贝叶斯个性化排序（BPR：Bayesian Personalized Ranking）
        基于贝叶斯理论在先验知识下极大化后验概率，实现从一个用户-项目矩阵训练出多个矩阵，
        且每个矩阵表示一个用户的项目偏好情况来获得用户多个项目的偏序关系，来进行排序的推荐系统

#### 5.交替最小二乘法（ALS_WR：ALS with Weighted--Regularization）
        用户没有明确反馈对商品的偏好，没有直接打分，通过用户的某些行为推断用户对商品的偏好
        ALS_WR通过置信度衡量
##结果
在u.data的结果为(仅供参考)

|目录|user_CF|item_CF|LFM|BPR|ALS_WR|
|:---|:---|:---|:---|:---|:---|
|precision|0.297028|0.296454|0.235244|0.2545068928950159|0.2706256627783669
|recall|0.139218|0.138919|0.110260|0.1234694927461673|0.1312892272867579
|coverage|0.317905|0.230207|0.358709|0.3393829401088929|0.39503932244404116
|popularity|5.245796|5.359162|5.235433|5.121795795790667|5.154377399784349

在small_data.csv的结果为(仅供参考)  
bpr:auc mean = 0.86 std = 0.11  
als_wr:auc mean =0.77 std = 0.22     

|目录|user_CF|item_CF|LFM|BPR|ALS_WR|
|:---|:---|:---|:---|:---|:---|
|precision|0.108502|0.115724|0.046713|0.10419407894736842|0.08890830592105263
|recall|0.199219|0.210743|0.085783|0.21724500075015538|0.18537411320916475
|coverage|0.997000|0.813000|0.452000|0.731|0.999
|popularity|5.628611|5.797764|6.883521|6.05680689158381|5.833611415438899




        
        

