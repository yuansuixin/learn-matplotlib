# Matplotlib


> 说明

- matplotlib主要是用来绘图，README中我就没有放图片（哈哈，有些小懒，没上传图片，你懂得~），我将图片上传到了github上，可以单独查看，或者是在IPython里运行代码都有相关的图片

> 环境

- jupyter-notebook






## 一，Matplotlib基础知识

Matplotlib中的基本图表包括的元素

*   x轴和y轴 axis 水平和垂直的轴线

*   轴标签 axisLabel 水平和垂直的轴标签

*   x轴和y轴刻度 tick 刻度标示坐标轴的分隔，包括最小刻度和最大刻度

*   x轴和y轴刻度标签 tick label 表示特定坐标轴的值

*   绘图区域（坐标系） axes 实际绘图的区域

*   画布 figure 呈现所有的坐标系



### 只含单一曲线的图
- 绘制线性图就是plot函数,必须要有两个参数
- 轴和y轴应该满足映射关系（数量对应，缺一不可）
- x轴应该是一个有序的


### 包含多个曲线的图

1、可以使用多个plot函数（推荐），在一个图中绘制多个曲线

2、也可以在一个plot函数中传入多对X,Y值，在一个图中绘制多个曲线
``plt.plot(x1,np.sin(x1),x2,np.cos(x2))``
### 设置子画布
``axes = plt.subplot()``
### 网格线

绘制正弦余弦

使用plt.grid方法可以开启网格线，使用plt面向对象的方法，创建多个子图显示不同网格线


*   lw代表linewidth，线的粗细
*   alpha表示线的明暗程度
*   color代表颜色
*   axis显示轴向

### 坐标轴界限
``plt.axis([xmin,xmax,ymin,ymax])``

plt.axis('xxx') 'tight'、'off'、'equal'……
设置坐标轴类型
关闭坐标轴


#### xlim方法和ylim方法

除了plt.axis方法，还可以通过xlim，ylim方法设置坐标轴范围


### 坐标轴标签

xlabel方法和ylabel方法
plt.ylabel('y = x^2 + 5',rotation = 60)旋转

color 标签颜色
fontsize 字体大小
rotation 旋转角度

### 标题
plt.title()方法

loc {left,center,right}
color 标签颜色
fontsize 字体大小
rotation 旋转角度




### loc参数

loc参数用于设置图例标签的位置，一般在legend函数内
matplotlib已经预定义好几种数字表示的位置
```
字符串    数值    字符串    数值
best    0    center left    6
upper right    1    center right    7
upper left    2    lower center    8
lower left    3    upper center    9
lower right    4    center    10
right    5
```
loc参数可以是2元素的元组，表示图例左下角的坐标

[0,0] 左下
[0,1] 左上
[1,0] 右下
[1,1] 右上
图例也可以超过图的界限loc = (-0.1,0.9)


### ncol参数
ncol控制图例中有几列,在legend中设置ncol,需要设置loc



### 保存图片
使用figure对象的savefig的函数

- filename
  含有文件路径的字符串或Python的文件型对象。图像格式由文件扩展名推断得出，例如，.pdf推断出PDF，.png推断出PNG （“png”、“pdf”、“svg”、“ps”、“eps”……）
- dpi
  图像分辨率（每英寸点数），默认为100
- facecolor
  图像的背景色，默认为“w”（白色）

## 设置plot的风格和样式

plot语句中支持除X,Y以外的参数，以字符串形式存在，来控制颜色、线型、点型等要素，语法形式为：
plt.plot(X, Y, 'format', ...)

### 点和线的样式
颜色
- 参数color或c
##### 颜色值的方式
+ 别名
    + color='r'

+ 合法的HTML颜色名
    + color = 'red'

|  颜色  |  别名  | HTML颜色名 |  颜色  |  别名  | HTML颜色名 |
| :--: | :--: | :-----: | :--: | :--: | :-----: |
|  蓝色  |  b   |  blue   |  绿色  |  g   |  green  |
|  红色  |  r   |   red   |  黄色  |  y   | yellow  |
|  青色  |  c   |  cyan   |  黑色  |  k   |  black  |
| 洋红色  |  m   | magenta |  白色  |  w   |  white  |




+ HTML十六进制字符串
    + color = '#eeefff'       


+ 归一化到[0, 1]的RGB元组
    + color = (0.3, 0.3, 0.4)

+ jpg png 区别

    - jpg是有0-255之间的数来表示颜色，使用整数
    - png是由0-1之间的数表示颜色，使用浮点数，更精确

