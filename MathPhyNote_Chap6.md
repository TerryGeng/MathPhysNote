## 数学物理方法 总结

[TOC]

### Chap 6. 拉普拉斯变换

#### 拉普拉斯变换

Fourier变换因为其对函数要求过于苛刻——函数需要在 $\mathbb{R}$ 上平方可积——导致对于很多函数都没有办法使用Fourier变换处理. 
一个常见的解决办法是：给不满足平方可积条件的函数乘上一个收敛性很强的收敛因子，比如 $e^{-\sigma t}$ ，这样对于大部分不太刁钻的函数，都可以在正无穷处收敛，满足平方可积. 虽然这样操作以后，得到的“频域”的意义会不是很清晰，但是用于像Fourier变换一样求解微分方程倒是十分方便. 这种乘上收敛因子 $e^{-\sigma t}$ 在进行Fourier变换的操作叫做 **Laplace变换**.

具体而言，我们只研究 $t>0$ 的情形，因此置
$$
f(t) = 0, \qquad \forall t < 0.
$$

构造函数
$$
g(t) = f(t) e^{-\sigma t},
$$
选取实数 $\sigma$ 足够大，以至于 $g(t)$ 在 $(0, +\infty)$ 上平方可积，然后对 $g(t)$ 实行Fourier变换
$$
G(\omega) = \frac{1}{2\pi} \int_{0}^{+\infty} f(t) e^{-(\sigma + i\omega) t} \mathrm{d}t.
$$
记 $\sigma + i\omega = p$，并设函数 $\bar{f}(p) = 2\pi G(\omega)$，
$$
\bar{f}(p) = \int_{0}^{+\infty} f(t) e^{-p t} \mathrm{d}t.
$$

称这个函数 $\bar{f}(p)$ 为 $f(t)$ 的 **Laplace变换函数**. 常记为
$$
\bar{f}(p) = \mathcal{L}[f(t)].
$$


同时，我们也可以写出逆变换
$$
\underline{\forall t>0,}
$$

$$
\begin{align}
f(t) &= g(t) e^{\sigma t} \\
&= e^{\sigma t} \int_{-\infty}^{+\infty} G(\omega) e^{i\omega t} \mathrm{d}\omega \\
&= \int_{-\infty}^{+\infty} G(\omega) e^{(\sigma + i\omega) t} \mathrm{d}\omega \\
&= \int_{\sigma-i\infty}^{\sigma+i\infty} \frac{1}{2\pi} \bar{f}(p) e^{p t} \frac{1}{i} \mathrm{d}p \\
&= \frac{1}{2\pi i}  \int_{\sigma-i\infty}^{\sigma+i\infty} \bar{f}(p) e^{p t}  \mathrm{d}p.
\end{align}
$$

常记为
$$
f(t) = \mathcal{L}^{-1}[\bar{f}(p) ].
$$

##### 一些常用函数的Laplace变换

$$
\begin{align}
&\mathcal{L}[1] = \frac{1}{p} \\
&\mathcal{L}[t] = \frac{1}{p^2} \\
&\mathcal{L}[e^{st}] = \frac{1}{p-s} \\
&\mathcal{L}[t^ne^{st}] = \frac{n!}{(p-s)^{n+1}} \\
&\mathcal{L}[\sin \omega t] = \frac{\omega}{p^2+\omega^2} \\
&\mathcal{L}[\cos \omega t] = \frac{p}{p^2+\omega^2}. \\
\end{align}
$$

##### 一些性质

###### 1. 像函数的导数 / 像函数的解析性质

$$
\frac{\mathrm{d} \bar{f}(p)}{\mathrm{d} p} = -\int_{0}^{+\infty} tf(t) e^{-p t} \mathrm{d}t. 
\implies \mathcal{L}[tf(t)] = -\frac{\mathrm{d} \bar{f}(p)}{\mathrm{d} p} \\
\implies \mathcal{L}[t^nf(t)] = (-1)^n\frac{\mathrm{d}^n \bar{f}(p)}{\mathrm{d} p^n}.
$$

