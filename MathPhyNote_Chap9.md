## 数学物理方法 总结

[TOC]



### Chap 9 二阶常微分方程级数解法 本征值问题

上一章中，我们讨论了一维情况下几种常见物理方程的分离变量解法. 这些方法也能应用到三维情况中，只需要分离出x,y,z三个方向的方程
$$
u = u(\mathbf{r}, t) = X(x)Y(y)Z(z)T(t),
$$

然后依次用x,y,z三个方向的独立的边界条件，比如
$$
\begin{cases}
u(0,y,z) = u(x_0,y,z) = 0,  \implies X(0) = X(x_0) = 0 \\
u(x,0,z) = u(x,y_0,z) = 0,  \implies Y(0) = Y(y_0) = 0 \\
u(x,y,0) = u(x,y,z_0) = 0,  \implies Z(0) = Z(z_0) = 0
\end{cases}
$$

这样，我们就能分别求解关于 $x,y,z$ 的方程，求出关于 $x,y,z$ 方向的本征函数，并用它们组合出一个解. 问题在于，这种做法在数学上是否严谨可靠，我们先前并没有讨论.

除此之外，边界条件当然可以取其他形式，按照之前的套路，必须能化为分别针对 $X,Y,Z$ 的形式，否则没办法解出本征函数. 这就意味着，边界条件必须是在一个“方盒子”的面上. 对于其他的复杂边界的形式，依然不好处理. 不过，如果边界条件拥有良好的对称性，比如轴对称、中心对称，那么通过坐标变换的方式把方程转化到极坐标或者球坐标下，我们也能够把边界条件写成只针对单个分离出来的函数的形式.

这个Chapter将分别处理这两个问题. 

#### Sturm–Liouville 本征值问题

到目前为止，我们求解偏微分方程的套路是：先分离变量，把偏微分方程化为常微分方程；解出本征函数族；线性组合本征函数族，使得我们的解满足初始条件.

这么做是有前提的：首先要证明本征函数两两（带权）正交，然后本征函数族完备（线性组合就能表示函数空间里的任何一个函数）. Sturm–Liouville定理告诉我们这些事情都是对的. 

**Sturm–Liouville 定理**：对于形如
$$
\frac{\mathrm{d}}{\mathrm{d} x}\left[ k(x) \frac{\mathrm{d} y}{\mathrm{d} x} \right] - q(x)y + \lambda \rho(x) y = 0
$$
的方程，其中 $k(x), q(x), \rho(x)$ 均取非负值 ，在一、二、三类边界条件
$$
\alpha_1 y(a) +  \alpha_2 y'(a) = 0, \\
\beta_1 y(b) +  \beta_2 y'(b) = 0 \\
$$
或者自然边界条件下，有：

1.  如果 $k, k' ,q$ 连续或者最多以 $x=a,b$ 为一阶极点，则存在无限个本征值 $\lambda_k$ 以及无限多本征函数 $y_k(x)$.

2.  所有本征值 $\lambda_k > 0$.

3.  不同本征值的本征函数带权正交

$$
\int_{a}^{b} \rho(x)y_n(x)y_m(x) \mathrm{d}x = 0.
$$
4.	本征函数族完备：只要 $f(x)$ 具有连续一阶导数和分段连续二阶导数，且满足本征函数族满足的边界条件，就可以展开为
$$
f(x) = \sum_{k=0}^{+\infty} f_n y_n(x).
$$

