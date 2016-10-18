##Lab2:DOL实例分析&编程##
_ _ _
######概要######

首先，这次实验任务是理解DOL的example文件，并在此基础上进行修改。掌握DOL的eaxmple文件结构和实现过程，并把修改后的结果截图，分析修改的思路。

###### EXAMPLE文件的组成

每个example文件主要是由.c文件、.h文件和.xml文件组成。其中，.c文件是c语言代码文件，负责实现具体的功能；.h文件是.c文件的头文件，定义了相关的全局变量和宏定义；.xml文件是定义各个不同的.c文件是如何按顺序执行，规定了信息变量是如何在进程之间传递。


###### ECAMPLE1文件分析和修改
一开始，example 1 文件的.c部分是由generater.cpp、consumer.cpp和square.cpp组成：generater.cpp是用循环输出变量i（i是从0到9的十个数），然后square.cpp是将接收的的i进行平方处理再传递给consumer.cpp，consumer.cpp是负责把i的平方结果输出到屏幕。
所以，要做的任务是将i的平方计算改为计算i的立方，并将结果显示出来。因此，只需将square.cpp文件以下代码：
```
i = i*i;     //平方
```
改为：
```
i = i*i*i;   //立方
```
输出结果：


![example1平方](https://github.com/XiaoZeLin/photo/blob/master/example1.PNG)

###### ECAMPLE2文件分析和修改
example 2的每个cpp文件和.h文件与eaxmple 1文件的一样，只是.xml文件不一样：example 2的xml文件使用iterator使square.cpp执行了三次，得到i^8(即i的8次方)。这次任务是把square的执行次数改为两次，即要得到i的4次方的结果。原xml文件：
```
 <variable value="2" name="N"/>

  <!-- instantiate resources -->
  <process name="generator">
    <port type="output" name="10"/>
    <source type="c" location="generator.c"/>
  </process>

  <iterator variable="i" range="N">
    <process name="square">
      <append function="i"/>
      <port type="input" name="0"/>
      <port type="output" name="1"/>
      <source type="c" location="square.c"/>
    </process>
  </iterator>

  <process name="consumer">
    <port type="input" name="100"/>
    <source type="c" location="consumer.c"/>
  </process>

  <iterator variable="i" range="N + 1">
    <sw_channel type="fifo" size="10" name="C2">
      <append function="i"/>
      <port type="input" name="0"/>
      <port type="output" name="1"/>
    </sw_channel>
  </iterator>

```




_ _ _
