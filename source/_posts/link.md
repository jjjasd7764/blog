title: su模型算法
date: 2025-2-1 17:49:32
tags: 算法问题
--------------

练习算法标题：（找习题的方法：点到下一章，往上一滑）

第01章 线性规划（以取得最大经济效益的问题）

第02章 整数规划（完全整数规划、部分整数规划，解决问题同上）

第03章 非线性规划（指在线性规划中包含非线性函数）

第04章 动态规划（最优解决多阶段过程转化为一系列单阶段问题。应用场景经济、生产、工程）

第05章 图与网络（解决路径问题）

第06章 排队论（解决军事、运输、维修、生产、服务、库存、医疗卫生、教育、水利灌溉之类的排队系统的问题）

第07章 对策论（解决对某个问题的决策）

第08章 层次分析法（解决多准则决策类问题）

第09章 插值与拟合（检测数据的准确性，和关系性，来拟合数据）

第10章 数据的统计描述和分析（数据统计画图，趋势特征关系、跟Excl表一样，MATLAB）

第11章 方差分析（数据对比指标，顾名思义求方差类，解决数据差异对比）

第12章 回归分析（解决随机数据，随机问题的回归模型）

第13章 微分方程建模（一般用于解决细微计算类问题最优化，例如火箭）

第14章 稳定状态模型（解决某一时间时间长了，动态过程变化的趋势,例如轮番砍伐树木和食饵与捕食者系统）

第15章 常微分方程的解法（解决微分角度问题，一般用于小船的航线曲线）

第16章 差分方程模型（解决汉罗塔问题、兔子n个月多少只、以及染色体遗传问题，类似等差数列）

第17章 马氏链模型（对随机变量进行预测，解决父母子女的教育概率，色盲等问题）

第18章 变分法模型（用于动态规划中的生产问题）

第19章 神经网络模型（解决将数据变为训练集和测试集，以解决拟合曲线）

第20章 偏微分方程的数值解（求边界问题，应用于热传导方程初边值问题）

第21章 目标规划（求某一目标的最大最小值问题，与线性规划不同的是可将多目标模型转化为单一目标的模型）

第22章 模糊数学模型（模型的背景和关系有模糊性，解决设计工程  （指标类问题））

第23章 现代优化算法（启发式算法：模拟退火模型、遗传算法、蚁群算法）

第24章 时间序列模型（随着时间的变化而变化的数据序列，解决用于每年产量和销量的问题）

第25章 存贮论（解决存储最优货量的问题）

第26章 经济与金融中的优化问题（使用lingo软件求解、解决价格提高对应消费欲望问题、投资经商问题）

第27章 生产与服务运作管理中的优化问题（优化类问题，还是解决最大经济收益问题）

第28章 灰色系统理论及其应用（关联度分析法用于农业经济、水利和宏观经济等）

第29章 多元分析（用于解决大量的数据，将数据聚类分析,主成分分析，典型相关分析，综合评价分析）

第30章 偏最小二乘回归（回归模型分析,同时具备多元分析的特征）

红色：优化类  蓝色：分析类  预测类：黑色    主要成分是：优化和分析，其次是预测

优化类-----分析类------预测类------优化类-----分析类

数学算法全收录：给出该模型方法的例子和限制条件和适用条件

第01章 线性规划

1. 指派问题的数学模型
2. 指派问题的匈牙利算法
3. 矩阵指派问题

第02章 整数规划

1.分枝定界法—可求纯或混合整数线性规划。

2.割平面法—可求纯或混合整数线性规划。

3.隐枚举法—求解“0-1”整数规划： ①过滤隐枚举法； ②分枝隐枚举法。

4.匈牙利法—解决指派问题（“0-1”规划特殊情形）。

5.蒙特卡洛法（随机取样法）—求解各种类型规划。

6.过滤隐枚举法

第03章 非线性规划

1. 二次插值法
2. 解析法
3. 梯度法
4. 最速下降法
5. 变尺度法
6. 拟牛顿法
7. 直接法
8. 罚函数法

第04章 动态规划

1. 最优策略和最优轨线
2. 递归方程
3. 动态规划解非线性规划
4. 最短路径问题
5. 生产计划模型
6. 资源分配问题

第05章 图与网络

1.最短路径问题

2.公路连接问题

3.指派问题

4.中国邮递员问题

5.旅行商问题

6.运输问题

7.邻接矩阵表示法

8.关联矩阵表示法

9.弧表表示法

10.邻接表表示法

11.星形表示法

12.prim算法

13.Kruskal算法构造最小生成树

14.人员指派问题

15.匈牙利算法

16.分配问题

17.kuhn-Munkers算法

18.Fleury算法

19.最大流问题

20.标号法

21.最小流问题

22.计划评审方法和关键路线法

23.计划网络图

第06章 排队论（多分布）

1.单服务台模型

2.多服务台模型

3.单服务台混合制模型

