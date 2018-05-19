---
typora-copy-images-to: ../数学物理方法 总结
---

## 数学物理方法 总结

[TOC]

### Chap 3. 幂级数展开

与实变函数的泰勒级数类似，复变函数也可以展开成类似的幂级数。

#### 3.1 复数项级数

##### 收敛

对于一个复数项级数
$$
\sum_{k=0}^{\infty} w_k = \lim_{n \to \infty} \, \sum_{k=0}^{n} w_k = w_0 + w_1 + \cdots + w_k + \cdots
$$
如果左边的极限确实存在，且不为无穷大，那么就说这个复数项级数是**收敛**的. 

可以用柯西收敛定理来描述这件事：级数 $\sum_{k=0}^{\infty} w_k$ 收敛的充分必要条件是若对于任意小正数$\epsilon$，必有一N存在，使得对于所有的$n>N$，都有
$$
\left| \sum_{k=n+1}^{n+p} w_k \right| < \epsilon,
$$
其中p为任意正整数.

实际上，由于该级数的每一项都可以分解为$w_k = u_k + i v_k$，从而
$$
\lim_{n \to \infty} \, \sum_{k=0}^{n} w_k = \lim_{n \to \infty} \, \sum_{k=0}^{n} u_k + i\lim_{n \to \infty} \, \sum_{k=0}^{n} v_k.
$$
于是一个复数项级数收敛的问题即可转化为两个实数项级数收敛的问题.

##### 绝对收敛

**绝对收敛**即级数每一项的模组成的级数也收敛，也就是实数项级数
$$
\sum_{k=0}^{\infty} |w_k| = \sum_{k=0}^{\infty} \sqrt{u_k^2 + v_k^2}
$$
收敛. 

绝对收敛的级数具有这样的性质：

- 各项先后次序可以任意改变，而级数值不变.

- 设两个绝对收敛级数 $\sum^{\infty} p_k = A, \sum^{\infty} q_k = B$，则 $\sum_{k}^{\infty} p_k \cdot \sum_{k}^{\infty} q_k = \sum_{k}^{\infty} \sum_{l}^{\infty} p_k q_l = AB$.

##### 函数项级数的一致收敛

现在讨论函数项级数
$$
\sum_{k=0}^{\infty} w_k(z) = w_0(z) + w_1(z) + \cdots + w_k(z) + \cdots,
$$

函数项级数一致收敛概念的核心在于：级数的收敛性不依赖于z. 使用柯西收敛定理的语言表述即是：如果对于某个区域B上所有的点，对于任意小正数$\epsilon$，必有一 $N(\epsilon)$ 存在，使得对于所有的$n>N(\epsilon)$，都有
$$
\left| \sum_{k=n+1}^{n+p} w_k \right| < \epsilon,
$$
其中p为任意正整数，那么则称函数项级数 $\sum_{k=0}^{\infty} w_k(z)$ 在B上一致收敛. 

注意上面定理的陈述中，N的选取只依赖于 $\epsilon$ ，与z取何值无关.

可以将实数项一致收敛级数收敛的一些性质照搬过来：
- **和函数连续：**如果在B上一致收敛的级数每一项 $w_k(z)$ 都是B上的连续函数，那么级数和 $w(z)$ 也是B上的连续函数.

- **逐项积分：**如果在l上一致收敛的级数每一项 $w_k(z)$ 都是l上的连续函数，那么级数和 $w(z)$ 也是l上的连续函数，且级数可以沿l逐项积分（积分号可以提出、拿进求和号）.

- **逐项求导：**若 $\sum_{k=0}^{\infty} w_k(z)$ 在 $\bar B$ 中一致收敛，$w_k(z)$ 在 $\bar B$ 中**单值解析**，则级数的和 $w(z)$ 也是 $\bar B$ 中的**单值解析**函数， $w(z)$ 的各阶导数可以由 $\sum w_k(z)$ 逐项求导得到，即 $ w^{(n)}(z) = \sum w_k^{(n)}(z) $. 且 $\sum w_k^{(n)}(z) $ 在$\bar B$ 中一致收敛.

- **M判别法：** 若在区域B上，$w_k(z)$ 满足 $|w_k(z)| \leq m_k$ ，而常数项级数 $\sum_{k=0}^{\infty} m_k$ 收敛，则 $\sum_{k=0}^{\infty} w_k(z)$ 在B上**绝对一致收敛**.




#### 3.2 幂级数

对于形如
$$
\sum_{k=0}^{\infty} a_k(z - z_0)^k = a_0 + a_1(z - z_0) + a_2(z - z_0)^2 + \cdots
$$
其中的 $z_0, a_k$ 都是复常数，这样的级数称以 $z_0$ 为中心的**幂级数**.

