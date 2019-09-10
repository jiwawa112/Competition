**Titanic: Machine Learning from Disaster**
**Start here! Predict survival on the Titanic and get familiar with ML basics**

<https://www.kaggle.com/c/titanic>

**处理流程**

**数据集缺失值处理办法**
1. 样本缺失特征数量超过一定阈值需要删除
2. 选用fillna（method='ffill',inplace=True）
3. 使用列均值/中位数/众数填补 [均值填补会受到存在异常值的影响]

**添加衍生数据特征**
1. 计算特征与均值/中位数的差值 
2. 计算最高票价与最低票价的差值；

**数据归一化**
1. 最大最小归一化
2. 标准归一化

**特征排名**
1.使用的是pandas中DataFrame对象corr()方法,该方法用来计算DataFrame对象中所有列之间的相关系数
默认使用的是pearson相关系数（其他还包括Kendall Tau相关系数和spearman秩相关）

**模型选择**
1. GradientBoostingRegressor
2. RandomForestRegressor
3. XGboost

**参数寻优**
1. 选择GridSearchCV进行模型网格最优参数搜索

**总结**
1、仅仅靠参数的调整和模型的小幅优化，确实是有一定的提升，但是没有达到质的飞跃，想要让模型的表现有个大幅度提升是不可能的。
2、要想让模型的表现有一个质的飞跃，需要依靠其他的手段，诸如，特征工程(feature egineering) ，模型组合(ensemble of model),以及堆叠(stacking)等。

**未来工作**
1.使用随机森林进行特征排名
2.使用KNN填充、随机森林等填充缺失的数据
3.添加更多特征衍生
4.尝试其他神经网络模型
