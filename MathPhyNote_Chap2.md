---
typora-copy-images-to: ../数学物理方法 总结
---

## 数学物理方法 总结

耿彦达 匡亚明学院 161240014

[TOC]

### Chapter 2. 复变函数的积分

#### 2.1 复变函数的积分

##### 几种形式

复变函数沿曲线$l$的路积分定义如下
$$
\begin{align}
\int_l f(z) \, \mathrm{d}z & = \lim_{\max|\Delta z_k| \to 0} \sum_{k=1}^{n} f({\xi}_k)\Delta z.
\end{align}
$$
如果该极限存在且不依赖于$\xi$的选择， 则称这个极限为**复变函数沿曲线$l$的路积分**.

如果将$f(z)$表示成
$$
z = x + iy\\
f(z) = u(x,y) + iv(x,y)
$$
则路积分可以以二元函数路径积分的形式表示出来
$$
\int_l f(z) \, \mathrm{d}z = \int_l \left( u(x, y) \, \mathrm{d}x - v(x, y) \, \mathrm{d}y \right) 
+ i\int_l \left( v(x, y) \, \mathrm{d}x + u(x, y) \, \mathrm{d}y \right).
$$
也可以将$x,y$按参数形式表示出来，得到
$$
\int_l f(z) \, \mathrm{d}z = \int_l \left( u\frac{\partial x}{\partial t} \, \mathrm{d}t - v \, \frac{\partial y}{\partial t} \mathrm{d}t \right) 
+ i\int_l \left( v \frac{\partial x}{\partial t} \, \mathrm{d}t + u \frac{\partial y}{\partial t} \, \mathrm{d}t \right).
$$

##### 积分不等式

路积分存在不等式
$$
\left| \int_l f(z) \, \mathrm{d}z \right| \leq \int_l |f(z)| \, |\mathrm{d}z| \leq \max_{l} f(z) \cdot L.
$$
值得注意的是对于复数$x,y$，有
$$
|x|\cdot|y| \equiv |x \cdot y|.
$$
因此，实际上该不等式的产生是因为
$$
|\int_{l_1} + \int_{l_2}| \leq |\int_{l_1}| + |\int_{l_2}|.
$$
其中的$\int_l |f(z)| \, |\mathrm{d}z|$已经完全类似第一类曲线积分的模式了. 如果将$l$表示为$l: y=x(t)$ 的模式，则
$$
\int_l |f(z)| \, |\mathrm{d}z| = \int_l |f(z)| \, \mathrm{d}l.
$$
因此可以很自然得到第二个不等号.



#### 2.2 柯西定理

当所给复变函数在积分路径上解析时，实部和虚部不是相互独立的，由此引入的新信息可以帮助我们求解路积分. 与多元函数的曲线积分一样，可以划分成两种情况讨论：

##### 单连通区域的情形

如果函数在单连通区域$\bar B$上**解析**，则沿$\bar B$上任意一**分段光滑闭合曲线**$l$有
$$
\oint_l f(z) \, \mathrm{d}z = 0.
$$
**证明如下**：对实部和虚部的曲线积分，分别使用Green公式：
$$
\begin{align}
\oint_l f(z) \, \mathrm{d}z &= \oint_l \left( u \, \mathrm{d}x - v \, \mathrm{d}y \right) 
+ i\oint_l \left( v \, \mathrm{d}x + u \, \mathrm{d}y \right) \\
&= \iint_S \left( - \frac{\partial v}{\partial x} - \frac{\partial u}{\partial y} \right) \mathrm{d}{\vec S} - i\iint_S \left( \frac{\partial u}{\partial x} - \frac{\partial v}{\partial y} \right) \mathrm{d}{\vec S}
\end{align}
$$
将解析函数的Cauchy方程
$$
\begin{cases}
\frac{\partial u}{\partial x} = \frac{\partial v}{\partial y} \\
\frac{\partial v}{\partial x} = -\frac{\partial u}{\partial y}
\end{cases}
$$
代入上式，显然得0.

需要注意的是：约定闭合环路的积分的正方向是**逆时针**方向。

##### 复连通区域的情形

注意到上述证明中使用了曲面积分，这意味着函数必须在曲线所围区域内部都保持解析. 但是，多数情况下，区域内会包括奇点与没有定义的点. 对于这种情况，可以做一条绕开奇点的满足Cauchy定理要求的路径$l'$. 

![422CE0FB-F3FC-4699-B29D-AB51C3DA6F84](img/422CE0FB-F3FC-4699-B29D-AB51C3DA6F84.png)

