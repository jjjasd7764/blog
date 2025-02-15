title: Hadoop
date: 2024-12-1 17:33:33
tags: hadoop
------------

#### hadoop概述

（1）大数据特征4v （2）hadoop特征 4高 （3）生态系统生态组件及功能 （4）liunx常用操作命令

4V：容量、价值、多样、高速

4高：高扩展性、高容错性、高可靠性、高效性

生态系统组件及功能：（核心组件）

Common:支持其他Hadoop模块的公共支持实用程序。

HDFS:分布式文件系统，提供对应用程序数据的高吞吐量访问。

YARN:作业调度和集群资源管理的框架。

MapReduce:基于YARN的大型数据集并行处理系统。

其他家庭成员：Hive、ZooKeeper、Tez、Pig、Spark、Flume、Sqoop、Ambari、Hbase、Zookeeper等等。

hadoop集群搭建：单机模式（本地/单机模式）、伪集群模式（模拟分布式模式）、集群模式（完全分布模式）

hadoop shell命令

创建文件，例如：

在hdfs文件系统中创建fsinput文件

```
hadoop fs -mkdir /fsinput
```

查询文件，例如

```
hadoop fs -ls <路径名>
```

上传文件到hdfs:(上传-put,本地路径：/soft/hadoop-3.1.3/input/，文件名info.txt，hdfs目录：fsinput)

```
hadoop fs -put /soft/hadoop-3.1.3/input/info.txt /fsinput
```

下载文件：（下载-get，从hdfs目录：fsinput，下载info.txt文件到本地的/tmp目录下，可修改info.txt为downloaded\_info.txt）

```
hadoop fs -get /fsinput/info.txt /tmp/hadoop fs -get /fsinput/info.txt /tmp/downloaded\_info.txt
```

删除文件：（例如删除HDFS中/fsinput/info.txt文件）

```
hadoop fs -rm /fsinput/info.txt
```

Zookeeper（分布式协调服务）

（1）Zookeeper是一个开放源码的分布式应用程序协调服务。

（2）Zookeeper的目标是封装好复杂易出错的关键服务，将简易易用的接口和性能高效、功能稳定的系统提供给用户。

（3）ZookeeperQuorum中除了存储-ROOT-表的地址和HMaster的地址，还存储了HRegionServer，使得HMaster可以随时感知到每个HRegionServer的健康状态。

考liunx常用的命令

目录创建

```
Mkdir /目录名
```

```
Ifconfig
```

```
Mkdir /imput
```

```
Cd /input
```

```
Vim 1.txt
```

输入i进入编辑模式，按esc退出编辑模式，输入wq保存并退出，或快捷键shift+zz

```
Ls /soft
```

```
Rm -rf 1.txt
```

#### 2. 配置与java有关的参数


```
Vi /etc/profile
```

```
Source /etc/profile
```

```
Java -version
```

#### 3. hadoop的配置

1)core-site.xml（core-site.xml文件包含读/写缓冲器、用于Hadoop实例的端口号信息、分配给文件系统存储和用于存储所述数据的存储器限制和大小等属性。）

2)hdfs-site.xml（hdfs-site.xml文件包含数据副本的个数、NameNode路径的信息、本地文件系统的数据节点的路径（存储Hadoop基础工具的位置）。）

3)yarn-site.xml（此文件用于配置资源管理器（ResourceManager）和节点管理器（NodeManager）。）

4)Mapred-site.xml（此文件用于指定正在使用MapReduce 的框架。）

4. 集群的搭建/通用命令 hadoop shell 文件的下载/上传等

```
hadoop dfs -put local_file.txt hadoop_file.txt
```

```
hadoop dfs -get hadoop_file.txt local_file.txt
```

5. HDFS分布式文件系统

Hadoop分布式文件系统(Hadoop Distributed File System,HDFS)是一个设计在通用硬件上运行的分布式文件系统。

HDFS是一个高度容错的文件系统，提供对应用数据的高吞吐量访问，特别适合于大数据集的应用处理。

Hdfs的缺点

1）不适合低延时数据访问

