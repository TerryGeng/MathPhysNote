## 数学物理方法 总结

[TOC]

### Chap 11. 柱函数

本章主要介绍了几种在求解柱坐标系下Laplace方程、Helmholtz方程以及在求坐标系下求解Helmholtz方程产生的具体解法，尤其是解中一些特殊函数的性质.

#### Bessel函数的引入，几种方程的解法

##### 柱坐标下的Laplace方程

柱坐标下的Laplace方程
$$
\frac{1}{r} \frac{\partial}{\partial r}\left( r  \frac{\partial u}{\partial r} \right) + \frac{1}{r^2}\frac{\partial^2 u}{ \partial \phi^2} + \frac{\partial^2 u}{ \partial z^2} = 0.
$$
**边界条件**只能取关于z的与关于r的，因为关于$\phi$已经有了隐含的自然边界条件. 如果出现了其他额外的关于$\phi$的边界条件，除非边界条件比较特殊，方程将不再能通过Strum-Liouville定理求解. 

按 $u = R(r) \Phi(\phi) Z(Z)$ 分离变量，得到
$$
\begin{cases}
\Phi'' + m^2 \Phi = 0, \\
Z'' - \mu Z = 0, \\
R'' + \frac{1}{r}R' + \left( \mu - \frac{m^2}{r^2} \right) R = 0.
\end{cases}
$$
其中第一式与隐含的周期性边界条件构成本征值问题，得到的解为
$$
\Phi(\phi) = A \cos m \phi + B \sin m\phi, \quad m = 0,1,2,3,\cdots
$$
之后的处理与边界条件的取法有关. 

**A. 如果边界条件取在r上**，径向方程与边界条件构成Strum-Liouville本征值问题. 将径向方程化为Strum-Liouville形式
$$
R'' + \frac{1}{r}R' + \left( \mu - \frac{m^2}{r^2} \right) R = 0 \\
\iff \frac{\mathrm{d}}{\mathrm{d} r}\left[ r \frac{\mathrm{d} R}{\mathrm{d} r} \right] - \frac{m^2}{r}  R  + \mu r R = 0
$$
可以看出，按照Strum-Liouville定理，在配上相应的边界条件以后，该方程的解为一族完备且带权正交的本征函数 $R_n(r)$ ，权为 $r$. 本征值为 $\mu_n$ ，且均大于等于0. 

径向方程的视 $\mu$ 的取值而划分成不同种类，每个种类的解有单独的符号（贝塞尔函数）表示. 对于 $\mu > 0$ ，令 $x = \sqrt{\mu}r$ ，$R$ 方向方程化为**m阶Bessel方程**
$$
x^2 R'' + xR' + (x^2 - m^2)R = 0.
$$
它的解为 $J_m, N_{m}$ . 于是 $R_n(r) = C_1 J_m(\sqrt{\mu_n}r) + C_2 N_m(\sqrt{\mu_n}r)$. 其中本征值 $\mu_n$ 的具体值与两常数由边界条件决定. 

例如，如果求解区域在圆柱内，由自然边界条件可得所有 $C_{n2}$ 都是 0（见下文）. 这时，对于边界条件 $u_{r = r_0} = 0,$ 那么有 $\sqrt{\mu_n}r_0$ 就是 $J_m$ 的零点. 如果设 $J_m$ 的零点从小到大分别为 $x_1, x_2, \cdots$ ，则
$$
\mu_n = \left( \frac{x_n}{r_0} \right)^2.
$$

如果有 $\mu = 0$ ，方程退化为Euler方程.
$$
R_n = 
\begin{cases}
E_1 + E_2 \ln \rho, \quad m=0 \\
E_1 r^m + E_2 r^{-m}, \quad m \neq 0.
\end{cases}
$$

综上，径向方程的本征函数可以写为
$$
m = 0 : \quad R_n(r) = 
\begin{cases}
C_{01} + C_{02} \ln \rho, \quad \mu_n = 0 \\
C_{n1} J_0(\sqrt{\mu_n}r) + C_{n2} N_0(\sqrt{\mu_n}r), \quad \mu_n > 0 \\
\end{cases} \\
\, \\
m \neq 0 : \quad R_n(r) = 
\begin{cases}
C_{01} r^m + C_{02} r^{-m}, \quad \mu_n = 0 \\
C_{n1} J_m(\sqrt{\mu_n}r) + C_{n2} N_m(\sqrt{\mu_n}r), \quad \mu_n > 0 \\
\end{cases}
$$

