#### 编程练习

某班的成绩出来了，现在老师要把班级的成绩打印出来。

效果图:

    XXXX年XX月X日 星期X--班级总分为:81

格式要求：

1、显示打印的日期。 格式为类似“XXXX年XX月XX日 星期X” 的当前的时间。

2、计算出该班级的平均分（保留整数）。

同学成绩数据如下：

"小明:87; 小花:81; 小红:97; 小天:76;小张:74;小小:94;小西:90;小伍:76;小迪:64;小曼:76"

#### 任务

第一步：可通过javascript的日期对象来得到当前的日期。

    提示:使用Date()日期对象，注意星期返回值为0-6，所以要转成文字"星期X"

第二步：一长窜的字符串不好弄，找规律后分割放到数组里更好操作哦。

第三步：分割字符串得到分数，然后求和取整。

    提示：parseInt() 字符串类型转成整型。