# 2. 量子力學基礎：態、測量與量子位元

[← 上一單元](01-introduction.md)　|　[回目錄](README.md)　|　[下一單元：量子閘與量子電路 →](03-circuits.md)

---

量子計算建立在量子力學的四個基本假設上。我們用有限維的複內積空間（希爾伯特空間 $\mathcal{H}=\mathbb{C}^d$）來表述。

## 2.1 假設一：狀態

一個孤立量子系統的狀態，由希爾伯特空間中的一個**單位向量** $\lvert\psi\rangle$ 描述（$\langle\psi\vert\psi\rangle=1$）。整體相位無物理意義：$\lvert\psi\rangle$ 與 $e^{i\gamma}\lvert\psi\rangle$ 代表同一個物理態。

**量子位元**就是 $d=2$ 的情形，計算基底為 $\lvert0\rangle=\begin{pmatrix}1\\0\end{pmatrix}$、$\lvert1\rangle=\begin{pmatrix}0\\1\end{pmatrix}$，一般態

$$
\lvert\psi\rangle=\alpha\lvert0\rangle+\beta\lvert1\rangle,\qquad \alpha,\beta\in\mathbb{C},\quad \lvert\alpha\rvert^2+\lvert\beta\rvert^2=1 .
$$

## 2.2 假設二：演化

封閉系統的演化由**么正算符（unitary）**描述：$\lvert\psi'\rangle=U\lvert\psi\rangle$，其中 $U^{\dagger}U=I$。么正性保證機率守恆（範數不變），也意味著量子閘**可逆**。連續時間下，演化遵守薛丁格方程

$$
i\hbar\frac{d}{dt}\lvert\psi(t)\rangle=H\lvert\psi(t)\rangle,
$$

$H$ 為厄米的哈密頓量，對應的演化 $U(t)=e^{-iHt/\hbar}$。

## 2.3 假設三：測量

對基底 $\{\lvert m\rangle\}$ 做投影測量，得到結果 $m$ 的機率為

$$
P(m)=\lvert\langle m\vert\psi\rangle\rvert^2 \quad(\text{Born 規則}),
$$

測量後狀態**塌縮**為 $\lvert m\rangle$。以量子位元為例，測得 $0$ 的機率是 $\lvert\alpha\rvert^2$、測得 $1$ 的機率是 $\lvert\beta\rvert^2$。更一般地，可用一組測量算符 $\{M_m\}$（滿足 $\sum_m M_m^{\dagger}M_m=I$），結果機率 $P(m)=\langle\psi\rvert M_m^{\dagger}M_m\lvert\psi\rangle$，測後態 $M_m\lvert\psi\rangle/\sqrt{P(m)}$。

## 2.4 假設四：複合系統

多體系統的狀態空間是各子系統的**張量積**：$\mathcal{H}=\mathcal{H}_1\otimes\mathcal{H}_2\otimes\cdots$。兩個量子位元的基底為 $\lvert00\rangle,\lvert01\rangle,\lvert10\rangle,\lvert11\rangle$（$\mathbb{C}^4$）。$n$ 個量子位元的維度為 $2^n$。

無法寫成 $\lvert a\rangle\otimes\lvert b\rangle$ 的狀態稱為**糾纏態**，例如貝爾態 $\frac{1}{\sqrt2}(\lvert00\rangle+\lvert11\rangle)$。

## 2.5 Bloch 球：單一量子位元的幾何

去掉整體相位後，任一量子位元純態可寫成

$$
\lvert\psi\rangle=\cos\frac{\theta}{2}\,\lvert0\rangle+e^{i\varphi}\sin\frac{\theta}{2}\,\lvert1\rangle,
$$

對應到單位球面上的一點 $\hat n=(\sin\theta\cos\varphi,\ \sin\theta\sin\varphi,\ \cos\theta)$。北極是 $\lvert0\rangle$、南極是 $\lvert1\rangle$；赤道上的 $\frac{1}{\sqrt2}(\lvert0\rangle\pm\lvert1\rangle)$ 等為等權疊加態。單一量子位元的么正操作，就是 Bloch 球上的旋轉。

## 2.6 Pauli 算符

$$
X=\begin{pmatrix}0&1\\1&0\end{pmatrix},\quad
Y=\begin{pmatrix}0&-i\\i&0\end{pmatrix},\quad
Z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}.
$$

它們是厄米且么正的，滿足 $X^2=Y^2=Z^2=I$，並有 $XY=iZ$（及其輪換）。$\{I,X,Y,Z\}$ 構成 $2\times2$ 複矩陣空間的一組基底，是描述單量子位元操作與雜訊的基本工具。

---

[← 上一單元](01-introduction.md)　|　[回目錄](README.md)　|　[下一單元：量子閘與量子電路 →](03-circuits.md)