注：具体 $\mu$ 是否可以取0，需要每次代入尝试. 如果可以取0，则0是本征值之一，否则不是.

我们将求得的一系列本征值 $\mu_n$ 代入 $Z'' - \mu Z = 0$ ，即可得到一系列 $Z$ 的解
$$
Z_n = 
\begin{cases}
A_n e^{\sqrt{\mu_n} z} + B_n e^{\sqrt{-\mu_n} z}, \quad \mu_n \neq 0, \\
A_0 + B_0z,\quad \mu_n = 0.
\end{cases}
$$


**B. 如果边界条件取在z上**，关于Z的方程 $ Z'' - \mu Z = 0$ 与边界条件构成Strum-Liouville本征值问题. 化为Strum-Liouville方程，
$$
\frac{\mathrm{d}}{\mathrm{d} z}\left[ \frac{\mathrm{d} Z}{\mathrm{d} z} \right] + (-\mu)  y = 0,
$$
根据Strum-Liouville定理，本征值 $-\mu > 0$ 即 $\mu < 0$ .  这一点也可以直接从该方程解的样式判断出来（ $\mu > 0$ 得到的是指数形式的解 ）.记 $-\mu = \nu^2$

因此，Z的一系列本征解即是
$$
Z_n = A_n \sin \nu_n z + B_n \cos \nu_n z.
$$
其中 $\nu_n$ 和常数由边界条件决定.

把求得的 $\nu_n$ 代入径向方程，令 $x = \nu_n r$ ，方程化为**m阶虚宗量Bessel方程**
$$
x^2 R'' + xR' - (x^2 + m^2)R = 0.
$$
它的解为 $I_m, K_m$. $R_n(r) = C_1 I_m(\nu_n r) + C_2 K_m(\nu_n r)$. 两常数由求解区域决定. 如果在柱内，由自然边界条件解只能取 $I_m$ ，而柱外只能取 $K_m$ .



##### 柱坐标下的Helmholtz方程

柱坐标下的Helmholtz方程
$$
\frac{1}{r} \frac{\partial}{\partial r}\left( r  \frac{\partial u}{\partial r} \right) + \frac{1}{r^2}\frac{\partial^2 u}{ \partial \phi^2} + \frac{\partial^2 u}{ \partial z^2} + k^2 v = 0,
$$

**边界条件必须是关于r和z齐次的，而不含关于 $\phi$ 的边界条件.** 这是由于，对于一个含有n个变量的偏微分方程，按照我们的处理方法，我们需要用n-1个其次“边界条件”定出n-1的变量的本征函数，再用这n-1个本征函数去展开剩下一个变量的“初始条件”. Helmholtz是由球坐标或者柱坐标下的扩散、波动方程给出的，一共四个变量，其中作为初始条件的是时间变量t. 因此对剩下的三个空间变量必须有其次边界条件. 而对于 $\phi$ ，已经有了隐含的周期性边界条件，因此边界条件不能再包含 $\phi$ 的边界条件（除非能和周期性边界条件统一起来，得到一组新的本征函数）. 对于边界条件不齐次的情况，需要按照Chap 8中介绍的方式，通过把边界条件齐次化的方式处理.

同样按 $u = R(r) \Phi(\phi) Z(Z)$ 分离变量，得到
$$
\Phi'' + m^2 \Phi = 0, \\
Z'' - \mu Z = 0, \\
R'' + \frac{1}{r}R' + \left( k^2+\mu - \frac{m^2}{r^2} \right) R = 0.
$$
二式和三式分别与给定的齐次边界条件构成Strum-Liouville本征值问题.

将二式写为Strum-Liouville形式
$$
\frac{\mathrm{d}}{\mathrm{d} z}\left[ \frac{\mathrm{d} Z}{\mathrm{d} z} \right] + (-\mu)  y = 0,
$$
根据Strum-Liouville定理，本征值 $-\mu > 0$ 即 $\mu < 0$ .因此，Z的一系列本征解即是
$$
Z_n = A_n \sin \sqrt{-\mu_n} z + B_n \cos \sqrt{-\mu_n} z.
$$
其中本征值 $\mu_n$ 和常数由边界条件决定. 为了形式优雅，取 $\sqrt{-\mu_n} = \nu_n$ ，
$$
Z_n = A_n \sin \nu_n z + B_n \cos \nu_n z.
$$


再将径向方程写成Strum-Liouville形式
$$
\frac{\mathrm{d}}{\mathrm{d} r}\left[ r \frac{\mathrm{d} R}{\mathrm{d} r} \right] -\frac{m^2}{r}R  + (-\nu^2+k^2) r R = 0.
$$


