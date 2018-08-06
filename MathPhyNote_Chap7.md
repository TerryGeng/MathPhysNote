---
typora-copy-images-to: ../数学物理方法 总结
---

## 数学物理方法 总结

[TOC]

### Chap7. 数学物理方程的导出  定解问题

对于一个物理问题，一方面得到描述各个物理量之间联系的**数学物理方程**（数学上称作**泛定方程**）是重要的；另一方面，明确问题在时间上的**初始条件**与在空间上的**边界条件**（合称为**定解条件**），也都是给出一个解所必须的。所谓**定解问题**，就是在给定的定解条件下，求解数学物理方程.

（我发现外国书上没有这么叫的）



#### 三类典型数学物理方程的导出

##### 双曲型方程 波动方程为代表

考虑均匀轻弦的微小振动：

![1B41CCBC-127B-444D-92F1-AEA379667FED](img/1B41CCBC-127B-444D-92F1-AEA379667FED.png)

因为张力很大，而弦很轻，因此弦本身的重量忽略不计. 记x为质点在弦中的位置，而u为质点在振动下的位移. 取其中一小段 $x, x + \mathrm{d}x$ 研究，对其施用牛顿第二定律：

纵向受力
$$
T_2 \sin \alpha_2 - T_1 \sin \alpha_1 = (\rho \mathrm{d}s) u_{tt}.
$$
横向受力（因为弦不横向移动）
$$
T_2\cos \alpha_2  = T_1  \cos \alpha_1.
$$
考虑到 $\alpha$ 很小：
$$
\sin \alpha_1 \approx \tan \alpha_1 = u_x |_x \\
\sin \alpha_2 \approx \tan \alpha_2 = u_x |_{x + \mathrm{d}x} \\
\cos \alpha_1 \approx
\cos \alpha_2 \approx 1\\
\mathrm{d}s \approx \mathrm{d}x.
$$

$$
T(u_x |_{x + \mathrm{d}x}  - u_x |_{x}) = (\rho\mathrm{d}x) u_{tt} \\
\implies  u_{tt} - \frac{T}{\rho} u_{xx} = 0.
$$

我们得到了一维弦振动的波动方程. 一般写作 $u_{tt} - a^2 u_{xx} = 0.$

在二、三维情况下，相同的推导可以得到 $u_{tt} - a^2 \nabla^2u = 0.$



**阻尼、外力驱动弦振动问题** 

如果弦本身还受到线性阻尼力$F(x,t) = -k \partial u / \partial t$  ，则方程改写为
$$
Tu_{xx} - ku_t = \rho u_{tt}. \\
$$

如果弦本身的振动还受到外力 $F(x, t)$ 驱动，则
$$
Tu_{xx} + F = \rho u_{tt}. \\
$$

##### 抛物型方程 扩散方程为代表

考虑三维空间中某物质的密度分布u，按照菲克定律有物质流
$$
\mathbf q = -D\nabla u.
$$
考虑无源的情况，代入连续性方程，
$$
u_{t} + \nabla (-D\nabla u) = 0.
$$
一般写作
$$
u_{t} - a^2 \nabla^2u = 0.
$$


##### 椭圆型方程 泊松方程为代表

考虑的是有源扩散的情况，有
$$
u_{t} - a^2 \nabla^2u = f(\mathbf r,t).
$$
如果系统最终能达到一个稳态，则最终满足
$$
a^2 \nabla^2u = -f(\mathbf r,t).
$$
此即泊松方程. 

如果是无源的情况，方程退化为拉普拉斯方程
$$
\nabla^2u =0.
$$

#### 定解条件

定解条件分为时间上的初始条件和空间上的边界条件.

##### 初始条件

如果方程中只出现对t的**一阶导数**，则只需要一个初始条件
$$
u|_{t=0} = f(x).
$$
如果方程中出现对t的**二阶导数**，那么需要两个初始条件
$$
u|_{t=0} = f(x). \\
\left. \frac{\partial u}{\partial t} \right|_{t=0} = g(x).
$$

##### 边界条件

分为三类，第一类和第二类是按照导数的阶数划分的，分别为

$$
u|_{x=a} = f(t) \\
\left. \frac{\partial u}{\partial x} \right|_{x=a} = g(t).
$$
第三类边界条件是第一类边界条件与第二类边界条件的线性叠加：
$$
(\left. u + H\frac{\partial u}{\partial x} )\right|_{t=0} = f(t).
$$