实际上，一般形式的二阶常微分方程都可以化为Sturm–Liouville形式，
$$
\frac{\mathrm{d}}{\mathrm{d} x}\left[ k(x) \frac{\mathrm{d} y}{\mathrm{d} x} \right] - q(x)y + \lambda \rho(x) y = 0 \\
\iff y'' + \frac{k'(x)}{k(x)} y' - \frac{q(x)}{k(x)}y + \lambda \frac{\rho(x)}{k(x)}y = 0
$$
对于一般形式的二阶常微分方程
$$
y'' + a(x)y' + b(x)y + \lambda c(x) y = 0,
$$
只需要解出k，
$$
\frac{k'(x)}{k(x)} = a(x). \\
\implies k(x) = \exp \left( \int a(x) \mathrm{d}x \right).
$$

则该二阶常微分方程可以写为
$$
\frac{\mathrm{d}}{\mathrm{d} x}\left[ k(x) \frac{\mathrm{d} y}{\mathrm{d} x} \right] - q(x)y + \lambda \rho(x) y = 0,
$$

其中
$$
q(x) = -b(x)k(x) = -b(x)\exp \left( \int a(x) \mathrm{d}x \right). \\
\rho(x) = c(x)k(x) = c(x) \exp \left( \int a(x) \mathrm{d}x \right).
$$

#### 不同坐标系下的Laplace算子的展开

先讨论如何把直角坐标下的方程写到球坐标和柱坐标下. 我们上一章研究的偏微分方程的一般形式为
$$
u_{tt} - a^2 \nabla^2 u = 0, \\
u_t - a^2 \nabla^2 u = 0, \\
\nabla^2 u = 0.
$$

其中，对空间的偏导数都是以 $\nabla^2u$ 的形式出现的. 首先要做的是，在不同坐标系下展开Laplace算子 $\nabla^2$.

##### 球坐标

直角坐标下
$$
\mathbf{r} = x \hat{\mathbf{x}} + y \hat{\mathbf{y}} + z \hat{\mathbf{z}},
$$

球坐标与直角坐标的转换关系为
$$
\begin{cases}
x = r \sin\theta \cos \phi, \\
y = r \sin\theta \sin \phi, \\
z = r \cos \theta.
\end{cases}
$$

三个方向矢量之间的转换关系可以通过几何方式，得到，也可以通过代数方式，计算
$$
\hat{\mathbf{r}} = \frac{ \frac{\partial \mathbf{r}}{\partial r} }{ \left| \frac{\partial \mathbf{r}}{\partial r} \right| }
$$
得到：

$$
\begin{cases}
\hat{\mathbf{r}} = 
\hat{\mathbf{x}} \sin \theta \cos \phi + \hat{\mathbf{y}} \sin \theta \sin \phi + \hat{\mathbf{z}} \cos \theta = \hat{\mathbf{r}}(\theta, \phi), \\
\hat{\mathbf{\theta}} =
\hat{\mathbf{x}} \cos \theta \cos \phi + \hat{\mathbf{y}} \cos \theta \sin \phi - \hat{\mathbf{z}} \sin \theta = \hat{\mathbf{\theta}}(\theta, \phi),\\
\hat{\mathbf{\phi}} =  - \hat{\mathbf{x}} \sin \phi + \hat{\mathbf{y} \cos \phi} = \hat{\mathbf{\phi}}(\phi).
\end{cases}
$$

则
$$
\begin{align}
\nabla &= \hat{\mathbf{x}} \frac{\partial }{\partial x} + \hat{\mathbf{y}} \frac{\partial }{\partial y} + \hat{\mathbf{z}} \frac{\partial }{\partial z}, \\
&= \hat{\mathbf{r}} (\hat{\mathbf{r}} \cdot \nabla) + \hat{\mathbf{\theta}} (\hat{\mathbf{\theta}} \cdot \nabla) + \hat{\mathbf{\phi}} (\hat{\mathbf{\phi}} \cdot \nabla) \\
&= \hat{\mathbf{r}} \left( \sin \theta \cos \phi \frac{\partial}{\partial x} + \sin \theta \sin \phi \frac{\partial}{\partial y} + \cos \theta \frac{\partial}{\partial z} \right) \\ 
&+  \hat{\mathbf{\theta}} \left( \cos \theta \cos \phi \frac{\partial}{\partial x} + \cos \theta \sin \phi \frac{\partial}{\partial y} + \cos \theta \frac{\partial}{\partial z} \right)\\
&+ \hat{\mathbf{\phi}} \left( -\sin \phi \frac{\partial}{\partial x} + \cos \phi \frac{\partial}{\partial y} \right) \\
&= \hat{\mathbf{r}} \frac{\partial}{\partial r} + \hat{\mathbf{\theta}} \frac{1}{r}\frac{\partial}{\partial \theta} +  \hat{\mathbf{\phi}} \frac{1}{r\sin\theta} \frac{\partial}{\partial \phi}.

\end{align}
$$

$$
\begin{align}
\nabla^2  &=  \hat{\mathbf{r}} \frac{\partial}{\partial r} \left(  \hat{\mathbf{r}} \frac{\partial}{\partial r} + \hat{\mathbf{\theta}} \frac{1}{r}\frac{\partial}{\partial \theta} +  \hat{\mathbf{\phi}} \frac{1}{r\sin\theta} \frac{\partial}{\partial \phi}\right)  \\
&+ \hat{\mathbf{\theta}} \frac{1}{r}\frac{\partial}{\partial \theta} \left(  \hat{\mathbf{r}} \frac{\partial}{\partial r} + \hat{\mathbf{\theta}} \frac{1}{r}\frac{\partial}{\partial \theta} +  \hat{\mathbf{\phi}} \frac{1}{r\sin\theta} \frac{\partial}{\partial \phi}\right)\\
&+  \hat{\mathbf{\phi}} \frac{1}{r\sin\theta} \frac{\partial}{\partial \phi} \left(  \hat{\mathbf{r}} \frac{\partial}{\partial r} + \hat{\mathbf{\theta}} \frac{1}{r}\frac{\partial}{\partial \theta} +  \hat{\mathbf{\phi}} \frac{1}{r\sin\theta} \frac{\partial}{\partial \phi}\right).
\end{align}
$$

代入
$$
\frac{\partial \hat{\mathbf{r}}}{\partial r} = \frac{\partial \hat{\mathbf{\theta}}}{\partial r} = \frac{\partial \hat{\mathbf{\phi}}}{\partial r} = 0,\\
\frac{\partial \hat{\mathbf{r}}}{\partial \theta} = \hat{\mathbf{\theta}} , \frac{\partial \hat{\mathbf{\theta}}}{\partial \theta} = -\hat{\mathbf{r}}, \frac{\partial \hat{\mathbf{\phi}}}{\partial \theta} = 0.\\
\frac{\partial \hat{\mathbf{r}}}{\partial \phi} = \hat{\mathbf{\phi}} \sin \theta, \frac{\partial \hat{\mathbf{\theta}}}{\partial \phi} = -\hat{\mathbf{\phi}} \cos \theta ,
\frac{\partial \hat{\mathbf{\phi}}}{\partial \phi} = -\hat{\mathbf{r}} \sin\theta -\hat{\mathbf{\theta}} \cos \theta.
$$
经过约化（大量项直接得0），有
$$
\nabla^2 u = \frac{1}{r^2}\frac{\partial }{\partial r} \left(r^2 \frac{\partial u}{\partial r} \right) 
+  \frac{1}{r^2 \sin \theta}\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial u}{\partial \theta}\right)
+  \frac{1}{r^2 \sin^2 \theta}\frac{\partial^2 u}{\partial \phi^2}.
$$