按照Strum-Liouville定理，在配上关于r的边界条件以后，该方程的解为一族完备且带权正交的本征函数 $R_{n,l}(r)$ ，权为 $r$. 本征值为 $-\nu^2+k^2$. 

本征值 $-\nu^2+k^2$ 大于0. 为了方便用已有的记号把解的形式表示出来，取 $x = \sqrt{-\nu^2+k^2} r$ ，方程再次化为**m阶Bessel方程**，
$$
x^2 R'' + xR' + (x^2 - m^2)R = 0.
$$
它的解为 $J_m, N_{m}$ . 于是 $R_{n,l}(r) = C_1 J_m(\sqrt{-\nu_n^2+k_{n,l}^2} r) + C_2 N_m(\sqrt{-\nu_n^2+k_{n,l}^2} r)$. 其中本征值 $-\nu_n^2+k_{n,l}^2$ 的具体值与两常数由关于r的边界条件决定. 记 $\mu'_{n,l} = -\nu_n^2+k_{n,l}^2$ ，于是
$$
R_{n,l}(r) = C_1 J_m(\sqrt{\mu'_{n,l}} r) + C_2 N_m(\sqrt{\mu'_{n,l}} r).
$$


##### 球坐标下的Helmholtz方程

球坐标下的Helmholtz方程
$$
\frac{1}{r^2}\frac{\partial }{\partial r} \left(r^2 \frac{\partial v}{\partial r} \right) 
+  \frac{1}{r^2 \sin \theta}\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial v}{\partial \theta}\right)
+  \frac{1}{r^2 \sin^2 \theta}\frac{\partial^2 v}{\partial \phi^2} + k^2 v= 0.
$$
**边界条件必须是关于 $r$ 齐次的，而不额外含关于 $\phi, \theta$ 的边界条件.** 因为关于 $\phi$ 有隐含的周期性边界条件，而关于 $\theta$ 有隐含的自然边界条件.

分离变量后角度相关的方程依然是球函数方程，径向方程比Laplace方程的情况化多出一项：
$$
\frac{\partial^2 \Phi}{\partial \phi^2} + m^2 \Phi = 0, \\
\sin \theta\frac{\partial }{\partial \theta} \left( \sin \theta  \frac{\partial \Theta}{\partial \theta}\right)
+  (  l(l+1) \sin^2\theta - m^2)\Theta = 0, \\
\frac{\partial }{\partial r} \left(r^2 \frac{\partial R}{\partial r} \right)  + [k^2r^2-l(l+1) ]R = 0.
$$
一式的解由周期性边界条件定出
$$
\Phi_m(\phi) = A_m \cos m\phi + B_m \sin m\phi, m = 0,1,2,\cdots.
$$
二式进行变量代换 $\cos \theta = x, x\in [-1,1]​$ ，记 $\Theta(\theta) = y(x)​$ ，
$$
\frac{\mathrm{d}}{\mathrm{d} x} \left[ (1-x^2) \frac{\mathrm{d}y}{\mathrm{d} x} \right] + \left[  l(l+1) - \frac{m^2}{1-x^2} \right] y = 0.
$$
得到连带Legendre方程. 在 $x = \pm 1$ 处函数值收敛的自然边界条件下， $l = 0,1,2,3,\cdots$ ，本征解为
$$
\Theta^m_l(\theta) =  P_l^m(x) =  A^m_l P_l^m(\cos \theta).
$$

对三式，又称为**球Bessel方程**，可以看出来该式本征值为 $k^2$ ，本征解 $R_n$ 以 $r^2$ 作为权正交. 进行变数代换，令 $x = kr, R(r) = \sqrt{\frac{\pi}{2x}}y(x)$ ，化为**半奇数阶Bessel方程**：
$$
x^2y'' + xy' + [x^2-(l+1/2)^2]y = 0
$$

$y$ 的解为 $J_{l+1/2},J_{-l-1/2}​$ （或者 $N_{l+1/2}​$ ，在这三个中任取两个），因此 
$$
\begin{align}
R_n(r) &= A_n \sqrt{\frac{\pi}{2x}} J_{l+1/2}(k_n r) + B_n \sqrt{\frac{\pi}{2x}} J_{-l-1/2}(k_n r) \\
&\equiv A_n j_l(k_n r) + B_n n_{l}(k_n r).
\end{align}
$$

其中 $k, A, B$ 由关于 $r$ 的边界条件决定.