##### 达朗贝尔判别法

对于上述幂级数，如果
$$
\lim_{k \to \infty} \frac{|a_{k+1}||z - z_0|^{k+1}}{|a_k||z - z_0|^{k}} = \lim_{k \to \infty} \frac{|a_{k+1}|}{|a_k|} |z - z_0| < 1,
$$
则该幂级数绝对收敛. 引入**收敛半径** 
$$
R = \lim_{k \to \infty} \frac{|a_{k}|}{|a_{k+1}|}, 
$$
于是若有
$$
|z-z_0| < R,
$$
则该幂级数**绝对一致收敛**，$|z-z_0| < R$ 所成的区域叫做**收敛圆**. 收敛圆以外的范围，级数必然是发散的；而位于收敛半径R上的点的敛散性需要具体分析.

收敛半径R也有从根值判别法得来的另一个表达式
$$
R = \lim_{k \to \infty} \frac{1}{\sqrt[n]{|a_k|}}.
$$

##### 和函数的解析性质

利用一致收敛级数可逐项积分的性质：对于幂级数
$$
w(\xi) = a_0 + a_1(\xi - z_0) + a_2(\xi - z_0)^2 + \cdots,
$$
用 $\frac{1}{2 \Pi i} \frac{1}{\xi - z}$ 遍乘各项，在沿收敛圆内一个缩小的圆周积分
$$
\begin{align}
\frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{w(\xi)}{\xi - z} \, \mathrm{d} \xi& = \\
& \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{a_0}{\xi - z} \, \mathrm{d} \xi + 
\frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{a_1(\xi - z_0)}{\xi - z} \, \mathrm{d} \xi + 
\frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{a_2(\xi - z_0)^2}{\xi - z}  \, \mathrm{d} \xi + \cdots,
\end{align}
$$

而右边的每一项中的幂函数在复平面上是解析的，应用柯西公式：
$$
\frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{w(\xi)}{\xi - z} \mathrm{d} \xi = w(z) = a_0 + a_1(z - z_0) + a_2(z - z_0)^2 + \cdots,
$$
这意味着**幂级数的和函数在收敛圆内是解析函数**，自然在收敛圆内可以求任意多次导，又可以逐项积分.



#### 3.3 泰勒级数展开

与实变函数类似，如果函数 $f(z)$ 在 $z_0$ 为圆心的圆 $C_R$ 中解析，则对园内任意的 $z$ 点，$f(z)$ 可以展开成幂级数
$$
f(z) = \sum_{k=0}^{\infty} a_k (z - z_0)^k,
$$
其中
$$
a_k = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{(\xi - z_0)^{k+1}} \mathrm{d} \xi = \frac{f^{(k)}(z_0)}{k!} ,
$$
$C_{R_1}$ 是 $C_R$ 内任意一个包含z的同心圆（其实由柯西公式，也可以不是圆）.

**证明** 对该定理的证明采用了技巧 $ \frac{1}{1-x} = 1 + x + x^2 + \cdots $，

先用柯西公式
$$
f(z) = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{\xi - z} \mathrm{d} \xi.
$$
为了写成 $z_0$ 处的展开，需要将 $\frac{f(\xi)}{\xi - z}$ 变成 $\frac{f(\xi)}{\xi - z_0}$ . 于是采用上面的技巧：
$$
f(z) = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{\xi - z_0} \cdot \frac{\xi - z_0}{\xi - z} \mathrm{d} \xi
$$
其中，
$$
\frac{\xi - z_0}{\xi - z} = \frac{1}{\frac{\xi - z}{\xi - z_0}} = \frac{1}{1 - \frac{z - z_0}{\xi - z_0}} = 
1 + \frac{z - z_0}{\xi - z_0} + \left( \frac{z - z_0}{\xi - z_0} \right)^2 + \left( \frac{z - z_0}{\xi - z_0} \right)^3 + \cdots.
$$
若要该级数收敛，需满足 $\left| \frac{z - z_0}{\xi - z_0} \right| < 1$ ，这是显然的，因为我们的积分路径包含了 $z,z_0$. 代回原式，
$$
\begin{align}
f(z) & = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{\xi - z_0} \cdot \left[ 1 + \frac{z - z_0}{\xi - z_0} + \left( \frac{z - z_0}{\xi - z_0} \right)^2 + \left( \frac{z - z_0}{\xi - z_0} \right)^3 + \cdots \right] \mathrm{d} \xi \\
& = \sum_{k=0}^{\infty} \frac{1}{2 \pi i} (z - z_0)^k \, \oint_{C_{R_1}} \frac{f(\xi)}{(\xi - z_0)^{k+1}} \, \mathrm{d} \xi \\
& = \sum_{k=0}^{\infty} \frac{f^{(k)}(z_0)}{k!}(z - z_0)^k.
\end{align}
$$
其中第三个等号利用了柯西公式以及解析函数可以任意次求导的性质.