途中的AB和A'B'路径正好反向，因此在两条线无线靠近，$l_1$无限小的情况下，AB和A'B'积分抵消. 而对于$l_1$而言，积分方向是顺时针的. 因此Cauchy定理可以写成
$$
\oint_{l'} = \oint_l - \sum_{i=1}^{n} \oint_{l_i}  = 0 \\
\oint_l f(z) \, \mathrm{d}z = \sum_{i=1}^{n} \oint_{l_i} f(z) \, \mathrm{d}z.
$$
这是很自然的结论. 但是要注意：**包围奇点的小路径的积分值需要根据定义计算**.



#### 2.3 不定积分

对于在区域上满足
$$
\oint_l f(z) \, \mathrm{d}z = 0
$$
的积分，如果选区不闭合的一段曲线，那么上面的路积分显然是不与路径有关的. 因此可以定义
$$
F(z) - F(z_0) = \int_{z_0}^{z} f(z) \, \mathrm{d}z.
$$
而且，通过施用中值定理，可以轻松证明$F'(z) = f(z)$.



##### 例子

**Ex.** 计算积分
$$
I = \int_a^b z^n \mathrm{d}z.
$$
其中n是整数.

解：

如果$n\neq -1$，那么
$$
I = \frac{1}{n+1} (b^{n+1} - a^{n+1}).
$$

如果$n = -1$，那么原函数是$\ln z$，故
$$
I = \ln |b| - \ln |a| + i(\mathrm{Arg}\,b - \mathrm{Arg}\,a)
$$

**注意，积分值的虚部与旋转方向和旋转圈数有关！**



#### 2.4 柯西公式

##### 正常情形

Cauchy公式建立在一个重要积分上：$l$是包含$a$的一个闭合回路，则
$$
\oint_l \frac{1}{z-a} \mathrm{d} z = 2 \pi i
$$
这是因为积分路径与积分值无关，所以取$l$为一绕$a$的小圆，则$z - a = \rho e^{i\phi}$，
$$
\begin{align}
\oint_l \frac{1}{z-a} \mathrm{d} z  & =  \oint_l {\rho}^{-1} e^{-i\phi} \mathrm{d} (\rho e^{i\phi}) \\
& = \oint_l {\rho}^{-1} e^{-i\phi} \cdot i \rho e^{i\phi} \mathrm{d} \rho \\
& = 2 \pi i.
\end{align}
$$
若考虑上式的变形$\oint_l \frac{f(z)}{z-a} \mathrm{d} z$，现在断言
$$
f(a) = \frac{1}{2 \pi i} \oint_l \frac{f(z)}{z-a} \mathrm{d} z
$$
证明如下：
$$
f(a) = \frac{1}{2 \pi i}\oint_l \frac{f(a)}{z-a} \mathrm{d} z
$$
考虑
$$
\begin{align}
\left| \frac{1}{2 \pi i} \oint_l \frac{f(z) - f(a)}{z-a} \mathrm{d} z \right| & \leq \max_{l} \left| \frac{f(z) - f(a)}{z-a} \right|\cdot |2 \pi \rho| \\
& \leq \max_{l}  \frac{| f(z) - f(a)|}{\rho} \cdot 2 \pi \rho
\end{align}
$$
由于$f(z)$是解析函数，因此在$\lim_{z \to a}$的情形下有$f(z) - f(a) \to 0$. 因此
$$
f(a) = \frac{1}{2 \pi i} \oint_l \frac{f(z)}{z-a} \mathrm{d} z.
$$
如果$f(z)$不满足在回路包围的区域上解析，可根据之前的方法，挖去奇点，对复连通域的边界 $l'$ 积分. **在全部积分路径以逆时针作为正方向的情况下**，柯西公式如下：
$$
\begin{align}
f(a) &= \frac{1}{2 \pi i} \oint_{l'} \frac{f(z)}{z-a} \mathrm{d} z \\
&= \frac{1}{2 \pi i} \oint_{l} \frac{f(z)}{z-a} \mathrm{d} z - \sum_{i=1}^{n} \frac{1}{2 \pi i} \oint_{l_i} \frac{f(z)}{z-a} \mathrm{d} z.
\end{align}
$$

##### a趋向于无穷远的情形

如果$|a| \to \infty$，乍一看不出在$l$包围的区域$S$内，但此时如果倒转回路方向，倒转过的回路则实际上相当于包围了$S$以外的全部区域. 因此，做一个很大的圆$C$，按照上式：
$$
f(a) = - \frac{1}{2 \pi i} \oint_l \frac{f(z)}{z-a} \mathrm{d} z + \frac{1}{2 \pi i} \oint_{C} \frac{f(z)}{z-a} \mathrm{d} z.
$$

在后一项中取C的半径趋向无穷大，如果存在
$$
\lim_{|z| \to \infty} f(z) = f(\infty),
$$
有
$$
f(a) = - \frac{1}{2 \pi i} \oint_l \frac{f(z)}{z-a} \mathrm{d} z + f(\infty).
$$
特别地，当$f(\infty) = 0$时，
$$
f(a) = - \frac{1}{2 \pi i} \oint_l \frac{f(z)}{z-a} \mathrm{d} z.
$$
**注意：上式的a不包含在l内，因此前面有一个负号.**



##### 柯西微分公式

Cauchy积分公式的一个重要推论是解析函数任意阶可导. 因为奇点不在积分路径上，因此可以用积分号下取微分法：
$$
f'(a) = \frac{1}{2 \pi i} \oint_l \frac{f(z)}{(z-a)^2} \mathrm{d} z. \\
f^{(n)}(a) = \frac{n!}{2 \pi i} \oint_l \frac{f(z)}{(z-a)^{n+1}} \mathrm{d} z.
$$

##### 例子

**Ex1.** 计算积分，其中C为不经过0和1的正向曲线：
$$
I =\frac{1}{2 \pi i} \oint_C \frac{e^z}{z(1-z)^3} \mathrm{d} z.
$$
**解：**

分母上有两个奇点，分别为0和1. 因此讨论路径是否包含0和1十分有必要. 

**Case 1.** 若路径既不包含0，也不包含1，那么由Cauchy定理直接得积分值为0.
**Case 2.** 如果积分包含0，不含1，那么实际上相当于
$$
I_1 =\frac{1}{2 \pi i} \oint_C \frac{e^z/(1-z)^3}{z} \mathrm{d} z = e^z/(1-z)^3 |_{z=0} = 1.
$$
**Case3.** 如果积分包含1，不含0，那么实际上相当于
$$
I_2 =-\frac{1}{2!} \cdot \frac{2!}{2 \pi i} \oint_C \frac{e^z/z}{(z-1)^3} \mathrm{d} z = -\frac{1}{2!} \cdot \left. \left(e^z/z\right)'' \right|_{z=1} = -\frac{e}{2}.
$$
**Case4.** 如果0和1都包含，那么
$$
I_3 = I_1+I_2 = 1-\frac{e}{2}.
$$