##### 柱坐标
处理方式同上. 转换关系为
$$
\begin{cases}
x = r \cos \theta,\\
y = r \sin\theta, \\
z = z.
\end{cases}
$$
有
$$
\nabla^2u  = \frac{1}{r} \frac{\partial}{\partial r}\left( r  \frac{\partial u}{\partial r} \right) + \frac{1}{r^2}\frac{\partial^2 u}{ \partial \theta^2} + \frac{\partial^2 u}{ \partial z^2}.
$$


#### 几种特殊常微分方程的导出

因为Laplace算子在不同坐标系下展开的形式不一样，因此分离变量后得到的常微分方程也各不相同. 、

注：这个Section讨论的只是怎么样形式上导出这些方程，给之后的“级数求解”寻找一些“靶子”. 配合上边界条件的详细讨论它们的求解过程分别在Chap 10 和 Chap 11.

##### Laplace方程

对于**球坐标**下的Laplace方程
$$
\nabla^2 u = 0.
$$

取 $u = R(r)Y(\theta, \phi)$ ，有
$$
\frac{1}{R} \frac{\partial }{\partial r} \left(r^2 \frac{\partial R}{\partial r} \right) 
= -  \frac{1}{Y \sin \theta}\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial Y}{\partial \theta}\right)
-  \frac{1}{Y \sin^2 \theta}\frac{\partial^2 Y}{\partial \phi^2}
= \mu.
$$
分离出径向方程和**球函数方程**
$$
\frac{\partial }{\partial r} \left(r^2 \frac{\partial R}{\partial r} \right)  - \mu R = 0, \\
\frac{1}{\sin \theta}\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial Y}{\partial \theta}\right)
+  \frac{1}{\sin^2 \theta}\frac{\partial^2 Y}{\partial \phi^2} + \mu Y = 0.
$$
径向方程是Euler方程. 记 $\mu = l(l+1)$ ，解为
$$
R(r) = Cr^l + Dr^{-(l+1)}.
$$
对于球函数方程，进一步分离变量 $Y = \Theta(\theta) \Phi(\phi)$ ，
$$
\frac{\sin \theta}{\Theta}\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial \Theta}{\partial \theta}\right)
+    l(l+1) \sin^2\theta = - \frac{1}{\Phi} \frac{\partial^2 \Phi}{\partial \phi^2} = \lambda. \\
\implies 
\begin{cases}
\frac{\partial^2 \Phi}{\partial \phi^2} + \lambda \Phi = 0, \\
\sin \theta\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial \Theta}{\partial \theta}\right)
+  (  l(l+1) \sin^2\theta - \lambda)\Theta = 0.
\end{cases}
$$