对于毫秒级的数据存储无能为力。

适合高吞吐率的场景，即在某一时间内写入大量的数据。

但是在低延时的情况下无能为力，如毫秒级以内读取数据。

2）无法高效存储大量小文件

存储大量小文件会占用NameNode大量的内存以存储文件、目录和块信息,从而消耗大量内存，而NameNode的内存总是有限的。

小文件存储的寻道时间会超过读取时间，这违反了HDFS的设计目标。

3）不支持并发写入和随机修改文件

一个文件只能由一个线程写入，不允许多个线程同时进行写入。

仅支持数据追加，不支持随机修改文件。

#### Hdfs不适合哪些场景？

1. 低延迟数据访问：HDFS是为了高吞吐量而设计的，因此在数据访问延迟上做了妥协。对于那些需要低延迟访问数据的场景，例如实时交易系统或股票市场实时数据分析，HDFS并不是一个理想的解决方案。
2. 大量小文件存储：HDFS在处理大文件时效率很高，但若涉及到大量小文件，则可能出现性能问题。这是因为每个文件和目录都需要在NameNode中占用一定的元数据空间，小文件过多容易导致NameNode的内存成为瓶颈。
3. 多用户实时更新：HDFS支持一次写入多次读取的模型，不支持多个用户同时对同一文件进行写操作。若需要频繁更新或修改数据，尤其是多用户环境下的实时更新，HDFS并不是最佳选择。
4. 结构化数据存储：虽然HDFS能够存储半结构化和非结构化数据，但对于需要有严格数据模式的结构化数据存储，HDFS并不擅长。它不支持结构化查询语言（SQL），对于需要此类功能的场景，HDFS不是理想的选择。
5. 数据量不大的情况：HDFS是为了处理大规模数据集（如TB或PB级别）设计的。如果数据量并不大，例如只有几十GB，使用HDFS可能并不划算，因为它引入的复杂性和资源开销可能超过其带来的好处。

在这些不适宜使用HDFS的场景中

如何解决？

需要将这些文件进行合并

数据块大小设置

HDFS数据块

思考：为什么块的大小不能设置太小，也不能设置太大？

（1） HDFS的块设置太小，会增加寻址时间，程序一直在找块的开始位置；

（2）如果块设置的太大，从磁盘传输数据的时间会明显大于定位这个块开始位置所需的时间。导致程序在处理这块数据时，会非常慢。

寻址时间为传输时间的1%时，为最佳状态。

Hdfs中分块存储，为什么设置为64M/128M？

总结: HDFS块的大小设置主要取决于磁盘传输速率。

如果块设置为1kb，要存储100kb的文件，那么需要将文件切分为100块，读取数据时，就需要去寻找100个块，寻找块的过程会很长。如果是128M的块，10kb存储在数据块中，就可以快速查找。

如果是1TB一个块，复制数据时需要很长时间，处理数据时也需要很长时间。

6. hdfs的特点

HDFS是 Hadoop自身的机架感知文件系统，是 Hadoop的一个基于Linux系统的文件系统。Hadoop的一个重要特点是对跨多台(数千台)主机的数据和计算进行分区，并且同时就近执行应用程序进行数据计算。

HDFS的优点

#### 1）高容错性

数据自动保存多个副本，通过增加副本的形式提高容错性。
某一个副本丢失以后，它可以自动恢复，这是由 HDFS内部机制实现的。

#### 2）适合大数据处理

数据规模：能够处理规模达到GB、TB甚至PB级别的数据。

文件规模：能够处理百万规模以上的文件数量。

#### 3）流式数据访问

HDFS的数据处理规模比较大，同时这些数据一般都是批量处理，而不是用户交互式处理；

流式读取最小化了硬盘的寻址开销，只需要寻址一次，就可一直读取。大文件更适合流式读取。

与流数据访问对应的是随机数据访问，它要求定位、查询或修改数据的延迟较小，比较适合于创建数据后再多次读写的情况。

#### 4）HDFS可构建在廉价机器上

通过多副本机制提高可靠性。提供了容错和恢复机制。