#### 几类Bessel函数 $J_\nu, N_\nu, H_\nu, I_\nu, K_\nu, j_\nu, n_\nu, h_\nu$

##### Bessel方程的解：$J_\nu, N_\nu, H_\nu$

可以看出来，作为Bessel方程以及球Bessel函数的解有很多种表达形式. 依次介绍之：

###### 第一类Bessel函数
$$
J_\nu(x) = \sum_{k=0}^{+\infty}  (-1)^k \frac{1}{k! \Gamma(\nu+k+1)} {\left(\frac{x}{2}\right)}^{2k+\nu}, \\
J_{-\nu}(x) = \sum_{k=0}^{+\infty}  (-1)^k \frac{1}{k! \Gamma(-\nu+k+1)} {\left(\frac{x}{2}\right)}^{2k-\nu}.
$$

当 $\nu = m$ 取整数时，上式化为
$$
J_m(x) = \sum_{k=0}^{+\infty}  (-1)^k \frac{1}{k! (m+k)!} {\left(\frac{x}{2}\right)}^{2k+m}. \\
J_{-m}(x) = \sum_{k=m}^{+\infty}  (-1)^k \frac{1}{k! \Gamma(-m+k+1)} {\left(\frac{x}{2}\right)}^{2k-m} = (-1)^m J_m(x).
$$

可以看出来 $J_{-m}$ 不再是Bessel方程的线性无关的一个解. 此时另一个线性无关解应使用Neumann函数表示.

**渐进行为：**
$$
\begin{align}
x \to \infty, \quad
J_\nu &\to \sqrt{\frac{2}{\pi x}} \cos \left(x - \nu \pi - \frac{\pi}{4} \right). \\
\end{align}
$$


