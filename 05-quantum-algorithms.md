# 5. 量子演算法：從 Deutsch–Jozsa 到 QFT 與 Grover

[← 上一單元](04-density-operator.md)　|　[回目錄](README.md)　|　[下一單元：量子雜訊與量子操作 →](06-noise-and-operations.md)

---

量子加速的共同核心是**干涉**：先用疊加把函數值「攤開」到所有振幅上，再用巧妙的么正操作讓我們**想要**的資訊以相長干涉浮現、其餘相消。

## 5.1 量子預言機與相位回踢

許多演算法把古典函數 $f$ 包成一個可逆的**預言機（oracle）**么正：

$$
U_f\,\lvert x\rangle\lvert y\rangle=\lvert x\rangle\lvert y\oplus f(x)\rangle .
$$

若把目標位元預備成 $\lvert-\rangle=\frac{1}{\sqrt2}(\lvert0\rangle-\lvert1\rangle)$，會發生**相位回踢（phase kickback）**：

$$
U_f\,\lvert x\rangle\lvert-\rangle=(-1)^{f(x)}\lvert x\rangle\lvert-\rangle .
$$

函數值被「踢」到了相位上——這是 Deutsch–Jozsa、Grover 等演算法的共同把戲。

## 5.2 Deutsch–Jozsa 演算法

**問題**：給定 $f:\{0,1\}^n\to\{0,1\}$，保證它要嘛是常數（constant），要嘛是平衡（balanced，恰好一半輸出 0、一半 1）。判斷是哪一種。古典最壞情況要查 $2^{n-1}+1$ 次；量子只需**一次**預言機呼叫。

**流程**：對 $n$ 個位元做 $H^{\otimes n}$ 製造均勻疊加 → 用相位回踢呼叫 $U_f$ → 再做 $H^{\otimes n}$ → 測量。最後測得全 $0$ 的機率為

$$
P(0\cdots0)=\left\lvert\frac{1}{2^n}\sum_{x}(-1)^{f(x)}\right\rvert^2 .
$$

常數函數時此值為 $1$（必測得全 0）；平衡函數時為 $0$（必不會全 0）。一次量子查詢就能完全分辨，是「干涉取代窮舉」的教科書範例。

## 5.3 量子傅立葉轉換（QFT）

QFT 是離散傅立葉轉換在量子振幅上的版本。對 $N=2^n$，

$$
\text{QFT}\,\lvert x\rangle=\frac{1}{\sqrt N}\sum_{k=0}^{N-1}e^{\,2\pi i\,xk/N}\,\lvert k\rangle .
$$

它有一個漂亮的**乘積形式**，正是高效電路的來源（$j_1j_2\cdots j_n$ 為 $x$ 的二進位）：

$$
\text{QFT}\,\lvert x\rangle=\frac{1}{\sqrt N}\bigotimes_{\ell=1}^{n}\Big(\lvert0\rangle+e^{\,2\pi i\,(0.j_{\ell}j_{\ell+1}\cdots j_n)}\lvert1\rangle\Big).
$$

**電路成本**：只用 Hadamard 與受控相位閘，共 $O(n^2)$ 個閘——相較於古典 FFT 的 $O(N\log N)=O(n2^n)$，是指數級的縮減（但要注意：QFT 把結果藏在振幅裡，不能直接讀出全部係數）。QFT 是**相位估計**與 **Shor 因式分解**演算法的引擎。

## 5.4 相位估計（Phase Estimation）

**問題**：給定么正 $U$ 及其特徵態 $\lvert u\rangle$（$U\lvert u\rangle=e^{2\pi i\varphi}\lvert u\rangle$），估計相位 $\varphi$。

**做法**：用 $t$ 個計數位元，透過受控 $U^{2^j}$ 把相位以二進位編碼進計數暫存器，再做**逆 QFT** 讀出 $\varphi$ 的最佳 $t$ 位近似。用 $t=n+\lceil\log(2+\frac{1}{2\epsilon})\rceil$ 個位元，可在機率 $\ge1-\epsilon$ 下得到 $n$ 位精度。相位估計是 Shor 演算法（透過求週期 / 階）以及許多量子模擬演算法的核心子程序。

## 5.5 Grover 搜尋

**問題**：在 $N=2^n$ 個項目中，找到滿足 $f(x)=1$ 的「被標記」項（假設有 $M$ 個解）。古典需 $O(N)$ 次查詢；Grover 只需 $O(\sqrt{N})$ 次——平方根加速。

**兩個反射**。每一輪 Grover 迭代 $G$ 由兩步組成：

1. **預言機反射** $O$：對被標記態加負號，$O=I-2\sum_{x:\,f(x)=1}\lvert x\rangle\langle x\rvert$。
2. **關於平均的反射（擴散算符）** $D=2\lvert s\rangle\langle s\rvert-I$，其中 $\lvert s\rangle=H^{\otimes n}\lvert0\rangle$ 是均勻疊加。

把初始均勻態 $\lvert s\rangle$ 分解到「解空間」與「非解空間」張成的二維平面上，$G$ 的作用就是在此平面內每次旋轉一個固定角 $\theta$，其中 $\sin\frac{\theta}{2}=\sqrt{M/N}$。經過

$$
R\approx\left\lfloor\frac{\pi}{4}\sqrt{\frac{N}{M}}\right\rfloor
$$

次迭代後，狀態幾乎完全落在解空間，測量即以高機率得到一個解。

**注意過度旋轉**：迭代太多次反而會「轉過頭」、成功機率下降——Grover 的振幅是正弦振盪，不是越多越好。此外可證明 $\Omega(\sqrt N)$ 是無結構搜尋的下界，故 Grover 在查詢複雜度上是最優的。

## 5.6 小結：加速從哪來？

| 演算法 | 加速來源 | 加速幅度 |
| --- | --- | --- |
| Deutsch–Jozsa | 相位回踢 + 干涉 | 指數（查詢數） |
| QFT / 相位估計 / Shor | 週期性 → 傅立葉峰值 | 指數 |
| Grover | 振幅放大（幾何旋轉） | 平方根 |

---

[← 上一單元](04-density-operator.md)　|　[回目錄](README.md)　|　[下一單元：量子雜訊與量子操作 →](06-noise-and-operations.md)
