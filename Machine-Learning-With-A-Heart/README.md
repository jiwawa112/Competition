**Data Mining the Water Table**

**竞赛链接**
+ <https://www.drivendata.org/competitions/54/machine-learning-with-a-heart>

**竞赛排名**
+ <img src="https://github.com/jiwawa112/Competition/raw/master/Machine-Learning-With-A-Heart/images/rank.png" width="500">


**数据预处理**
+ 1.对于数据特征中的类别数据，使用哑变量转换
+ 2.对于数值特征,由于各个数据特征的尺度不同，因此需要考虑对数据归一化
+ 3.添加衍生数据特征(通常建模过程中需要尝试添加衍生特征来增强模型性能，如各样本与其各类别对应特征中位数/均值差等)

**数据归一化**
+ 1. 最大最小归一化
+ 2. 标准归一化

**特征排名**
+ 1.使用随机森林对特征排名

**模型选择**
+ 1. LogisticRegression
+ 2. RandomForest
+ 3. KNN
+ 4. GaussianNB()
+ 5. BayesianRidge

**增加特征**
+ 1.平均值
+ 2.方差
+ 3.中位数

**总结**
+ 1.尝试模型融合。
