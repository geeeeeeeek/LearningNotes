
#### 先验概率
- 事件发生前的预判概率。可以是基于历史数据的统计，可以由背景常识得出，也可以是人的主观观点给出。一般都是单独事件概率，如P(x),P(y)。
- 例：根据若干年的统计（经验）或者气候（常识），某地方下雨的概率

#### 后验概率
- 事件发生后求的反向条件概率；或者说，基于先验概率求得的反向条件概率。概率形式与条件概率相同。
- 例：根据天上有乌云（原因或者证据 or 观察数据），下雨（结果）的概率
- 例：医生看病（头痛-感冒）[1]
- 例：雨天车祸、酒吧把妹 [2]

#### 条件概率
- 一个事件发生后另一个事件发生的概率。一般的形式为P(x|y)表示y发生的条件下x发生的概率。
- 后验概率在某些情况下是条件概率的一种

#### 贝叶斯公式
-  P(y|x) = ( P(x|y) * P(y) ) / P(x)
- 这里：P(y|x) 是后验概率，一般是我们求解的目标。
- P(x|y) 是条件概率，又叫似然概率，一般是通过历史数据统计得到。一般不把它叫做先验概率，但从定义上也符合先验定义。
- P(y) 是先验概率，一般都是人主观给出的。贝叶斯中的先验概率一般特指它。
- P(x) 其实也是先验概率，只是在贝叶斯的很多应用中不重要（因为只要最大后验不求绝对值），需要时往往用全概率公式计算得到。

#### 似然函数
- L(θ|x) = f(x|θ)
- 是根据已知结果去推测固有性质的可能性（likelihood），是对固有性质的拟合程度
- 就是说，不要管什么下雨的概率，只care乌云与下雨的关系。如果下雨了，那么对乌云这一属性的拟合程度有多大。似然函数，一般写成L（乌云 | 已知下雨），和后验概率非常像，区别在于似然函数把（乌云）看成一个肯定存在的属性，而后验概率把（乌云）看成一个随机变量。

#### 似然函数和条件概率的关系
- 似然函数就是条件概率的逆反
- 意思是：L（乌云 | 已知下雨）= C × P（下雨 | 乌云），C是常数。具体来说，现在有1000天有乌云，800天下雨，那条件概率是0.8。那我也可以说，这1000天下雨的可能性是0.8C。

#### 监督学习
- 通过已有的训练样本（即已知数据以及其对应的输出）来训练，从而得到一个最优模型，再利用这个模型将所有新的数据样本映射为相应的输出结果。特点是带答案，有label
- 监督学习可分为“回归”和“分类”问题。

#### 监督学习举例
- 回归：通过房地产市场的数据，预测一个给定面积的房屋的价格就是一个回归问题。这里我们可以把价格看成是面积的函数，它是一个连续的输出值。 但是，当把上面的问题改为“预测一个给定面积的房屋的价格是否比一个特定的价格高或者低”的时候，这就变成了一个分类问题, 因为此时的输出是‘高’或者‘低’两个离散的值。
 ![回归](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/012.jpg)

- 分类：给定医学数据，通过肿瘤的大小和年龄来预测该肿瘤是恶性瘤还是良性瘤，这就是一个分类问题，它的输出是0或者1两个离散的值。(0代表良性，1代表恶性)。![分类](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/031.jpg)

#### 无监督学习
- 在无监督学习中，我们基本上不知道结果会是什么样子，但我们可以通过聚类的方式从数据中提取一个特殊的结构。在无监督学习中给定的数据是和监督学习中给定的数据是不一样的。在无监督学习中给定的数据没有任何标签或者说只有同一种标签。如下图所示：

#### 无监督学习举例
- 聚类 ：如下图所示，在无监督学习中，我们只是给定了一组数据，我们的目标是发现这组数据中的特殊结构。例如我们使用无监督学习算法会将这组数据分成两个不同的簇,，这样的算法就叫聚类算法。![聚类](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/011.png)

- 新闻分类：搜集网上的新闻，并且根据新闻的主题将新闻分成许多簇, 然后将在同一个簇的新闻放在一起。国内、国外、体育、财经、。。。
![聚类](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/049.png)

- 其他：社交网络分析，市场划分，天文数据分析等

#### 决策树
- 假设我们有一组数据，该数据记录了用户的性别、年龄和下载的APP。我们首先根据年龄对用户下载的APP进行分类，然后再根据性别进行分类，这种方式就是决策树。
![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/050.jpg)

#### 朴素贝叶斯（Naive Bayes）
- 假设我们想分类垃圾邮件，通过统计我们发现，有80%垃圾邮件包含字眼“cheap”，有70%垃圾邮件包含拼写错误，有95%垃圾邮件没有标题，朴素贝叶斯方法简单说就是利用这些统计数据和下图中的条件概率分布公式实现垃圾邮件分类：![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/051.jpg)
![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/052.jpg)  

