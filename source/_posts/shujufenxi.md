title: 数据分析练习
date: 2025-2-3 17:49:32
tags: 数据分析
--------------

1. 缺失值处理
2. 重复值处理
3. 数据类型转换
4. 字符串处理
5. 数据规范化与标准化
6. 异常值处理
7. 数据分组和聚合
8. 数据透视与透视表
9. 日期时间处理
10. 数据合并与连接

## 题目 1: 删除缺失值

数据集：

```
import pandas as pd
data = {'Name': ['Alice', 'Bob', 'Charlie', None, 'Edward'],'Age': [25, 30, 35, 40, None]
'Name': ['Alice', 'Bob', 'Charlie', None, 'Edward'],'Age': [25, 30, 35, 40, None]
}
df = pd.DataFrame(data)
print(df)
```

代码解释：

`import pandas as pd`：这行代码导入了Pandas库，并将其命名为pd。Pandas是一个强大的数据分析和数据处理工具，它提供了数据结构和数据分析工具。

`data = {'Name': ['Alice', 'Bob', 'Charlie', None, 'Edward'], 'Age': [25, 30, 35, 40, None]}`：这里定义了一个名为data的字典。这个字典包含两个键：‘Name’和’Age’，它们分别对应一个列表。列表中的每个元素代表一行数据，其中一些元素为None，表示缺失值。

`df = pd.DataFrame(data)`：这行代码使用Pandas的DataFrame构造函数将data字典转换为一个数据框（DataFrame）对象，并将其赋值给变量df。DataFrame是Pandas中的一种数据结构，类似于电子表格，可以方便地进行数据操作和分析。

print(df)：这行代码将DataFrame df打印到控制台，显示其内容。

综上所述，这段代码的作用是创建一个包含名字和年龄的简单数据集，并将其转换为Pandas DataFrame，然后将其内容打印出来。

运行结果：

Name   Age
0    Alice  25.0

1      Bob  30.0

2  Charlie  35.0

3     None  40.0

4   Edward   NaN

练习： 删除任何包含缺失值的行。（删除蓝色这一项）

参考答案：

```
df_cleaned = df.dropna()
```

```
print("\n删除任何包含缺失值的行的 DataFrame:")
```

```
print(df_cleaned)
```

运行结果：

Name   Age
0    Alice  25.0

1      Bob  30.0

2  Charlie  35.0

代码解释：

```
df_cleaned = df.dropna()
```

这行代码创建一个新的 DataFrame df\_cleaned，它包含了从原 DataFrame df 中删除缺失值后的结果。由于没有使用 inplace=True，原 DataFrame df 保持不变。如果在原表改动，则df.dropna(inplace=True)

知识点：

dropna(): 删除包含缺失值的行。

inplace=True: 修改原 DataFrame。

应用： 在数据分析或建模前，清除缺失值以避免错误。

## 题目 2: 替换缺失值

数据集：

```
import pandas as pd
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Edward'],'Age': [25, None, 35, None, 40]
}
df = pd.DataFrame(data)
print(df)
```

运行结果：

Name   Age
0    Alice  25.0

1      Bob   NaN

2  Charlie  35.0

3    David   NaN

4   Edward  40.0

练习： 将缺失值替换为列的均值。

参考答案：

```
age_mean = df['Age'].mean()
df_filled = df.copy()  
df_filled['Age'] = df_filled['Age'].fillna(age_mean)  
print("\n填充缺失值后的 DataFrame:")print(df_filled)
```

运行结果：

Name        Age
0    Alice  25.000000

1      Bob  33.333333

2  Charlie  35.000000

3    David  33.333333

4   Edward  40.000000

代码解释：

#计算 Age 列的平均值

```
age_mean = df['Age'].mean()
```

#使用平均值填充缺失值，生成一个新的 DataFrame

```
df_filled = df.copy()  # 先创建 df 的副本
```

```
df_filled['Age'] = df_filled['Age'].fillna(age_mean)  # 用平均值替换缺失值
```

```
print("\n填充缺失值后的 DataFrame:")
```

```
print(df_filled)
```

知识点：

fillna(): 填补缺失值。

mean(): 计算均值。

应用： 在数据集中，均值替代法是处理缺失值的常用方法。

## 题目 3: 删除重复行

数据集：

```
import pandas as pd
```

```
data = { 'Name': ['Alice', 'Bob', 'Alice', 'David', 'Alice'], 'Age': [25, 30, 25, 40, 25] }
```

```
df = pd.DataFrame(data)
```

```
print("原始 DataFrame:")
```

```
print(df)
```

运行结果：

原始 DataFrame:

Name  Age
0  Alice   25

1    Bob   30

2  Alice   25

3  David   40

4  Alice   25

练习： 删除重复的行。

参考答案：

#使用 drop_duplicates() 方法生成一个新的DataFrame

```
df_no_duplicates = df.drop_duplicates()
```

```
print("\n删除重复行后的 DataFrame:")
```

```
print(df_no_duplicates)
```

运行结果：

删除重复行后的 DataFrame:

Name  Age
0  Alice   25

1    Bob   30

3  David   40

知识点解释：

drop_duplicates(): 删除重复行。

应用： 确保数据集中不包含重复的数据，以防止错误分析。

## 题目 4: 重命名列