4.多服务台混合制模型

5.有限资源排队模型

6.服务率或到达率依赖状态的排队模型

7.非生灭过程排队模型

8.H/G/1排队模型

9.考虑定长服务时间M/D/1模型

10.爱尔郎排队模型

11.排队系统的优化模型

第07章 对策论

1. 纯策略问题
2. 混合对策问题

第08章 层次分析法

1.构造判断矩阵

2.层次单排序及一致性检验

第09章 插值与拟合

1.拉格朗日多项式插值

2.牛顿插值

3.分段线性插值

4.Hermite 插值

5.三次样条插值

6.lagrange插值

7.埃尔米特(Hermite)插值

8.B样条函数插值方法

9.二维插值

10.线性最小二乘法

第10章 数据的统计描述和分析

1.分布拟合检验

2.中位数检验

3.signrank Wilcoxon符合秩检验

4.signrank符号检验

第11章 方差分析

1.单因素方差分析

2.双因素方差分析

3.无交互影响的双因素方差分析

4.关于交互效应的双因素方差分析

5.正交试验设计与方差分析

第12章 回归分析

1.一元线性回归

2.最小二乘法

3.回归模型的线性关系检验

4.多元线性回归分析的模型

5.统计分析

6.回归模型的假设检验

7.利用回归模型进行预测

8.多项式回归

9.一元多项式回归

10.多元二项式回归

11.非线性回归和逐步分析

12.逐步回归

第13章 微分方程建模

1.按规律直接列方程

2.微元分析法与任意区域上取积分的方法

3.模拟近似法

4.人口模型

5.战争模型

6.正规战模型

7.游击战模型

8.混合战模型

9.一个战争实例

第14章 稳定状态模型

1.资源开发模型

2.经济效益模型

3.种群相互竞争模型

4.Voltera 模型

5.形成模型

6.模型分析

第15章 常微分方程的解法

1.常微分方程的离散化

2.用差商近似导数

3.用数值积分方法

4.Taylor多项式近似

5.欧拉（Euler）方法

6.Euler 方法的误差估计

7. 改进欧拉（Euler）方法

8.龙格—库塔（Runge—Kutta）方法

9.线性多步法

10.一阶微分方程组的数值解法

11.高阶微分方程的数值解法

12.非刚性常微分方程的解法

13.刚性常微分方程的解法

14.常微分方程的解析解

15.求解常微分方程的通解

第17章 马氏链模型

1.马尔可夫链的应用

2.吸收链

第18章 变分法模型

1.变分法

2.无约束条件的泛函极值

3.最简泛函的几种特殊情形

4.最简泛函的推广

5.有约束条件的泛函极值

6.生产设备的最大经济效益

第19章 神经网络模型

1.人工神经元模型

2.蠓虫分类问题与多层前馈网络

3.向后传播算法

4.LVQ方法

第20章 偏微分方程的数值解

1.偏微分方程的定解问题

2.偏微分方程的差分解法

3.抛物型方程的差分解法

4.古典显式格式

5.古典隐式格式

6.杜福特—弗兰克尔（DoFort—Frankel）格式

7.扩散系统值浓度分布

8.二维状态空间的偏微分方程的 MATLAB 解法

9.偏微分方程的 pdetool 解法

第21章 目标规划

1.加权系数法

2.优先等级法

3.有效解法

4.目标规划的一般数学模型

5.求解目标规划的序贯式算法

6.多目标规划的MATLAB解法

第22章 模糊数学模型

1.模糊统计方法

2.指派方法

3.其他方法（矩阵型、梯形型，k次抛物型、Γ型、正态型、柯西型）

4.模糊模式识别

5.模糊模式识别原则

6.模糊聚类分析方法

7.传递闭包法

8.布尔矩阵法

9.直接聚类法

10.模糊综合评价法

11.多目标模糊综合评价决策法

12.多层次模糊综合评价模型的数学方法

13.模糊多属性决策方法

14.折衷型模糊多属性决策方法

第23章 现代优化算法

1.模拟退火算法

2.模拟算法

3.禁忌搜索算法

4.改进的遗传算法

5.蚁群算法

第24章 时间序列模型

1.移动平均法

2.简单移动平均法

3.加权移动平均法

4.趋势移动平均法

5.指数平滑法

6.加权系数的选择

7.二次指数平滑法

8.三次指数平滑法

9.差分指数平滑法

10.自适应滤波法

11.趋势外推预测方法

12.指数曲线法

13.修正指数曲线法

14.logistic曲线（生长曲线）

15.平稳时间序列模型

16.ARMA模型的特性

第25章 存贮论

1.无约束的确定型存贮模型

2.不允许缺货，补充时间极短-基本的经济订购批量存贮模型

3.允许缺货，补充时间较长—经济生产批量存贮模型

4.不允许缺货，补充时间较长—基本的经济生产批量存贮模型

5.允许缺货，补充时间极短的经济订购批量存贮模型