**由此可知，$\bar{f}(p)$ 在 $\mathrm{Re} p > \sigma_0$ 的区域上解析，因为其导数处处存在.** 

同时，像函数必然在 $\mathrm{Re} p <= \sigma_0$ 有一个以上的奇点，否则反演回去原函数会是0. 

**Eg.** 
$$
\frac{1}{p^{n+1}} = (-1)^n \frac{1}{n!}\frac{\mathrm{d}^n (1/p)}{\mathrm{d} p^n}. \\
\implies \mathcal{L}[t^n\cdot 1] = \frac{n!}{p^{n+1}}.
$$

###### 2. 像函数的积分
$$
\begin{align}
\int_{p'}^{+\infty} \bar{f}(p) \mathrm{d} p &= \int_{p'}^{+\infty} \int_{0}^{+\infty} f(t) e^{-p' t} \mathrm{d}t \mathrm{d} p' \\
&= \int_{0}^{+\infty} f(t) \int_{p'}^{+\infty} e^{-p' t} \mathrm{d} p' \mathrm{d}t \\
&= \int_{0}^{+\infty} \frac{f(t)}{t} e^{-p' t} \mathrm{d}t.
\end{align}
$$

必须注意的是：这里对像函数的积分从 $p'$ 到 $+\infty$ 指的是**沿着实轴的积分**. 解析函数的积分虽然不依赖路径，但是肯定是依赖始末位置的，而 $+\infty$ 实际上并不是一个特定的始末位置，所以这里要特别强调这个 $+\infty$ 是实轴上的.

**Eg.**
$$
\begin{align}
\int_{0}^{+\infty} \frac{\sin x}{x} \mathrm{d}x &= 
\int_{0}^{+\infty} \mathcal{L}[\sin x](p) \mathrm{d}p \\
&= \int_{0}^{+\infty} \frac{1}{1+p^2} \mathrm{d}p = \frac{\pi}{2}.
\end{align}
$$

###### 3. 线性性质
显然的，有
$$
\mathcal{L}[c_1 f_1(t) + c_2 f_2(t)] = c_1 \mathcal{L}[f_1(t)] + c_2 \mathcal{L}[f_2(t)].
$$

###### 4. 导数定理
$$
\mathcal{L}[f'(t)] = p \mathcal{L}[f(t)] - f(0).
$$

证明：
$$
\begin{align}
\mathcal{L}[f'(t)] &= \int_{0}^{+\infty} f'(t) e^{-pt} \mathrm{d}t \\
&= \int_{0}^{+\infty}  e^{-pt} \mathrm{d}f(t) \\
&= \left. e^{-pt}f(t) \right|_{t=0}^{+\infty} + \int_{0}^{+\infty}  p f(t) e^{-pt} \mathrm{d} \\
&= p\mathcal{L}[f(t)] - f(0).
\end{align}
$$

###### 5. 积分定理

逆着用导数定理，得到
$$
\mathcal{L} [\int_{0}^{t} f(\tau) \mathrm{d} \tau] = \frac{1}{p} \mathcal{L} [f(t)].
$$

###### 6. 位移定理（像函数位移）

显而易见：
$$
\mathcal{L}[f(t)](p + \lambda) = \int_{0}^{+\infty} f(t) e^{-(p+\lambda) t} \mathrm{d}t 
= e^{-\lambda t} \mathcal{L}[f(t)](p).
$$

###### 7. 延迟定理（原函数延迟）

$$
\mathcal{L}[f(t-t_0)] = \int_{t_0}^{+\infty} f(t-t_0) e^{-pt} \mathrm{d} t =  \int_{0}^{+\infty} f(u) e^{-p(u + t_0)} \mathrm{d} u 
= e^{-pt_0} \mathcal{L}[f(t)]
$$

###### 8. 卷积定理

$$
\mathcal{L}[f_1(t) * f_2(t)] = \mathcal{L}[f_1(t)]  \mathcal{L}[f_2(t)]
$$

卷积的定义和Fourier变换那一章中定义一样：
$$
f_1(t) * f_2(t) = \int_{-\infty}^{+\infty} f_1(\tau) f_2(t - \tau) \mathrm{d} \tau.
$$

但是注意到对于Laplace变换，$\forall t<0, f_1(t) = f_2(t) = 0.$ 因此，
$$
f_1(t) * f_2(t) = \int_{0}^{t} f_1(\tau) f_2(t - \tau) \mathrm{d} \tau.
$$

这个定理的证明与Fourier变换中卷积定理的证明是几乎一样的：
$$
\begin{align}
\mathcal{L}[f_1(t) * f_2(t)] &= \int_{0}^{+\infty} \int_{0}^{t} f_1(\tau) f_2(t - \tau) \mathrm{d} \tau e^{-pt} \mathrm{d}t \\
\end{align}
$$

变换积分顺序，积分上下限也需要跟着调整：$t \in (0, +\infty),\,  \tau \in (0, t) \implies \tau \in (0, +\infty), \, t \in (\tau, +\infty)$
$$
\begin{align}
\mathcal{L}[f_1(t) * f_2(t)] &= \int_{0}^{+\infty} f_1(\tau) e^{-p \tau} \mathrm{d} \tau  \int_{\tau}^{+\infty} f_2(t - \tau)  e^{-p(t - \tau)} \mathrm{d}t \\
&= \int_{0}^{+\infty} f_1(\tau) e^{-p \tau} \mathrm{d} \tau  \int_{0}^{+\infty} f_2(u)  e^{-pu} \mathrm{d}u \\
&= \mathcal{L}[f_1(t)]  \mathcal{L}[f_2(t)].
\end{align}
$$

**Eg. 综合应用案例：求解线性微分方程**

接在交流电源两端的RC电路的方程如下：
$$
\begin{cases}
L \frac{\mathrm{d}j}{\mathrm{d}t} + Rj = E_0 \sin \omega t \\
j(0) = 0.
\end{cases}
$$
将方程两端做Laplace变换：
$$
L(p\bar{j} - j(0)) + R\bar{j} = E_0 \frac{\omega}{p^2+\omega^2}. \\
\bar{j} = \frac{E_0}{L}\frac{1}{p+R/L} \frac{\omega}{p^2+\omega^2}.
$$
注意到上式可以改写成
$$
\mathcal{L}[j] = \bar{j} = \frac{E_0}{L} \mathcal{L}[e^{-R/L \cdot t}]  \mathcal{L}[\sin \omega t].
$$
应用卷积定理：
$$
\begin{align}
j &= \frac{E_0}{L} \int_{0}^{t} e^{-R/L \cdot (t-\tau)} \sin \omega t \,\mathrm{d}\tau \\
&= \frac{E_0}{R^2+L^2\omega^2} (R\sin \omega t - \omega L \cos \omega t) + \frac{E_0\omega L}{R^2+L^2\omega^2} e^{-R/L \cdot t}.
\end{align}
$$



#### 拉普拉斯变换的反演

反演，即通过像函数求原函数. 除了通过上述应用案例展示的依靠拆项，拼凑，观察进行反演的方法，更一般的方式是回到定义
$$
f(t) = \frac{1}{2\pi i}  \int_{\sigma-i\infty}^{\sigma+i\infty} \bar{f}(p) e^{p t}  \mathrm{d}p.
$$

这个积分类似于实轴上无穷限的反常积分. 通过换元换回去：
$$
f(t) = \frac{1}{2\pi} \int_{-\infty}^{+\infty} \bar{f}(\sigma + i\omega) e^{(\sigma + i\omega) t} \mathrm{d}\omega.
$$

根据Riemann–Lebesgue引理，
$$
\bar{f}(\sigma + i \omega) = \int_{0}^{\infty} f(t) e^{-\sigma t} \, e^{-i\omega t} \mathrm{d} t \to 0 \qquad\text{ as } |\omega| \to \infty.
$$

因此可以放心使用Jordan引理，得到
$$
f(t) = \sum \mathrm{Res} \left[ \bar{f}(p) e^{p t} \right].
$$