关于 $\Phi$ 方向的方程是一个普通的二阶线性常微分方程，从球坐标的几何含义上看，有周期性边界条件
$$
\Phi(\phi) = \Phi(\phi + 2\pi)
$$

因此解得
$$
\Phi(\phi) = A \cos m\phi + B \sin m\phi, \lambda = m^2, m = 0,1,2,\cdots.
$$
而关于 $\Theta$ 的方程，进行变量代换 $\cos \theta = x, x\in [-1,1]$ ，记 $\Theta(\theta) = y(x)$ ，
$$
\frac{\mathrm{d}}{\mathrm{d} x} \left[ (1-x^2) \frac{\mathrm{d}y}{\mathrm{d} x} \right] + \left[  l(l+1) - \frac{m^2}{1-x^2} \right] y = 0.
$$
该方程称为**连带Legendre方程**.

当 $m = 0$ ，该方程退化为**Legendre方程**
$$
\frac{\mathrm{d}}{\mathrm{d} x} \left[ (1-x^2) \frac{\mathrm{d}y}{\mathrm{d} x} \right] + \mu y = 0 \\ 
\iff  (1-x^2) \frac{\mathrm{d}^2y}{\mathrm{d} x^2} -2x \frac{\mathrm{d}y}{\mathrm{d} x}  + \mu y = 0, \quad x\in[-1,1].
$$
对于**柱坐标**下的Laplace方程
$$
\frac{1}{r} \frac{\partial}{\partial r}\left( r  \frac{\partial u}{\partial r} \right) + \frac{1}{r^2}\frac{\partial^2 u}{ \partial \phi^2} + \frac{\partial^2 u}{ \partial z^2} = 0.
$$

分离变量 $u = R(r) \Phi(\phi) Z(Z)$ ，得到
$$
\frac{r}{R}\frac{\partial}{\partial r}\left( r  \frac{\partial R}{\partial r} \right) + 
\frac{r^2}{Z} \frac{\partial^2 Z}{ \partial z^2} = - \frac{1}{\Phi}\frac{\partial^2 \Phi}{ \partial \phi^2} = m^2.
$$
进一步分离变量
$$
\frac{1}{rR}\frac{\mathrm{\partial}}{\partial r}\left( r  \frac{\partial R}{\partial r} \right)  - \frac{m^2}{r^2} = -\frac{1}{Z}\frac{\partial^2 Z}{ \partial z^2} = -\mu. \\
\implies 
\begin{cases}
\Phi'' + m^2 \Phi = 0, \\
Z'' - \mu Z = 0, \\
R'' + \frac{1}{r}R' + \left( \mu - \frac{m^2}{r^2} \right) R = 0.
\end{cases}
$$

对于不同的 $\mu$ 的取值，如果有 $\mu < 0$. 令 $x = \sqrt{-\mu}r$ ，$R$ 方向方程化为**m阶虚宗量Bessel方程**
$$
x^2 R'' + xR' - (x^2 + m^2)R = 0.
$$

