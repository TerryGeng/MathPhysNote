## 数学物理方法 总结

[TOC]

### Chap4. 留数定理

#### 留数定理

留数定理是一种算复变函数回路积分的巧妙办法。其发源于对积分
$$
I = \oint_l (z-a)^n \mathrm{d} z
$$
的讨论上. 在路径 $l$ 包围奇点 $z = a$ 的情况下，该积分值可由以下方法求得：因为积分值与路径无关，取一个包围奇点的半径为1的小圆作为积分路径，同时做变量代换
$$
z - a = e^{i \phi},
$$
原积分化为
$$
\begin{align}
I &= \oint_{C_R} e^{ni\phi} \mathrm{d} e^{i\phi} \\
&= i \int_{0}^{2\pi} e^{i(n+1)\phi} \mathrm{d} \phi \\
&= 
\begin{cases}
0 & \quad \text{if } n \neq -1, \\
2\pi i & \quad \text{if } n = -1.

\end{cases}
\end{align}
$$
因此，积分
$$
I = \oint_{C_R} \sum_{k=0}^{\infty} a_k (z - z_0)^k \mathrm{d} z = 2\pi i a_{-1}
$$
的值实际上跟 $k \neq -1$ 没什么关系. 

因此对于一个可以表示成幂级数展开的函数（显然除了奇点以外都是解析的）
$$
f(z) = \sum_{k=-\infty}^{\infty} a_k(z-z_0)^k,
$$
绕奇点处的积分就可以写成
$$
I = \oint_{C_R} f(z) \, \mathrm{d}z = 2 \pi i a_{-1}.
$$
我们称函数 $f(z)$ 在 $z=a$ 上的展开式的负一阶项的系数为该点处的**留数**，记为 $\mathrm{Res} f(a)$.

而若函数在积分区域上有多个奇点也没有关系，积分值就可以表示为
$$
I = 2 \pi i \left(\sum_i \mathrm{Res} f(z_i) \right).
$$
其中 $z_i$ 是奇点. 



#### 留数的求法

我们已经把求环路积分的问题转化为了求留数的问题. 那么接下来的问题就是如何求出奇点处的留数. 常规的思路是，对函数做洛朗展开，取负一次幂前的系数. 然而每次都这样做未免有些麻烦. 下面讨论一些特殊情况下留数的简便求法：

##### 单极点处的留数