透明度
- alpha参数

背景色
- 设置背景色，通过plt.subplot()方法传入facecolor参数，来设置坐标系的背景色

线型
- 参数linestyle或ls

| 线条风格 |  描述  |     线条风格     |  描述   |
| :--: | :--: | :----------: | :---: |
| '-'  |  实线  |     ':'      |  虚线   |
| '--' | 破折线  |   'steps'    |  阶梯线  |
| '-.' | 点划线  | 'None' / '，' | 什么都不画 |

线宽
- linewidth或lw参数

不同宽度的破折线
- dashes参数 eg.dashes = [20,50,5,2,10,5]

设置破折号序列各段的宽度
![](index_files/279189296.png)

点型
- marker 设置点形
- markersize 设置点形大小

|  标记  |    描述    |  标记  |    描述    |
| :--: | :------: | :--: | :------: |
| '1'  | 一角朝下的三脚架 | '3'  | 一角朝左的三脚架 |
| '2'  | 一角朝上的三脚架 | '4'  | 一角朝右的三脚架 |


|  标记  |  描述  |  标记  |  描述  |
| :--: | :--: | :--: | :--: |
| 's'  | 正方形  | 'p'  | 五边形  |
| 'h'  | 六边形1 | 'H'  | 六边形2 |
| '8'  | 八边形  |      |      |



|  标记  |  描述  |  标记  |  描述  |
| :--: | :--: | :--: | :--: |
| '.'  |  点   | 'x'  |  X   |
| '\*' |  星号  | '+'  |  加号  |
| ','  |  像素  |      |      |


|  标记  |  描述  |         标记         |  描述  |
| :--: | :--: | :----------------: | :--: |
| 'o'  |  圆圈  |        'D'         |  菱形  |
| 'd'  | 小菱形  | '','None',' ',None |  无   |



| 标记     | 描述     | 标记   |  描述 |
| :--------: |:----------:| :------:| :----:|
| '\_'     |  水平线    | '&#124;'     |  竖线   

![](index_files/279276781.png)


|  标记  |    描述    |  标记  |    描述    |
| :--: | :------: | :--: | :------: |
| 'v'  | 一角朝下的三角形 | '<'  | 一角朝左的三角形 |
| '^'  | 一角朝上的三角形 | '>'  | 一角朝右的三角形 |


多参数连用
- 颜色、点型、线型，可以把几种参数写在一个字符串内进行设置 'r-.o'

#### 更多点和线的设置

- markeredgecolor = 'green',
- markeredgewidth = 2,
- markerfacecolor = 'purple'

|       参数        |   描述   |       参数        |   描述   |
| :-------------: | :----: | :-------------: | :----: |
|     color或c     |  线的颜色  |  linestyle或ls   |   线型   |
|  linewidth或lw   |   线宽   |     marker      |   点型   |
| markeredgecolor | 点边缘的颜色 | markeredgewidth | 点边缘的宽度 |
| markerfacecolor | 点内部的颜色 |   markersize    |  点的大小  |





### 在一条语句中为多个曲线进行设置
#### 多个曲线同一设置
属性名声明，不可以多参数连用

plt.plot(x1, y1, x2, y2, fmt, ...)

#### 多个曲线不同设置
多个都进行设置时，多参数连用 plt.plot(x1, y1, fmt1, x2, y2, fmt2, ...)


### 三种设置方式
- 向方法传入关键字参数
  import matplotlib as mpl
- 对实例使用一系列的setter方法
  plt.plot()方法返回一个包含所有线的列表，设置每一个线需要获取该线对象
  eg: lines = plt.plot(); line = lines[0]
  line.set_linewith()
  line.set_linestyle()
  line.set_color()
- 对坐标系使用一系列的setter方法
  axes = plt.subplot()获取坐标系
  set_title()
  set_facecolor()
  set_xticks、set_yticks 设置刻度值
  set_xticklabels、set_yticklabels 设置刻度名称

### X、Y轴坐标刻度
plt.xticks()和plt.yticks()方法

- 需指定刻度值和刻度名称 plt.xticks([刻度列表],[名称列表])
- 支持fontsize、rotation、color等参数设置

## 三，2D图形



### 直方图

【直方图的参数只有一个x！！！不像条形图需要传入x,y】

hist()的参数
+ bins  
  可以是一个bin数量的整数值，也可以是表示bin的一个序列。默认值为10
