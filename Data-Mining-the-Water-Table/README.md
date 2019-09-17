**Pump it Up: Data Mining the Water Table**

**竞赛链接**
+ <https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table>
+ <img src="https://github.com/jiwawa112/Competition/tree/master/Data-Mining-the-Water-Table/images/rank.png" width="500">


**原始数据存在的一些问题**
+ 1.绝大多数特征都是分类变量，同时有4个数值特征，以及两个时间特征。
+ 2.数字特征虽然是完整的，但仔细检查观察发现，每个特征包含许多零，在这种情况下，它们与缺失的意义是相同的。
+ 3.一些分类特征也存在2的情况。
+ 4.一些分类变量具有非常多的唯一值。用get_dummies进行one-hot编码时，会造成非常稀疏的情况。需要考虑低频值的处理。
+ 5.存在多个冗余的特征，它们或多或少包含一些相同或类似的数据。例如region 和 region_code。

**处理流程**
+ 通过对数据的观察，删除无用列
+ id 不是一个有用的特征
+ amount_tsh 大多是空值
+ num_private 基本全为0 
+ scheme_name 将近一半为空值
+ region 和 region_code 高度相关
+ quantity 和 quantity_group 高度相关
+ quality_group 和 quality 高度相关
+ source_type 和 source 高度相关
+ payment 和 payment_type 高度相关
+ waterpoint_type_group 和 waterpoint_type 高度相关
+ extraction_type_group 和 extraction_type 高度相关

**数据预处理**
1. 样本缺失特征数量超过一定阈值需要删除
2. 选用fillna（method='ffill',inplace=True）
3. 使用列均值/中位数/众数填补 [均值填补会受到存在异常值的影响]

**数据归一化**
1. 最大最小归一化
2. 标准归一化

**特征排名**
1.使用的是pandas中DataFrame对象corr()方法,该方法用来计算DataFrame对象中所有列之间的相关系数
默认使用的是pearson相关系数（其他还包括Kendall Tau相关系数和spearman秩相关）
2.使用随机森林对特征排名

**模型选择**
1. LogisticRegression
2. XGboost
3. RandomForest

**参数寻优**
+ 选择GridSearchCV进行模型网格最优参数搜索
+ 需要调整的主要参数如下:
+ n_estimators
+ max_depth'       
+ max_features
+ min_samples_leaf
+ min_samples_split

**总结**
+ 1.仅仅靠参数的调整和模型的小幅优化，确实是有一定的提升，但是没有达到质的飞跃，想要让模型的表现有个大幅度提升是不可能的。
+ 2.要让模型的表现有个大幅度提升，需要考虑模型组合(ensemble of model)等。
+ 3.有几个分类特征的产生数值在200-1000的范围。用get_dummies进行one-hot编码，对整个数据集来说属于低频值，会极大增加计算成本，故未使用

**未来工作**
+ 1.尝试模型组合(ensemble of model)
+ 2.考虑如何使用这几个未使用的特征