有的函数的某个奇点是单极点：即洛朗展开可以写成
$$
f(z) = a_{-1}(z-z_0)^{-1} + a_0 + a_1 (z-z_0) + a_2(z-z_0)^2 + \cdots
$$
对于这样的函数，留数就比较好求. 有
$$
\mathrm{Res} f(z_0) = \lim_{z\to z_0} (z-z_0)f(z),
$$
因为
$$
\lim_{z\to z_0} (z-z_0)f(z) = \lim_{z\to z_0} a_{-1} + a_0 (z-z_0) + a_1(z-z_0)^2 + \cdots = a_{-1}.
$$
或者，对$P(z)/Q(z)$ 型函数，而 $z_0$ 是 $Q(z)$ 的一阶零点，则由洛必达法则，
$$
\mathrm{Res} \frac{P(z_0)}{Q(z_0)} = \lim_{z\to z_0} (z-z_0)\frac{P(z)}{Q(z)} = \frac{P(z_0)}{Q'(z_0)}.
$$

##### m阶极点处的留数

对于一些函数，洛朗展开可以写成下面的形式
$$
f(z) = a_{-m}(z-z_0)^{-m} + \cdots + a_{-1}(z-z_0)^{-1} + a_0 + a_1 (z-z_0) + a_2(z-z_0)^2 + \cdots,
$$
那么，求留数可以通过下面的方式：
$$
\mathrm{Res} f(z_0) = \lim_{z\to z_0} \frac{1}{(k-1)!} \frac{\mathrm{d}^{k-1}}{\mathrm{d} z^{k-1}} \left[ (z-z_0)^k f(z) \right]\qquad (k \geq m).
$$
在这个操作中，乘 $(z-z_0)^k$ 的操作把任何负数幂全都拉成了正数，然后再通过求 k-1 阶导数，把比 -1 阶数更低的项消去，而取 $z \to z_0$ 的极限把其他更高阶的项消去，只剩下 -1 次项的系数，然后除以 $(k - 1)!$ ，消除求导产生的额外系数.

然而要使用这个公式，首先需要确定阶数m. 这可以通过计算极限值
$$
\lim_{z \to z_0} (z - z_0)^m f(z)
$$
实现. 如果我们估计的阶数m与实际阶数相同，那么极限值为非零有限数；而如果估低了，则极限不收敛；估高了则极限值为0.

##### 本性奇点处的留数

没什么好办法，只能直接洛朗展开.



#### 推广到无穷远点的留数定理

我们可以把无穷远点也当做是一个奇点. 把无穷远点包围起来做回路积分，实际上就是用一个大圆圈住所有除了无穷远点以外的积分，然后沿着大圆反方向进行回路积分。这样，左手侧就是围住的积分区域。这个积分可以表示为
$$
I = - \oint_{C_R} f(z) \, \mathrm{d}z = - \oint_{C_R} \sum_{k = -\infty}^{\infty} a_k (z-z_0)^k \, \mathrm{d}z.
$$

其中的幂级数展开是**无穷远点处的展开式**，得到它的方法是，用 $t = 1/z$ 进行变量替换，然后在 $t=0$ 附近展开.

于是
$$
I = - 2 \pi i \mathrm{Res} \, f(\infty).
$$
而我们刚才又推出了
$$
I = 2 \pi i \left(\sum_i \mathrm{Res} f(z_i) \right).
$$
因此，我们得到了重要关系
$$
\sum_i \mathrm{Res} f(z_i) + \mathrm{Res} \, f(\infty) = 0.
$$
利用这个关系，在知道了全部有限点的留数以后，可以轻松求出无穷远点的留数.


#### 求留数、用留数算积分的例子

**Ex1. 计算积分**
$$
\oint_{|z| = 1} \frac{\mathrm{d}z}{\epsilon z^2 + 2z + \epsilon} \quad(0<\epsilon<1).
$$
首先确定奇点及其阶数. $\epsilon z^2 + 2z + \epsilon = 0$ 的解有两个，分别是
$$
z_1 = \frac{-1 + \sqrt{1 - \epsilon^2}}{\epsilon}, \quad z_2 = \frac{-1 - \sqrt{1 - \epsilon^2}}{\epsilon}.
$$
判断这两个单奇点是否在积分回路内. 显然第二个不在。对第一个进行放缩
$$
\begin{align}
\left |\frac{-1 + \sqrt{1 - \epsilon^2}}{\epsilon} \right | &= \frac{1 - \sqrt{1 - \epsilon^2}}{\epsilon} \\
&= \frac{1 - \sqrt{(1 - \epsilon)(1 + \epsilon)}}{\epsilon} \\
&< \frac{1 - \sqrt{(1 - \epsilon)^2}}{\epsilon} = 1.
\end{align}
$$
因此$z_1$ 在回路内.
$$
\mathrm{Res} f(z_1) = \lim_{z \to z_1} \frac{1}{\epsilon(z + \frac{1 + \sqrt{1 - \epsilon^2}}{\epsilon})} = \frac{1}{2 \sqrt{1 - \epsilon^2}}
$$

$$
\oint_{|z| = 1} \frac{\mathrm{d}z}{\epsilon z^2 + 2z + \epsilon} = 2 \pi i \mathrm{Res} f(z_1) = \frac{\pi i}{\sqrt{1 - \epsilon^2}}.
$$
 **Ex2. 需要使用一些技巧来确定奇点阶数的例子**

对于函数
$$
f(z) = \frac{1}{1 + z^{2n}},
$$
虽然一眼就可以看出来奇点是 $z^{2n} = -1$ （即 $z = e^{i \frac{(1+2m)\pi}{2n}}$），但是要断定奇点的阶数还是有些困难. 不妨这么处理：
$$
\frac{1}{1 + z^{2n}} = \frac{1}{1 - (-1) z^{2n}} = \frac{1}{1 - {((-1)^{1/2n}z)}^{2n}} = \frac{1}{1 - {(ze^{-i \frac{(1+2k)\pi}{2n}})}^{2n}}
$$
由级数求和公式，
$$
1 + x + \cdots + x^{n-1} = \frac{1 - x^{n}}{1 - x},
$$
上式变为
$$
\frac{1}{1 + z^{2n}} = \frac{1}{(1 + ze^{-i \pi \frac{1+2k}{2n}} + \cdots + z^{2n-1}e^{i \pi \frac{-(1+2k)(2n-1)}{2n}})(1-ze^{i \frac{-(1+2k)\pi}{2n}})}.
$$

可以看出，
$$
z = e^{i \frac{(1+2k)\pi}{2n}}, \quad k \in \mathbb{Z}
$$
是单极点（分母中的第一个括号中的每一个项都是1）. 这与我们之前求出的结果相符. 相应的留数可以通过下式求得：
$$
\lim_{z \to z_0} (z - e^{i \frac{(1+2k)\pi}{2n}}) \frac{1}{1 + z^{2n}} = \lim_{z \to z_0} \frac{1}{2nz^{2n-1}} = \frac{1}{2n} e^{-i \frac{(1+2k)(2n-1)\pi}{2n}} = -\frac{1}{2n} e^{i \frac{(1+2k)\pi}{2n}}
$$
其实也可以大胆一些，直接用上面的式子猜函数的奇点阶数. 



**Ex3. 一个巧妙计算留数的例子**

对于函数
$$
f(z) = \frac{z - \sin z}{z^6},
$$
奇点为0. 其留数可以通过直接写出洛朗展开以及求m阶极点留数的公式进行.

$f(z)$ 的洛朗展开：
$$
\begin{align}
f(z) &= \frac{1}{z^6} \left[z - (z - \frac{z^3}{3!} + \frac{z^5}{5!} - \cdots)\right] \\
&= \frac{z^{-3}}{3!} - \frac{z^{-1}}{5!} + \cdots \\
\end{align}
$$

因此
$$
\mathrm{Res} \, f(0) = - \frac{1}{5!}.
$$
或者，在公式
$$
\mathrm{Res} f(0) = \lim_{z\to 0} \frac{1}{(k-1)!} \frac{\mathrm{d}^{k-1}}{\mathrm{d} z^{k-1}} \left[ z^k \frac{z - \sin z}{z^6} \right]
$$
中取 $k = 6$ ，
$$
\mathrm{Res} f(0) = \lim_{z\to 0} \frac{1}{5!} \frac{\mathrm{d}^{5}}{\mathrm{d} z^{5}} \left( z - \sin z \right) = - \frac{1}{5!}.
$$

**Ex4. 一个比较综合的计算积分的例子**

对于一个在实际情况中应该遇不到的复杂积分
$$
I = \oint_{|z|<R} \frac{z^2}{e^{2\pi iz^3} - 1} \mathrm{d}z \qquad (n<R^3<n+1, n\in \mathbb{Z}),
$$
我们还是应当先确定积分回路内奇点的情况.

首先，奇点都在分母为0处产生，也就是
$$
2\pi i z^3 = 2k\pi i \implies z^3=k, \quad k\in \mathbb{Z}.
$$
按照所给的条件 $n<R^3<n+1$，可以看出积分回路上并没有奇点，而回路包含的区域 $ |z| < R $ 中，奇点是
$$
z = k^{1/3} \cdot e^{i2k\pi /3}, \quad k = -n, \cdots, 0, \cdots, n.
$$

**注意：复平面上的开方操作会导致多值性.**

由式子的结构可以看出奇点应该是一阶极点，因此留数
$$
\mathrm{Res} f(k^{1/3} \cdot e^{i2k\pi /3}) = \lim_{z \to z_0} (z-z_0)\frac{z^2}{e^{2\pi iz^3} - 1}
$$
由于分子分母同时趋于0，对上式使用洛必达法则
$$
\begin{align}
\lim_{z \to z_0} (z-z_0)\frac{z^2}{e^{2\pi iz^3} - 1} &= \lim_{z \to z_0} \frac{3z^2 - 2z_0z}{6\pi i z^2 e^{2\pi iz^3}} \\
\end{align}
$$
在 $z \neq 0$ 的情况下，直接代入 $z = z_0$ 得到
$$
\mathrm{Res} f(k^{1/3} \cdot e^{i2k\pi /3}) = \frac{1}{6 \pi i}, \quad z \neq 0.
$$
这是一共 $6n$ 个奇点的留数.

在 $z = 0$ 的情况下，代入上式，
$$
\mathrm{Res} f(0) = \frac{1}{2 \pi i}.
$$

因此原积分
$$
I = 2 \pi i (6n \cdot \frac{1}{6 \pi i} + \frac{1}{2 \pi i}) = 2n+1.
$$


#### 应用留数定理计算实变函数的定积分

这一节的要领在于，将实变函数的积分转化为复变函数的回路积分（包括进行变量替换；连接出一条回路，然后证明处于我们增补的路径上积分是0），然后用复变函数的回路积分的计算方法，也就是留数定理算出积分值.

##### Type I.  三角有理式在0到 $2\pi$ 的定积分
$$
I = \int_0^{2\pi} R(\cos x, \sin x) \mathrm{d}x.
$$

做代换
$$
z = e^{ix}.
$$
有
$$
\cos x = \frac{1}{2} (z + z^{-1}), \qquad \sin x = \frac{1}{2i} (z - z^{-1}), \qquad \mathrm{d}x = \frac{1}{iz} \mathrm{d}z.
$$

因此
$$
I = \oint_{|z| = 1} R\left( \frac{z + z^{-1}}{2}, \frac{z - z^{-1}}{2i} \right) \frac{1}{iz} \mathrm{d}z.
$$

**注意：实函数的积分不可能是虚的，因此最终结果一定是个实数。**

**Ex. 计算积分** 

$$
\begin{align}
I &= \int_0^{2\pi} \frac{1}{1 + \epsilon \cos x} \mathrm{d}x \\
&= \oint_{|z| = 1} \frac{1}{1 + \epsilon \frac{z + z^{-1}}{2}} \frac{1}{iz} \mathrm{d}z \\
&= -i \oint_{|z| = 1} \frac{\mathrm{d}z}{\epsilon z^2 + 2z + \epsilon}
\end{align}
$$
由之前的例题，
$$
I = -2i \cdot \frac{\pi i}{\sqrt{1 - \epsilon^2}} = \frac{2\pi}{\sqrt{1 - \epsilon^2}}.
$$



**Ex. 计算积分**
$$
\begin{align}
I = \int_{-\pi}^{\pi} \frac{1- \alpha^2}{1 - 2\alpha \cos x + \alpha^2} \cos kx \mathrm{d}x, \qquad \alpha \in (-1,1).
\end{align}
$$

由于积分区间并不在 $0, 2\pi$ 上，进行变数代换，$u = x + \pi$，
$$
\begin{align}
I = \int_{0}^{2\pi} \frac{1- \alpha^2}{1 + 2\alpha \cos u + \alpha^2} \cos k(u - \pi) \mathrm{d}x.
\end{align}
$$
**k是偶数**时，
$$
\begin{align}
I_1 = \int_{0}^{2\pi} \frac{1- \alpha^2}{1 + 2\alpha \cos u + \alpha^2} \cos ku \mathrm{d}x.
\end{align}
$$

做代换 $\cos u = \frac{1}{2} (e^{i\phi} + e^{-i\phi})$ ，有
$$
\begin{align}
I_1 &= \frac{1- \alpha^2}{2i} \oint_{|z| = 1} \frac{z^{k} + z^{-k}}{z + \alpha  (z^2 + 1) + \alpha^2z}  \mathrm{d}z \\
&= \frac{1- \alpha^2}{2i} \left\{\oint_{|z| = 1} \frac{z^{k} }{ (\alpha z+1)(z + \alpha)}  \mathrm{d}z + \oint_{|z| = 1} \frac{z^{-k} }{ (\alpha z+1)(z + \alpha)}  \mathrm{d}z \right\}.
\end{align}
$$

使用留数定理求这个积分. 可以看出来，这两个积分在上半平面没有奇点，奇点全部在实轴上. 前者的奇点分别为$x = -1/\alpha, -\alpha$，后者为 $x = 0, 1/\alpha, -\alpha$ . 在半径为1的圆内，包含的奇点是 $0, -\alpha$. 则
$$
\begin{align}
\text{Let }  & f_1(z) = \frac{z^{-k} }{ (\alpha z+1)(z + \alpha)} , \qquad f_2(z) = \frac{z^{k} }{ (\alpha z+1)(z + \alpha)}\\
I_1 &= \frac{1- \alpha^2}{2i} \left( \pi i \mathrm{Res} f_1(0) +  \pi i \mathrm{Res} f_1(-\alpha) +  \pi i \mathrm{Res} f_2(-\alpha)  \right)\\
&= \frac{1- \alpha^2}{2i} \left(  \pi i \mathrm{Res} f_1(0) +  \pi i \mathrm{Res} f_1(-\alpha)+ \pi i \frac{\alpha^k}{1 - \alpha^2} \right).
\end{align}
$$

由于前者的0处是一个k阶奇点，再者表达式形式又复杂，反复求导做起来会很困难. 转而试求奇点 $x = \infty$ 处的留数. 做代换 $t = 1/z$, 
$$
\mathrm{Res} f_1(\infty) = \mathrm{Res}\left( \left. \frac{t^{k+2}}{(\alpha t+1)(t + \alpha)} \right) \right|_{t = 0} = 0
$$

则
$$
\mathrm{Res} f_1(0) + \mathrm{Res} f_1(-\alpha) = - \mathrm{Res} f_1(\infty) - \mathrm{Res} f_1(-\frac{1}{\alpha}) = -\frac{\alpha^{k}}{ \alpha^2 - 1}. \\
I_1 = \frac{1- \alpha^2}{2i} 2\pi i \frac{2\alpha^k}{1 - \alpha^2} = 2 \pi \alpha^k.
$$

同理可得，k为奇数是，积分值也是 $I_2 = 2 \pi \alpha^k$ ，因此
$$
\int_{-\pi}^{\pi} \frac{1- \alpha^2}{1 - 2\alpha \cos x + \alpha^2} \cos kx \mathrm{d}x = 2 \pi \alpha^k.
$$



##### Type II. 一类特定的无穷限反常积分

对于积分主值
$$
I = P \int_{-\infty}^{\infty} f(x) \mathrm{d}x,
$$
如果它满足以下条件：

1. 在实轴上无奇点；
2. 在上半平面（或下半平面）除有限个奇点外解析；
3. **在上半平面（或下半平面）和实轴上当 $z \to \infty$ 有 $z f(z) \to \infty$ （无穷远处分母比分子高两阶）.**

那么它的**积分主值**
$$
P \int_{-\infty}^{\infty} f(x) \mathrm{d}x = 2 \pi i \, \sum_{i} \mathrm{Res} \, f(z_i).
$$
其中，$z_i$ 是上半平面（或下班平面）的奇点.

**证明**    在上半平面做一个半圆路径 $C_R$ ，连接实轴上的 $z = \pm R$ 两点. 现在我们便形成了一个积分回路，可以对这条回路进行回路积分.
$$
P\int_{-\infty}^{\infty} f(x) \mathrm{d}x + \int_{C_R} f(z) \, \mathrm{d}z = 2 \pi i \, \sum_{i} \mathrm{Res} \, f(z_i).
$$

我们试图证明，在 $R \to \infty$ 的时候，上式的第二项，即半圆上的积分值为0. 由积分不等式和条件3，这是显然的：
$$
\left| \int_{C_R} f(z) \, \mathrm{d}z \right| \leq \max |f(z)| \cdot L = \max_{|z| = R} |f(z)| \cdot \pi R \\ 
= \pi \cdot \max_{|z| = R} |zf(z)| \to 0.
$$
因此
$$
P \int_{-\infty}^{\infty} f(x) \mathrm{d}x = 2 \pi i \, \sum_{i} \mathrm{Res} \, f(z_i).
$$
**注意**：

1. 积分主值

$$
P \int_{-\infty}^{\infty} f(x) \mathrm{d}x = \lim_{R \to \infty} \int_{-R}^{R} f(x) \mathrm{d}x.
$$

这个积分上下限的R是同步趋于无穷大的，因此和一般的无穷限反常积分不一样. 具体而言，**积分主值存在，反常积分不一定会存在；另外若反常积分存在，那么积分主值必然是反常积分值.**

2. 如果把上半平面改成下半平面，那么，由于路积分的正方向是逆时针的，于是路积分变成了这样：
$$
P\int_{\infty}^{-\infty} f(x) \mathrm{d}x + \int_{C_R} f(z) \, \mathrm{d}z = 2 \pi i \, \sum_{i} \mathrm{Res} \, f(z_i).
$$

因此，
$$
P \int_{-\infty}^{\infty} f(x) \mathrm{d}x = - 2 \pi i \, \sum_{i} \mathrm{Res} \, f(z_i).
$$
其中 $z_i$ 是下半平面的奇点.

**Ex. 对于积分**
$$
I = \int_{-\infty}^{\infty} \frac{\mathrm{d}x}{(1+x^2)^n} \qquad(n=1,2,3,\cdots),
$$
检查发现其满足：实轴上无奇点；只有两个奇点 $z = \pm i$ ，而且 $z \to \infty$ 时 $z / (1+z^2)^n \to 0$ . 因此可以采用上述方法求积分值.

经过变形
$$
\frac{1}{(1+x^2)^n} = \frac{1}{(x - i)^n (x+i)^n }
$$
因此，i是n阶极点，
$$
\begin{align}
\mathrm{Res} f(i) &= \frac{1}{(n-1)!} \lim_{x \to i} \frac{\mathrm{d}^{n-1}}{\mathrm{d} z^{n-1}} (x+i)^{-n} \\
&= \frac{1}{(n-1)!} (-n)(-n-1)\cdots(-2n+2)\cdot(2i)^{-2n+1} \\
&= \frac{1}{(n-1)!} (n)(n+1)\cdots(2n-2)\cdot(-1)^{n-1} \cdot(2)^{-2n+1} \cdot i(i)^{2n-2} \\
&= \frac{1}{(n-1)!} (n)(n+1)\cdots(2n-2)\cdot (2)^{-2n+1} \cdot i \\
&= \frac{(2n-2)!}{[(n-1)!]^2} (2)^{-2n+1} \cdot i
\end{align}
$$
因此
$$
P \int_{-\infty}^{\infty} \frac{\mathrm{d}x}{(1+x^2)^n} = - \pi \frac{(2n-2)!}{[(n-1)!]^2} 2^{-2n+2}.
$$
由阶估法可以显然看出这个反常积分是收敛的，因此积分主值就是定积分值.



##### Type III. 奇函数、偶函数分别与 $\sin x$ 、 $\cos x$ 的乘积在0到无穷的积分

Type II中对被积函数给出了很严格的要求：无穷处 $zf(z) \to 0$. 但是对于不满足这一条件的函数的积分，也不一定不存在. 如果被积函数

1. 可以表示成 $F(x) \cos mx$ 或者 $G(x) \sin mx$ 的形式，
2. 且上式中的 $F(x)$ 、 $G(x)$ 分别是偶函数和奇函数，
2. 且在上半平面（或下半平面）和实轴上满足当 $z \to \infty$ 时一致收敛于0.

则这种积分也是可以求的：
$$
\int_{0}^{\infty} F(x) \cos mx \mathrm{d}x = \frac{1}{2} \int_{-\infty}^{\infty} F(x) e^{imx} \mathrm{d}x, \\
\int_{0}^{\infty} G(x) \sin mx \mathrm{d}x = \frac{1}{2i} \int_{-\infty}^{\infty} G(x) e^{imx} \mathrm{d}x.
$$

**这是因为**

可以对上面两式进行变形：
$$
\begin{align}
\int_{0}^{\infty} F(x) \cos mx \mathrm{d}x 
&= \int_{0}^{\infty} F(x) \frac{e^{imx} + e^{-imx}}{2} \mathrm{d}x \\
&= \frac{1}{2} \int_{0}^{\infty} F(x) e^{imx} \mathrm{d}x - \frac{1}{2} \int_{0}^{-\infty} F(-x) e^{imx} \mathrm{d}x
\end{align}
$$
因为 $F(x)$ 是偶函数，上式
$$
\begin{align}
&= \frac{1}{2} \int_{0}^{\infty} F(x) e^{imx} \mathrm{d}x + \frac{1}{2} \int_{-\infty}^{0} F(x) e^{imx} \mathrm{d}x \\
&= \frac{1}{2} \int_{-\infty}^{\infty} F(x) e^{imx} \mathrm{d}x.
\end{align}
$$
同理，
$$
\begin{align}
\int_{0}^{\infty} G(x) \sin mx \mathrm{d}x 
&= \int_{0}^{\infty} G(x) \frac{e^{imx} - e^{-imx}}{2i} \mathrm{d}x \\
&= \frac{1}{2i} \int_{0}^{\infty} G(x) e^{imx} \mathrm{d}x + \frac{1}{2i} \int_{0}^{-\infty} G(-x) e^{imx} \mathrm{d}x \\
&= \frac{1}{2i} \int_{0}^{\infty} G(x) e^{imx} \mathrm{d}x - \frac{1}{2i} \int_{0}^{-\infty} G(x) e^{imx} \mathrm{d}x \\
&= \frac{1}{2i} \int_{-\infty}^{\infty} G(x) e^{imx} \mathrm{d}x.
\end{align}
$$
接下来问题就变成了证明在上半个平面上，函数 $F(x) e^{imx}$ 和函数 $G(x) e^{imx}$ 在无限大的半圆 $C_R$ 上的路积分是0. 即
$$
\lim_{R \to \infty} \int_{C_R} F(z) e^{imz} \mathrm{d}z = 0.
$$

将z表示为 $z = Re^{i\phi} = R(\cos \phi + i\sin \phi)$ ，
$$
\begin{align}
\left| \int_{C_R} F(z) e^{imz} \mathrm{d}z \right| &= \left| \int_0^{\pi} F(z) e^{imR \cos \phi} \cdot e^{-mR \sin \phi} iRe^{i\phi}\mathrm{d}\phi \right| \\
&\leq \max_{|z| = R} |F(z)| \cdot \left| 2\int_0^{\pi/2} Re^{-mR \sin \phi} \mathrm{d}\phi \right|
\end{align}
$$

后面这个积分可以通过放缩的方法估计出上界. 具体而言，因为 $e\sin \phi$ 在 $0 \to \pi/2$ 上是上凸的，因此
$$
\sin \phi \geq \frac{2}{\pi} \phi \\
e^{-mR \sin \phi} \leq e^{-mR \frac{2}{\pi} \phi}.
$$
注意到 $m > 0$ 的条件：
$$
\begin{align}
\left|\int_0^{\pi/2} Re^{-mR \sin \phi} \mathrm{d}\phi \right| &\leq \left|\int_0^{\pi/2} Re^{-mR \frac{2}{\pi} \phi} \mathrm{d}\phi \right| \\
&= \left| \frac{\pi}{2mR} \left. Re^{-mR \frac{2}{\pi} \phi} \right|_{\phi = 0}^{\pi/2} \right|\\
&= \left| \frac{\pi}{2m}(e^{-mR}- 1) \right| \to \frac{\pi}{2m}.
\end{align}
$$

而
$$
\max_{|z| = R} |F(z)| \to 0.
$$
因此在半圆上的积分为0. 这即是**约当引理**.

**Ex. 对于积分**
$$
\int_{-\infty}^{\infty} \frac{e^{imx}}{x-ia} \mathrm{d}x,\qquad \int_{-\infty}^{\infty} \frac{e^{imx}}{x+ia} \mathrm{d}x \quad(m>0, \mathrm{Re} \, \alpha > 0),
$$
可以看出它们都是约当引理适用的积分，前者的极点是 $z = ia$， 后者的极点是 $z = -ia$. 容易按照柯西公式得到
$$
\int_{-\infty}^{\infty} \frac{e^{imx}}{x-ia} = 2\pi i e^{-ma}.
$$

但是，对于第二个积分，注意到在上半平面做回路积分直接得0，而下半部分积分不为0. 那这是否意味着我对同一个积分获得了两个结果？ 并不是这样的. 实际上，**由于我们这里有 $m > 0$，因此按照约当引理，积分只能在上半平面进行**.

因此
$$
\int_{-\infty}^{\infty} \frac{e^{imx}}{x+ia} = 0.
$$


##### 实轴上有有限个单极点的情况

在Type II, III中，函数被限定了在实轴上没有奇点. 实际上，对于实轴上有有限个奇点的情况，我们也可以处理. 考虑奇点 $x_i$，我们在做积分的时候先画一个小半圆 $C_\epsilon$ 绕开它：
$$
\int_{\infty}^{-\infty} f(x) \mathrm{d}x + \int_{C_R} f(z) \, \mathrm{d}z - \int_{|z - x_i| < \epsilon} f(x) \mathrm{d}x = 2 \pi i \, \sum_{i} \mathrm{Res} \, f(z_i).
$$

对于小半圆上的积分
$$
\begin{align}
\int_{|z - x_i| < \epsilon} f(x) \mathrm{d}x &= \int_{|z - x_i| < \epsilon} \frac{a^{-1}}{z - x_i} \mathrm{d}x \\
&= \int_{0}^{\pi} a^{-1} {\epsilon}^{-1} e^{-i \phi} \cdot i\epsilon e^{i \phi} \mathrm{d}x \\
&= \pi i \mathrm{Res} \, f(x_i).
\end{align}
$$

因此
$$
\int_{\infty}^{-\infty} f(x) \mathrm{d}x = 2 \pi i \, \sum_{i} \mathrm{Res} \, f(z_i) + \pi i \mathrm{Res} \, f(x_i).
$$
**Ex.** 对于狄利克雷积分
$$
\int_{0}^{\infty} \frac{\sin x}{x} \mathrm{d}x,
$$
其满足Type III的条件，因此可以改写为：
$$
\frac{1}{2i} \int_{-\infty}^{\infty} \frac{e^{ix}}{x} \mathrm{d}x.
$$

观察这个积分，其除0点外无奇点. 按照上述说明
$$
\frac{1}{2i} \int_{-\infty}^{\infty} \frac{e^{ix}}{x} \mathrm{d}x = \frac{1}{2i} \pi i \cdot 1 = \frac{\pi}{2}.
$$

即
$$
\int_{0}^{\infty} \frac{\sin x}{x} \mathrm{d}x = \frac{\pi}{2}.
$$