**解析函数在某个邻域的泰勒展开是唯一的.** 这一点可以通过设一个解析函数在同一点有两组展开系数，然后通过对原函数反复求导，证明这些系数都是一样的.

作为幂级数的泰勒展开，必然也存在收敛半径的概念. 这个收敛一般是达到最近非解析点的距离. 值得说明的是，在收敛半径内时，这个无穷级数的和在一点的值就是确切的的原函数在这一点的值. 

##### 例子

##### Ex 1. 函数 $e^z$ 在 $z_0 = 0$ 点处的展开

首先， $e^z$ 的解析性质足够好，在 $z_0 = 0$ 处必然是解析的，因此在该处展开是可行的. 另外，显然也有
$$
\left. (e^z)^{(k)} \right|_{z = 0} = 1,
$$
因此得到$e^z$ 在 $z_0 = 0$ 点处的展开式
$$
e^z = 1 + \frac{z}{1!} + \frac{z^2}{2!} + \frac{z^3}{3!} + \cdots = \sum_{k=0}^{\infty} \frac{z^k}{k!}.
$$
计算收敛半径得到
$$
R = \lim_{k \to \infty} \frac{|1/k!|}{|1/(k+1)!|} = \lim_{k \to \infty} (k+1) = \infty.
$$
因此，该幂级数对 $z < \infty$ 全部收敛. 考虑到 $e^z$ 本身就是在整个复平面收敛，这一点并不奇怪.

##### Ex 2. 函数 $\sin z$ 在 $z_0 = 0$ 点处的展开

首先，$\sin z$ 在 $z_0 = 0$ 处解析，因此可以泰勒展开. 不过既然泰勒展式唯一，我们可以不通过直接求导的方式，而通过其他间接的手段展开它，比如利用
$$
\begin{align}
\sin z &= \frac{1}{2i} \left( e^{iz} - e^{-iz} \right) \\
&= \frac{1}{2i} \left[ \left( \frac{iz}{1!} + \frac{(iz)^2}{2!} + \frac{(iz)^3}{3!} + \cdots \right) - 
\left( \frac{(-iz)}{1!} + \frac{(-iz)^2}{2!} + \frac{(-iz)^3}{3!} + \cdots \right) \right] \\
&= \frac{1}{2i} \left( \frac{2iz}{1!} + \frac{2(iz)^3}{3!} + \cdots \right) \\
&= \frac{z}{1!} - \frac{z^3}{3!} + \frac{z^5}{5!} + \cdots.
\end{align}
$$
收敛半径是无穷大.

##### Ex 3. 函数 $\sqrt[m]{z}$ 在 $z_0 = 1$ 处的展开 —— 警惕函数的多值性

这里的例子采用的 $\sqrt[m]{z}$ 是一个典型的多值函数. 多值性体现在
$$
\sqrt[m]{z} = \sqrt[m]{\rho e^{i(\phi + 2k\pi)}} 
= \rho^{\frac{1}{m}} e^{i\frac{\phi}{m}} \cdot e^{i\frac{2k\pi}{m}} \quad (k=0, 1, \cdots , m-1).
$$