通过简单地添加普通服务器扩展计算能力﹑存储能力和I/О带宽
HDFS分布式文件系统

Hdfs中数据块大小的设置

例题：假如200M，现有hadoop 3.x 进行拆分，如何设置hdfs中数据块的大小

解：先在判断hadoop 3.x 默认配置中是128M ，

所以拆分为两个数据块 就能容纳200M

但是是在hadoop 3.x里，所以要乘上3

答案为6

7. YARN的应用程序

Yarn支持哪些应用程序？

不仅仅支持MapReduce，理论上支持各种计算程序

Yarn的体系架构？

![](file:///C:\Users\28622\AppData\Local\Temp\ksohtml20976\wps1.jpg)

架构的组成？

各组件的作用？

YARN有下面几大构成组件。

（1）一个全局的资源管理器（ResourceManager,RM）。

作用

1）处理客户端请求；

2）启动或监控ApplicationMaster；

3）监控NodeManager；

4）资源的分配与调度。

（2）每个节点上的任务和资源管理器(NodeManager,NM)。

1）管理单个节点上的资源；

2）定时向RM汇报本节点上的资源使用情况和各个Container的运行状态；

3）接收并处理来自AM的Container启动或停止等各种请求。

（3）每个应用的应用程序主控器（ApplicationMaster,AM）。

1）负责将一个应用分割成多个任务，并与RM调度器协调，以获取资源（用Container表示）。

2）与NM通信，以启动或停止任务。

3）监控所有任务的运行状态，并在任务运行失败时重新为任务申请资源，以重启任务。

（4）某个节点上封装多维度资源的资源容器（Container）。

对任务运行环境进行抽象，封装CPU、内存等多维度的资源以及环境变量、启动命令等任务运行相关的信息。

YARN工作流程？

1. 用户向YARN中提交应用程序（比如Hadoop jar 提交MR程序）；
2. ResourceManager为应用程序分配第一个Container，并与对应的NodeManager通信，要求他在container中启动这个应用程序的ApplicationMaster；
3. ApplicationMaster首先向ResourceManager注册并保持通信（用户可以通过RM查看应用程序的运行状态），然后重复步骤4-7直到执行结束；
4. ApplicationMaster采用轮询的方式向ResourceManager申请和领取子任务资源，并监控它们的运行状态；
5. ApplicationMaster与对应的NodeManager通信，要求它启动任务；
6. NodeManager为任务设置好运行环境（包括环境变量、JAR包、二进制程序），将任务启动命令写到一个脚本中，并通过运行该脚本启动任务。
7. 各个任务向ApplicationMaster汇报自己的状态和进度，使ApplicationMaster能够随时掌握各个任务的运行状态，从而可以在任务失败时重新启动任务。在应用程序运行过程中，用户可随时通过RPC向ApplicationMaster查询应用程序的当前运行状态；
8. 应用程序运行完成后，ApplicationMaster向Resource Manager注销并关闭自己。

Yarn的资源调度的策略

如何进行资源调度？

(1) Application Client。Application Client应用程序客户端的作用是将应用程序提交到YARN上，使应用程序运行在YARN上，监控应用程序的运行状态并控制应用程序的运行。

(2) Application Master。Application Master( AM)负责整个应用程序的运行控制，包括向YARN注册应用、申请资源、启动容器等，应用程序的实际工作在容器中进行。

(3) Application Worker。并不是所有的应用程序都需要编写工作程序( Worker)。节点管理器启动Application Master 发送过来的容器，容器内部封装了该ApplicationWorker运行时所需的资源和启动命令。

Mapreduce计算题：

Hadoop3.x默认配置中，本地又HDFS上的目录包含50个纯文本文件，每个文件300MB。使用TextInputFormat作为输入格式类，将该目录作为作业输入，将会启动几个MapTask？

解：默认情况下，针对50个300MB的文件：

如果HDFS块大小是128MB，则每个文件会被划分为3个块，总共会有大约150个块。

因此，在默认配置下，会启动150个MapTask，每个任务处理一个块。

Map阶段、作用与任务，Reduce阶段，作用与任务Shuffle阶段，作用与任务。

8. Mapreduce关键概念的认识

主要功能

1)数据划分和计算任务调度