+ normed  
  如果值为True，直方图的值将进行归一化处理，形成概率密度，默认值为False
+ color  
  指定直方图的颜色。可以是单一颜色值或颜色的序列。如果指定了多个数据集合，颜色序列将会设置为相同的顺序。如果未指定，将会使用一个默认的线条颜色
+ orientation  
  通过设置orientation为horizontal创建水平直方图。默认值为vertical

### 条形图

【条形图有两个参数x,y】

- width 纵向设置条形宽度
- height 横向设置条形高度
  bar()、barh()


### 饼图

【饼图也只有一个参数x！】
pie()  
饼图适合展示各部分占总体的比例，条形图适合比较各部分的大小

##### 饼图阴影、分裂等属性设置
- labels参数设置每一块的标签；
- labeldistance参数设置标签距离圆心的距离（比例值,只能设置一个浮点小数）
- autopct参数设置比例值的显示格式(%1.1f%%)；
- pctdistance参数设置比例值文字距离圆心的距离
- explode参数设置每一块顶点距圆形的长度（比例值,列表）；
- colors参数设置每一块的颜色（列表）；
- shadow参数为布尔值，设置是否绘制阴影
- startangle参数设置饼图起始角度

### 散点图

【散点图需要两个参数x,y，但此时x不是表示x轴的刻度，而是每个点的横坐标！】
scatter()  

## 四，图形内的文字，注释，箭头

控制文字属性的方法:  


|  pyplot函数   |            API方法             |         描述         |
| :---------: | :--------------------------: | :----------------: |
|   text()    |     mpl.axes.Axes.text()     |  在Axes对象的任意位置添加文字  |
|  xlabel()   |  mpl.axes.Axes.set_xlabel()  |      为X轴添加标签       |
|  ylabel()   |  mpl.axes.Axes.set_ylabel()  |      为Y轴添加标签       |
|   title()   |  mpl.axes.Axes.set_title()   |    为Axes对象添加标题     |
|  legend()   |    mpl.axes.Axes.legend()    |    为Axes对象添加图例     |
|  figtext()  |   mpl.figure.Figure.text()   | 在Figure对象的任意位置添加文字 |
| suptitle()  | mpl.figure.Figure.suptitle() | 为Figure对象添加中心化的标题  |
| annnotate() |   mpl.axes.Axes.annotate()   | 为Axes对象添加注释（箭头可选）  |


所有的方法会返回一个matplotlib.text.Text对象


### 注释
annotate()
- xy参数设置箭头指示的位置
- xytext参数设置注释文字的位置  
- arrowprops参数以字典的形式设置箭头的样式  
- width参数设置箭头长方形部分的宽度
- headlength参数设置箭头尖端的长度，  
- headwidth参数设置箭头尖端底部的宽度
- shrink参数设置箭头顶点、尾部与指示点、注释文字的距离（比例值），可以理解为控制箭头的长度



如下都是arrowstyle可以选择的风格样式
```

    ``'->'``       head_length=0.4,head_width=0.2
    ``'-['``       widthB=1.0,lengthB=0.2,angleB=None
    ``'|-|'``      widthA=1.0,widthB=1.0
    ``'-|>'``      head_length=0.4,head_width=0.2
    ``'<-'``       head_length=0.4,head_width=0.2
    ``'<->'``      head_length=0.4,head_width=0.2
    ``'<|-'``      head_length=0.4,head_width=0.2
    ``'<|-|>'``    head_length=0.4,head_width=0.2
    ``'fancy'``    head_length=0.4,head_width=0.4,tail_width=0.4
    ``'simple'``   head_length=0.5,head_width=0.5,tail_width=0.2
    ``'wedge'``    tail_width=0.3,shrink_factor=0.5

```

## 五，3D图




导包  
- from mpl_toolkits.mplot3d.axes3d import Axes3D

使用mershgrid函数切割x,y轴
- X,Y = np.meshgrid(x, y)

创建3d坐标系
- axes = plt.subplot(projection='3d')

绘制3d图形
- p = axes.plot_surface(X,Y,Z,color='red',cmap='summer',rstride=5,cstride=5)

添加colorbar
- plt.colorbar(p,shrink=0.5)


### 玫瑰图、极坐标条形图



创建极坐标，设置polar属性
- plt.axes(polar = True)

绘制极坐标条形图
- index = np.arange(-np.pi,np.pi,2*np.pi/6)
- plt.bar(x=index ,height = [1,2,3,4,5,6] ,width = 2*np.pi/6)



