# 6. 量子雜訊與量子操作

[← 上一單元](05-quantum-algorithms.md)　|　[回目錄](README.md)　|　[下一單元：糾錯碼 →](07-error-correction.md)

---

真實的量子位元不是封閉系統——它們會和環境耦合而**退相干**。要描述這種開放系統的演化，么正算符不夠用，需要更一般的「量子操作 / 量子通道」。

## 6.1 量子通道與算符和表示（Kraus）

一個物理上合理的演化 $\mathcal{E}$（保跡、完全正定，CPTP map）一定可寫成**算符和表示**：

$$
\mathcal{E}(\rho)=\sum_k E_k\,\rho\,E_k^{\dagger},\qquad \sum_k E_k^{\dagger}E_k=I .
$$

$\{E_k\}$ 稱為 **Kraus 算符**。直觀理解：環境以某些「方式」$k$ 作用於系統，$\sum_k E_k^{\dagger}E_k=I$ 保證總機率守恆。么正演化是只有一個 Kraus 算符（$E_0=U$）的特例。

**等價觀點（Stinespring）**：任一通道都可看成「系統 + 環境做么正演化，再對環境取偏跡」：

$$
\mathcal{E}(\rho)=\mathrm{tr}_{E}\big[U(\rho\otimes\lvert0\rangle_E\langle0\rvert)U^{\dagger}\big].
$$

雜訊，本質上就是資訊洩漏到環境。

## 6.2 常見的單量子位元雜訊通道

**位元翻轉（bit flip）**：以機率 $p$ 施加 $X$。

$$
\mathcal{E}(\rho)=(1-p)\,\rho+p\,X\rho X,\qquad E_0=\sqrt{1-p}\,I,\ E_1=\sqrt{p}\,X .
$$

**相位翻轉（phase flip）**：把上式的 $X$ 換成 $Z$。

**去極化通道（depolarizing）**：以機率 $p$ 把狀態換成最大混合態：

$$
\mathcal{E}(\rho)=(1-p)\,\rho+\frac{p}{3}\big(X\rho X+Y\rho Y+Z\rho Z\big).
$$

**振幅阻尼（amplitude damping）**：描述能量耗散（如激發態自發輻射 $\lvert1\rangle\to\lvert0\rangle$），Kraus 算符

$$
E_0=\begin{pmatrix}1&0\\0&\sqrt{1-\gamma}\end{pmatrix},\qquad
E_1=\begin{pmatrix}0&\sqrt{\gamma}\\0&0\end{pmatrix},
$$

$\gamma$ 為衰減機率。注意 $E_1$ 把 $\lvert1\rangle$ 變回 $\lvert0\rangle$——這是不可逆的能量損失。

## 6.3 在 Bloch 球上看雜訊

雜訊通道在 Bloch 球上是**把球收縮 / 變形**的仿射映射 $\vec r\mapsto M\vec r+\vec c$：

- 去極化：球均勻向中心收縮，$\vec r\to(1-p)\vec r$。
- 相位翻轉：$x,y$ 方向收縮、$z$ 不變（破壞相干、保留布居）。
- 振幅阻尼：球往北極（$\lvert0\rangle$）收縮並偏移——終態趨向基態。

## 6.4 退相干的兩個時間尺度

- $T_1$（縱向 / 能量弛豫）：布居趨向平衡的時間（對應振幅阻尼）。
- $T_2$（橫向 / 相位弛豫）：疊加相干性消失的時間（對應相位翻轉類過程），且 $T_2\le 2T_1$。

延長 $T_1,T_2$（讓退相干慢於閘操作）正是 DiVincenzo 準則第三條的要求，也是硬體工程的核心挑戰。下一章要問的是：既然雜訊無法完全消除，能不能用**編碼**把資訊保護起來？

---

[← 上一單元](05-quantum-algorithms.md)　|　[回目錄](README.md)　|　[下一單元：糾錯碼 →](07-error-correction.md)
