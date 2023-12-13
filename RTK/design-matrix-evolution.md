---
description: 从伪距单差到载波相位双差，设计矩阵A的变换
---

## 伪距单差

方程：忽略电离层等
$$
\begin{align*}
\rho_i &= r_i + c\cdot dt + \epsilon_i \\
 &= \sqrt{(x_r-x^s)^2 + (y_r-y^s)^2 + (z_r-z^s)^2} + c\cdot dt + \epsilon_i \\
 &= ||p_r -p^s|| + c\cdot dt + \epsilon_i \\
 &= f(\chi)
\end{align*}
$$

$$
\chi = [p_r ~~c\cdot dt] = [x_r~~y_r~~z_r~~c\cdot dt]
$$

通常也会忽略$$\varepsilon$$

$$f$$是一个非线性函数，按照上一节的理论，可以表示为：
$$
\delta \Rho = A \cdot \delta \Chi + V
$$
这里的$$A$$ 就是：
$$
\begin{align*}
A = \frac{\partial \Rho}{\partial \Chi}_{|\Chi=\Chi_0} &= [\frac{||p_r -p^s||}{\partial x}_{|x=x_0}~~\frac{||p_r -p^s||}{\partial y}_{|y=y_0}~~\frac{||p_r -p^s||}{\partial z}_{|z=z_0}~~1] \\
&= [\frac{x_0-x^s}{r} ~~ \frac{y_0-y^s}{r} ~~\frac{z_0-z^s}{r} ~~1]
\end{align*}
$$

## 双差

方程：（注意相位已经转换成距离量）

$$
\begin{align*}
\Phi_{DD} &= R_{DD} + \lambda \cdot N_{DD} -  c\cdot dt+ \varepsilon_{DD} = f(p_r, N_{DD}) = f(\Chi)\\
\Rho_{DD} &= R_{DD} -  c\cdot dt+ \epsilon_{DD} = h(p_r) \\
\end{align*}
$$

注意到有：
$$
f(p_r, N_{DD}) = h(p_r)+ \lambda \cdot N_{DD}
$$
根据上一节理论：
$$
A_{\Rho_{DD}} = \frac{\partial \Rho_{DD}}{\partial \Chi'}_{|\Chi'=\Chi'_0} = [\frac{x_0-x^s}{r} ~~ \frac{y_0-y^s}{r} ~~\frac{z_0-z^s}{r} ~~-1] \\
A_{\Phi_{DD}} = \frac{\partial \Phi_{DD}}{\partial \Chi}_{|\Chi=\Chi_0} = [A_{\Rho_{DD}} ~~~\lambda \cdot I]
$$
当然如果不转换为距离量，结果就应该是：
$$
[\lambda^{-1} \cdot A_{\Rho_{DD}} ~~~I]
$$
这也是一些论文里会出现的形式

应该留意到：
$$
\frac{\partial \Phi_{DD}}{\partial p}_{|p=p_0} =\frac{\partial \Rho_{DD}}{\partial p}_{|p=p_0}
$$
所以完整的载波相位双差方程的设计矩阵：

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/2023/12/13/95d6b0d1cc35a9377cfa99fe3b536add-image-20231213133942697-cf121b.png" alt="image-20231213133942697" style="zoom:100%;" />

## 浮点解

同样这个就是可以通过最小二乘方程来解，解的状态向量中的$$N_{DD}$$大概不是整数，所以叫浮点解

即：
$$
\delta \Phi_{DD} = A \cdot \delta\Chi + V, ~~\Chi=[X,~Y,~Z,~N_{DD}]
$$

$$
\delta\hat{\Chi} = (A^T R^{-1} A) ^{-1} A^T R^{-1} \delta\Phi_{DD}
$$

考虑到非线性最小二乘需要一个已知的点，所以一般用的是`EKF`

这就涉及到EKF与N-WLS的区别与联系了

