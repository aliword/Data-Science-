# 一、认识matplotlib

Matplotlib是一个**Python 2D**绘图库，能够以多种硬拷贝格式和跨平台的交互式环境生成出版物质量的图形，用来绘制各种静态，动态，交互式的图表。

Matplotlib可用于Python脚本，Python和IPython Shell、Jupyter notebook，Web应用程序服务器和各种图形用户界面工具包等。

Matplotlib是Python数据可视化库中的泰斗，它已经成为python中公认的数据可视化工具，我们所熟知的pandas和seaborn的绘图接口其实也是基于matplotlib所作的高级封装。

为了对matplotlib有更好的理解，让我们从一些最基本的概念开始认识它，再逐渐过渡到一些高级技巧中。

# 二、一个简单的绘图例子

Matplotlib的图像是画在**figure**（如windows，jupyter窗体）上的，每一个figure又包含了一个或多个**axes**（一个可以指定坐标系的子区域）。最简单的创建figure以及axes的方式是通过pyplot.subplots命令，创建axes以后，可以使用Axes.plot绘制最简易的折线图。


```python
import matplotlib.pyplot as plt
import numpy as np
```

**创建一个包含一个axis的figure，并绘图**


```python
fig, ax = plt.subplots()
ax.plot([1,2,3,4],[3,4,1,2])
```




    [<matplotlib.lines.Line2D at 0x18c15bcc310>]




![png](output_6_1.png)


和MATLAB命令类似，你还可以通过一种更简单的方式绘制图像，matplotlib.pyplot方法能够直接在当前axes上绘制图像，如果用户未指定axes，matplotlib会帮你自动创建一个。所以上面的例子也可以简化为以下这一行代码。


```python
plt.plot([1,2,3,4],[3,4,1,2])
```




    [<matplotlib.lines.Line2D at 0x18c15c25a90>]




![png](output_8_1.png)


# 三、figure的组成

现在我们来深入看一下figure的组成。通过一张figure解剖图，我们可以看到一个完整的matplotlib图像通常会包括以下四个层级，这些层级也被称为容器（container），下一节会详细介绍。在matplotlib的世界中，我们将通过各种命令方法来操纵图像中的每一个部分，从而达到数据可视化的最终效果，一副完整的图像实际上是各类子元素的集合。  
* Figure：顶层级，用来容纳所有绘图元素
* Axes：matplotlib宇宙的核心，容纳了大量元素用来构造一幅幅子图，一个figure可以由一个或多个子图组成
* Axis：axes的下属层级，用于处理所有和坐标轴，网格有关的元素
* Tick：axis的下属层级，用来处理所有和刻度有关的元素

![图片](http://datawhale.club/uploads/default/optimized/1X/269a5697ad37c63a906c47c8d0bb6c6aa59911ed_2_500x500.png)

# 四、两种绘图接口

matplotlib提供了两种最常用的绘图接口

* 显式创建figure和axes，在上面调用绘图方法，也被称为OO模式（object-oriented style)  


* 依赖pyplot自动创建figure和axes，并绘图

使用第一种绘图接口，是这样的：


```python
x = np.linspace(0, 2, 100)

figure, ax = plt.subplots()
y1 = x
y2 = x**2
y3 = x**3
y4 = x*np.log(x+ 1e-5)
ax.plot(x, y1, label="linear")
ax.plot(x, y2, label="quadratic")
ax.plot(x, y3, label="cubic")
ax.plot(x, y4, label="ln")
ax.set_xlabel("x label")
ax.set_ylabel("y label")
ax.set_title("simple plot")
ax.legend()
```




    <matplotlib.legend.Legend at 0x18c15f29ca0>




![png](output_14_1.png)


而如果采用**第二种绘图接口**，绘制同样的图，代码是这样的：


```python
x = np.linspace(0, 2, 100)

y1 = x
y2 = x**2
y3 = x**3
y4 = x*np.log(x+ 1e-5)

plt.plot(x, y1, label="linear")
plt.plot(x, y2, label="quadratic")
plt.plot(x, y3, label="cubic")
plt.plot(x, y4, label="ln")
plt.xlabel("x label")
plt.ylabel("y label")
plt.title("simple plot")
plt.legend()
```




    <matplotlib.legend.Legend at 0x18c15b9e790>




![png](output_16_1.png)


**参考资料**

[1.matplotlib官网用户指南](https://matplotlib.org/tutorials/introductory/usage.html#sphx-glr-tutorials-introductory-usage-py)

### 作业  
你在工作或学习中通常何时会用到数据可视化，希望通过可视化达到什么目的？

进行数据分析的时候，需要将用可视化直观的将数据中的特性展示出来，如折线图、直方图、饼状图等，应用于业务决策。个人希望通过python可视化来更好地表达数据中的内容，熟练应用各种图形，处理相较于excel能处理的更大量级的数据。