因此，在展开的时候，需要小心谨慎而不能损失该函数的每一支.
$$
\left( \sqrt[m]{z} \right)' = \frac{1}{m} z^{\frac{1}{m} - 1} \implies \left. \left( \sqrt[m]{z} \right)' \right|_{z = 1} = \frac{1}{m} \cdot 1^{\frac{1}{m}}, \\
\left( \sqrt[m]{z} \right)'' = \frac{1}{m} \left( \frac{1}{m} - 1 \right) z^{\frac{1}{m} - 2} \implies \left. \left( \sqrt[m]{z} \right)' \right|_{z = 1} = \frac{1}{m} \left( \frac{1}{m} - 1 \right) \cdot 1^{\frac{1}{m}}, \\
\vdots \\
\left( \sqrt[m]{z} \right)^{(n)} = \prod_{k=0}^{n - 1}\left( \frac{1}{m} - k \right) z^{\frac{1}{m} - n} \implies \left. \left( \sqrt[m]{z} \right)^{(n)} \right|_{z = 1} = \prod_{k=0}^{n - 1}\left( \frac{1}{m} - k \right) \cdot 1^{\frac{1}{m}}. \\
$$
因此，
$$
\begin{align}
\sqrt[m]{z} &= 1^{\frac{1}{m}} + \frac{1}{1!}\frac{1}{m} \cdot 1^{\frac{1}{m}} (z-z_0) + \frac{1}{2!}\frac{1}{m} \left( \frac{1}{m} - 1 \right) \cdot 1^{\frac{1}{m}} (z-z_0)^2 + \cdots + \frac{1}{n!}\prod_{k=0}^{n - 1}\left( \frac{1}{m} - k \right) \cdot 1^{\frac{1}{m}} (z-z_0)^n + \cdots \\
&= 1^{\frac{1}{m}} \sum_{n=0}^{\infty} \frac{1}{n!}\prod_{k=0}^{n - 1}\left( \frac{1}{m} - k \right) (z-z_0)^n.
\end{align}
$$
函数的多值性保留在因子 $1^{\frac{1}{m}}$ 上. 求得收敛半径为 $R=1.$

有一个值得注意的细节：当给定了多值函数的某一支，即指定了因子 $e^{i\frac{2k\pi}{m}}$ 中的k之后，**继续求导并不会使得导数也产生多值性**. 换言说，原函数的k和导数的k是保持一致的. 这一点应该显然——一个单值分支的分支导数存在且唯一，这是可导的定义所规定的. 没有求着求着导就跑到其他分支上的道理.

#### 3.4 解析延拓

若函数 $f(z)$ 在区域b中解析，函数 $F(z)$ 在区域B中解析，且B包含b，在b上有
$$
f(z) = F(z),
$$
则称 $F(z)$ 为 $f(z)$ 在b中的解析延拓.

**一个重要的性质：一个函数的解析延拓是唯一的.** 一般地说：如果两个解析函数在某个域中相等，那么他们在整个定义域上都相等. 这是解析函数无限阶可导的必然结果. 这一性质对于连续可导实函数而言没有. 因此可见解析是一个非常强的要求.

#### 3.5 洛朗级数展开

泰勒级数展开要一个解析区域内才能进行；当所研究的区域上出现奇点了以后，就不能再把函数展开成泰勒级数，而需要转而考虑在去除奇点的**环域**上展开。这样的展开叫做**洛朗级数展开**。

洛朗级数跟泰勒级数最大的不同就在于它引入了负幂次项：
$$
\cdots + a_{-2}(z-z_0)^{-2} + a_{-1}(z-z_0)^{-1} + a_0 + a_{1}(z-z_0) + a_{1}(z-z_0)^2 + \cdots
$$
先研究这种级数的收敛性问题. 正幂部分的收敛情况不再赘述；负幂部分的的收敛情况，也可以通过比值判别法来判断收敛半径 $R_2$ ：
$$
1 > \lim_{k \to \infty} \frac{a_{-(k+1)}(z-z_0)^{-(k+1)}}{a_{-k}(z-z_0)^{-k}} = \lim_{k \to \infty} \frac{a_{-(k+1)}}{a_{-k}}(z-z_0)^{-1} \\
\implies R_2 = \lim_{k \to \infty} \frac{a_{-k}}{a_{-(k+1)}}.
$$

##### 将函数展开为洛朗级数

设函数 $f(z)$ 在环域上单值解析，则对环域上的任意一点z，$f(z)$ 可以展成幂级数
$$
f(z) = \sum_{k=-\infty}^{\infty} a_k(z-z_0)^k.
$$
其中，展开系数
$$
a_k = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{(\xi - z_0)^{k+1}} \mathrm{d} \xi.
$$
需要小心的是，虽然看上去和泰勒展开系数一模一样，但是这个系数已经不再是 $f^{(k)}(z_0)/{k!}$. 

