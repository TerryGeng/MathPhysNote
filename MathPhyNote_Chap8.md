## 数学物理方法 总结

[TOC]

### Chap8. 分离变量法

这一章讨论的是二阶线性偏微分方程的求解. 我们介绍了：

1. 二阶**齐次**偏微分方程 + 边界条件**取0** + 任意初始条件；
2. 二阶**非齐次**偏微分方程 + 边界条件**取0** + 任意初始条件；
3. 二阶**齐次/非齐次**偏微分方程 + 边界条件**取非0值** + 任意初始条件；

#### 分离变量法的基本思想

分离变量法求解线性齐次方程的基本思想是：先把**齐次**偏微分方程的求解转化为一系列常微分方程在特定边界条件下的求解，然后利用齐次线性方程的任意解的线性组合也是它的解的性质，将解组合出满足初始条件要求的形式.

举个例子，对于波动方程与它的定解条件
$$
\begin{cases}
u_{tt} - a^2 u_{xx} = 0, \\
u |_{x=0} =  u |_{x=L} = 0, \\
u |_{t=0} = \phi(x), u_t |_{t=0} = \psi(x).
\end{cases}
$$
如果我们令 $u(x, t) = X(x)T(t)$ ，则代入上面的方程中，**因为方程的右手边为0（齐次）**，我们得到：

$$
\frac{X''(x)}{X(x)} = \frac{T''(t)}{a^2 T(t)}.
$$
可以看出，等式两边分别是 $x$ 的函数与 $t$ 的函数. 我们断言等式两边必然等于一常数，因为假设两边不等于常数，则固定左侧 $x = x_0$ ，左边将取一定值. 而因为没有限定 $t$ ，则右手侧可以随意变化. 因为两边取等，这是不可能的. 唯一的可能是右边与 $t$ 无关，因此不会随 $t$ 改变而任意变化. 同理，反向使用这一论证，得到左边与 $x$ 无关. 因而等式两边为一常数：

$$
\frac{X''(x)}{X(x)} = \frac{T''(t)}{a^2 T(t)} = - \lambda. 
\implies
\begin{cases}
X''(x) + \lambda X(x) = 0 \\
T''(t) + a^2 \lambda T(t) = 0
\end{cases}
.
$$

现在，我们已经成功把求解偏微分方程的问题转化为了两个常微分方程求解的问题. 

$u(x,t)$ 的边界条件也可以相应修改为关于 $X$ 的限制条件：因为对于 $x = 0, x = L$ ，不论 $t$ 如何取值，u的取值 **总是0** （“总是0”这一点非常重要，因为只有为0的边界/初始条件才能够被首先处理，这一点会在下文详细讨论）. 因此，必有
$$
X(0) = X(L) = 0.
$$

*不要妄图对初始条件 $u |_{t=0} = \phi(x), u_t |_{t=0} = \psi(x)$ 做这种修改，因为它不为0.*

根据所给的边界条件，我们可以定出常微分方程若干个（无限个）解 $X_n(x), T_n(t)$ ，从而得到一系列解

$$
u_n(x, t) = X_n(x) T_n(t).
$$

现在，我们利用线性算子的性质
$$
\begin{cases}
\left( \frac{\partial^2 }{ \partial t^2} - a^2 \frac{\partial^2 }{ \partial x^2} \right) 
u = 0, \\
\left( \frac{\partial^2 }{ \partial t^2} - a^2 \frac{\partial^2 }{ \partial x^2} \right) 
v = 0 
\end{cases}
\\
\implies
\left( \frac{\partial^2 }{ \partial t^2} - a^2 \frac{\partial^2 }{ \partial x^2} \right) 
(u + v) = 0
$$
我们写出方程在给定边界条件下特解的形式
$$
u = \sum_{n} C_nu_n.
$$
其中 $C_n$ 是任意常数.

然而除此之外我们还必须使得我们的解**满足初始条件**，为此我们调整 $C_n$ 的取值，使得 $u$ 满足初始条件. 因为物理问题对应的偏微分方程，解具有唯一性，我们可以确信我们得到的解就是该偏微分方程在给定边界条件和初始条件下的解.



#### 线性齐次二阶偏微分方程的具体求解

按照线性齐次二阶偏微分方程的分类，依次讨论波动方程（双曲型）、扩散方程（抛物型）以及拉普拉斯方程（椭圆型）的求解问题.

##### 基本原理详述：以波动方程为例

一般一维的齐次波动方程与它的定解条件如下：
$$
\begin{cases}
u_{tt} - a^2 u_{xx} = 0, \\
u |_{x=0} =  u |_{x=L} = 0, \\
u |_{t=0} = \phi(x), u_t |_{t=0} = \psi(x).
\end{cases}
$$
按照上法分离变量 $u(x, t) = X(x)T(t)$ ，
$$
\begin{cases}
X''(x) + \lambda X(x) = 0  \\
T''(t) + a^2 \lambda T(t) = 0
\end{cases}
$$

