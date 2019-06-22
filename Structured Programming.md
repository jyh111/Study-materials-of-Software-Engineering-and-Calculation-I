结构化编程
=========

#### 思想:自顶向下,逐步求精
#### 格式:算法 + 数据结构

<br>
<br>

### 树状结构

<br>

* 理解
  * 结构图最上层由输入、处理、输出三个部分组成<br>
  * 接着对每一个部分进行拆分，输入、处理、输出分别包含哪些过程<br>

<br>

* 示例1(参见Headfirst P96)
> 模拟棋盘类的战舰游戏,对方战舰的位置随机分布,目标为猜测对方战舰的坐标,然后开炮攻击,命中数发可以打沉战舰,根据发炮的次数评估你的表现<br>

* 树状图:
![达康公司树状结构](https://github.com/jyh111/Study-materials-of-Software-Engineering-and-Calculation-I/blob/master/%E8%BD%AF%E5%B7%A5I%E6%9C%9F%E6%9C%AB/img/09%20-%20%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%BC%96%E7%A8%8B%20I-%E6%80%9D%E6%83%B3_%E9%A1%B5%E9%9D%A2_008.jpg)

* 示例2(参见之前的lab关于课程表的实现)
> 通过输入命令对课程表文件进行增删改查,并给出反馈<br>
* 树状图:
![课程表应用树状结构](https://github.com/jyh111/Study-materials-of-Software-Engineering-and-Calculation-I/blob/master/%E8%BD%AF%E5%B7%A5I%E6%9C%9F%E6%9C%AB/img/09%20-%20%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%BC%96%E7%A8%8B%20I-%E6%80%9D%E6%83%B3_%E9%A1%B5%E9%9D%A2_030.jpg)

<br>
<br>

### 数据流图
* 理解
  * 系统是过程的集合.
  * 过程是对数据的处理,必须包含输入和输出,且输入输出应有所不同

* 示例1(订货系统)
> 一家工厂采购部门每天需要一张订货报表,列出所有需要再次订货的零件<br>
> 仓库管理员会做入库/出库事务,并将事务提交给订货系统,当库存小于临界值时,需要再次订货<br>

* 过程分析
> 仓库管理员将入库/事务传给订货系统<br>
> 订货系统接收事务<br>
> 订货系统根据原有库存清单和事务更新库存清单<br>
> 订货系统根据新生成的库存清单生成需要订货的订货清单<br>
> 订货系统将订货清单提交给采购员<br>
> 采购员接受订货清单<br>

* 数据流图
![订货系统数据流图](https://github.com/jyh111/Study-materials-of-Software-Engineering-and-Calculation-I/blob/master/%E8%BD%AF%E5%B7%A5I%E6%9C%9F%E6%9C%AB/img/%E7%BB%93%E6%9E%84%E5%8C%96%E7%BC%96%E7%A8%8BI-%E6%80%9D%E6%83%B3/06%20-%20%E7%BB%93%E6%9E%84%E5%8C%96%E7%BC%96%E7%A8%8B%20I%20-%20%E6%80%9D%E6%83%B3_%E9%A1%B5%E9%9D%A2_19.jpg)
* 注:先分析过程,再对每个过程细化,最后分析每个过程的输入和输出<br>

<br>

* 示例2(课程表系统)
> 建立一个课程表
> 输入命令对课程表进行增、删、改、查
> 数据保存在文件里

* 过程分析
> 学生输入命令
> 课程表系统接收和分析命令
> 课程表系统根据文件中的数据和命令对文件进行操作
> 课程表返回结果(文件结果、控制台结果)
> 学生接收控制台结果

* 数据流图
![课程表数据流图](https://github.com/jyh111/Study-materials-of-Software-Engineering-and-Calculation-I/blob/master/%E8%BD%AF%E5%B7%A5I%E6%9C%9F%E6%9C%AB/img/%E7%BB%93%E6%9E%84%E5%8C%96%E7%BC%96%E7%A8%8BI-%E6%80%9D%E6%83%B3/06%20-%20%E7%BB%93%E6%9E%84%E5%8C%96%E7%BC%96%E7%A8%8B%20I%20-%20%E6%80%9D%E6%83%B3_%E9%A1%B5%E9%9D%A2_26.jpg)

<br>
<br>