系统自动将一个作业待处理的大数据划分为多个数据块，每个数据块对应于一个计算任务(Task)，并自动调度计算节点以处理相应的数据块。作业和任务调度功能主要负责分配和调度计算节点(Map节点或Reduce节点)，同时负责监控这些节点的执行状态，并负责Map节点执行的同步控制。

2)数据/代码互定位

为了减少数据通信，基本原则是本地化数据处理，即一个计算节点尽可能多地处理其本地磁盘上分布存储的数据，从而实现代码向数据的迁移；当无法进行这种本地化数据处理时，再寻找其他可用节点，并将数据从网络上传送给该节点(数据向代码迁移)。

3)系统优化

为了减少数据通信开销，中间结果数据在进入Reduce节点前会进行一定的合并处理。一个Reduce节点处理的数据可能来自多个Map节点。为了避免在Reduce计算阶段发生数据相关性，Map节点输出的中间结果需要使用一定的策略进行适当的划分处理，保证相关性数据发送到同一个Reduce节点。此外，系统还进行一些计算性能优化处理，例如对最慢的计算任务采用多备份执行，选择最快完成者作为结果。

4)出错检测和恢复

在由低端商用服务器构成的大规模MapReduce计算集群中，节点硬件(主机、磁盘、内存等)出错和软件出错是常态，因此MapReduce需要能够检测并隔离出错节点，并调度分配新的节点接管出错节点的计算任务。同时，系统还将维护数据存储的可靠性，用多备份冗余存储机制提高数据存储的可靠性，并及时检测和恢复出错的数据。

分区/切片

Map的任务？

在Map函数开始产生输出时，并不是简单地写到磁盘上，出于效率的原因会先写到内存的缓冲区，并做一些预排序处理，最后才写到磁盘。每个Map任务都有一个环形的内存缓冲区，用于存储Map的输出。缓冲区的大小默认为100MB（可以通过设置mapreduce.task.io.sort.mb属性调整）。当缓冲区中的内容达到指定阈值的大小（由mapreduce. map. sort. spill. percent属性设置，默认为0.8或80%）时，一个后台进程就开始将缓冲区中的内容溢出(Spill)到磁盘上。当Spill发生时，Map的输出就可以继续写到缓冲区中，但是在这期间，如果缓冲区被填满了，则该Map将被锁定，直到Spill完成。Spill以循环(Round-Robin)的方式将溢出的内容写到由mapreduce.cluster.local.dir属性指定的目录中，该目录为当前Job的一个子目录。

在写到磁盘之前，线程先将数据分区，每个分区对应于它们最终被发送到的Reducer。在每个分区内，后台进程会在内存中按key排序，如果有combiner函数，则它将在已排序的输出上运行。运行combiner函数可以使Map的输出更加紧凑，所以应将有更少的数据写到本地磁盘和传递给Reducer中的reduce函数。

因为内存缓冲区每次达到Spill的阈值都会创建一个Spill文件，所以在Map任务写完最后的输出记录后，可能会存在多个Spill文件。在任务结束之前，这些Spill 文件将被合并成一个已分区和排序好的输出文件。配置mapreduce.task.io.sort.factor属性可控制每次合并Spill 文件的最大数量，默认为10。

如果有至少3个Spill文件( mapreduce.map.combine.minspills属性设置至少为3)，则在写入输出文件之前，combiner函数将会再次运行。combiner 函数对输入反复运行，并不影响最终的结果。因为如果仅有1个或2个Spill文件，再调用combiner函数以减少Map输出的大小并不值得，所以它不会再运行Map的输出。

当Map输出写到磁盘时，建议对其进行压缩，因为这样可以使Map输出较快地写到磁盘上，节省存储空间，并减少传递reduce函数的数据量。默认Map输出是不压缩的，但是可以通过将mapreduce. map. output. compress属性设置为true启用压缩，使用的压缩库由mapreduce. map.output. compress. codec属性指定。