通过统计我们知道了以下概率：  
1. 垃圾邮件包含字眼“cheap”的概率是80%（公式中的P(data|class)）    
2. 垃圾邮件占所有邮件的比例是50%（公式中的P(class)）  
3. 包含字眼“cheap”的邮件占所有邮件的比例是60%（公式中的P(data)）    
那么通过公式我们就可以得到包含字眼“cheap”的邮件是垃圾邮件的比例

#### 梯度下降（Gradient Descent）
- 梯度下降法是一个一阶最优化算法，通常也称为最速下降法。要使用梯度下降法找到一个函数的局部极小值，必须向函数上当前点对于梯度（或者是近似梯度）的反方向的规定步长距离点进行迭代搜索。所以梯度下降法可以帮助我们求解某个函数的极小值或者最小值。对于n维问题就最优解，梯度下降法是最常用的方法之一。
- ![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/053.jpg)
- 上图中，纵坐标是代价值，横坐标是参数值，梯度下降就是让参数值从一个起始点开始，一步一步朝着代价值最小的方向变化。

#### 什么是熵(Entropy) 
- 放在信息论的语境里面来说，就是一个事件所包含的信息量。[6]
- 我们常常听到“这句话信息量好大”，比如“世界杯中国队战胜了巴西队”。这句话为什么信息量大？因为它的内容出乎意料，违反常理。
- 特征1：越不可能的事件，信息量越大，引出比如“我不会死”这句话信息量就很大。而确定事件的信息量就很低，比如“我是我妈生的”，信息量就很低甚至为0
- 特征2：独立事件的信息量可叠加。比如“a. 张三今天喝了菊花茶 b. 李四前天喝了茉莉茶”的信息量就应该恰好等于a+b的信息量，如果张三李四喝什么茶是两个独立事件
- ![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/054.png)  
- 对于一个一定会发生的事件，其发生概率为1，S(x) =-log(1) * 1 = -0*1=0，信息量为0
 
#### KL散度
- KL散度，有时候也叫KL距离，一般被用于计算两个分布之间的不同
- 数学定义：  
![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/055.svg)  
![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/056.svg)

#### 交叉熵
- 来计算两个分布间的不同   [7]
![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/057.png)
- 与KL散度等价，那么我们优先选择更简单的公式，因此选择交叉熵。
- 交叉熵可以用于计算“学习模型的分布”与“训练数据分布”之间的不同。当交叉熵最低时(等于训练数据分布的熵)，我们学到了“最好的模型”。

#### 各种距离 [8]

#### 欧式距离
- 二维平面上点a(x1,y1)与b(x2,y2)间的欧氏距离:
- ![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/058.png)
- n维空间点a(x11,x12,…,x1n)与b(x21,x22,…,x2n)间的欧氏距离（两个n维向量）
- ![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/060.png)
 #### 夹角余弦
- ![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/061.png)

#### 激活函数 [9]
- 激活函数是用来加入非线性因素的，解决线性模型所不能解决的问题。
- 首先我们有这个需求，就是二分类问题，如我要将下面的三角形和圆形点进行正确的分类，如下图  
![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/062.jpg)  
- ![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/064.jpg)  
- 很容易能够看出，我给出的样本点根本不是线性可分的
- 引入非线性函数
- ![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/065.jpg)
- ![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/066.jpg)

#### 损失函数 [10]
- 损失函数（loss function）是用来估量你模型的预测值f(x)与真实值Y的不一致程度，它是一个非负实值函数,通常使用L(Y, f(x))来表示，损失函数越小，模型的鲁棒性就越好.
- 一个模型的训练过程如下：  
![](https://github.com/geeeeeeeek/LearningNotes/blob/master/Images/067.jpg)
- 几种比较主流的损失函数计算方法
  - 平方损失函数
  - 交叉熵损失函数
  - 对数似然函数损失函数

#### Todo
- 随机森林、激活函数、过拟合、损失函数、one-hot向量、softmax、

#### 参考文献
- [1] https://blog.csdn.net/yewei11/article/details/50537648
- [2] https://www.zhihu.com/question/24261751
- [3] 数学之美
- [4] 机器学习(Tom M.Michell)
- [5] 机器学习实战
- [6] https://www.zhihu.com/question/65288314
- [7] https://www.zhihu.com/question/41252833
- [8] https://my.oschina.net/hunglish/blog/787596
- [9] https://zhuanlan.zhihu.com/p/25279356
- [10] https://zhuanlan.zhihu.com/p/28761075
