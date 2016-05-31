# 数据摘要

#### 概述

数据摘要部分主要进行的处理有以下两个方面：

 1. 对标称属性，给出每个可能取值的频数
 2. 数值属性，给出最大、最小、均值、中位数、四分位数及缺失值的个数

#### 实现方法

   语言：python
   
   结果：json
   
   依赖包：xlrd
  
   ** 实现步骤 **

   + 把原始数据导入excel表格
   + 
       通过excel表格的“数据”-->“来自文本” 导入

   + 利用python脚本实现数据摘要的获得

        脚本为：statistics.py ，该脚本涉及到的关键函数如下：

        init()  #从excel获取数据，分离出每一个属性的数据集
       
        nominalDataFrequency #对标称属性，给出每个可能取值的频数，
   
        statistic(chemicalParameters,frequency)   #数值属性，给出最大、最小、均值、中位数、四分位数及缺失值的个数

   + 统计结果保存为json数据
   
         
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

       
  
      

       