6.经济定购批量折扣模型

7.有约束的确定型存贮模型

8.带有约束的经济订购批量存贮模型

9.具有资金约束的 EOQ 模型

10.具有库容约束的 EOQ 模型

11.兼有资金与库容约束的最佳批量模型

12.带有约束允许缺货模型

13.带有约束的经济生产批量存贮模型

14.单周期随机库存模型

第26章 经济与金融中的优化问题

1.交通流均衡问题

2.基本的投资组合模型

3.存在无风险资产时的投资组合模型

4.考虑交易成本的投资组合模型

5.利用股票指数简化投资组合模型

6.其他目标下投资组合模型

第27章 生产与服务运作管理中的优化问题

1.有瓶颈设备的多级生产计划问题

2.钢管下料问题

3.易拉罐下料问题

4.面试顺序与消防车调度问题

5.消防车调度问题

6.飞机定位和飞行计划问题

7.飞行计划问题

第28章 灰色系统理论及其应用

1.关联分析

2.数据变化技术

3.优势分析

4.生成数

5.灰色模型 GM

6.GM(1, N) 模型

7.GM(1, N) 的白化型

8.灰色预测

9.灾变预测

10.道路交通事故灰色 Verhulst 预测模型

11.Verhulst 预测模型

12.道路交通事故 Verhulst 预测模型

13.残差合格模型

14.关联度合格模型

15.均方差比合格模型

16.小误差概率合格模型

17.DGM(2,1)模型

18.GM(1, N) 模型

19.GM(0, N) 模型

第29章多元分析

1.聚类分析（绝对值距离、欧式距离、Chebyshev 距离、马氏（Mahalanobis）距离）

2.最短距离法

3.最长距离法

4.重心法

5.类平均法

6.离差平方和法

7.系统聚类法

8.最短聚类法与最长距离法

9.变量聚类法

10.最大系数法

11.最小系数法

12.R型聚类分析

13.Q型聚类分析

14.主成分分析

15.基于主成分分析法的综合评价

16.因子分析

17.因子分析模型

18.因子旋转

19.方差最大法

20.四次方最大旋转

21.等量最大法

22.因子得分

23.巴特莱特因子得分(加权最小二乘法）

24.回归方法

25.主成分分析法与因子分析法数学模型的异同比较

26.判别分析

27.Fisher 判别

28.Bayes判别

29.两总体的Bayes判别

30.典型相关性分析

31.典型相关的数学描述

32.原始变量与典型变量之间的相关性

33.典型相关系数的检验

34.部分总体典型相关系数为零的检验

35.典型相关分析案例

36.中国城市竞争力与基础设施的典型相关分析

37.典型冗余分析

38.城市竞争力与基础设施关系的典型相关分析

39.典型相关关系系数及其检验

40.典型相关模型

41.典型结构

42.典型冗余分析与解释能力

第30章 偏最小二乘回归

1.偏最小二乘回归

2.利用Lagrange乘数法

3.交叉有效性检验

4.回归性模型

评价模型：

层次分析法、模糊综合评价、Topsis优劣解距离法、灰色关联分析、主成分分析法、BP神经网络综合评价法、秩和比综合评价法

优化模型：

线性规划、整数规划、非线性规划、排队论模型

、分类和聚类模型

聚类分析（k-means、k-means++、DBSCAN）

决策树、随机森林、朴素贝叶斯

数理统计：

参数估计、假设检验、方差分析、回归分析、协方差分析、主成分分析、因子分析、典型相关分析

预测模型：

微分方程（人口增长模型、食铒捕食者模型、传染病模型）

拟含算法、插值算法、时间序列（差分方程）、灰色预测模型、马尔科夫预测、支持向量机、神经网络预测

图论：

最短路径算法（迪杰斯特拉算法、贝尔曼福特算法、弗罗伊德算法）

网络最大流问题、最小费用最大流问题、旅行商问题

算法：

插值算法、拟合算法、微分方程、时间序列、聚类分析

全国大学生数学建模竞赛中，常见的算法模型有以下30种：

最小二乘法

数值分析方法

图论算法

线性规划

整数规划

动态规划

贪心算法

分支定界法

蒙特卡洛方法

随机游走算法

遗传算法

粒子群算法

神经网络算法

人工智能算法

模糊数学

时间序列分析（根据时间变化，数据的变动随之改变）

马尔可夫链（评测类模型）

决策树

支持向量机

朴素贝叶斯算法

KNN算法

AdaBoost算法

集成学习算法

梯度下降算法

主成分分析

回归分析

聚类分析

关联分析

非线性优化

深度学习算法

皮尔逊分析（用于描述两个变量之间的线性相关性）

线性规划：

决策变量、目标函数、约束条件、数学规划

整数规划

拟合算法要经过所有的点

插值不一定要经过所有的点。

2017建模论文

多项式回归、支持向量机或神经网络