**Eg. 弦振动问题中的边界条件**
比较常见的边界条件是弦的一端或者两端固定. 这实际上是一个几何条件，可以轻松写出
$$
u(0, t) = 0.
$$

比较费劲的是所谓“端点自由振动”条件. 这个条件意味着端点可以上下自由振动而不改变其左右位置，不妨理解为端点上有个小环，小环套在一根光滑竖直杆上. 这个条件不是个几何条件而是个力学条件. 考虑到端点只是一个点，这个点的质量无限小，但是这个端点只有一端受到纵向的力. 如果这个纵向的力不为0，那么加速度会是无穷的——这是个不物理的结果. 事实上，为什么弦中间不会出现这种无穷的讨论，是因为中间的点受到两端的力，这两端的力相差是无穷小的.

没有纵向的力，意味着张力的方向水平，即弦在端点附近应该是平行于x轴的. 可以写成
$$
u_x(0, t) = 0.
$$

##### 衔接条件

如果研究的系统在不同的区域受不同的泛定方程支配，那么在区域间的衔接处，泛定方程失去意义. 但是，边界上的物理量往往保持一定的关联. 在衔接处描述这种关联的条件就叫做衔接条件.



#### 线性二阶偏微分方程的化简与分类

我们上面给出的方程都是二阶线性偏微分方程. 通过研究线性偏微分方程的分类，并讨论如何将一般形式的二阶线性偏微分方程化为某一类特殊的形式，那么只需要知道如何求解这些特殊形式的方程，就可以解决所有二阶线性偏微分方程.

二阶线性偏微分方程可以写成下面的形式：
$$
a_{11}u_{xx} + 2a_{12}u_{xy} + a_{22}u_{yy} + b_1u_x + b_2u_y + cu + f = 0.
$$
其中 $a_{11}, a_{12}, a_{22}, b_1,d b_2, c, f$ 都只是 $x, y$ 的函数.

考虑通过一定的代换，消去形如 $u_xx$ 与 $u_yy$ 的项. 为了达到这个目的，进行非奇异变数代换 $u(x,y) \implies u(\xi,\eta).$

$$
\begin{cases}
x = x(\xi, \eta), \\
y = y(\xi, \eta)
\end{cases}
\qquad \frac{\partial(\xi, \eta)}{\partial(x, y)} \neq 0
$$

这样，上式中的 $u_x,u_y, u_{xx}, u_{yy}, u_{xy}​$ 即可化成
$$
\begin{align}
u_x &= u_{\xi}\xi_x + u_{\eta} \eta_x \\
u_y &= u_{\xi}\xi_y + u_{\eta} \eta_y \\
u_{xx} &= u_{\xi\xi} \xi_x^2 + u_{\eta\eta} \eta_x^2 + 2\eta_x\xi_x u_{\xi\eta} + \xi_{xx}u_{\xi} + \eta_{xx}u_{\eta} \\
u_{yy} &= u_{\xi\xi} \xi_y^2 + u_{\eta\eta} \eta_y^2 + 2\eta_y\xi_y u_{\xi\eta} + \xi_{yy}u_{\xi} + \eta_{yy}u_{\eta} \\
u_{xy} &= u_{\xi\xi} \xi_x \xi_y + u_{\eta\eta} \eta_x \eta_y + u_{\xi\eta} (\xi_x \eta_y + \xi_y \eta_x) + u_{\xi} \xi_{xy} + u_{\eta} \eta_{xy}.
\end{align}
$$

代入上式，能够得到新的方程
$$
A_{11}u_{\xi\xi} + 2A_{12}u_{\xi\eta} + A_{22}u_{\eta\eta} + B_1u_{\xi} + B_2u_{\eta}+ Cu + F = 0. \\
\begin{cases}
A_{11} = a_{11} \xi_x^2 + 2a_{12}\xi_x\xi_y + a_{22}\xi_y^2, \\
A_{22} = a_{11} \eta_x^2 + 2a_{12}\eta_x\eta_y + a_{22}\eta_y^2, \\
A_{12} = a_{11}\eta_x\xi_x + a_{22}\eta_y\xi_y + a_{12} (\xi_x \eta_y + \xi_y \eta_x) \\
\qquad \qquad \qquad \qquad\vdots
\end{cases}
$$
采取令 $A_{11} = 0, A_{22} = 0$ 的方式求解使得 $u_{\xi\xi}, u_{\eta\eta}$ 消去的变换 $\xi, \eta$. 这两个方程形式完全一致，用 $z$ 去表示 $\xi, \eta$, 
$$
a_{11}(-\frac{z_x}{z_y})^2 + 2a_{12}(-\frac{z_x}{z_y}) + a_{22} = 0
$$

