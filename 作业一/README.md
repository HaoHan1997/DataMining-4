# 问题描述
  海藻数据的分析，相关要求 [点此查看](http://bitdm.github.io/2016/assignment1/)

#结果

## 1. 文件介绍

  **数据摘要**
  
     “数据摘要”目录下包含对海藻数据进行数据摘要获取的方法及结果
     
  **数据可视化**
  
       “数据可视化”目录下包含的是对数值数据的可视化实现方法及结果，数据可视化在第一步“数据摘要”的基础上进一步处理得到

## 2. 语言及环境依赖

      语言： python
      依赖的包：xlrd, pylab, matplotlib, scipy, numpy
  
  xlrd: 数据摘要处理时用到
  
  pylab, matplotlib, scipy, numpy：数据可视化时用于生成图
  
## 3. 实现方法

### 3.1 数据摘要

#### 3.1.1 概述

数据摘要部分主要进行的处理有以下两个方面：

   1. 对标称属性，给出每个可能取值的频数
   2. 数值属性，给出最大、最小、均值、中位数、四分位数及缺失值的个数

#### 3.1.2 实现方法

    语言：python
   
    结果：json
   
    依赖包：xlrd
  

 
**1. 把原始数据导入excel表格**
   
       通过excel表格的“数据”-->“来自文本” 导入

**2. 利用python脚本实现数据摘要的获得**

        脚本为：statistics.py ，该脚本涉及到的关键函数如下：

        init()  #从excel获取数据，分离出每一个属性的数据集
       
        nominalDataFrequency #对标称属性，给出每个可能取值的频数，
   
        statistic(chemicalParameters,frequency)   #数值属性，给出最大、最小、均值、中位数、四分位数及缺失值的个数

**3. 统计结果保存为json数据** 
   
         
  nominalDataFrequency.json  是标称属性每个可能取值的频数统计结果

   其格式如下：

         ```
            {
               "riverSize": {
                             "small": 71, 
                             "large": 45, 
                             "medium": 84
                            }, 
              "season": {
                            "autumn": 40, 
                            "spring": 53, 
                            "winter": 62, 
                            "summer": 45
                        }, 
               "riverSpeed": {
                           "high": 84, 
                           "medium": 83, 
                           "low": 33
                       }
            }

        ```
        
      "riverSize"下记录的是河流大小包含的三个属性各自的频数
      
      "season"下记录的是水样收集的季节，包含的四个属性各自的频数
      
      "riverSpeed"下记录的是河水速度包含的三个属性各自的频数

   statistic_max_min_etc.json 是数值属性，最大、最小、均值、中位数、四分位数及缺失值的个数的统计结果
           其格式如下：

        ```
          {
            "Cl": {
                    "min": 最大值, 
                    "max": 最小值, 
                    "midian": 中位数, 
                     "quartiles": [
                                 四分位数（三个值）
                             ], 
                    "miss_num": 1缺失值个数 
                    "mean": 均值
                    }, 
             "mxPH":{同上格式},
              ......
           }
      ```

### 3.2 数据可视化

#### 3.2.1 概述

数据可视部分主要进行的处理是把数值部分的每一个属性包含的数据分别可视化（绘制成直方图，qq图，盒图）：



#### 3.2.2 实现方法

      语言：python
    
     结果：直方图，qq图，盒图
     
     依赖包：pylab, matplotlib, scipy, numpy
  

 
**1. 提取出数值数据，以json格式保存**

   利用“数据摘要”的方法，把原数据中的数值数据提取出来，以json格式保存，结果是[data.json](https://github.com/jennyzhang8800/DataMining/blob/master/作业一/数据可视化/结果/data.json)
   此部分用到的脚本为[cleaning.py](https://github.com/jennyzhang8800/DataMining/blob/master/作业一/数据可视化/程序/cleaning.py)
   
**2. 绘制直方图，qq图，盒图**

   + 直方图的绘制方法：主要用到的是pylab.hist()方法
   + qq图的绘制方法：主要用到的是scipy.stats.probplot方法
   + 盒图的给制方法：主要用到的是boxplot()方法

   代码详见[show.py](https://github.com/jennyzhang8800/DataMining/blob/master/作业一/数据可视化/程序/show.py)     
   
**3. 结果展示**

  结果图分别以svg和jpg两种格式保存
  [点此查看](https://github.com/jennyzhang8800/DataMining/tree/master/作业一/数据可视化/结果/plot)