如果有 $\mu > 0$ ，令 $x = \sqrt{\mu}r$ ，$R$ 方向方程化为**m阶Bessel方程**
$$
x^2 R'' + xR' + (x^2 - m^2)R = 0.
$$

如果有 $\mu = 0$ ，方程退化为Euler方程.

##### Helmholtz方程

将波动方程中的时间项分解出去，得到
$$
\nabla^2v + k^2v = 0, \\
T'' + k^2a^2T = 0.
$$

在球坐标系中，
$$
\frac{1}{r^2}\frac{\partial }{\partial r} \left(r^2 \frac{\partial v}{\partial r} \right) 
+  \frac{1}{r^2 \sin \theta}\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial v}{\partial \theta}\right)
+  \frac{1}{r^2 \sin^2 \theta}\frac{\partial^2 v}{\partial \phi^2} + k^2 v= 0.
$$
分离变量，取 $u = R(r)Y(\theta, \phi)$ ，有
$$
\frac{1}{R} \frac{\partial }{\partial r} \left(r^2 \frac{\partial R}{\partial r} \right)  + k^2 r^2
= -  \frac{1}{Y \sin \theta}\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial Y}{\partial \theta}\right)
-  \frac{1}{Y \sin^2 \theta}\frac{\partial^2 Y}{\partial \phi^2}
= l(l+1).
$$
分离出角度相关的方程没有改变，依然是球函数方程. 径向方程多出一项：
$$
\frac{\partial }{\partial r} \left(r^2 \frac{\partial R}{\partial r} \right)  + [k^2r^2-l(l+1) ]R = 0, \\
\iff r^2R'' + 2rR' + [k^2r^2-l(l+1) ]R = 0.
$$
令 $x = kr, R(r) = \sqrt{\frac{\pi}{2x}}y(x)$ ，经过一番代数运算，上式化为**半奇数阶Bessel方程**：
$$
x^2y'' + xy' + [x^2-(l+1/2)^2]y = 0
$$

同样，对于柱坐标，径向方程化为
$$
R'' + \frac{1}{r}R' + \left(k^2+ \mu - \frac{m^2}{r^2} \right) R = 0.
$$
令 $x = \sqrt{k^2 + \mu} r$ ，方程再次化为 **m阶Bessel方程**：
$$
x^2 R'' + xR' + (x^2 - m^2)R = 0.
$$


#### 常点邻域上的级数解法

对一个二阶常微分方程
$$
\frac{\mathrm{d}^2 w}{\mathrm{d} z^2} + p(z) \frac{\mathrm{d}w}{\mathrm{d} z} + q(z)w = 0.
$$

其中 $p(z), q(z)$ 都是复变函数.



**有这么一个定理（Fuchs' theorem）：**

如果  $p(z), q(z)$ 在圆 $|z - z_0| < R$ 内是单值解析的，则方程
$$
\frac{\mathrm{d}^2 w}{\mathrm{d} z^2} + p(z) \frac{\mathrm{d}w}{\mathrm{d} z} + q(z)w = 0
$$
在这圆内有唯一的一个单值解析的 $w(z)$ 是方程的解，满足初始条件 
$$
w(z_0) = c_0, w'(z_0) = c_1,
$$
其中 $c_0, c_1$ 是任意常数.

既然解存在，且解析性质良好，可以展开为Taylor级数
$$
w(z) = \sum_{k=0}^{+\infty}a_k(z-z_0)^k,
$$

佐以
$$
p(z) = \sum_{k=0}^{+\infty}b_k(z-z_0)^k,
q(z) = \sum_{k=0}^{+\infty}c_k(z-z_0)^k.
$$

将它们代回方程，合并同幂项即有
$$
\sum_{k=0}^{+\infty} \left[ (k+2)(k+1)a_{k+1} + \sum_{m=0}^{k}(k-m+1)a_{k-m+1} + \sum_{n=0}^k c_n a_{k-a}\right](z-z_0)^k = 0
$$

显然，每一个 $(z-z_0)^k$ 前的系数必须等于0. 通过此法可以定出所有待求的 $a_k$ .

##### 以解Legendre方程为例

