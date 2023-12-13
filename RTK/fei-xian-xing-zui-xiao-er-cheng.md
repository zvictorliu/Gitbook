---
description: 非常基础
---

# 非线性最小二乘

关于残差的最小二乘：

先看简单情况: $$f$$ 是非线性函数，进行Taylor展开：

$$
y = f(x) = f(x_0 ) + \frac{\partial f}{\partial x}|_{x=x_0} \cdot \delta x + v
$$

于是写成：

$$
\delta y = \frac{\partial f}{\partial x}|_{x=x_0} \cdot \delta x + v
$$

若是线性函数，即

$$
\delta Y = H \cdot \delta X + V
$$

这就是最小二乘问题标准形式，加权最小二乘解：

$$
\delta \hat{X} = (H^T R^{-1} H) ^{-1} H^T R^{-1} \delta Y
$$

我们重点看 $$H$$ ，意识到：

$$
y = f(x) \\ \frac{\partial y}{\partial x} = \frac{\partial f}{\partial x}
$$

所以其实可以写成：

$$
\delta y = \frac{\partial y}{\partial x}|_{x=x_0} \cdot \delta x + v
$$

这就是后面方程的基础
