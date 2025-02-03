title: 线性规划例子之求某工厂安排的生产计划问题
date: 2024-12-1 17:33:33
tags:
-----

某厂生产三种产品 I，II，III。每种产品要经过 A, B 两道工序加工。设该厂有
两种规格的设备能完成 A 工序，它们以 A1, A2 表示；有三种规格的设备能完成 B 工序，
它们以 B1, B2 , B3 表示。产品 I 可在 A, B 任何一种规格设备上加工。产品 II 可在任何规
格的 A 设备上加工，但完成 B 工序时，只能在 B1设备上加工；产品 III 只能在 A2 与 B2
设备上加工。已知在各种机床设备的单件工时，原材料费，产品销售价格，各种设备有
效台时以及满负荷操作时机床设备的费用，求安排最优的生产计划，使该厂利润
最大？

```
import pulp

# 定义每种产品的利润
profit_I = 1.25 - 0.25  # 产品 I 的利润
profit_II = 2.00 - 0.35  # 产品 II 的利润
profit_III = 2.80 - 0.50  # 产品 III 的利润

# 定义设备参数
A1_params = {'I': 5, 'II': 10, 'III': 0, 'efficiency': 6000, 'cost': 300}
A2_params = {'I': 8, 'II': 9, 'III': 12, 'efficiency': 10000, 'cost': 321}
B1_params = {'I': 6, 'II': 8, 'III': 0, 'efficiency': 4000, 'cost': 250}
B2_params = {'I': 4, 'II': 0, 'III': 11, 'efficiency': 7000, 'cost': 783}
B3_params = {'I': 7, 'II': 0, 'III': 0, 'efficiency': 4000, 'cost': 200}

# 创建线性规划问题
prob = pulp.LpProblem("Maximize_Profit", pulp.LpMaximize)

# 定义变量
x_I = pulp.LpVariable('x_I', lowBound=0, cat='Continuous')
x_II = pulp.LpVariable('x_II', lowBound=0, cat='Continuous')
x_III = pulp.LpVariable('x_III', lowBound=0, cat='Continuous')

# 目标函数
prob += profit_I * x_I + profit_II * x_II + profit_III * x_III

# 约束条件
# A1 约束
prob += 5 * x_I + 10 * x_II <= 6000
# A2 约束
prob += 7 * x_I + 9 * x_II + 12 * x_III <= 10000
# B1 约束
prob += 6 * x_I + 8 * x_II <= 4000
# B2 约束
prob += 4 * x_I + 11 * x_III <= 7000
# B3 约束
prob += 7 * x_I <= 4000

# 求解线性规划问题
prob.solve()

# 输出结果
print("Solution:")
print("Status:", pulp.LpStatus[prob.status])
print("Product I:", pulp.value(x_I))
print("Product II:", pulp.value(x_II))
print("Product III:", pulp.value(x_III))
print("Total Profit:", pulp.value(prob.objective))

```