**证明** 依旧是套用柯西公式，不过这次需要应用复连通域的柯西公式：
$$
f(z) = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{\xi - z} \mathrm{d} \xi - 
\frac{1}{2 \pi i} \oint_{C_{R_2}} \frac{f(\xi)}{\xi - z} \mathrm{d} \xi .
$$
其中， $R_1$ 是处于外面的大圆，$R_2$ 是处于里面的小圆. 同样做变形处理：
$$
\begin{align}
f(z) & = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{\xi - z_0} \cdot \frac{\xi - z_0}{\xi - z} \mathrm{d} \xi - 
\frac{1}{2 \pi i} \oint_{C_{R_2}} \frac{f(\xi)}{\xi - z_0}\cdot \frac{\xi - z_0}{\xi - z} \mathrm{d} \xi \\
& = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{\xi - z_0} \frac{1}{1 - \frac{z - z_0}{\xi - z_0}} \mathrm{d} \xi - \frac{1}{2 \pi i} \oint_{C_{R_2}} \frac{f(\xi)}{\xi - z_0}\cdot \left( - \frac{1}{z - z_0} \frac{1}{1 - \frac{\xi - z_0}{z - z_0}} \right) \mathrm{d} \xi . \\
& = \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{\xi - z_0} \cdot \left[ 1 + \frac{z - z_0}{\xi - z_0} + \left( \frac{z - z_0}{\xi - z_0} \right)^2 + \left( \frac{z - z_0}{\xi - z_0} \right)^3 + \cdots \right] \mathrm{d} \xi \\
& + \frac{1}{2 \pi i} \oint_{C_{R_2}} \frac{f(\xi)}{\xi - z_0} \cdot \left[ (\frac{z - z_0}{\xi - z_0})^{-1} + \left( \frac{z - z_0}{\xi - z_0} \right)^{-2} + \left( \frac{z - z_0}{\xi - z_0} \right)^{-3} + \cdots \right] \mathrm{d} \xi \\
\end{align}
$$
上式第二个等号做的变形中，由于 $ \frac{1}{1-x} = 1 + x + x^2 + \cdots $ 的收敛域是 $R < 1$，而在小圆处，有 $\xi - z_0$ 小于 $z - z_0$，因此采用这样的变形方式，使得较大的 $z - z_0$ 在分母上，从而便能够使用上述展开式.

右考虑到，因为该函数在环域上解析，因此可以把第二个积分号中的 $C_{R_2}$ 扩张到 $C_{R_1}$ 而不改变其值. 这样处理后，两个积分可以合并成一个：
$$
f(z) = \sum_{k=-\infty}^{\infty} (z-z_0)^k \cdot \frac{1}{2 \pi i} \oint_{C_{R_1}} \frac{f(\xi)}{(\xi - z_0)^{k+1}} \mathrm{d} \xi.
$$


##### 洛朗展开的唯一性

**证明**比较有趣.

设一个函数可以展开成两个洛朗级数
$$
f(z) = \sum_{k=-\infty}^{\infty} a_k(z-z_0)^k = \sum_{k=-\infty}^{\infty} b_k(z-z_0)^k.
$$
两遍乘上 $(z - z_0)^{-n-1}$ ，然后两边沿着收敛环域的一个小回路积分：
$$
\sum_{k=-\infty}^{\infty} \oint a_k(z-z_0)^{k-n-1} \mathrm{d}z = \sum_{k=-\infty}^{\infty} \oint b_k(z-z_0)^{k-n-1} \mathrm{d}z.
$$

因为在该区域上解析性质足够好，我们把求和号提出了积分号. 而
$$
\oint a_k(z-z_0)^{k-n-1} \mathrm{d}z = 2\pi i a_k \, \delta_{k,n}
$$
因此可以得到每一项 $a_k = b_k$. 洛朗级数的唯一性得证.



#### 3.6 孤立奇点的分类

##### 孤立奇点、非孤立奇点
若 $f(z)$ 在 $z = z_0$ 不可导，可是在 $z = z_0$ 的小邻域内的其他点都可导，则 $z_0$ 是孤立奇点。如果在任意小邻域里都能找到其他奇点， $z_0$ 就是非孤立奇点。

##### 可去奇点、极点、本性奇点
若 $f(z)$ 在孤立奇点 $z = z_0$ 处形成的环域上展成的洛朗级数没有负幂项，则 $z = z_0$ 是**可去奇点**。
Ex. $f(z) = \sin z / z, z = 0.$

若有有限个负幂项，则称 $z = z_0$ 是**极点**，根据负幂项的个数（m个），称为**m阶极点**.

若有无穷个负幂项，则称 $z = z_0$ 是**本性奇点**.

##### 例子

Ex.研究下面这个函数的奇点
$$
f(z) = \frac{(z^2-1)(z-2)^3}{(\sin \pi z)^3}.
$$

首先，在 $z \notin \mathbb{Z}$ 的地方，该函数全都解析. 讨论 $z \in \mathbb{Z}$ 的情况：
- 在 $z = \pm 1$ 的地方，意识到只要往分子上补上一个 $(z \pm 1)^2$ ，该函数就能恢复解析性质，因此 $\pm 1$ 是二级极点.
- 在 $z = 2$ 的地方，由于该点极限存在，因此是一个可去极点.