解关于 $X$ 的方程，根据 $\lambda$ 的取值讨论解的情况：

**1. ** 当 $\lambda = 0$ 时，
$$
X(x) = Ax + B.
$$

为了满足边界条件 $u |_{x=0} =  u |_{x=L} = 0$ ，必须有 $A = B = 0$. 我们得到了 $X(x) = 0$ ，是一个平庸解.

**2.** 当 $\lambda < 0$ 时，
$$
X(x) = A e^{\sqrt{- \lambda} x} + B e^{- \sqrt{- \lambda} x}.
$$

代入边界条件
$$
\begin{cases}
X(0) = A + B = 0, \\
X(L) = A e^{\sqrt{- \lambda} L} + B e^{- \sqrt{- \lambda} L}.
\end{cases}
$$

因为系数行列式非0，所以上面这关于 $A, B$ 的方程只有平庸解 $A = B = 0$ ，因此又得到了 $X(x) = 0$ ，是一个平庸解.

**3.当 $\lambda > 0$ 时 ** ，
$$
X(x) = A \sin \sqrt{\lambda} x + B \cos{\sqrt{\lambda} x}.
$$

代入边界条件
$$
\begin{cases}
X(0) = B = 0, \\
X(L) = A \sin{\sqrt{\lambda} L} + B \cos{\sqrt{\lambda} L}.
\end{cases}
\\
\implies
\sqrt \lambda = \frac{n \pi}{L}.
$$

至此，我们已经完全解出了 $X$ ：
$$
X_n(x) = A \sin \sqrt{\lambda_n} x = A_n \sin \frac{n \pi}{L} x.
$$

这被称作方程u的**本征函数族**.

我们再讨论 $T$ 的解法：
$$
T''(t) + a^2 \lambda T(t) = 0 \\
\implies T''(t) + \left( \frac{n \pi a}{L} \right)^2T(t) = 0
$$

同上，因为 ${n \pi a}/{L} > 0$ ，从而
$$
T_n(t) = C_n \sin \frac{n \pi a}{L} t + D_n \cos{\frac{n \pi a}{L} t}.
$$
这时，我们得到了
$$
u = \sum_{n=1}^{+\infty} u_n = \sum_{n=1}^{+\infty} T(t)X(x) 
= \sum_{n=1}^{+\infty} \left( C_n \sin \frac{n \pi a}{L} t + D_n \cos{\frac{n \pi a}{L} t} \right) \sin \frac{n \pi}{L} x.
$$
这里有两点解说：

1. 首先是求和指标从1开始，是因为如果 $n=0$ ，那么对应的 $u_0 = 0$ . 
2. 以及，原本位于 $X_n$ 中的常数 $A_n$ 被并入了 $C_n, D_n$ 中. 这么处理很重要，因为我们必须把待定的常数化为相互独立的形式，这样才好唯一定出他们的值. 事实上，有多少个定解条件，就能定出多少个唯一常数. 所以处理过后，要求起码常数的数量要等于条件的数量.

为了定出常数 $C_n, D_n$ ，我们使用我们目前还没有使用的初始条件
$$
u |_{t=0} = \phi(x), u_t |_{t=0} = \psi(x) \implies \\
\,
\\
\begin{cases}
\sum_{n=1}^{+\infty} D_n \sin \frac{n \pi}{L} x = \phi(x), \\
\\
\sum_{n=1}^{+\infty} C_n \frac{n \pi a}{L}\sin \frac{n \pi}{L} x = \psi(x).
\end{cases}
$$

这是我们太熟悉的Fourier级数的形式，我们采用Fourier级数中的方法，利用Euler-Fourier公式求解Fourier系数 $D_n$ 和 $C_n \frac{n \pi a}{L}$ .

$$
D_n = \frac{2}{L} \int_{0}^{L} \phi(x) \sin \frac{n \pi}{L} x \, \mathrm{d}x\\
C_n = \frac{2}{n \pi a} \int_{0}^{L} \psi(x) \sin \frac{n \pi}{L} x \, \mathrm{d}x.
$$
至此我们已经解出了波动方程在该边界条件与初始条件下的解. 由微分方程理论以及我们问题的提法，**这个偏微分方程的解存在且唯一**. 因此我们确信我们找到的解就是该偏微分方程的唯一解.


##### 边界条件、初始条件对解的影响

上文的求解过程是局限于边界条件、初始条件
$$
\begin{cases}
u |_{x=0} =  u |_{x=L} = 0, \\
u |_{t=0} = \phi(x), u_t |_{t=0} = \psi(x).
\end{cases}
$$
下的. 我们不妨考虑一下，采用其他形式的边界条件和初始条件会对解有什么额外的影响.