输出文件的分区通过HTTP提供给reduce 函数。用于文件分区的最大工作线程的数量是由mapreduce.shuffle.max.threads属性控制的。此设置针对的是每个NodeManager，而不是Map任务，默认为0，设置为零表示工作线程的最大数量为机器处理器数量（由Runtime.availableProcessors()报告）的2倍。

1. 总结Map阶段执行过程

第一阶段︰把输入目录下文件按照一定的标准逐个进行逻辑切片，形成切片规划。默认Split size = Block size ( 128M )，每一个切片由一个MapTask处理。( getSplits )

第二阶段:对切片中的数据按照一定的规则读取解析返回<key, value>对。默认是按行读取数据。key是每一行的起始位置偏移量，value是本行的文本内容。(TextInputFormat )

第三阶段∶调用Mapper类中的map方法处理数据。

每读取解析出来的一个<key, value>，调用一次map方法。

第四阶段︰按照一定的规则对Map输出的键值对进行分区partition。默认不分区，因为只有一个reducetask。分区的数量就是reducetask运行的数量。

第五阶段∶Map输出数据写入内存缓冲区，达到比例溢出到磁盘上。溢出spill的时候根据key进行排序sort。默认根据key字典序排序。

第六阶段∶对所有溢出文件进行最终的merge合并，成为一个文件。

Reduce的任务

第一阶段：ReduceTask会主动从MapTask复制拉取属于需要自己处理的数据。

第二阶段：把拉取来数据，全部进行合并merge，即把分散的数据合并成一个大的数据。再对合并后的数据排序。

第三阶段：对排序后的键值对调用reduce方法。键相等的键值对调用一次reduce方法。最后把这些输出的键值对写入到HDFS文件中。

Shuffle的任务

