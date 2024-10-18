---
{"dg-publish":true,"dg-home":true,"permalink":"/matlab/matlab/","tags":["gardenEntry"],"dgPassFrontmatter":true,"created":"2024-09-19T20:30:29.805+08:00","updated":"2024-10-18T15:50:09.329+08:00"}
---

!运算和指令

内容：+ - * / ^

优先级： 小括号>^>* / >+-

clear 变量名（删除变量）

clear  （变量全部清除）

close all   (关闭所有图像)

clc （清空命令窗口）

who （展示工作区的变量）

whos  （展示工作区的变量更详细的信息）

format (long/short/shortE/longE/bank/rat/hex)
 
 改变变量的显示位数长短
e+多少表示乘10的多少次方
eg. 
3.1416e+00表示3.1416×十的零次方

bank：保留两位小数，类似于货币计量）

hex：十六进制

rat：转换成有理数（例如把无穷不循环小数改成分数）

指令后面加分号(;)表示不显示计算结果


箭头(👆👇）展示前后的指令

矩阵和向量使用[]框起来

使用空格/逗号横向排列

使用分号（;）换行纵向排列

矩阵计算(行乘列）
例如： [1 2 3 4]*[1;2;3;4]=1+4+9+16
![](https://i.imgur.com/uKi3l02.png)


矩阵索引
例如：a=[1 2 3;4 5 6;7 8 9]

a（8）=6: 竖着数第三个

a（[1 3 5]）=[1 7 5] :竖着数第1，3，5个元素横着拍成一个新矩阵

a([1 3;1 3])= [1 7;1 7]:竖着数第1，3个元素横向排列，然后换行再取1，3元素放在第二行

a(3,2)=8：第三行第二列的元素

a([1 3],[1 3])= [1 3;7 9]:逗号左边是行，逗号右边是列
即第1，3行和第1，3列的交集元素

等差数列
不需要中括号

a=1:5   (从1到5闭区间，公差默认为1）

a=1:2:5   （从1到5，公差为2）

a=linspace(首项，步长，尾项)

可以使用分号（;）进行换行，例如a=[1:5;2:3:15;-2:0.5:0]

a(行，列)=新元素

行和列可以使用冒号（:）表示全部列

a(3,:)=[7 8 9]

a(3,:)=[]       表示删去第三行


矩阵拼接

c=[a,b]    表示a和b横向拼接

c=[a:b]    表示a和b纵向拼接

特殊矩阵函数

eye(n)    n*n的单位矩阵

zeros(m,n)     m*n的全是0的矩阵

ones(m,n)       m*n的全是1的矩阵

diag()              只有主对角线非零
例如 diag([2 3 4])= [2 0 0;0 3 0;0 0 4]

rand(行，列)    随机生成一个元素在0到1的矩阵

max(a)     从每一列中选出最大数再横向拼成一个矩阵

max(max(a))     这个矩阵最大的数

min(a)         同理

sum(a)        将每一列分别加起来再横向组成一个矩阵

mean(a)      算出每一列的平均数再横向拼成一个矩阵

sort(a)     将每一列分别从小到大排序

sort(a,'descend')    将每一列分别从大到小排序

sortrows(a)   对第一列进行从小到大的排序，排序时要把元素那一行都进行移动

size(a)     输出矩阵a的行数和列数

size（a,1）表示行数

size(a,2)    表示列数

length(a)   输出矩阵a更长那条边的长度

find()    找元素
例如：find（a==5）就是找出矩阵a中元素5的位置


!程序编写
%   单行注释

%%   分块，当分割线

左侧点击行数，则该行不执行，该行以上部分执行，该点就是中断点

ctrl+I     智能缩进

~=         不等于

&&          和

||               或


if,elseif,else结构



```
if 条件
    语句
elseif 条件
    语句
else
    语句
end

```



switch,case,otherwise结构


```
switch 变量
case 值
    语句；
case 值
    语句；
......
otherwise
    语句；
end
```



while结构

```
while 条件
    循环语句；
end
```


for结构

```
for 变量=首项:步长:尾项
    语句；
end
```

tic-toc 计时

```
tic
程序
toc
```

break结构

break用于跳出循环

...
当一行指令太长了，使用三个点换到下一行继续


ctrl+C
中断程序


```
edit(which('mean.m'))
```

找到mean函数并打开编辑

自定义函数
输入和输出变量都有可能有多个，有中括号和逗号构成，计算代码注意乘法使用点乘！

```
function 输出变量名=函数名称（输入变量名）
计算过程
```


!画图

plot(x,y) 

line用于画直线

line([x起点,x终点],[y起点,y终点])

plot(y)   （x就是1：1：y的个数）

hold on/off   (让中间画的图不被覆盖，画在一个窗口)

plot(x,y,'str')       (str可以填以下几种，用于修改画图的线条颜色，）
tip1: plot可以在后面加逗号继续画图，比如 plot（x,y,'bd-',x,h,'gp:',x,w,'ro-',x,g,'c^-'）

tips2：可以在后面使用（‘属性’，值）改变线条粗细颜色等信息

![](https://i.imgur.com/3jyMddS.png)


更多代码去官方文档找linespec

legend()
用于在右上角加上图标

例如：legend(‘sin(x)','cos(x)');    
单引号里写每条线的名称

标题
title（’标题名‘）

xlabel('x名称')   ylabel,zlabel同理


文字图形标注

使用text函数，可以使用LaTeX语法

text(x起始点，y起始点，str)

也可以使用annotation函数创建线条或箭头

例如：annotation（'arrow',[x起点,x终点],[y起点,y终点]）
注意这里xy的位置使用百分比填，0到1的数字


获取图形信息

get(plot(x,y))

修改信息

set(某一个物件handle，'某个属性'，数值)

也可以使用以下方法修改
例如：变量=gca，变量.属性=值
![](https://i.imgur.com/ZAAS7Xg.png)


修改xy轴范围

xlim([起点，终点])中间可以加上步长

ylim同理

一些handle句柄
gcf：figure，显示图形和界面的窗口
gca：axes，轴


打开多个窗口打开多个图形
figure,plot(x,y1)
figure,plot(x,y2)

一个窗口分多个小窗口
序号是从1开始横着数
subplot（行，列，序号）；plot(x,y);

ceil()   向上取整

solve（方程式）
用于解方程

注意：使用该函数解方程时，需要使用“syms 未知数”提前进行定义符号变量，而不是数值

fliplr倒序排列行向量

flipud倒序排列列向量

dot(x,y)    向量x，y内积