由此可解出 $-z_x/z_y$ 但是仅由两个偏导数的比值并不能唯一确定一个函数z，因此设函数 $y(x)$，有 $\mathrm{d}y/\mathrm{d}x = -z_x/z_y$. 则可以解该常微分方程得到函数y.

$$
\frac{\mathrm{d}y}{\mathrm{d}x} = -\frac{z_x}{z_y} = \frac{a_{12} \pm \sqrt{a_{12}^2 - a_{11}a_{22}}}{a_{11}}.
$$
容易验证 $z = y - y(x)$ 就是满足方程的z.

需要讨论根号下的正负问题.

**当 $a_{12}^2 - a_{11}a_{22} > 0$ 时**，进行变数代换
$$
\begin{cases}
\xi = \alpha + \beta, \\
\eta = \alpha - \beta
\end{cases}
\implies 
u_{\alpha\alpha} - u_{\beta\beta} = -\frac{1}{A_{12}}[(B_1+B_2)u_\alpha + (B_1-B_2) u_\beta + 2Cu+2F].
$$
得到了双曲型标准方程. 波动方程就是这个形式的.

**当 $a_{12}^2 - a_{11}a_{22} = 0$ 时**，上述方程只能给出一个z. 试令 $\xi = z(x,y)$, 将它与 $a_{12}^2 - a_{11}a_{22} = 0$ 代入$A_{11}, A_{12}$ 的表达式，惊奇地发现他们都等于0. 因此得到了方程
$$
u_{\eta\eta}  -\frac{1}{A_{22}}(B_1 u_\xi + B_2 u_\eta + Cu + F).
$$
得到了抛物线型方程的标准形式. 扩散方程就是这个形式.

**当 $a_{12}^2 - a_{11}a_{22} < 0$ 时**，得到的 $\xi$ 和 $\eta$ 是负的. 进行变数代换
$$
\begin{cases}
\xi = \alpha + i\beta, \\
\eta = \alpha - i\beta
\end{cases}
\implies 
u_{\alpha\alpha} - u_{\beta\beta} = -\frac{1}{A_{12}}[(B_1+B_2)u_\alpha + i(B_1-B_2) u_\beta + 2Cu+2F].
$$
得到了椭圆型方程的标准形式. 泊松方程就是这个形式.



#### 行波法求解波动方程：达朗贝尔公式

##### 一维波动方程的通解

对于极少数的方程，我们有希望先给出其通解，再用定解条件确定其待定函数. 这里给出的是波动方程的例子.

对于波动方程
$$
u_{tt} - a^2 u_{xx} = 0,
$$

从物理经验上很容易猜测其解应当有 $u = f(x + at), u = f(x - at)$ 的形式，也容易验证这是解的一种形式. 因此考虑变数代换
$$
\begin{cases}
\xi = x + at, \\
\eta = x - at
\end{cases}
$$

从而有
$$
\begin{align}
u_{x} &= u_{\xi} \xi_{x} + u_{\eta} \eta_{x} = u_{\xi} + u_{\eta} 
= \left( \frac{\partial}{\partial \xi} + \frac{\partial}{\partial \eta} \right)u, \\
u_{t} &= u_{\xi} \xi_{t} + u_{\eta} \eta_{t} = au_{\xi} - au_{\eta}
= \left( a\frac{\partial}{\partial \xi} - a\frac{\partial}{\partial \eta} \right)u\\
u_{xx} &= \left( \frac{\partial}{\partial \xi} + \frac{\partial}{\partial \eta} \right)^2 u, \\
u_{tt} &= a^2\left( \frac{\partial}{\partial \xi} - \frac{\partial}{\partial \eta} \right)^2 u.
\end{align}
$$

因此，原方程化为
$$
\frac{\partial^2 }{\partial \xi \partial \eta} u = 0. \implies \frac{\partial}{\partial \xi} \left(  \frac{\partial }{\partial \eta} u\right) = 0.
$$
这意味着函数 $\partial u/ \partial \eta$ 与 $\xi$ 无关.

$$
\frac{\partial }{\partial \eta} u = h(\eta).
$$

对上式积分，
$$
\begin{align}
u &= \int h(\eta) \,\mathrm{d} \eta + f(\xi) = f(\xi) + g(\eta) \\
 &= f(x+at) + g(x-at).