**先考虑其他可行的初始条件的形式.** 按照上文对于定出常数的要求，由于分离出的 $X$ 的解有两个待定常数，已经消耗了两个边界条件去定出它们，而 $T$ 也有两个待定常数，因此也需要两个初始条件去定出它们. 只要满足两个+相互独立，都可以唯一定出待定常数. 比如，如果初始条件按照下面的形式给出：
$$
u |_{t=0} = \phi(x), u |_{t=t_0} = \psi(x).
$$

相当于
$$
\begin{align}
&\begin{cases}
\sum_{n=1}^{+\infty} D_n \sin \frac{n \pi}{L} x = \phi(x), \\
\\
\sum_{n=1}^{+\infty} \left( C_n \sin \frac{n \pi a}{L} t_0 + D_n \cos{\frac{n \pi a}{L} t_0} \right) \sin \frac{n \pi}{L} x = \psi(x).
\end{cases}
\\
\,
\\
\implies &\begin{cases}
D_n = \frac{2}{L} \int_{0}^{L} \phi(x) \sin \frac{n \pi}{L} x \, \mathrm{d}x\\
C_n = \frac{1}{\sin \frac{n \pi a}{L} t_0} \left(\frac{2}{L}\int_{0}^{L} \psi(x) \sin \frac{n \pi}{L} x \, \mathrm{d}x - D_n \cos{\frac{n \pi a}{L} t_0}  \right).
\end{cases}
\end{align}
$$

同理，还可以有各种组合方式.



**再考虑边界条件的问题.** 必须要强调：我们这一套处理方式其实是很特殊的. **我们利用了边界条件为0的条件**，才可以把原本是对 $u = X(x)T(t)$ 的限制转化为对 $X(x)$ 的限制. 如果不为0的话，这种处理方式在第一步就会遇到困难.

实际上，这种处理可以看做，利用**一族满足边界条件的三角本征函数（基底），把一个形式可以是任意函数的解做了Fourier展开**. 从数学上，把解表示成这种形式要求本征函数族具有完备性，而这是在Fourier理论中得到了证明的. 再次强调，这一套处理方式是很特殊的. 

甚至，如果明白了其中的奥义，**我们甚至可以连方程长什么样都先不管（管它齐不齐次），在一开始就信口开河**说，由于方程必须满足边界条件 $u |_{x=0} =  u |_{x=L} = 0,$ 我们故意设解的形式是
$$
u = \sum_{n=1}^{+\infty} u_n = \sum_{n=1}^{+\infty} T(t) \sin \frac{n \pi}{L} x.
$$

这样做不失普遍性，因为任何一个满足两个端点 $0, L$ 处为0的函数都可以用本征函数族 $\sin \frac{n \pi}{L} x$ 展开. 所以解必然具有这个形式. 接下来再考虑，这个泛定方程是什么样子的，从而求出 $T(t)$ ；初始条件又是什么样子的，从而定出 $T(t)$ 中的待定常数.实质上，这种做法就是我们处理非齐次泛定方程的通用方法. 这一点会在后文详述. 

我们先考虑其他可行的边界条件，

比如
$$
u_x |_{x=0} = 0,  u_x |_{x=L} = 0,
$$

相当于
$$
\begin{cases}
X(0) = \sqrt{\lambda} A = 0, \\
X(L) = A \sqrt{\lambda} \cos{\sqrt{\lambda} L} - B \sqrt{\lambda} \sin{\sqrt{\lambda} L} = 0.
\end{cases}
\\
\implies
\sqrt \lambda = \frac{n \pi}{L}.
$$

我们得到了本征函数族 
$$
\left\{ \cos \frac{n \pi}{L} x \right\}_{n=0}^{+\infty}.
$$

于是解的形式就是
$$
u = \sum_{n=1}^{+\infty} T(t) \cos \frac{n \pi}{L} x.
$$

其他组合方式按照上法也可以得出类似的本征函数族. 这里做一整理：
$$
\begin{align}
u |_{x=0} =  u |_{x=L} = 0 
&\implies \left\{ \sin \frac{n \pi}{L} x \right\}_{n=1}^{+\infty} \\
u_x |_{x=0} = 0,  u_x |_{x=L} = 0
&\implies \left\{ \cos \frac{n \pi}{L} x \right\}_{n=0}^{+\infty} \\
u |_{x=0} = 0,  u_x |_{x=L} = 0 
&\implies \left\{ \sin \frac{(n+ \frac{1}{2}) \pi}{L} x \right\}_{n=0}^{+\infty} \\
u_x |_{x=0} = 0,  u |_{x=L} = 0 
&\implies \left\{ \cos \frac{(n+ \frac{1}{2}) \pi}{L} x \right\}_{n=0}^{+\infty}.
\end{align}
$$