Legendre方程：
$$
(1-x^2) \frac{\mathrm{d}^2y}{\mathrm{d} x^2} -2x \frac{\mathrm{d}y}{\mathrm{d} x}  + \mu y = 0,  \quad x \in [-1,1],\\
p(x) = \frac{-2x}{1-x^2}, \quad q(x)=\frac{\mu}{1-x^2}.
$$

可见 $x=0$ 是方程的常点. 可在该点进行Taylor展开. 而当 $x = \pm 1$ 时 $p,q$ 是奇点. 所以我们的解将仅局限于 $|x-0| = 1$ 的范围内. 我们自然不关心 $|x| > 1$ 的情形，不过对 $x = \pm 1$ 需要细致讨论.

设
$$
y(x) = \sum_{k=0}^{\infty}a_k x^k,
$$

代入Legendre方程：
$$
(1-x^2) \sum_{k=2}^{\infty} a_k k(k-1) x^{k-2} - 2x \sum_{k=1}^{\infty} a_k k x^{k-1} + \mu \sum_{k=0}^{\infty} a_k x^k = 0 \\
\implies  \sum_{k=0}^{\infty} a_{k+2} (k+2)(k+1) x^{k} - \sum_{k=0}^{\infty} a_k k(k-1) x^{k} - 2 \sum_{k=0}^{\infty} a_k k x^{k} + \mu \sum_{k=0}^{\infty} a_k x^k = 0 \\
\implies \sum_{k=0}^{\infty} \left[ a_{k+2} (k+2)(k+1)  - a_k k(k-1)  - 2 a_k k + \mu a_k \right]x^k  = 0 \\
\implies a_{k+2} = \frac{k(k+1) - \mu}{(k+2)(k+1)}a_k, \quad k=0,1,2,\cdots.
$$

因此Legendre方程的通解可以写成
$$
y(x) = a_0 y_0(x) + a_1 y_1(x). \\
y_0(x) = \sum_{k=0}^{\infty} a_{2k} x^{2k} = 1 + \frac{-\mu}{2} x^2 + \frac{-\mu}{2} \frac{(2\cdot 3-\mu)}{3 \cdot 4} x^4 + \cdots, \\
y_1(x) = \sum_{k=0}^{\infty} a_{2k+1} x^{2k+1} = x + \frac{1\cdot2 -\mu}{2\cdot 3} x^3 + \frac{(1\cdot2 -\mu)}{2\cdot 3} \frac{(3\cdot 4-\mu)}{4 \cdot 5} x^5 + \cdots.
$$

讨论这两个解在 $|x| < 1$ 范围内是否收敛：由达朗贝尔原理，收敛半径
$$
R = \lim_{k\to\infty} \left| \frac{a_k}{a_k+2} \right| = 1.
$$

在 $x = \pm 1$ 处需要特别讨论. 形式上看，
$$
a_{2k} = \frac{(1\cdot2 -\mu)(3\cdot4 -\mu)\cdots((2k-2)(2k-1) -\mu)}{(2k)!}a_0,
$$

当 $\mu \neq l(l+1)$ 时，该级数每一项都不为0，分子上的增长速度最快的项 $\sim (2k-1)$ ，剩下的项因为 $\mu$ 前的负号一定程度相互抵消，因此每一项 $\sim 1/{(2k)}$ 级数是不收敛的. 数学上的证明可以通过高斯判别法完成. 这是不行的，因为 $x = \pm 1$ 对应的是 $\cos \theta$ 取 $\theta = 0, \pi$ 的情况. 由自然边界条件，此处 $|u| < +\infty$ ，因此必须有 $|y| < \infty$ .

所以，仅当 $\mu = l(l+1)$ ，$y_0, y_1$ 从无穷级数退化为多项式，收敛性满足要求. 

若 $l = 2n$ ，则 $y_0$ 退化为多项式，$a_{2n+2} = 0$ 最高次幂为 $x^{2n}$ . 而 $y_1$ 依然发散. 此时方程的解为 $y = a_0 y_0(x).$
若 $l = 2n+1$ ，则 $y_1$ 退化为多项式，$a_{2n+3} = 0$ 最高次幂为 $x^{2n+1}$ . 而 $y_0$ 依然发散. 此时方程的解为 $y = a_1 y_1(x)$.