数据集：

```
import pandas as pd
```

```
data = { 'FirstName': ['Alice', 'Bob', 'Charlie'], 'Age': [25, 30, 35] }
```

```
df = pd.DataFrame(data)
```

```
print("原始 DataFrame:")
```

```
print(df)
```

运行结果：

FirstName  Age

0     Alice   25

1       Bob   30

2   Charlie   35

练习： 将"FirstName"列重命名为"Name"。

参考答案：

#使用 rename() 方法生成一个新的 DataFrame

```
df_renamed = df.rename(columns={'FirstName': 'Name'})
```

```
print("\n更改列名后的 DataFrame:")
```

```
print(df_renamed)
```

运行结果：

更改列名后的 DataFrame:

Name  Age
0    Alice   25

1      Bob   30

2  Charlie   35

知识点解释：

rename(): 重命名列。

更新字段名称以更好地理解数据。

## 题目 5: 更改数据类型

数据集：

```
import pandas as pd
```

```
data = { 'ID': ['1', '2', '3'], 'Score': ['85.5', '90.0', '78.0'] }
```

```
df = pd.DataFrame(data)
```

```
print("原始 DataFrame:")
```

```
print(df)
```

#查看 ID 列的数据类型

```
id_dtype = df['ID'].dtype
```

```
Score_dtype = df['Score'].dtype
```

```
print("ID列的数据类型:")
```

```
print(id_dtype)
```

```
print("Score列的数据类型:")
```

```
print(Score_dtype)
```

运行结果：

原始 DataFrame:

ID Score

0  1  85.5

1  2  90.0

2  3  78.0

ID列的数据类型:

```
object
```

Score列的数据类型:

object

练习： 将"ID"转换为整数，将"Score"转换为浮点数。

参考答案：

#将 "ID" 列转换为整数类型

```
df['ID'] = df['ID'].astype(int)
```

#将 "Score" 列转换为浮点数类型

```
df['Score'] = df['Score'].astype(float)
```

#查看转换后的 DataFrame 和数据类型

```
print("转换后的 DataFrame:")
```

```
print(df)
```

```
print("数据类型:")
```

```
print(df.dtypes)
```

运行结果：

转换后的 DataFrame:

ID  Score

0   1   85.5

1   2   90.0

2   3   78.0

数据类型:

ID         int64

Score    float64

dtype: object

知识点解释：

astype(): 转换数据类型。

应用： 确保数据类型正确以便进行数值计算和分析。

## 题目 6: 去除空格

数据集：

```
import pandas as pd
```

#创建数据

```
data = { 'Name': [' Alice ', ' Bob', ' Charlie '], 'Age': [25, 30, 35] }
```

```
df = pd.DataFrame(data)  
```

```
print(df)
```

运行结果：

Name  Age
0     Alice    25

1        Bob   30

2   Charlie    35

练习： 删除名字中的多余空格。

参考答案：

删除 Name 列中的多余空格

```
df['Name'] = df['Name'].str.strip()
```

查看修改后的DataFrame

```
print("删除多余空格后的 DataFrame:")
```

```
print(df)
```

运行结果：

删除多余空格后的 DataFrame:

Name  Age
0    Alice   25

1      Bob   30

2  Charlie   35

知识点解释：

str.strip(): 去除字符串的首尾空格。

应用： 清理字符串数据，提高数据一致性。

## 题目 7: 字符串替换

数据集：

