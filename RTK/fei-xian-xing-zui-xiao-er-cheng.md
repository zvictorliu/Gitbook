---
description: 非常基础
---

# Non-Linear WLS

一个线性最小二乘方程的标准形式是：
$$
Y = AX + V
$$
$$A$$是设计矩阵，$$X$$是待估计参数，$$Y$$是测量量，$$V$$是残差，注意不要再带入直线拟合的符号标记

若带权（一般是方差倒数），解为：
$$
\hat{X} = (A^T R^{-1} A) ^{-1} A^T R^{-1} Y
$$
其中$$R^{-1}$$为权重矩阵

现在拓展到非线性最小二乘：关于$$\delta$$的最小二乘

先看简单情况: $$f$$ 是非线性函数，进行Taylor展开：

$$
y = f(x) = f(x_0 ) + \frac{\partial f}{\partial x}_{|x=x_0} \cdot \delta x + v
$$

于是写成：

$$
\delta y = \frac{\partial f}{\partial x}_{|x=x_0} \cdot \delta x + v
$$

若是线性函数，即

$$
\delta Y = A \cdot \delta X + V
$$

这就是最小二乘问题标准形式，加权最小二乘解：

$$
\delta \hat{X} = (A^T R^{-1} A) ^{-1} A^T R^{-1} \delta Y
$$

我们重点看 $$A$$ ，意识到：

$$
y = f(x) \\ \frac{\partial y}{\partial x} = \frac{\partial f}{\partial x}
$$

所以其实可以写成：

$$
\delta y = \frac{\partial y}{\partial x}_{|x=x_0} \cdot \delta x + v
$$

也就是：
$$
A = \frac{\partial Y}{\partial X}_{|X=X_0}
$$