选取适当 $a_0, a_1$ 取得方程的一个特解，使得最高次幂系数满足
$$
a_l = \frac{(2l)!}{2^l(l!)^2}.
$$

这意味着
$$
a_{l-2} = \frac{l(l-1)}{(l-2)(l-1) - l(l+1)}a_l = \frac{l(l-1)}{-2(2l-1)}a_l =  \frac{l(l-1)}{-2(2l-1)} \frac{(2l)!}{2^l(l!)^2} = -\frac{(2l-2)!}{2^l(l-1)!(l-2)!}. \\
\vdots \\
a_{l-2k} = (-1)^k \frac{(2l-2k)!}{2^l(l-k)!(l-2k)!}.
$$

这样得到Legendre多项式，
$$
P_l(x) = \sum_{k=0}^{\lfloor l/2 \rfloor}(-1)^k \frac{(2l-2k)!}{2^l(l-k)!(l-2k)!} x^{l-2k}.
$$

Legendre多项式的更多性质将在下一章给出.

**Note:** 对比我们得到Legendre方程本征值的方法和在Chap 8中我们得到二阶齐次线性方程本征值的差别，可以看出，
- 二阶齐次线性方程本征值由边界处的第一、二、三类边界条件定出的；

- Legendre方程的本征值仅仅是由边界 $x = \pm 1$ 处不发散的自然边界条件给出. 这意味着：具体物理问题中，Legendre方程的本征值 $l(l+1)$ **并不需要额外的关于 $\theta$ 的边界条件**. 任何边界条件下，其本征值总是 $l(l+1)$ .

  ​

#### 正则奇点邻域上的级数解法

对于
$$
\frac{\mathrm{d}^2 w}{\mathrm{d} z^2} + p(z) \frac{\mathrm{d}w}{\mathrm{d} z} + q(z)w = 0
$$

还是由Fuchs' theorem：如果 $z_0$ 是  $p(z), q(z)$ 的奇点，则在环形解析邻域 $ 0 < |z - z_0| < R$ 内，方程有两个线性无关解，可以写成
$$
w_1(z) = (z-z_0)^{s_1} \sum_{k=-\infty}^{\infty} a_k (z-z_0)^k,\\
w_1(z) = (z-z_0)^{s_2} \sum_{k=-\infty}^{\infty} b_k (z-z_0)^k,
$$

对于某些情况，这样形式的两个解可能不满足互相线性无关，则需要使用下式产生线性无关的解：
$$
w_2(z) = A w_1 \ln(z-z_0) + (z-z_0)^{s_2} \sum_{k=-\infty}^{\infty} c_k (z-z_0)^k.
$$

然而实际情况是，对于任意的p、q，我们只能得到无限联立的代数方程，无法得到系数的递推公式. 只有在 $z_0$ 至多是 $p(z)$ 的一阶极点、 $q(z)$ 的二阶极点的情况下，才能求出两个 $s_1, s_2$ ，使得方程的解只有有限个负幂项. 设
$$
w(z) = \sum_{k=0}^{\infty} a_k z^{k+s},\\
p(z) = \sum_{l=0}^{+\infty} p_{l-m} z^{l-m}, \\
q(z) = \sum_{l=0}^{+\infty} q_{l-n} z^{l-n},
$$

类似之前的步骤，代入方程得到
$$
\sum_{k=0}^{+\infty} a_k(k+s)(k+s-1)z^{k+s-2} 
+ \left( \sum_{k=0}^{+\infty} p_{k-m}z^{k-m} \right) \sum_{k=0}^{+\infty} a_k(k+s)z^{k+s-1} + \left( \sum_{k=0}^{+\infty} q_{k-n}z^{k-n} \right) \sum_{k=0}^{\infty} a_k z^{k+s}= 0.
$$

在挑出这式子的三项中每项的最低幂次项，分别是
$$
a_0s(s-1)z^{s-2}, \quad p_{-m}a_{0}sz^{s-m-1}, \quad a_0q_{-n}z^{s-n}.
$$

如果 $z_0$ 至多是 $p(z)$ 的一阶极点、 $q(z)$ 的二阶极点，那么 $m=1$ ，$n=2$ ，这三项幂次相同，可以获得关于s的二次方程
$$
s(s-1) + s p_{-1} + q_{-2} = 0.
$$