![](file:///C:\Users\28622\AppData\Local\Temp\ksohtml20976\wps2.jpg)

Collect阶段：将MapTask的结果收集输出到默认大小为100M的环形缓冲区，保存之前会对key进行分区的计算，默认Hash分区。

Spill阶段：当内存中的数据量达到一定的阀值的时候，就会将数据写入本地磁盘，在将数据写入磁盘之前需要对数据进行一次排序的操作，如果配置了combiner，还会将有相同分区号和key的数据进行排序。

Merge阶段：把所有溢出的临时文件进行一次合并操作，以确保一个MapTask最终只产生一个中间数据文件。

Copy阶段：ReduceTask启动Fetcher线程到已经完成MapTask的节点上复制一份属于自己的数据。

Merge阶段：在ReduceTask远程复制数据的同时，会在后台开启两个线程对内存到本地的数据文件进行合并操作。

Sort阶段：在对数据进行合并的同时，会进行排序操作，由于MapTask阶段已经对数据进行了局部的排序，ReduceTask只需保证Copy的数据的最终整体有效性即可。

9. Hbase的操作

表的建立：

表数据的插入/查询等

10. Hbase的基础知识

特点/物理模型/数据模型

(1) 表中所有行都按照Row Key的字典序排列。

(2) 表在行的方向，上被分割为多个Region。

(3) 表按大小分割，每个表开始只有一个Region。随着数据的增多， Region不断增大。当增大到一个阈值时，Region就会等分为两个新的Region，之后会出现越来越多的Region。

(4) Region是HBase中分布式存储和负载均衡的最小单元，不同的Region会分布到不同的RegionServer 上。

(5)Region虽然是分布式存储的最小单元，但并不是存储的最小单元。Region由一个或者多个Store组成，每个Store保存一个列族；每个Strore又由一个memStore和0至多个StoreFile组成，StoreFile包含HFile；memStore存储在内存中，StoreFile存储在HDFS中。

1.需求说明

为了更好地管理数据，每个数据表的设计都是需要经过仔细思考。某高校学院为了便于管理学生信息，决定将学生的基本信息和学生成绩信息合并在一起。现已为该需求设计了一张表，为student 表，表结构如表所示。请根据student 表的表结构，使用 HBase创建该表，并将学生数据插入student 表中，以便后线对学生信息进行查询、分析。

![](file:///C:\Users\28622\AppData\Local\Temp\ksohtml20976\wps3.jpg)

2. 实现思路及步骤

（1）启动 HBase 服务，进人 HBase Shell 界面。

（2）使用“list” 命令查看当前 HBase 中的表，若没有则建立新表，若有则先删除表。根据 student 表的表结构创建 student 表，包含两个列族address 和 score

(3）查看 student 表的描述信息，同时使得该表处于启用状态。

(4）向student 表中添加表所示的数据。

11. Hive的体系结构

Hive的体系结构可以分为以下几个部分。

(1) 用户接口：包括shell命令JDBC/ODBC和Web UI，其中最常用的是shell命令接口。

(2) Hive解析器(驱动Driver)：Hive解析器的核心功能是根据用户编写的SQL语法匹配出相应的MapReduce模板，形成对应的MapReduce job进行执行。

(3) Hive 元数据库( MetaStore): Hive 将表中的元数据信息存储在数据库中，如Derby(自带的)、MySQL(实际工作中配置的)；Hive中的元数据信息包括表的名字、表的列和分区、表的属性(是否为外部表等)、表的数据所在的目录等。Hive 中的解析器在运行时会读取元数据库MetaStore中的相关信息。

(4) Hadoop: Hive用HDFS进行存储，用MapReduce进行计算。Hive 数据仓库中的数据存储在HDFS中，业务实际分析计算是利用MapReduce执行的。

12. Hive的基础知识

作用/特点/数据模型

Hive是一个数据仓库基础工具，在Hadoop中用来处理结构化数据。Hive架构在Hadoop之上，是处理大数据的重要工具。Hive 可以使查询和分析更加方便，并提供简单SQL查询功能，可以将SQL语句转换为MapReduce任务运行。

Hive是一种数据库技术，可以定义数据库和表以分析结构化数据。主体结构化数据分析以表的方式存储数据，并通过查询进行分析。

Hive的特点如下。

(1)可以通过SQL处理Hadoop的大数据。

(2)是专门为OLAP设计的。

(3)提供的SQL类型查询语言称为HiveQL或HQL。

(4)是熟知、快速和可扩展的。

13. Spark

Spark与Hadoop的关系

(1) 数据处理速度更快。由于Spark使用了弹性分布式数据集(Resilient Distributed Dataset,RDD)，因此可以在内存上透明地存储数据，把处理过程的中间数据存储在内存中，减少对磁盘的读写次数，从而使数据处理的速度更快。

(2) Spark的集群是为特定类型的工作负载设计的。Spark 和Hadoop一样，都是一种集群计算环境，但它可以针对那些在处理过程中需要大量重用数据集的迭代型工作进行负载。除了可以对数据集进行反复查询外，Spark的典型应用场景就是各种机器学习算法的模型训练，模型训练过程一般都需要在某个特定的数据集上进行迭代运算。

(3)形式多样的数据集操作原语。在Hadoop中，最基本的数据原语是MapReduce提供的map和reduce，由此产生的一个局限就是有些算法无法用MapReduce实现。Spark提供的数据集操作类型非常多（Spark算子），即所谓的Transformations（变换/转换算子），包括map、filter、flatMap、sample、groupByKey、 reduceByKey、union、 join、cogroup、mapValues、sort、partionBy等，以及Count、collect、reduce、lookup、save等多种操作。

(4)流式计算、交互式计算和批量计算的支持。在Spark出现之前，存在3种计算模式，即批量计算(MapReduce)、流式实时计算（Storm)，交互式计算(Impala)，尚缺乏一种可以同时进行这3种计算的灵活框架。

(5) 支持多语言。Spark 运行于Java 虚拟机上，支持Java、Scala、R和Python快速编写应用程序，这有助于开发人员用他们熟悉的编程语言创建并执行应用程序，特别是使用Scala可以像操作本地集合对象一样容易地操作分布式数据集。

Spark的运行模式/生态系统的组件，及其作用

![](file:///C:\Users\28622\AppData\Local\Temp\ksohtml20976\wps4.jpg)
