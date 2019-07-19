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

设 $f_i\left(o_j\right)$ 是用户评分函数， $i=1,\dots,n$ 是用户 ID ， $j=1,\dots,m$ 是对象 ID。令 $\textbf{f}_i=\left(f_i\left(o_1\right),\dots,f_i\left(o_m\right)\right)$ 表示用户的评分向量 ， $F=\left(\textbf{f}_1,\dots,\textbf{f}_n\right)^T$ 表示所有用户评分构成的评分矩阵。
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYzMTYzOTU0Miw3MjEyMzAxMzldfQ==
-->