如果p，q不满足上述条件，这三项幂次不同，将无法解出两个s，这意味着方程没有有限级数解，或没有两个线性独立的有限级数解. 

##### 以解Bessel方程为例

Bessel方程：
$$
x^2 R'' + xR' + (x^2 - \nu^2)R = 0. \\
p(x) = \frac{1}{x}, \quad q(x) = 1-\frac{\nu^2}{x^2}
$$

p在0处有一阶极点，q在0处有二阶极点，满足要求. 从上式解出s，
$$
s_1 = \nu, \quad s_2 = -\nu, \quad(\nu>0).
$$

我们先取 $s = \nu$ ，可以得到一个解
$$
y_1(x) = x^{\nu} \sum_{k=0}^{+\infty} a_k x^k, \quad y_2(x) = x^{-\nu} \sum_{k=0}^{+\infty} a_k x^k.
$$

代入方程，合并后有
$$
\sum_{k=0}\left[ (k+\nu)^2 - \nu^2 \right]a_k x^{k+\nu} + \sum_{k=2}a_{k-2}x^{k+\nu} = 0 \\
\implies 
\begin{cases}
[(1+\nu)^2 - \nu^2]a_1 = 0 ,\\
[(k+\nu)^2 - \nu^2]a_k + a_{k-2} = 0, \quad k\geq2.
\end{cases}
$$

得到所有奇数项系数为0，偶数项系数为
$$
a_{k+2} = - \frac{1}{(k + 2+\nu)^2 - \nu^2}a_k =- \frac{1}{(k + 2)(k+2+2\nu)}a_k , \\
a_2 = -\frac{1}{4\cdot 1(\nu+1)}a_0, \quad a_4 = - \frac{1}{4\cdot 2(\nu+2)}a_2, \quad a_6 = -\frac{1}{4 \cdot3(\nu+3)}  \cdots \\
\implies a_{2k} = (-1)^k \frac{1}{4^k \cdot k! (\nu+1)(\nu+2)\cdots(\nu+k)}a_0 \\
\, \\
y_1(x) = a_0x^\nu \sum_{k=0}^{+\infty}  (-1)^k \frac{1}{k! (\nu+1)(\nu+2)\cdots(\nu+k)} {\left(\frac{x}{2}\right)}^{2k}
$$
取 $a_0 = 1/(2^\nu \Gamma(\nu + 1))$，得到的特解记为**Bessel函数**
$$
J_\nu(x) = \sum_{k=0}^{+\infty}  (-1)^k \frac{1}{k! \Gamma(\nu+k+1)} {\left(\frac{x}{2}\right)}^{2k+\nu}.
$$

容易直接看出来Bessel函数在全复平面除零点外都是收敛的. 

我们现在试着得到第二个线性无关的解：先试着代入 $s = -\nu$ ，
$$
\begin{cases}
[(1-\nu)^2 - \nu^2]a_1 = 0 ,\\
[(k-\nu)^2 - \nu^2]a_k + a_{k-2} = 0, \quad k\geq2.
\end{cases}
$$

我们发现，第二式不能再直接把 $a_k$ 前的因子随便除过去了，如果 $\nu = m$ 是整数或者半整数，当 $k = 2m$ ，该式干脆就变成了 $a_{k-2} = 0$ ，这不仅会与已经给定的 $a_0$ 引发冲突，而且 $a_k$ 干脆就求不出来了.

事实上，不仅是对Bessel方程，可以证明，一般情况下，如果通过这种方法求出的 $s_1 - s_2 = h \in \mathbb{Z}$ ，那么都会面临着这种问题. 这个时候，就需要使用
$$
y_2(x) = A y_1 \ln x + x^{-m} \sum_{k=-\infty}^{\infty} c_k x^k.
$$

去生成第二个线性独立的解. 这个解与 $J_m$ 进行复杂的线性组合，得到Neumann函数，因此方程的解可以写成
$$
y = c_1 J_m(x) + c_2 N_m(x)
$$

当然，如果 $\nu$ 不是半整数，一切好说，解
$$
y = c_1 J_\nu(x) + c_2 J_{-\nu}(x).
$$