##### 更多应用：以扩散方程为例

在进行完比较一般化的讨论后，我们立即考虑理论的运用. 

讨论均匀铁棒的热传导问题，铁棒两端绝热，可以列出以下方程（以u表示温度）：
$$
\begin{cases}
u_{t} - a^2 u_{xx} = 0, \\
u_x |_{x=0} = 0, u_x |_{x=L} = 0 \\
u |_{t=0} = \phi(x),
\end{cases}
$$

根据上面的经验，我们立刻知道解的形式是
$$
u = \sum_{n=0}^{\infty} T_n(t) \cos \frac{n \pi}{L} x,
$$

而由泛定方程，代入我们给出的u的形式，

$$
\sum_{n=0}^{\infty} \left( T_n'(t) + \left( \frac{n \pi a}{L} \right)^2 T_n(t)\right) \cos \frac{n \pi}{L} x = 0, \\
\begin{align}
&\implies T_n'(t) + \left( \frac{n \pi a}{L} \right)^2 T_n(t) = 0 \\
&\implies T_n(t) = A_n \exp \left(  - \left( \frac{n \pi a}{L} \right)^2 t\right)
\end{align}
$$

从而，u具有形式
$$
u = \sum_{n=0}^{\infty} A_n \exp \left(  - \left( \frac{n \pi a}{L} \right)^2 t\right) \cos \frac{n \pi}{L} x.
$$

代入 $u |_{t=0} = \phi(x), $ 我们有
$$
u = \sum_{n=0}^{\infty} A_n \cos \frac{n \pi}{L} x = \phi(x), \\
\implies A_n = \frac{2}{L} \int_{0}^{L} \phi(x) \cos \frac{n \pi}{L} x.
$$

从这个例子，我们注意到：如果方程中包含的是u对t的一阶导数，那么求出来后关于时间部分就是一个衰减的指数形式. 




**第三类边界条件的处理**

对于扩散问题而言，有一类特殊的边界条件，即自由散热条件：
$$
\left(u +h\frac{\partial u}{\partial x} \right) |_{x=L} = 0,
$$

其本质上是一个第三类边界条件. 我们这里考虑其本征函数的形式，先分离变量
$$
\frac{X''(x)}{X(x)} = \frac{T'(t)}{a^2 T(t)} = - \lambda
\implies
\begin{cases}
X''(x) + \lambda X(x) = 0 \\
T'(t) + a^2 \lambda T(t) = 0
\end{cases}
. \\
\implies X = A \sin \sqrt{\lambda} x + B \cos{\sqrt{\lambda} x}.
$$

代入边界条件
$$
\begin{cases}
u_x |_{x=0} = 0, \\
\left(u +h\frac{\partial u}{\partial x} \right) |_{x=L} = 0,
\end{cases}
\\\implies
\begin{cases}
A = 0, \\
(A - hB \sqrt{\lambda} ) \sin \sqrt{\lambda} L + (B + hA \sqrt{\lambda} L)\cos \sqrt{\lambda} L = 0.
\end{cases} \\
\implies - h \sqrt{\lambda}\sin \sqrt{\lambda} L +  \cos \sqrt{\lambda} L = 0
$$

这个方程是一个超越方程，得到解最方便的方式是查表，因此把它化成标准型：令 $\mu = \sqrt{\lambda} L$ ， $k = h / L$ ，
$$
\implies \cot \mu = k \mu.
$$
有解 $ \pm \mu_1, \pm \mu_2, \pm \mu_3 \cdots $ .

因此本征函数族为
$$
\left\{ \cos \frac{\mu_n}{L} x \right\}_{n=1}^{+\infty}.
$$
可以证明，**这样的一族本征函数是完备的.**

对称地有，对于边界条件
$$
\left(u +h\frac{\partial u}{\partial x} \right) |_{x=0} = 0, \\
u_x |_{x=L} = 0, \\
\implies \left\{ \sin \frac{\mu_n}{L} x \right\}_{n=1}^{+\infty}.
$$

##### 更多应用：（圆域上的）拉普拉斯方程

拉普拉斯方程形如
$$
\nabla^2 u=0.
$$

在二维平面上，用直角坐标展开成
$$
u_{xx} + u_{yy} = 0.
$$

如果我们将波动方程的t看成是y，并认为 $a=0$ ，得到的就是上述方程. 因此波动方程的解就可以直接用于其上，此处不再赘述.

然而， $\nabla^2$ 算子在不同的坐标下展开形式也不一样，而在极坐标下的展开形式适合求解边界条件、初始条件也以极坐标方式给出的情况，因此对这种情况加以讨论. 

设均匀圆盘边缘温度满足某一特定分布，则方程写作：
$$
\begin{cases}
\nabla^2 u = 0, \\
u|_{\rho = \rho_0} = f(\theta).
\end{cases}
$$

极坐标下 $\nabla^2$ 展开为
$$
\nabla^2 = \frac{\partial^2 }{\partial \rho^2} + \frac{1}{\rho} \frac{\partial }{\partial \rho} + \frac{1}{\rho^2}\frac{\partial^2 }{\partial \theta^2}.
$$
按分离变数法思想，设 $u(x, t) = R(\rho)\Phi(\theta)$ ，

$$
\implies 
\begin{cases}
\Phi''(\theta) + \lambda \Phi(\theta) = 0, \\
\rho^2 R''(\rho) + \rho R'(\rho) - \lambda R(\rho) = 0.
\end{cases}
$$

关于 $\Phi$ 的方程的解法我们已经多次讨论过. 唯一需要注意的是，极坐标下有一个隐含的边界条件
$$
\Phi(\theta) = \Phi(\theta + 2\pi).
$$

通过该边界条件，我们求得
$$
\sqrt \lambda = n = 0, 1, 2, \cdots \\
\Phi_n(\theta) = A_n \cos n \theta + B_n \sin n \theta.
$$

关于 $R$ 的方程是欧拉方程，有解
$$
R(\rho) = 
\begin{cases}
c_0 + d_0 \ln \rho, \quad n = 0, \\
c_n \rho^n + d_n \rho^{-n}, \quad n \neq 0.
\end{cases}
$$

因为我们这里讨论的圆域包含 $\rho = 0$ 的点，而圆盘上的温度总是有界的，这叫做**自然边界条件**. 因此在0处不收敛的项前面的系数全为0. 从而
$$
R_n(\rho) = c_n \rho^n, \quad n = 0, 1, 2, \cdots
$$

则方程的解有形式
$$
u = \sum_{n=0}^{+\infty} \rho^n \left( A_n \cos n \theta + B_n \sin n \theta \right)
$$

又
$$
u|_{\rho = \rho_0} = f(\theta) \implies \rho_0^n \left( A_n \cos n \theta + B_n \sin n \theta \right) = f(\theta).
$$

之后操作同上不再详述.

**注：自然边界条件往往只适用于圆域的情况，因为0点处很可能是奇点. 对于圆环则没有这样的限制，负数次幂当然可以存在.**

#### 非齐次方程的处理

非齐次方程，即等号右边不为0的方程，如果以波动方程为例写作
$$
u_{tt} - a^2 u_{xx} = f(x, t).
$$

下面介绍两种求解方式.

##### 本征函数法

上一节已经讨论过，对于满足边界条件 $u |_{x=0} =  u |_{x=L} = 0$ （或者类似形式的，只要能写出本征函数族），我们都可以断言解的形式是
$$
u = \sum_{n=1}^{+\infty} T(t) \sin \frac{n \pi}{L} x.
$$

当然采用的齐次边界条件不一样，上面式中的sin也要改写成相应本征函数族. 之后定出 $T_n(t)$ 就是了.

不妨以波动方程为例：若有波动方程与定解条件
$$
\begin{cases}
u_{tt} - a^2 u_{xx} = f(x, t), \\
u |_{x=0} =  u |_{x=L} = 0, \\
u |_{t=0} = \phi(x), u_t |_{t=0} = \psi(x).
\end{cases}
$$

首先，为了方便下文的处理，我们不妨先利用线性方程解的性质，设 $v, h$ 满足
$$
\begin{cases}
v_{tt} - a^2 v_{xx} = f(x, t), \\
v |_{x=0} =  v |_{x=L} = 0, \\
v |_{t=0} = 0, v_t |_{t=0} = 0.
\end{cases} \\
\begin{cases}
h_{tt} - a^2 h_{xx} = 0, \\
h |_{x=0} =  h |_{x=L} = 0, \\
h |_{t=0} = \phi(x), h_t |_{t=0} = \psi(x).
\end{cases}
$$

这样分解以后，u就可以写作 $u = h+v$ ，易验证这么做是满足边界条件和非齐次方程形式的. 我们先解第一个方程，

设
$$
v = \sum_{n=1}^{+\infty} T(t) \sin \frac{n \pi}{L} x.
$$

则
$$
\sum_{n=0}^{\infty} \left( T_n''(t) + \left( \frac{n \pi a}{L} \right)^2 T_n(t)\right) \sin \frac{n \pi}{L} x = f(x,t), \\
\implies T_n''(t) + \left( \frac{n \pi a}{L} \right)^2 T_n(t) = \frac{2}{L} \int_{0}^{L} f(x,t) \sin \frac{n \pi}{L} x \mathrm{d}x  \equiv f_n(t).
$$

这一族方程可以用待定系数法或者Laplace变换法求解.

1.	**待定系数法**
解齐次方程
$$
T_n''(t) + \left( \frac{n \pi a}{L} \right)^2 T_n(t) = 0
$$
可以获得形式为
$$
T_n(t) = A_n \sin \frac{n \pi a}{L}t + B_n \cos \frac{n \pi a}{L}t
$$
的解.

现在设非齐次方程
$$
T_n''(t) + \left( \frac{n \pi a}{L} \right)^2 T_n(t) = f_n(t)
$$
的解形式为
$$
T_n(t) = A_n(t) \sin \frac{n \pi a}{L}t + B_n(t) \cos \frac{n \pi a}{L}t
$$

则按照待定系数法的要求， $A_n(t), B_n(t)$ 满足
$$
\begin{cases}
A_n'(t) \sin \frac{n \pi a}{L}t + B_n'(t) \cos \frac{n \pi a}{L}t = 0, \\
A_n'(t) \cos \frac{n \pi a}{L}t - B_n'(t)  \sin \frac{n \pi a}{L}t = \frac{L}{n \pi a} f_n(t).
\end{cases}
$$

这实际上是关于 $A_n(t), B_n(t)$ 的一个线性方程组，
$$
\begin{cases}
A_n'(t) = \frac{L}{n \pi a} \cos \frac{n \pi a}{L}t \, f_n(t), \\
B_n'(t) = -\frac{L}{n \pi a} \sin \frac{n \pi a}{L}t \, f_n(t).
\end{cases}
$$

佐以初始条件即可解出对应的 $A_n, B_n$ .
$$
\begin{align}
T_n(t) &= 
\sin \frac{n \pi a}{L}t \int_0^t \frac{L}{n \pi a} \cos \frac{n \pi a}{L}\tau \, f_n(\tau) \mathrm{d}\tau
- \cos \frac{n \pi a}{L}t \int_0^t \frac{L}{n \pi a} \sin \frac{n \pi a}{L}\tau \, f_n(\tau) \mathrm{d}\tau \\
&= \frac{L}{n \pi a} \int_0^t f_n(\tau) \sin \left( \frac{n \pi a}{L}(t - \tau) \right) \, \mathrm{d}\tau.
\end{align}
$$


2. **Laplace变换法**
虽然待定系数法适用性很强，但是在 $f(x, t)$ 形式简单的情况下，未免显得繁琐. 我们可以利用Laplace变换的性质
$$
\begin{align}
&\mathcal{L}[T_n(t)] \equiv \bar{T_n}(t) \\
&\mathcal{L}[T_n'(t)] = p \bar{T_n}(t) - T_n(0) \\
&\mathcal{L}[T_n''(t)] = p^2 \bar{T_n}(t) - p T_n(0) - T_n'(0).
\end{align}
$$

于是对上述方程两遍做Laplace变换，
$$
\mathcal{L}[T_n''(t) + \left( \frac{n \pi a}{L} \right)^2 T_n(t)] = \bar{f_n}(t) \\
\implies p^2 \bar{T_n}(p) - p T_n(0) - T_n'(0) + \left( \frac{n \pi a}{L} \right)^2 \bar{T_n}(p) = \bar{f_n}(p).
$$

在上式中，$T_n(0), T_n'(0)$ 项的处理可能并不是很好办，不过我们通过上面的拆分，强行把u拆成h和v，而对于v而言，
$$
T_n(0) = 0, T_n'(0) = 0.
$$

因此，
$$
p^2 \bar{T_n}(p) + \left( \frac{n \pi a}{L} \right)^2 \bar{T_n}(p) = \bar{f_n}(p). \\
\implies  \bar{T_n}(p)  = \frac{1}{p^2 + \left( \frac{n \pi a}{L} \right)^2 }\bar{f_n}(p).
$$

由Laplace变换像函数的卷积定理，
$$
T_n(t) = \frac{L}{n \pi a} \int_0^t f_n(\tau) \sin \left( \frac{n \pi a}{L}(t - \tau) \right) \, \mathrm{d}\tau.
$$

因此求得
$$
v (x, t) = \sum_{n=1}^{\infty} \left( \frac{L}{n \pi a} \int_0^t f_n(\tau) \sin \left( \frac{n \pi a}{L}(t - \tau) \right) \, \mathrm{d}\tau \right) \sin \frac{n \pi}{L} x
$$


而h的解在一开始便求得：
$$
h = \sum_{n=1}^{+\infty} \left[ \left( \frac{2}{L} \int_{0}^{L} \phi(x) \sin \frac{n \pi}{L} x \, \mathrm{d}x  \right)\sin \frac{n \pi a}{L} t + \left( \frac{2}{n \pi a} \int_{0}^{L} \psi(x) \sin \frac{n \pi}{L} x \, \mathrm{d}x \right) \cos{\frac{n \pi a}{L} t} \right] \sin \frac{n \pi}{L} x.
$$

则 $u = h + v$ ，此处不再展开写.

##### 冲量定理法 Duhamel's principle
Duhamel's principle 利用方程线性性质，将方程右手侧非齐次函数转化成一堆关于t的 $ \delta $ 函数相加，同时将解u看成是一系列解 $u_n$ 的叠加，每个 $u_n$ 的方程都对应着右边一系列 $ \delta $ 函数的一项. 按照“冲量定理”的思想，我们可以认为右边这瞬间施加的一个**冲量**，实际上造成了**速度的一个瞬态改变**. 将每个 $u_n$ 经历的这一系列瞬态改变相加（求积分），即可合成一个最终的解.

将上面的思想用数学语言来表述，以波动方程为例，即是：将f分解为
$$
f(x,t) = \sum_{n=1}^{\infty} f(x, t_n)  \Delta t \,\delta(t - t_n), \quad \Delta t \to 0,
$$

式中 $\Delta t$ 是 $t_n, t_{n+1}$ 之间的间隔. 这是因为
$$
\int_{t_0}^{t} \sum_{n=1}^{\infty} f(x, t_n)  \Delta t \,\delta(t - t_n) \mathrm{d}t = 
\sum_{t = t_0}^{t_n} f(x, t) \Delta t = \int_{t_0}^{t} f(x, t) \mathrm{d}t \\
\implies f(x,t) = \sum_{n=1}^{n_0} f(x, t_n)  \Delta t \,\delta(t - t_n), \quad \Delta t \to 0.
$$

替换掉原来方程里的f：
$$
\begin{cases}
u_{tt} - a^2 u_{xx} = f(x,t) = \sum_{n=1}^{\infty} f(x, t_n)  \Delta t \,\delta(t - t_n), \quad \Delta t \to 0\\
u |_{x=0} =  u |_{x=L} = 0, \\
u |_{t=0} = 0, u_t |_{t=0} = 0.
\end{cases}
\\
\,
\\
\implies
\begin{cases}
\frac{\partial^2 u_1}{\partial t^2} - a^2 \frac{\partial^2 u_1}{\partial x^2} = f(x, t_1)\Delta t \, \delta(t - t_1), \\
\frac{\partial^2 u_2}{\partial t^2} - a^2 \frac{\partial^2 u_2}{\partial x^2} = f(x, t_2) \Delta t \,\delta(t - t_2), \\
\vdots \\
\frac{\partial^2 u_n}{\partial t^2} - a^2 \frac{\partial^2 u_n}{\partial x^2} = f(x, t_n)\Delta t \, \delta(t - t_n), 
\end{cases}
\\
u = \sum_{n=1}^{n_0} u_n.
$$

为了方便处理，所有的初始条件这里都置0. 如果初始条件不为0，前文已经介绍了单独处理初始条件的方法（化为 $u = h + v$ ）.

下面，对于每个 $u_n$，
$$
\begin{cases}
\frac{\partial^2 u_n}{\partial t^2} - a^2 \frac{\partial^2 u_n}{\partial x^2} = f(x, t_n) \Delta t \, \delta(t - t_n), \\
u_n |_{x=0} =  u_n |_{x=L} = 0, \\
u_n |_{t=0} = 0, \frac{\partial u_n}{\partial t} |_{t=0} = 0.
\end{cases}
$$

在 $t = t_n$ ，也就是 $f(x, t_n) \delta(t - t_n)$ 起作用之前，弦实际上不震动. 弦在 $t = t_n$ 后开始振动. 那一刻有 $u_{xx}$ 有界，因此，实际上这一时刻满足方程

$$
\int_{t_n - \delta t}^{t_n + \delta t} \frac{\partial^2 u_n}{\partial t^2}(x_0, t) \, \mathrm{d}t
- a^2 \int_{t_n - \delta t}^{t_n + \delta t} \frac{\partial^2 u_n}{\partial x^2}(x_0, t) \,  \mathrm{d}t
= f(x_0, t_n) \Delta t.
$$

而
$$
\left|\frac{\partial^2 u_n}{\partial x^2} \right|_{t < t_n + \delta t} < M, \\
\int_{t_n - \delta t}^{t_n + \delta t} \frac{\partial^2 u_n}{\partial x^2}(x_0, t)  \,  \mathrm{d}t< 2M\delta t.
$$

取 $\delta t \to 0$ ，该项取0.
$$
\frac{\partial^2 u_n}{\partial t^2}(x_0, t) \, \mathrm{d}t = d \left( \frac{\partial u_n}{\partial t}(x_0, t) \right),\\
\frac{\partial u_n}{\partial t}(x_0, t_n+0) = f(x_0, t_n) \Delta t， \\
\text{i.e.} \quad
\left. \frac{\partial u_n}{\partial t} \right|_{t=t_n} = f(x, t_n) \Delta t.
$$

而 $t = t_n$ 之后，实际上弦的方程又恢复了齐次的形式，因此方程实际上可以写为
$$
\begin{cases}
\frac{\partial^2 u_n}{\partial t^2} - a^2 \frac{\partial^2 u_n}{\partial x^2} = 0, \\
u_n |_{x=0} =  u_n |_{x=L} = 0, \\
u_n |_{t=t_n} = 0, \frac{\partial u_n}{\partial t} |_{t=t_n} = f(x, t_n) \Delta t.
\end{cases}
$$

因此，解出
$$
u_n = v_n(x, t) \Delta t \equiv v(x, t; t_n) \Delta t.
$$
从而，
$$
u = \sum_{n=1}^{n_0} u_n = \sum_{n=1}^{n_0} v(x, t; t_n) \Delta t = \int_{0}^{t}\ v(x, t;  \tau) \, \mathrm{d}\tau.
$$

在此例弦振动中，容易解出
$$
v_n \Delta t= \sum_{n=1}^{\infty} A_n \Delta t\sin \left(\frac{n \pi a}{L}(t-t_n) \right) \sin \frac{n \pi x}{L}. \\
A_n = \frac{2}{n\pi a} \int_{0}^{L} f(x, t_n) \sin \frac{n \pi x}{L} \mathrm{d}x.
$$
因此
$$
u(x, t) = \sum_{n=1}^{\infty}  \int_{0}^{t} A_n\sin \left(\frac{n \pi a}{L}(t-\tau) \right) \sin \frac{n \pi x}{L} \mathrm{d}\tau.
$$
为了与前文所得的结论比较，我们采用与之前一样的记号
$$
\frac{n\pi a}{L}\frac{2}{n \pi a} \int_{0}^{L} f(x,t) \sin \frac{n \pi}{L} x \mathrm{d}x  \equiv f_n(t) \implies A_n = \frac{L}{n\pi a} f_n(x).
$$

$$
u(x, t) = \sum_{n=1}^{\infty}  \frac{L}{n\pi a} \int_{0}^{t}  f_n(x)\sin \left(\frac{n \pi a}{L}(t-\tau) \right) \sin \frac{n \pi x}{L} \mathrm{d}\tau.
$$

这与本征函数法得到的结论相同.


#### 非齐次边界条件的处理
我们多次强调了我们分离变量法的基础是边界条件其次（为0），这样不论边界条件取什么形式，我们都可以可以把原本是对 $u = X(x)T(t)$ 的限制转化为对单纯对 $X(x)$ 的限制，由此能找到完备的本征函数族.

如果遇到非齐次的边界条件，
$$
u |_{x=0} = g(t), u |_{x=L} = h(t),
$$
我们若希望使用分离变量法的思路，只能想方设法将方程的边界条件变成齐次的形式. 我们采用与之前的思路一致的方法，将方程拆分为

$$
u = v + r, \\
\text{s.t.} \quad 
\begin{cases}
v |_{x=0} = 0, v |_{x=L} = 0, \\
r |_{x=0} = g(t), r |_{x=L} = h(t),
\end{cases}
$$

在这种情况下，r可取
$$
r = g(t) + \frac{x}{L}(h(t) - g(t)).
$$

这样，关于v的方程的边界条件变成了齐次边界条件，解关于v的方程即可. 以弦振动为例，
$$
\begin{cases}
u_{tt} - a^2 u_{xx} = f(x, t), \\
u |_{x=0} = g(t), u |_{x=L} = h(t), \\
u |_{t=0} = \phi(x), u_t |_{t=0} = \psi(x).
\end{cases}
$$

取 $ u = h+v+r $,
$$
\begin{align}
&\begin{cases}
h_{tt} - a^2 h_{xx} = 0, \\
h |_{x=0} = 0, h |_{x=L} = 0, \\
h |_{t=0} = \phi(x), h_t |_{t=0} = \psi(x).
\end{cases}
\\
&\begin{cases}
v_{tt} - a^2 v_{xx} = f(x, t) - \left( r_{tt} - a^2 r_{xx} \right), \\
v |_{x=0} = 0, u |_{x=L} = 0, \\
v |_{t=0} = 0, u_t |_{t=0} = 0.
\end{cases}
\\
&r |_{x=0} = g(t), r |_{x=L} = h(t).
\end{align}
$$
由此，上面三个方程的求解方式均已经介绍过.