![Bessel_Functions_(1st_Kind,_n=0,1,2)](https://github.com/TerryGeng/MathPhysNote/raw/master/img/Bessel_Functions_(1st_Kind%2C_n%3D0%2C1%2C2).svg)



![BesselJ_Function3D](https://github.com/TerryGeng/MathPhysNote/raw/master/img/BesselJ_Function3D.png)


在不同其次边界条件下，$J_m$ 的模可以分别写成

1. 对于第一类齐次边界条件 $ J_m(\sqrt{\mu_n} r_0) = 0$ ，
$$
[N^{(m)}_n]^2 = \frac{1}{2} r_0^2 [J_{m+1}(\mu_n) r_0]^2.
$$

2. 对于第二类齐次边界条件 $ J'_m(\sqrt{\mu_n} r_0) = 0 $ ，
$$
[N^{(m)}_n]^2 = \frac{1}{2} \left( r_0^2 -\frac{m^2}{\mu_n} \right) [J_{m+1}(\mu_n) r_0]^2.
$$

3. 对于第三类齐次边界条件 $ J_m(\sqrt{\mu_n} r_0) + H \sqrt{\mu_n}  J'_m(\sqrt{\mu_n} r_0) = 0$ ，
$$
[N^{(m)}_n]^2 = \frac{1}{2} \left( r_0^2 -\frac{m^2}{\mu_n} + \frac{r_0^2}{\mu_n H} \right) [J_{m+1}(\mu_n) r_0]^2.
$$

######第二类Bessel函数，Neumann函数

$$
N_{\nu}(x) = \frac{J_v(x) \cos \nu \pi - J_{-\nu}(x)}{\sin \nu \pi}.
$$

所有Neumann函数在零点处都发散.

**渐进行为：**
$$
\begin{align}
x \to \infty, \quad
N_\nu &\to \sqrt{\frac{2}{\pi x}} \sin \left(x - \nu \pi - \frac{\pi}{4} \right). \\
\end{align}
$$
![Bessel_Functions_(2nd_Kind,_n=0,1,2)](img/Bessel_Functions_(2nd_Kind,_n=0,1,2).svg)



###### Hankel函数

$$
H^{(1)}_\nu = J_\nu(x) + i N_\nu(x), \\
H^{(2)}_\nu = J_\nu(x) - i N_\nu(x).
$$

Hankel函数的作用更多是理论层面上而不是实用角度上.



###### 递推公式

容易证明，$J_\nu, N_\nu, H_\nu$ 都满足（统一记为 $Z_{\nu}$ ）都满足以下关系：
$$
\frac{\mathrm{d}}{\mathrm{d}x} \left( \frac{Z_\nu(x)}{x^{\nu}} \right) = - \frac{Z_{\nu+1}(x)}{x^\nu}. \\
\frac{\mathrm{d}}{\mathrm{d}x} [x^\nu Z_\nu(x)] = x^\nu Z_{\nu-1}(x).
$$

这几个公式在对Bessel函数求导数的情况下特别管用.

特别地有
$$
J_0'(x) = -J_1(x).
$$


##### 虚宗量Bessel方程的解： $ I_{\nu}, K_{\nu} $

虚宗量Bessel方程的解分为 $ I_{\nu}, K_{\nu}$ ，分别是

$$
I_{\nu} = i^{-\nu} J_{\nu}(ix)  = \sum_{k=0}^{\infty} \frac{1}{k! \Gamma(\nu+k+1)} {\left(\frac{x}{2}\right)}^{2k+\nu}. \\
I_{-\nu} = i^{\nu} J_{-\nu}(ix)  = \sum_{k=0}^{\infty} \frac{1}{k! \Gamma(-\nu+k+1)} {\left(\frac{x}{2}\right)}^{2k-\nu}.
$$

同样，当 $\nu$ 取整数时，两个方程不再线性独立. 因此取
$$
K_{\nu}(x) = \frac{\pi}{2} \frac{I_{-\nu}(x) - I_{\nu}(x)}{\sin \nu \pi}.
$$

**渐进行为：**
$$
\begin{align}
x \to 0, \quad I_0(0) &= 1, I_m(0) = 0,\\
K_m(0) &\to \infty. \\
x \to \infty,  \quad I_m &\to \frac{1}{2\sqrt{x}}e^x \\
K_m & \to \frac{\pi}{2\sqrt{x}} e^{-x}.
\end{align}
$$
![BesselI_Functions_(1st_Kind,_n=0,1,2,3)](img/BesselI_Functions_(1st_Kind,_n=0,1,2,3).svg)



![BesselK_Functions_(n=0,1,2,3)](img/BesselK_Functions_(n=0,1,2,3).svg)



###### 球Bessel函数的解： $j_\nu, n_\nu, h_\nu$

$$
j_l(x) = \sqrt{\frac{\pi}{2x}} J_{l+1/2}(x), \\
j_{-l}(x) = \sqrt{\frac{\pi}{2x}} J_{-(l+1/2)}(x), \\
n_l(x) = \sqrt{\frac{\pi}{2x}} N_{l+1/2}(x) = (-1)^{l+1} \sqrt{\frac{\pi}{2x}} J_{-(l+\frac{1}{2})}(x)., \\
$$

球Hankle函数同上，不再赘述.

球Bessel函数还可以写成微分式
$$
\begin{align}
j_l(x) &= (-x)^l \left(\frac{1}{x}\frac{d}{dx}\right)^l\,\frac{\sin x}{x}, \\
n_l(x) &= -(-x)^l \left(\frac{1}{x}\frac{d}{dx}\right)^l\,\frac{\cos x}{x}.
\end{align}
$$
由此，球Bessel函数的前几项
$$
\begin{align}
j_0(x) &= \frac{\sin x}{x}. \\
j_1(x) &= \frac{\sin x}{x^2} - \frac{\cos x}{x}, \\
\, \\
n_0(x) &= -j_{-1}(x) = -\frac{\cos x}{x}, \\
n_1(x) &= j_{-2}(x)  = -\frac{\cos x}{x^2} - \frac{\sin x}{x}, \\
\end{align}
$$
![Spherical_Bessel_j_Functions_(n=0,1,2)](img/Spherical_Bessel_j_Functions_(n=0,1,2).svg)



![Spherical_Bessel_y_Functions_(n=0,1,2)](img/Spherical_Bessel_y_Functions_(n=0,1,2).svg)



#### 例子

##### 柱坐标下的Laplace方程

**侧面绝热，上下表面温度分布给定的轴对称圆柱体的稳态温度分布问题**

我们可以写出稳态下热传导方程
$$
\begin{cases}
\nabla^2 u = 0, \\
u_r |_{r = r_0} = 0, \\
u |_{z=0} = f_1(r), u |_{z=L} = f_2(r).
\end{cases}
$$
这是柱坐标下的Laplace方程. 并且属于有关于 $r$ 的齐次边界条件的情况. 于是关于 z 的条件就被视作是方程的“初始条件”. 

分离变量，$u = R(r) \Phi(\phi) Z(Z)$ ，按照上文有
$$
\Phi_m(\phi) = A \cos m \phi + B \sin m\phi, \quad m = 0,1,2,3,\cdots
$$
但是因为方程的“初始条件”根本不含 $\phi$ ，因此 $ \Phi(\phi) = \text{const}, m=0$ . （考虑最后用 $\cos m\phi, \sin m\phi$ 展开与 $\phi$ 无关的一个量，那么除了 $\cos 0x = 1$ 以外不会有其他的项前系数不为0）

同时因为关于 $r$ 有齐次边界条件，而我们讨论的又是柱内，在 $r < r_0$  有自然边界条件，则
$$
R_n(r) = 
\begin{cases}
A_n J_0(\sqrt{\mu_n} r) , \quad \mu_n \neq 0, \\
A_0 \cdot 1 , \quad \mu_n = 0.
\end{cases}
$$

为了满足 $u_r |_{r = r_0} = 0 \implies R'(r_0) = 0,$ 对于 $\mu = 0$ 显然满足，而其他情况下
$$
A_n \sqrt{\mu_n}  J'_0(\sqrt{\mu_n} r_0) = 0. \\
\iff J_1(\sqrt{\mu_n} r_0) = 0.
$$


这实际上也意味着0不由分说一定是方程的本征值（有时候 $\mu = 0$ 就不是方程的本征值，需要特别判断），记为 $\mu_0 = 0$ . 同时 $ \sqrt{\mu_n} r_0$ 必须是 $J_1$ 的零点. 设 $J_1$ 的一系列零点小到大分别为 $x_1, x_2,\cdots$ ，则其他本征值
$$
\mu_n = \left( \frac{x_n}{r_0} \right)^2.
$$
把得到的 $\mu_n$ 带回Z的方程中，Z方向的解为
$$
Z_0 = B_0 + C_0 z. \\
n \neq 0, Z_n = B_n e^{\sqrt{\mu_n}z} + C_n e^{-\sqrt{\mu_n} z}.
$$

由此组合起来
$$
u = B_0 + C_0 z + \sum_{n=1}^{+\infty}( B_n e^{\sqrt{\mu_n}z} + C_n e^{-\sqrt{\mu_n} z})J_0(\sqrt{\mu_n} r).
$$

代入所谓的“初始条件”，
$$
f_1(r) = B_0 + \sum_{n=1}^{+\infty}( B_n + C_n)J_0(\sqrt{\mu_n} r). \\
f_2(r) = B_0 + C_0 L + \sum_{n=1}^{+\infty}( B_n e^{\sqrt{\mu_n}L} + C_n e^{-\sqrt{\mu_n} L})J_0(\sqrt{\mu_n} r).
$$
用 $J_0(\sqrt{\mu_n} r)$ 进行展开，
$$
\begin{align}
B_0 &= \frac{2}{r_0^2}\int_{0}^{r_0} f_1(r) r\mathrm{d} r. \\
B_0 + C_0 L &= \frac{2}{r_0^2}\int_{0}^{r_0} f_2(r) r\mathrm{d} r. \\
B_n + C_n &= \frac{1}{[N_n]^2}\int_{0}^{r_0} f_1(r) J_0(\sqrt{\mu_n} r) r\mathrm{d} r. \\
B_n e^{\sqrt{\mu_n}L} + C_n e^{-\sqrt{\mu_n} L} &= \frac{1}{[N_n]^2}\int_{0}^{r_0} f_2(r) J_0(\sqrt{\mu_n} r) r\mathrm{d} r.
\end{align}
$$

联立解出常数即可. 



**上下表面温度为T，侧面表面温度分布给定的轴对称圆柱体的稳态温度分布问题**

写出方程
$$
\begin{cases}
\nabla^2 u = 0, \\
u_r |_{r = r_0} = f(z), \\
u |_{z=0} = T, u |_{z=L} = T.
\end{cases}
$$

方程没有齐次边界条件可用，需要齐次化. 有两种选项：对r进行齐次化处理以及对z进行齐次化处理. 鉴于对r齐次化后方程会变成非齐次的形式，给我们添加额外的麻烦，因此对z进行齐次化处理：设

$$
v = u - T,
$$

则方程化为
$$
\begin{cases}
\nabla^2 v = 0, \\
v_r |_{r = r_0} = f(z) - T \equiv g(z), \\
v |_{z=0} = 0, v |_{z=L} = 0.
\end{cases}
$$
分离变量，$u = R(r) \Phi(\phi) Z(Z)$ ，同理，因方程定解条件与 $\phi$ 无关，因此有 $m = 0, \Phi(\phi) = \text{const}.$

对于z方向的齐次边界条件，有解
$$
Z_n = A_n \sin \nu_n z + B_n \cos \nu_n z.
$$
其中，根据边界条件
$$
\nu_n = \frac{n\pi}{L}, B_n = 0. \\
\implies Z_n = A_n \sin \frac{n\pi}{L} z.
$$
从而关于r有
$$
R_n(r) = C_1 I_m(\nu_n r) + C_2 K_m(\nu_n r),
$$
由于是柱内，发散项前系数为0，
$$
R_n(r) = C_n  I_0(\frac{n\pi}{L} r).
$$
因此，方程的解的形式为
$$
v = \sum_{n=1}^{+\infty} A_n I_0(\frac{n\pi}{L} r) \sin \frac{n\pi}{L} z .
$$
代入所谓的“初始条件”，
$$
g(z) = \sum_{n=1}^{+\infty} A_n I_0(\frac{n\pi}{L} r_0) \sin \frac{n\pi}{L} z. \\
\implies A_n = \frac{1}{I_0(\frac{n\pi}{L} r_0)} \frac{2}{L} \int_0^L g(z)\sin \frac{n\pi}{L} z \, \mathrm{d}z.
$$
由此，
$$
u = \sum_{n=1}^{+\infty} A_n I_0(\frac{n\pi}{L} r) \sin \frac{n\pi}{L} z  + T.
$$
常数上面已给出.



##### 柱坐标下的Helmholtz方程

**内外温度为 $T_0$ 的空心无限长圆柱体的热传导问题**

我们可以写出热传导方程
$$
\begin{cases}
u_t - a^2\nabla^2 u = 0, \\
u |_{r=r_1} = T_0, u |_{r=r_2} = T_0,\\
u |_{t = 0} = f(r), \\
\end{cases}
$$

对于Helmholtz方程，我们必须把全部边界条件齐次化. 因此引入v，使得
$$
v = u - T_0. 
\\
\begin{cases}
v_t - a^2\nabla^2 v = 0, \\
v |_{r=r_1} = 0, v |_{r=r_2} = 0,\\
v |_{t = 0} = f(r) - T_0, \\
\end{cases}
$$

分离变量，$u = T(t) R(r) \Phi(\phi) Z(Z)​$ ，同理，因方程定解条件与 $\phi​$ 无关，因此有 $m = 0, \Phi(\phi) = \text{const}.​$

对于变量z，由于我们考虑的是一个“无限长”圆柱，实际上解中应该不含z. 因此，本来
$$
Z_n = A_n \sin \nu_n z + B_n \cos \nu_n z.
$$

我们知道只有 $\nu_0 = 0$ 的时候，$Z_0 = \text{const}$ 是不含有z的.

接下来处理r. 由于是空心圆柱，所以不包含0点，无法除去解中的Neumann函数，
$$
\begin{align}
R_{l}(r) &= A_l J_0(\sqrt{-\nu_0^2+k_{n,l}^2} r) + B_l N_0(\sqrt{-\nu_0^2+k_{n,l}^2} r) \\
&= A_l J_0(k_{l} r) + B_l N_0(k_{l} r).
\end{align}
$$

不过这也无妨，因为r方向的边界条件数量足够定出A和B. 我们知道为了满足边界条件
$$
\begin{cases}
A_l J_0(k_{l} r_1) + B_l N_0(k_{l} r_1) = 0, \\
A_l J_0(k_{l} r_2) + B_l N_0(k_{l} r_2) = 0,
\end{cases}
$$

如果要有非零 $A_l, B_l$ 的话，必须满足
$$
J_0(k_{l} r_1) N_0(k_{l} r_2) - J_0(k_{l} r_2) N_0(k_{l} r_1) = 0.
$$

这个方程的解实际上就是我们需要的 $k_l$ 的值. 利用这个关系也可以顺带着解出A，B的关系：
$$
A_l J_0(k_{l} r_1) = - B_l N_0(k_{l} r_1), \\
\implies \\
\begin{align}
J_0(k_{l} r_1) R_{l}(r) &= A_l J_0(k_{l} r_1) J_0(k_{l} r) + B_l J_0(k_{l} r_1) N_0(k_{l} r) \\
&= - B_l N_0(k_{l} r_1) J_0(k_{l} r) + B_l J_0(k_{l} r_1) N_0(k_{l} r)  \\
R_{l}(r) &= C_l (J_0(k_{l} r_1) N_0(k_{l} r) - J_0(k_{l} r) N_0(k_{l} r_1)).
\end{align}
$$

时间部分的解为
$$
T(t) = Ce^{-k^2a^2t}.
$$


组合起来，方程的解的形式为
$$
v = \sum_{l=1}^{+\infty} C_l (J_0(k_{l} r_1) N_0(k_{l} r) - J_0(k_{l} r) N_0(k_{l} r_1)) e^{-k^2a^2t}.
$$

定出常数的过程此处就略去了. 无非是把本征函数 $R_{l}(r) = J_0(k_{l} r_1) N_0(k_{l} r) - J_0(k_{l} r) N_0(k_{l} r_1)$ 用来做广义Fourier展开. 按照Strum-Liouville定理，它是带权r正交的.



##### 球坐标下的Helmholtz方程

**球面发射声波的速度势**

速度势（[Velocity Potential](https://en.wikipedia.org/wiki/Velocity_potential)）是声学中一个常用的概念，它的梯度即是声场该点处的速度. 用速度势不仅可以用来得到速度，也可以轻易得到声场某点的压强.

我们讨论的情况是一个半径为 $r_0$ 的球面内的声场，它的表面的速度为 $v = v_0 \sin \omega t.$ 用它作为边界条件，我们列出波动方程
$$
u_{tt} - a^2 \nabla^2 u = 0, \\
u_r|_{r=r_0} = v_0 \sin \omega t.
$$

没有列出初始条件是因为初始条件不重要. 即使初始条件不同，声场也总会在球面的驱动下，达到同一个稳态声场.

我们开始着手分析这个问题. 对于波动方程的非齐次边界条件，我们需要先齐次化. 于是设
$$
\begin{align}
v &= u - r u_0 \sin \omega t, \\
\implies \nabla^2 v &= \nabla^2 u - \nabla^2(r u_0 \sin \omega t) \\
&= \nabla^2 u - \frac{2}{r}v_0 \sin \omega t. \\
u_{tt} &= v_{tt} - rv_0 \omega^2 \sin \omega t.

\end{align}
$$

则得到关于v的方程
$$
\begin{cases}
v_{tt} - a^2 \nabla^2 v = (rv_0\omega^2 + \frac{2}{r}v_0) \sin \omega t, \\
v_r|_{r=r_0} = 0.
\end{cases}
$$

方程变成了非齐次的形式. 不过这不要紧. 对于一个齐次方程而言，先分离变量$u = T(t) R(r) \Theta(\theta) \Phi(\phi) $. 

对于空间部分，分离后得到变为Helmholtz方程，在这个边界条件下，首先因为其与 $\phi$ 无关，所以立刻断言 $m = 0$. 再者它跟 $\theta$ 也无关，所以也可以立刻断言 $l = 0$. 

现在只剩下了r. 按照上文，Helmholtz方程的解应当是 $R_n(r) = A_n j_l(k_n r) + B_n n_{l}(k_n r).$ 由于 $l=0$ ，且我们考虑的是球内区域，由自然边界条件，
$$
\begin{align}
R_n(r) &= A_n j_{0}(k_n r) \\
&= A_n \left( \frac{\sin k_nr}{k_nr} \right).
\end{align}
$$

为了满足边界条件， $k_n$ 的取值必须满足
$$
\frac{\partial}{\partial r}\left.\left(\frac{\sin k_nr}{k_nr} \right)\right|_{r = r_0} = 0 \\
\implies k_nr_0 \cos k_n r_0 - \sin k_n r_0 = 0,  \\
\implies \tan k_nr_0 = k_nr_0.
$$

根据Chap 8中处理非齐次方程的一般方法，设解的形式为
$$
v = \sum_{n=1}^{+\infty} A_n T_n(t) j_0(k_n r).
$$
代回原方程，因为 $j_0(k_n r)$ 是Helmholtz方程 $\nabla^2 v + k^2 v = 0$ 的解，有
$$
\nabla^2 j_0(k_nr) = - k^2 j_0(k_nr)
$$

因此
$$
v_{tt} - a^2 \nabla^2 v 
= \sum_{n=1}^{+\infty}A_n \left( T_n''(t) +a^2k_n^2 T_n(t) \right)j_0(k_nr) = (rv_0\omega^2 + \frac{2}{r}v_0) \sin \omega t.
$$

对等式右边用 $j_0(k_n r)$ 展开，
$$
B_n \left( T_n''(t) +a^2k_n^2 T_n(t) \right)
= \sin \omega t  \frac{1}{[N_n]^2} \int_{0}^{r_0} \left(rv_0\omega^2 + \frac{2}{r}v_0 \right) j_0(k_nr) r^2 \mathrm{d} r.
$$

这里就不再费力气求解这个积分了.