\end{align}
$$
这与我们猜测的一致. 不过，通过上面的推导，我们确定了方程的所有解都可以写成这种形式，即是方程的**通解**. 这是光凭猜测无法证明的.



##### 确定通解中的任意常数

我们的通解是两个任意函数相加的形式. 但是在实际场合，我们需要的波形函数总需要满足一定定解条件：其在 $t=0$ 时的形态与在边界处的情况，即初始条件和边界条件. 其实，求出通解对于绝大多数偏微分方程，已经是可遇不可求之事；而根据通解定出符合定解条件的任意函数，往往也很难（解得形式都需要以级数来表示）. 所以，此处只讨论一些简单的情况.

我们先考虑只有初始条件（即给定初始位移和初始速度），没有边界条件（无限长弦）的情形：
$$
u = u(x, t), \qquad
\begin{cases}
u(x, 0) = \phi(x), \\
u_t(x, 0) = \psi(x)
\end{cases}
$$

代入上述通解
$$
\begin{cases}
f(x) + g(x) = \phi(x), \\
af'(x) - ag'(x) = \psi(x).
\end{cases}
\implies
\begin{cases}
f(x) + g(x) = \phi(x), \\
f(x) - g(x) = \frac{1}{a} \int_{x_0}^{x} \psi(x) \mathrm{d}x.
\end{cases}
\\
\,
\\
\begin{align}
\implies u &= f(x+at) + g(x-at) \\
&= \frac{1}{2}[\phi(x+at) + \phi(x-at)] + \frac{1}{2a}\int_{x-at}^{x+at} \psi(x) \mathrm{d}x.
\end{align}
$$

此即给定初始条件下波动方程的一个特解.

如果考虑边界条件，情况就会变得复杂. 比如说，一个端点固定住的半无限长弦，其满足边界条件和初始条件
$$
\begin{cases}
u(0, t) = 0, \\
u(x, 0) = \phi(x), \\
u_t(x, 0) = \psi(x), x > 0.
\end{cases}
$$

此时，因为是半无限长弦，所以有 $x>0$ 的条件. 原来的函数在 $x < 0$ 是没有定义的. 按照当前的初始条件，直接应用前述的解肯定是不行的，需要对初始条件进行沿拓. 而我们希望我们选取的沿拓方式，能够恰好满足边界条件 $u(0, t) = 0$ 的规定.

我们考虑前述解
$$
u(x, t) = \frac{1}{2}[\phi(x+at) + \phi(x-at)] + \frac{1}{2a}\int_{x-at}^{x+at} \psi(x) \mathrm{d}x
$$
的一个性质：如果 $\phi, \psi$ 都是奇函数的话，得到的解 $u(x,t)$ 也是关于x的奇函数：

$$
\begin{align}
u(-x, t) &= \frac{1}{2}[\phi(-x+at) + \phi(-x-at)] + \frac{1}{2a}\int_{-x-at}^{-x+at} \psi(\xi) \mathrm{d}\xi \\
&= \frac{1}{2}[-\phi(x-at) - \phi(x+at)] + \frac{1}{2a}\int_{x+at}^{x-at} \psi(-\eta) \mathrm{d}(-\eta) \\
&= -\left[\frac{1}{2}[\phi(x+at) + \phi(x-at)] + \frac{1}{2a}\int_{x-at}^{x+at} \psi(\eta) \mathrm{d}\eta \right] = -u(x,t)
\end{align}
$$

所以，对初始条件进行奇沿拓，这样解出的 u 也会是个奇函数，自然满足 $u(0, t) = 0$ ：
$$
\phi_1(x) =  
\begin{cases}
\phi(x), \quad x \leq 0 \\
-\phi(-x), \quad x < 0.
\end{cases}
\\
\psi_1(x) =  
\begin{cases}
\psi(x), \quad x \leq 0 \\
-\psi(-x), \quad x < 0.
\end{cases}
\\
\,
\\

\begin{cases}
u(x, 0) = \phi_1(x), \\
u_t(x, 0) = \psi_1(x).
\end{cases}
$$

将沿拓过的 $\phi_1, \psi_1$ 代入之前不含边界条件的解u，然后取 $x \leq 0$ 的部分，即得到所求.

同理，如果端点不是固定的而是自由的，即满足边界条件
$$
u_t(0, t) = 0,
$$
我们可以通过偶沿拓来求解. 但是对于两端都固定的情况，问题开始复杂化，我们知道解的形式应当是一三角级数的形式，肯定不是这种随随便便沿拓就能猜出来的.