```
data = {'Product': ['A_1', 'B_1', 'C_1'],'Price': [10, 20, 30]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

运行结果：

Product  Price

0     A\_1     10

1     B\_1     20

2     C\_1     30

练习： 将下划线替换为空格。

参考答案：

```
df['Product'] = df['Product'].str.replace('_', ' ')
```

```
print("将下划线替换为空格的 DataFrame:")
```

```
print(df)
```

运行结果：

将下划线替换为空格的 DataFrame:

Product  Price

0     A 1     10

1     B 1     20

2     C 1     30

知识点解释：

str.replace(): 字符串替换。

应用： 根据需要清理和格式化字符串数据。

## 题目 8: 拼接数据框

数据集：

```
data1 = {'Product': ['A', 'B'],'Price': [10, 20]
}
```

```
data2 = {'Product': ['C', 'D'],'Price': [30, 40]
}
```

```
df1 = pd.DataFrame(data1)
```

```
df2 = pd.DataFrame(data2)
```

```
print(df1)
```

```
print(df2)
```

运行结果：

Product  Price

0       A     10

1       B     20

Product  Price

0       C     30

1       D     40

练习： 行方向上拼接两个数据框。

参考答案：

```
df_combined = pd.concat([df1, df2], ignore_index=True)
```

```
print(df_combined)
```

运行结果：

行方向上拼接两个数据框

Product  Price

0       A     10

1       B     20

2       C     30

3       D     40

知识点解释：

pd.concat(): 拼接数据框。

ignore_index=True: 重置索引。

应用： 合并数据源，创建一个完整的数据集。

## 题目 9: 拆分列

数据集：

```
data = {'FullName': ['Alice Smith', 'Bob Brown', 'Charlie Johnson']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

运行结果：

FullName
0      Alice Smith

1        Bob Brown

2  Charlie Johnson

练习： 将"FullName"拆分为"FirstName"和"LastName"两列。

参考答案：

```
df[['FirstName', 'LastName']] = df['FullName'].str.split(' ', expand=True)
```

```
print(df)
```

运行结果：

将"FullName"拆分为"FirstName"和"LastName"两列后：

FullName FirstName LastName
0      Alice Smith     Alice    Smith

1        Bob Brown       Bob    Brown

2  Charlie Johnson   Charlie  Johnson

知识点解释：

str.split(): 按指定分隔符拆分字符串，让数据列可以独立处理。

expand=True：这个参数的作用是将拆分后的结果直接展开成一个 DataFrame，而不是返回一个列表。这样可以得到一个新的 DataFrame，其中每列对应一个拆分出的部分。

## 题目 10: 合并列

数据集：

```
data = {'FirstName': ['Alice', 'Bob'],'LastName': ['Smith', 'Brown']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

运行结果：

FirstName LastName

0     Alice    Smith

1       Bob    Brown

练习： 将"FirstName"和"LastName"合并为"FullName"。

参考答案：

df['FullName'] = df['FirstName'] + ' ' + df['LastName']

print(df)

运行结果：

FirstName LastName     FullName

0     Alice    Smith  Alice Smith

1       Bob    Brown    Bob Brown

知识点解释：

字符串加法：将字符串列合并为一个新的列。

## 题目 11: 条件筛选

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

运行结果：

Name  Age
0    Alice   25

1      Bob   30

2  Charlie   35

练习： 筛选出年龄大于30的行。

参考答案：

```
filtered_df = df[df['Age'] > 30]
```

```
print(filtered_df)
```

运行结果：

Name  Age
2  Charlie   35

知识点解释：

布尔索引：使用条件筛选DataFrame中的行。

## 题目 12: 按列排序

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [30, 25, 35]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

运行结果：

Name  Age
0    Alice   30

1      Bob   25

2  Charlie   35

练习： 按年龄列进行升序排序。

参考答案：

```
df_sorted = df.sort_values(by='Age')
```

```
print(df_sorted)
```

运行结果：

Name  Age
1      Bob   25

0    Alice   30

2  Charlie   35

知识点解释：

sort_values(): 按指定列排序DataFrame。

## 题目 13: 更改列顺序

数据集：

```
data = {'Name': ['Alice', 'Bob'],'Age': [30, 25]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将列顺序调整为 Age在前，Name在后。

参考答案：

```
df = df[['Age', 'Name']]
```

```
print(df)
```

知识点解释：

DataFrame列重排：调整列的顺序以满足要求。

## 题目 14: 聚合数据

数据集：

```
data = {'Department': ['HR', 'IT', 'HR', 'IT'],'Salary': [50000, 60000, 70000, 80000]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 计算每个部门的平均工资。

参考答案：

```
average_salary = df.groupby('Department')['Salary'].mean().reset_index()
```

```
print(average_salary)
```

知识点解释：

groupby(): 分组数据。

mean(): 计算平均值。

## 题目 15: 转换日期格式

数据集：

```
data = {'Date': ['20210101', '20210102', '20210103'],'Sales': [200, 150, 300]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将"Date"列转换为 datetime 类型。

参考答案：

```
df['Date'] = pd.to_datetime(df['Date'])
```

```
print(df)
```

知识点解释：

pd.to_datetime(): 将字符串转换为日期时间格式。

## 题目 16: 添加新列

数据集：

```
data = {'Total': [100, 200, 300],'Quantity': [10, 20, 30]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 增加一个新列"UnitPrice"，其值为 Total / Quantity。

参考答案：

```
df['UnitPrice'] = df['Total'] / df['Quantity']
```

```
print(df)
```

知识点解释：

列操作：在现有列基础上计算新列。

## 题目 17: 处理字符串列

数据集：

```
data = {'Email': ['john.doe@example.com', 'jane.doe@domain.com']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 提取邮箱的用户名部分。

参考答案：

```
df['Username'] = df['Email'].apply(lambda x: x.split('@')[0])
```

```
print(df)
```

知识点解释：

字符串操作与apply函数：应用自定义函数处理字符串。

## 题目 18: 填补空值（向前填充）

数据集：

```
data = {'Date': ['20210101', '20210102', '20210103'],'Temperature': [23, None, 25]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 用前一个值填补空值。

参考答案：

```
df['Temperature'].fillna(method='ffill', inplace=True)
```

```
print(df)
```

知识点解释：

ffill: 前向填充，适用于时间序列数据。

## 题目 19: 填补空值（向后填充）

数据集：

```
data = {'Date': ['20210101', '20210102', '20210103'],'Temperature': [23, None, 25]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 用后一个值填补空值。

参考答案：

```
df['Temperature'].fillna(method='bfill', inplace=True)
```

```
print(df)
```

知识点解释：

bfill: 后向填充，适用于时间序列数据。

## 题目 20: 数据截取

数据集：

```
data = {'ID': [1, 2, 3, 4, 5],'Score': [50, 60, 70, 80, 90]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 提取前3行数据。

参考答案：

```
subset_df = df.head(3)
```

```
print(subset_df)
```

知识点解释：

head(): 提取指定数量的行。

## 题目 21: 数据抽样

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Edward'],'Age': [25, 26, 23, 23, 29]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 随机抽样2行数据。

参考答案：

```
sample_df = df.sample(n=2)
```

```
print(sample_df)
```

知识点解释：

sample(): 从 DataFrame 中随机抽取样本。

## 题目 22: 数据分组统计

数据集：

```
data = {'Category': ['A', 'B', 'A', 'B', 'A'],'Values': [100, 150, 200, 50, 300]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 统计每个类别的总值。

参考答案：

```
grouped_df = df.groupby('Category')['Values'].sum().reset_index()
```

```
print(grouped_df)
```

知识点解释：

groupby() 和 sum(): 按关键列分组后求和。

## 题目 23: 数据透视表

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Month': ['Jan', 'Feb', 'Mar'],'Sales': [200, 100, 300]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 创建一个数据透视表，以“Month”为列，“Sales”为值。

参考答案：

```
pivot_table = df.pivot(columns='Month', values='Sales')
```

```
print(pivot_table)
```

知识点解释：

pivot(): 重塑 DataFrame 以创建数据透视表。

## 题目 24: 填充NaN值

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David'],'Score': [85, None, 78, None]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 用 0 填充 NaN 值。

参考答案：

df['Score'].fillna(0, inplace=True)

print(df)

知识点解释：

fillna(0): 用指定值填充 DataFrame 中的 NaN 值。

## 题目 25: 替换特定值

数据集：

```
data = {'Product': ['A', 'B', 'C', 'D'],'Price': [100, 200, 150, None]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将“None”替换为 0。

参考答案：

df['Price'].fillna(0, inplace=True)

print(df)

知识点解释：

fillna(): 替换 DataFrame 中的特定值。

## 题目 26: 数据标准化

数据集：

```
import numpy as np
```

```
data = {'Height': [150, 160, 170, 180, 190]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将 Height 列标准化（Zscore 标准化）。

参考答案：

df['Height_zscore'] = (df['Height']  df['Height'].mean()) / df['Height'].std()

print(df)

知识点解释：

Zscore 标准化：将数据转换为标准正态分布。

## 题目 27: 数据归一化

数据集：

```
data = {'Income': [5000, 6000, 7000, 8000]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将 Income 列归一化到 [0, 1] 范围。

参考答案：

df['Income_normalized'] = (df['Income']  df['Income'].min()) / (df['Income'].max()  df['Income'].min())

print(df)

知识点解释：

最小最大归一化：将数值缩放到 [0, 1] 范围。

## 题目 28: 数据分类

数据集：

```
data = {'Score': [50, 60, 70, 80, 90, 100]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将 Score 列分为“Low”，“Medium”和“High”三个类别。

参考答案：

bins = [0, 59, 79, 100]

labels = ['Low', 'Medium', 'High']

df['Category'] = pd.cut(df['Score'], bins=bins, labels=labels)

print(df)

知识点解释：

pd.cut(): 将数值数据分为离散的类别。

## 题目 29: 条件列筛选

数据集：

```
data = {'Product': ['A', 'B', 'C', 'D'],'Price': [250, 150, 300, 450]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 筛选出价格大于200的产品。

参考答案：

```
filtered_df = df[df['Price'] > 200]
```

```
print(filtered_df)
```

知识点解释：

布尔索引：使用条件筛选DataFrame中的行。

## 题目 30: 日期列提取年、月、日

数据集：

```
data = {'Date': ['20210101', '20210215', '20210320']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 提取“Date”列的年、月、日为单独列。

参考答案：

```
df['Date'] = pd.to_datetime(df['Date'])
```

```
df['Year'] = df['Date'].dt.year
```

```
df['Month'] = df['Date'].dt.month
```

```
df['Day'] = df['Date'].dt.day
```

```
print(df)
```

知识点解释：

dt.year, dt.month, dt.day: 提取日期的年、月、日部分。

## 题目 31: 指定列数据类型转换

数据集：

```
data = {'Height': ['5.1', '5.8', '6.0'],'Weight': ['70', '80', '75']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将“Height”转换为浮点数，将“Weight”转换为整数。

参考答案：

```
df['Height'] = df['Height'].astype(float)
```

```
df['Weight'] = df['Weight'].astype(int)
```

```
print(df)
```

知识点解释：

astype(): 转换数据类型，以便进一步数值操作或分析。

## 题目 32: 删除特定列

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35],'Country': ['USA', 'UK', 'Canada']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 删除“Country”列。

参考答案：

```
df.drop(columns=['Country'], inplace=True)
```

```
print(df)
```

知识点解释：

drop(columns=[]): 删除指定列。

## 题目 33: 数值列求和

数据集：

```
data = {'A': [1, 2, 3],'B': [4, 5, 6]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 计算列“A”和列“B”的总和。

参考答案：

```
df['A+B'] = df['A'] + df['B']
```

```
print(df)
```

知识点解释：

列操作：直接在列进行加法运算，生成新列。

## 题目 34: 数据转置

数据集：

```
data = {'Name': ['Alice', 'Bob'],'Age': [25, 30]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将 DataFrame 转置。

参考答案：

```
transposed_df = df.T
```

```
print(transposed_df)
```

知识点解释：

T: 转置（将行变为列或列变为行）。

## 题目 35: 追加行

数据集：

```
data = {'Name': ['Alice', 'Bob'],'Age': [25, 30]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 追加一行数据。

参考答案：

```
new_row = pd.DataFrame([[35, 'Charlie']], columns=['Age', 'Name'])
```

```
df = pd.concat([df, new_row], ignore_index=True)
```

```
print(df)
```

知识点解释：

concat(): 合并 DataFrame 用于追加行，ignore_index=True 重置索引。

## 题目 36: 连接两个数据集

数据集：

```
data1 = {'Name': ['Alice', 'Bob'],'Age': [25, 30]
}
```

```
data2 = {'Name': ['Charlie', 'David'],'Age': [35, 40]
}
```

```
df1 = pd.DataFrame(data1)
```

```
df2 = pd.DataFrame(data2)
```

```
print(df1)
```

```
print(df2)
```

练习： 将两个数据集行方向上连接。

参考答案：

```
df_combined = pd.concat([df1, df2], ignore_index=True)
```

```
print(df_combined)
```

知识点解释：

concat(): 行方向上合并 DataFrame 并重置索引。

## 题目 37: 数据分类统计

数据集：

```
data = {'Person': ['John', 'Jane', 'Alice', 'John', 'Jane'],'Score': [85, 92, 78, 75, 89]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 计算每个人的平均分。

参考答案：

```
average_score = df.groupby('Person')['Score'].mean().reset_index()
```

```
print(average_score)
```

知识点解释：

分组聚合: 使用 groupby() 和 mean() 计算每个分组的平均分。

## 题目 38: 条件列替换

数据集：

```
data = {'Height(cm)': [150, 160, 170, 180, 120],'Category': ['Short', 'Medium', 'Tall', 'Tall', 'Short']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将所有“Category”列中的“Short”替换为“Low”。

参考答案：

```
df['Category'] = df['Category'].replace('Short', 'Low')
```

```
print(df)
```

知识点解释：

replace(): 替换列中的特定值。

## 题目 39: 重塑数据

数据集：

```
data = {'Name': ['John', 'Jane', 'Alice'],'Math': [85, 92, 78],'English': [90, 88, 85],'Science': [75, 89, 92]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将数据重塑为长格式。

参考答案：

```
melted_df = pd.melt(df, id_vars=['Name'], var_name='Subject', value_name='Score')
```

```
print(melted_df)
```

知识点解释：

melt(): 将数据从宽格式转换为长格式，有利于某些数据分析或可视化。

## 题目 40: 拆分时间列

数据集：

```
data = {'Timestamp': ['20210101 12:30:45', '20210215 13:45:50', '20210320 14:55:55']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 从“Timestamp”列中提取日期和时间。

参考答案：

```
df['Timestamp'] = pd.to_datetime(df['Timestamp'])
```

```
df['Date'] = df['Timestamp'].dt.date
```

```
df['Time'] = df['Timestamp'].dt.time
```

```
print(df)
```

知识点解释：

dt.date, dt.time: 提取 datetime 列中的日期和时间部分。

## 题目 41: 批量处理字符串

数据集：

```
data = {'Text': ['Hello world', '  Pandas is awesome  ', '  Data cleaning is important']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 去除每个字符串的首尾空格。

参考答案：

```
df['Text'] = df['Text'].str.strip()
```

```
print(df)
```

知识点解释：

str.strip(): 去除字符串中的首尾空格，清洁数据。

## 题目 42: 检查重复值

数据集：

```
data = {'ID': [1, 2, 2, 3, 4],'Value': [10, 20, 20, 30, 40]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 检查并获取重复的行。

参考答案：

```
duplicate_rows = df[df.duplicated()]
```

```
print(duplicate_rows)
```

知识点解释：

duplicated(): 检查 DataFrame 是否有重复行。

## 题目 43: 获取唯一值

数据集：

```
data = {'Items': ['Apple', 'Banana', 'Apple', 'Orange', 'Banana']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 获取“Items”列的唯一值。

参考答案：

```
unique_items = df['Items'].unique()
```

```
print(unique_items)
```

知识点解释：

unique(): 返回去重后的值列表。

## 题目 44: 热编码

数据集：

```
data = {'Category': ['A', 'B', 'A', 'C']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 对“Category”列进行独热编码。

参考答案：

```
one_hot_encoded_df = pd.get_dummies(df, columns=['Category'])
```

```
print(one_hot_encoded_df)
```

知识点解释：

get_dummies(): 对分类变量进行独热编码，有助于机器学习模型处理分类数据。

## 题目 45: 分类型数据转化为数值

数据集：

```
data = {'Category': ['Low', 'Medium', 'High', 'Low']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将“Category”列转化为数值类型。

参考答案：

```
category_mapping = {'Low': 1, 'Medium': 2, 'High': 3}
```

```
df['Category'] = df['Category'].map(category_mapping)
```

```
print(df)
```

知识点解释：

map(): 将分类变量映射到数值，有助于数据分析和机器学习。

## 题目 46: 数据抽样（指定比例）

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Edward'],'Age': [25, 26, 23, 23, 29]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 随机抽样50%行数据。

参考答案：

```
sample_df = df.sample(frac=0.5)
```

```
print(sample_df)
```

知识点解释：

sample(frac=0.5): 抽取50%行数作为样本。

## 题目 47: 处理不存在的列

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 检查并尝试访问不存在的列。

参考答案：

if 'Gender' in df.columns:

print(df['Gender'])
else:

print("Column 'Gender' does not exist.")
知识点解释：

列存在性检查：确保访问的列存在于 DataFrame 中以避免错误。

## 题目 48: 插入列

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 在第二列位置插入“Country”列。

参考答案：

df.insert(1, 'Country', ['USA', 'UK', 'Canada'])

print(df)

知识点解释：

insert(): 在指定位置插入新列。

## 题目 49: 索引重置

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
df.set_index('Name', inplace=True)
```

```
print(df)
```

练习： 重置索引。

参考答案：

```
df.reset_index(inplace=True)
```

```
print(df)
```

知识点解释：

reset_index(): 重置 DataFrame 的索引，有助于恢复默认整数索引。

## 题目 50: 读取CSV文件

数据集：

创建示例CSV文件

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
df.to_csv('example.csv', index=False)
```

练习： 读取CSV文件“example.csv”。

参考答案：

```
df = pd.read_csv('example.csv')
```

```
print(df)
```

知识点解释：

read_csv(): 从CSV文件读取数据到DataFrame。

## 题目 51: 写入CSV文件

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将DataFrame写入CSV文件“output.csv”。

参考答案：

```
df.to_csv('output.csv', index=False)
```

知识点解释：

to_csv(): 将DataFrame写入 CSV 文件。

## 题目 52: 读取Excel文件

数据集：

创建示例Excel文件

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
df.to_excel('example.xlsx', index=False)
```

练习： 读取Excel文件“example.xlsx”。

参考答案：

```
df = pd.read_excel('example.xlsx')
```

print(df)

知识点解释：

read_excel(): 从Excel文件读取数据到DataFrame。

## 题目 53: 写入Excel文件

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将DataFrame写入Excel文件“output.xlsx”。

参考答案：

```
df.to_excel('output.xlsx', index=False)
```

知识点解释：

to_excel(): 将DataFrame写入 Excel 文件。

## 题目 54: 通过索引进行行过滤

数据集：

```
data = {'ID': [1, 2, 3, 4, 5],'Score': [55, 78, 85, 45, 92]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 筛选出索引为1、3、4的行。

参考答案：

```
filtered_df = df.loc[[1, 3, 4]]
print(filtered_df)
```

知识点解释：

loc[]: 根据索引标签进行行过滤。

## 题目 55: 通过条件更改列值

数据集：

```
data = {'ID': [1, 2, 3, 4, 5],'Score': [55, 78, 85, 45, 92]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将“Score”列中大于80的值更改为“PASS”。

参考答案：

```
df.loc[df['Score'] > 80, 'Score'] = 'PASS'
```

```
print(df)
```

知识点解释：

布尔索引和loc[]: 根据条件更新列中的值。

## 题目 56: 数据集堆叠

数据集：

```
data1 = {'Team': ['A', 'B', 'C'],'Points': [25, 30, 35]
}
```

```
data2 = {'Team': ['D', 'E', 'F'],'Points': [40, 45, 50]
}
```

```
df1 = pd.DataFrame(data1)
```

```
df2 = pd.DataFrame(data2)
```

```
print(df1)
```

```
print(df2)
```

练习： 将两个DataFrame垂直堆叠。

参考答案：

```
stacked_df = pd.concat([df1, df2], axis=0, ignore_index=True)
```

```
print(stacked_df)
```

知识点解释：

concat()：按行堆叠数据框。

题目 57: 按列计算

数据集：

```
data = {'A': [1, 2, 3],'B': [4, 5, 6]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 计算“A”列和“B”列的差值。

参考答案：

df['AB

## 题目 57: 按列计算

数据集：

```
data = {'A': [1, 2, 3],'B': [4, 5, 6]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 计算“A”列和“B”列的差值。

参考答案：

```
df['AB'] = df['A'] - df['B']
```

```
print(df)
```

知识点解释：

列操作：直接在列进行减法运算，生成新列。

## 题目 58: 数据集拆分

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Edward'],'Score': [85, 90, 75, 60, 95],'Age': [25, 22, 23, 24, 26]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将数据集按索引拆分为训练集 (80%) 和测试集 (20%)。

参考答案：

```
train_df = df.sample(frac=0.8, random_state=1)
```

```
test_df = df.drop(train_df.index)
```

```
print("Train DataFrame:")
```

```
print(train_df)
```

```
print("Test DataFrame:")
```

```
print(test_df)
```

知识点解释：

数据抽样和拆分：使用 sample() 和 drop() 按比例拆分数据集。

## 题目 59: 处理缺失值

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David'],'Age': [25, None, 23, None],'Score': [85, 90, None, 95]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 使用均值填充“Age”列中的缺失值，使用上一个值填充“Score”列中的缺失值。

参考答案：

```
df['Age'].fillna(df['Age'].mean(), inplace=True)
```

```
df['Score'].fillna(method='ffill', inplace=True)
```

```
print(df)
```

知识点解释：

fillna(): 使用特定值或方法填充缺失值。

## 题目 60: 数据透视表

数据集：

```
data = {'Product': ['A', 'B', 'A', 'B'],'Year': [2020, 2020, 2021, 2021],'Sales': [250, 300, 400, 350]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 创建一个数据透视表，显示每年每个产品的总销售额。

参考答案：

```
pivot_table = df.pivot_table(values='Sales', index='Year', columns='Product', aggfunc='sum')
```

```
print(pivot_table)
```

知识点解释：

pivot_table(): 创建数据透视表，用于整理和汇总数据。

## 题目 61: 批量应用函数

数据集：

```
data = {'Value': [1, 2, 3, 4, 5]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将“Value”列中的每个值平方。

参考答案：

```
df['Value'] = df['Value'].apply(lambda x: x  2)
```

```
print(df)
```

知识点解释：

apply(): 将函数应用于列中的每个元素。

## 题目 62: 数据融合（Merge）

数据集：

```
data1 = {'Key': ['A', 'B', 'C'],'Value1': [1, 2, 3]
}
```

```
data2 = {'Key': ['B', 'C', 'D'],'Value2': [4, 5, 6]
}
```

```
df1 = pd.DataFrame(data1)
```

```
df2 = pd.DataFrame(data2)
```

```
print(df1)
```

```
print(df2)
```

练习： 合并两个 DataFrame，要求包含所有键。

参考答案：

```
merged_df = pd.merge(df1, df2, on='Key', how='outer')
```

```
print(merged_df)
```

知识点解释：

merge(): 基于键合并多个数据集，how='outer' 表示全外连接。

## 题目 63: 多索引 DataFrame

数据集：

```
data = {'City': ['New York', 'New York', 'London', 'London'],'Year': [2020, 2021, 2020, 2021],'Population': [8000000, 8500000, 9000000, 9200000]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 设置“City”和“Year”作为多级索引。

参考答案：

```
df.set_index(['City', 'Year'], inplace=True)
```

```
print(df)
```

知识点解释：

多级索引：用于多维数据，更好地组织和查询数据。

## 题目 64: 索引切片

数据集：

```
data = {'City': ['New York', 'New York', 'London', 'London', 'Tokyo', 'Tokyo'],'Year': [2020, 2021, 2020, 2021, 2020, 2021],'Population': [8000000, 8500000, 9000000, 9200000, 3700000, 3800000]
}
```

```
df = pd.DataFrame(data)
```

```
df.set_index(['City', 'Year'], inplace=True)
```

```
print(df)
```

练习： 筛选出 London 2021 和 Tokyo 2020 的数据。

参考答案：

```
sliced_df = df.loc[('London', 2021):('Tokyo', 2020)]
```

```
print(sliced_df)
```

知识点解释：

多级索引切片：用 loc[] 实现复杂数据的索引过滤。

## 题目 65: 部分数据聚合

数据集：

```
data = {'Team': ['A', 'B', 'A', 'B', 'A', 'B'],'Points': [10, 20, 30, 40, 50, 60]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 计算每个团队的总积分。

参考答案：

```
aggregated_points = df.groupby('Team')['Points'].sum().reset_index()
```

```
print(aggregated_points)
```

知识点解释：

分组聚合：用 groupby() 和 sum() 对部分数据进行统计汇总。

## 题目 66: 创建时间序列

数据集：

没有指定数据集

练习： 创建一个包含日期从2024年1月1日至2024年1月10日的时间序列。

参考答案：

```
date_range = pd.date_range(start='20240101', end='20240110')
```

```
print(date_range)
```

知识点解释：

date_range(): 创建指定范围的时间序列。

## 题目 67: 重采样（Resampling）

数据集：

```
date_rng = pd.date_range(start='20240101', end='20240110', freq='D')
```

```
data = {'Date': date_rng,'Value': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
}
```

```
df = pd.DataFrame(data)
```

```
df.set_index('Date', inplace=True)
```

```
print(df)
```

练习： 将每日数据重采样为每周数据，并计算每周的总和。

参考答案：

```
weekly_df = df.resample('W').sum()
```

```
print(weekly_df)
```

知识点解释：

resample(): 将时间序列数据按照新的时间频率进行重新采样。

## 题目 68: 移动窗口（Rolling Window）

数据集：

```
date_rng = pd.date_range(start='20240101', end='20240110', freq='D')
```

```
data = {'Date': date_rng,'Value': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
}
```

```
df = pd.DataFrame(data)
```

```
df.set_index('Date', inplace=True)
```

```
print(df)
```

练习： 计算3天滚动窗口的均值。

参考答案：

```
rolling_mean = df.rolling(window=3).mean()
```

```
print(rolling_mean)
```

知识点解释：

rolling(window=3).mean(): 计算滚动窗口的均值。

## 题目 69: 数据补充

数据集：

```
date_rng = pd.date_range(start='20240101', end='20240110', freq='D')
```

```
data = {'Date': date_rng,'Value': [1, None, 3, None, 5, 6, None, 8, 9, 10]
}
```

```
df = pd.DataFrame(data)
```

```
df.set_index('Date', inplace=True)
```

```
print(df)
```

练习： 用前一个值补充缺失值。

参考答案：

```
df_filled = df.fillna(method='ffill')
```

```
print(df_filled)
```

知识点解释：

fillna(method='ffill'): 用前一个有效值填充缺失值。

## 题目 70: 数据拼接

数据集：

```
data1 = {'Key': ['A', 'B', 'C'],'Value1': [1, 2, 3]
}
```

```
data2 = {'Key': ['B', 'C', 'D'],'Value2': [4, 5, 6]
}
```

```
df1 = pd.DataFrame(data1)
```

```
df2 = pd.DataFrame(data2)
```

```
print(df1)
```

```
print(df2)
```

练习： 将两个DataFrame在列方向上合并。

参考答案：

```
joined_df = pd.merge(df1, df2, on='Key', how='left')
```

```
print(joined_df)
```

知识点解释：

merge(): 基于键合并多个数据集，how='left' 表示左连接。

## 题目 71: 重命名列

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将“Name”列重命名为“Full Name”。

参考答案：

```
df.rename(columns={'Name': 'Full Name'}, inplace=True)
```

```
print(df)
```

知识点解释：

rename(): 重命名 DataFrame 的列。

## 题目 72: 数据框的基本描述

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Age': [25, 30, 35],'Score': [85, 90, 95]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 获取数据框的描述性统计信息。

参考答案：

```
description = df.describe()
```

```
print(description)
```

知识点解释：

describe(): 获取数据框的描述性统计信息，包括计数、均值、标准差、最小值、四分位数和最大值。

## 题目 73: 数据框透视表

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie', 'Alice', 'Bob'],'Semester': ['Semester1', 'Semester1', 'Semester1', 'Semester2', 'Semester2'],'Score': [85, 90, 95, 88, 92]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 创建一个数据透视表，显示每个学生每个学期的平均分数。

参考答案：

```
pivot_table = df.pivot_table(values='Score', index='Name', columns='Semester', aggfunc='mean')
```

```
print(pivot_table)
```

知识点解释：

pivot_table(): 创建数据透视表，用于整理和汇总数据。

## 题目 74: 按列条件过滤

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Score': [85, 90, 95]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 筛选出分数大于或等于90的学生。

参考答案：

```
filtered_df = df[df['Score'] >= 90]
```

```
print(filtered_df)
```

知识点解释：

条件过滤：使用布尔索引筛选行，基于特定条件。

## 题目 75: 多条件列筛选

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David'],'Score': [85, 90, 95, 80],'Age': [25, 30, 35, 28]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 筛选出分数大于80且年龄小于30的学生。

参考答案：

```
filtered_df = df[(df['Score'] > 80) & (df['Age'] < 30)]
```

```
print(filtered_df)
```

知识点解释：

多条件过滤：使用布尔运算符组合多个条件进行筛选。

## 题目 76: 查看数据框信息

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David'],'Score': [85, 90, 95, 80]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 获取数据框的摘要信息。

参考答案：

info = df.info()

print(info)

知识点解释：

info(): 获取DataFrame的摘要信息，包括列的名称、非空值数量、数据类型等。

## 题目 77: 逐项应用函数

数据集：

```
data = {'Value': [1, 2, 3, 4, 5]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 为数据框中的每个元素应用一个函数，例如计算它们的平方。

参考答案：

```
df['Value'] = df['Value'].apply(lambda x: x  2)
```

```
print(df)
```

知识点解释：

apply(): 将函数应用于每个元素，广泛用于数据变换和计算。

## 题目 78: 填充缺失值

数据集：

```
data = {'Name': ['Alice', 'Bob', 'Charlie'],'Score': [85, None, 95]
}
```

df = pd.DataFrame(data)

print(df)

练习： 用平均值填充“Score”列中的缺失值。

参考答案：

df['Score'].fillna(df['Score'].mean(), inplace=True)

print(df)

知识点解释：

fillna(): 填充缺失值，可以使用具体值或统计量（如均值）。

## 题目 79: 时间数据提取

数据集：

```
data = {'Date': ['20240501', '20240615', '20240730']
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 从“Date”列中提取月份。

参考答案：

```
df['Date'] = pd.to_datetime(df['Date'])
```

```
df['Month'] = df['Date'].dt.month
```

```
print(df)
```

知识点解释：

to_datetime()：将字符串转换为时间戳类型，便于提取日期的各个部分（如年、月、日）。

## 题目 80: 条件列替换

数据集：

```
data = {'Student': ['John', 'Jane', 'Alice', 'John', 'Jane'],'Score': [85, 92, 78, 75, 89]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 将“Score”小于80的替换成‘Fail’，其余的替换成‘Pass’。

参考答案：

```
df['Result'] = df['Score'].apply(lambda x: 'Pass' if x >= 80 else 'Fail')
```

```
print(df)
```

知识点解释：

条件替换：使用apply()和lambda函数根据条件进行替换。

## 题目 81: 分组统计

数据集：

```
data = {'Department': ['HR', 'HR', 'Engineering', 'Engineering', 'Marketing', 'Marketing'],'Employee': ['Alice', 'Bob', 'Charlie', 'David', 'Edward', 'Fiona'],'Salary': [50000, 60000, 80000, 95000, 72000, 85000]
}
```

```
df = pd.DataFrame(data)
```

```
print(df)
```

练习： 按部门统计员工的平均工资。

参考答案：

```
average_salary = df.groupby('Department')['Salary'].mean().reset_index()
```

```
print(average_salary)
```

知识点解释：

分组聚合：使用groupby()和mean()等函数计算分组统计量。
