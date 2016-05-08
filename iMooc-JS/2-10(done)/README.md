#### 编程挑战

现在利用之前我们学过的JavaScript知识，实现选项卡切换的效果。

效果图:

![pic](http://img.mukewang.com/53bd0e9e000163d203390200.jpg)

文字素材:

    房产：

        275万购昌平邻铁三居 总价20万买一居
        200万内购五环三居 140万安家东三环
        北京首现零首付楼盘 53万购东5环50平
        京楼盘直降5000 中信府 公园楼王现房

    家居:

         40平出租屋大改造 美少女的混搭小窝
         经典清新简欧爱家 90平老房焕发新生
         新中式的酷色温情 66平撞色活泼家居
         瓷砖就像选好老婆 卫生间烟道的设计

    二手房：

         通州豪华3居260万 二环稀缺2居250w甩
         西3环通透2居290万 130万2居限量抢购
         黄城根小学学区仅260万 121平70万抛!
         独家别墅280万 苏州桥2居优惠价248万

#### 任务

大家先思考和分析实现思路，然后在动手实现

一、HTML页面布局

    提示:
    选项卡标题使用ul..li
    选项卡内容使用div

二、CSS样式制作

    提示:
    整个选项卡的样式设置
    选项卡标题的样式设置
    选项卡内容的样式设置
    一开始只显示一个选项卡内容，其它选项卡内容隐藏。

三、JS实现选项卡切换

    提示:
    获取选项卡标题和选项卡内容
    选项卡内容多个，需要循环遍历来操作，得知哪个选项卡和哪个选项内容匹配
    通过改变DOM的css类名称,当前点击的选项卡显示，其它隐藏。