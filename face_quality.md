参考：[线性代数的直觉](https://limuzhi.com/2018/07/15/Linear-algebra-feeling/)

**实对称矩阵**：元素都为实数的矩阵，且转置矩阵和自身相等的矩阵：
$$A^T=A\space.$$

**推论1**：对于任意矩阵 $M$ ， $MM^T$ 为实对称矩阵，因为 $MM^T=\left(M^T\right)^TM^T=\left(MM^T\right)^T$ 。

---

**酉矩阵**：$n$ 阶复方阵 $U$ ，满足$U^{-1}=U^*$ 即为酉矩阵（式中 $U^*$ 为复共轭转置）。

**舒尔分解定理**：若 $A$ 是 $n$ 阶复方阵，则存在 $n$ 阶酉矩阵 $Q$ ， $n$ 阶上三角矩阵 $U$ ，使得：$$A=QUQ^{-1}\space.$$

**推论2**：因为 $U=Q^TAQ$ ，其转置矩阵 $U^T=\left(Q^TAQ\right)^T=Q^TAQ$ ，即 $U$ 为对称阵。由 $U$ 即是上三角阵又是对称阵可知 $U$ 是对角阵，可知对于实对称阵 $A$ ，存在正交阵 $Q$ ，和对角阵 $\Sigma$ 使得 $A=Q\Sigma Q^T$ ，即**任意实对称阵都可对角化**。

---

**特征值与特征向量**：给定一个方阵 $A$ ，它的特征向量 $v$  经过 $A$ 所表示的线性变换之后，得到的新向量 $v'=Av$ 仍然与原来的 $v$ 保持在同一条直线上，但其长度也许会改变。即：$$Av=\lambda v$$

若对于 $n$ 阶方阵 $A$，存在非 $0$ 向量 $v$ 使得上式，即 $\left(A-\lambda I\right)v=0$ 成立，等价于齐次线性方程组 $\left(A-\lambda I\right)v=0$ 存在非 $0$ 解，因此 $\text{rank}\left(A-\lambda I\right)<n$，故 $\text{det}\left(A-\lambda I\right)=0$，求解该行列式方程可得所有特征值。

**特征分解**：设 $A$ 为 $n$ 阶方阵，且有 $n$ 个相互独立的特征向量 $q_i (i=1,\dots,N)$ ，那么 $A$ 可以被分解为：$$A=Q\Sigma Q^{-1}$$

**推论3**：根据推论2可知，对 $n$ 阶实对称矩阵 $A$ 存在正交矩阵 $Q$ 使得$A=Q\Sigma Q^T$成立，因此**实对称矩阵有 $n$ 个线性无关的特征向量**。

---

**奇异值分解**：对于复矩阵 $M_{m \times n}$ ，存在一个分解使得 $$M=U\Sigma V^*$$ 其中 $U_{m \times m}$ 和 $V_{n \times n}$ 为酉矩阵，$\Sigma$ 是 $m \times m$ 阶非负实数对角矩阵。

$MM^T=U\Sigma V^*V\Sigma U^*=U\Sigma^2U^*$ ，故 $U$ 是 复对称矩阵 $MM^T$ 的特征向量，同理可知 $V$ 是 $M^TM$ 的特征向量。

---

设 $f_i\left(o_j\right)$ 是用户评分函数， $i=1,\dots,n$ 是用户 ID ， $j=1,\dots,m$ 是对象 ID。令 $\textbf{f}_i=\left(f_i\left(o_1\right),\dots,f_i\left(o_m\right)\right)$ 表示用户的评分向量 ， $F=\left(\textbf{f}_1,\dots,\textbf{f}_n\right)^T$ 表示所有用户评分构成的评分矩阵， 其中 $F_{i,j}$ 为用户 $i$ 给对象 $j$ 的评分。

令 $o_j\succ_{u_i}o_k$ 表示用户 $i$ 给对象 $j$ 的评分高于 $k$ ， $\Omega=\left\{\left(u_i,o_j,o_k\right):o_j\succ_{u_i}o_k\right\}$ 为这样一组关系的集合，即「成对」（pairwise）的比较结果 。 $\Omega_t=\left\{\left(j,k\right):o_j\succ_{u_t}o_k\right\}$ 表示用户 $t$ 给对象 $j$ 的评分高于 $k$。

若以获得的一组成对比较结果 $\Omega$ 作为真值，估计一个评分矩阵 $F$ 那么可用下面的式子来评估该矩阵与真值的一致性： 
$$\sum_{\left(i,j,k\right)\in\Omega}{l\left(F_{i,j}-F_{i,k}\right)}\space,$$

式中 $l$ 为某一损失函数。

若所有用户的偏好都是趋近于一致的，那么矩阵 $F$ 应该是低秩的，特别的，但所有用户的偏好都相同， $F$ 是一个秩 1 矩阵。因此可以将估计 $F$ 的问题转化为一个优化问题：
$$\min_{F\in\R^{n\times m}}L\left(F\right)=\lambda \text{rank}\left(F\right)+\sum_{\left(i,j,k\right)\in\Omega}{l\left(F_{i,j}-F_{i,k}\right)}\;\;\;\;(1)$$

要解决这个优化问题，必须先解决以下两个子问题：
 1. 需要多大的规模的 $\Omega$ 才能使估计的 $F$ 是可信的？ 
 2. 怎样优化这个离散非凸函数？

为了解决子问题1，先引入 Kendall tau 距离的定义。

**Kendall tau 距离** 给定两个评分列表 $\tau_1$ 和 $\tau_2$ ，它们之间的归一化的 Kendall tau 距离 $K$ 定义如下：
$$K\left(\tau_1,\tau_2\right)=\frac{1}{C_m^2}\sum_{j=1}^m{\sum_{i>j}^m{\bar{K}_{ij}\left(\tau_1,\tau_2\right)}}\space,$$
其中，若 $i$ 和 $j$ 在 $\tau_1$ 和 $\tau_2$ 中的位置相同，$\bar{K}_{ij}\left(\tau_1,\tau_2\right)=0$ ，否则为 $1$ 。根据 Kendall tau 距离的定义，有以下定理：

定理1. 设 $l\left(z\right)$ 是 hinge loss function，若 $F$ 的秩最大为 $r$，且$\Omega$ 是以均匀分布随机投取的成对比较结果集合，那么 估计矩阵 $F$ 和真值矩阵 $\hat{F}$ 之间的 Kendall tau 距离以概率 $1-\delta$ 具有上界：
$$\frac{r\left(m+n\right)\left[\log{m}+\log{\left(1/\delta\right)}\right]}{\left|\Omega\right|}\space.$$

因为 $\left|\Omega\right|=nC_m^2$ ，所以上述距离的范围是 $\left[0,1\right]$ 。若我们设 $\delta=m^{-2}$，代入上式可得：
$$\frac{3r\left(m+n\right)\log{m}}{\left|\Omega\right|}$$ 
若要使该上界低于 $0.1$ ，即估计的矩阵 $F$ 和真值的差异不超过 $10%$， 需使 $\left|\Omega\right|\ge 30r\left(m+n\right)\log{m}$。

论文中为了突显其方法优势，使用算法复杂度来表示 $\left|\Omega\right|$ 的规模：因为 $r$ 和 $m$ 都远小于 $n$，且 $30$ 为常量系数，因此 $O\left(\left|\Omega\right|\right)=rn\log{m}$ ，即对于每个用户只需收集 $r\log{m}$ 数量级的对象评分，即可估计出整个矩阵 $F$ ，且与真值的误差以 $1-m^{-1}$ 的概率小于 $10%$ 。

接下来解决问题2，如何优化函数(1)。

如果矩阵的秩为 $r$ 那么它一定具有 $r$ 个非零奇异值，所以 $\text{rank}\left(F\right)$ 就是 $F$ 中非零奇异值的数量，那么优化问题即可转化为「优化奇异值之和」，这个和又被称为「核范数」：
$$\|F\|_*=\sum_{k=1}^{\min{\left(m,n\right)}}\sigma_k\left(F\right)$$
其中 $\sigma_k\left(F\right)$ 表示 $F$ 中第 $k$ 大的奇异值。实际上，核范数是 $\text{rank}$ 函数的最佳凸松弛，这一技术在 PCA 中也被应用。

因为奇异值和特征值的相关性，且矩阵的特征值之和等于迹，所以核范数又被称为「迹范数」：
$$\sum_{k=1}^{\min{\left(m,n\right)}}\sigma_k\left(F\right)$$


故前述优化问题可表述如下：
$$\min_{F\in\R^{n\times m}}L\left(F\right)=\lambda \left|F\right|_{tr}+\sum_{\left(i,j,k\right)\in\Omega}{l\left(F_{i,j}-F_{i,k}\right)}\;\;\;\;(1)$$
式中 $\left|F\right|_{tr}$ 为矩阵 $F$ 的迹范数。


令$l\left(z\right)=\max{\left(0,1-z\right)}$ 为hinge 损失函数，希望可以
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM2MDI5MzI3MiwxMzUzNzU3MjQsMzIwOD
cyODI4LC0xMDg1MDc0MjU4LC00NDM2MTY5ODUsMTYyNjg3OTg5
MSwtMjEzMzcxNTAzMiw2MDYxMDk0Niw3MjEyMzAxMzldfQ==
-->