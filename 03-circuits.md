# 3. 量子閘與量子電路

[← 上一單元](02-foundations.md)　|　[回目錄](README.md)　|　[下一單元：密度算符 →](04-density-operator.md)

---

量子電路模型把計算描述成：對量子位元施加一連串**量子閘**（么正算符），最後做測量。因為么正算符可逆，量子閘也都可逆——這與古典邏輯閘（如 AND、OR 會丟失資訊）很不一樣。

## 3.1 單量子位元閘

| 閘 | 矩陣 | 作用 |
| --- | --- | --- |
| $X$（NOT） | $\begin{pmatrix}0&1\\1&0\end{pmatrix}$ | 翻轉 $\lvert0\rangle\leftrightarrow\lvert1\rangle$ |
| $Z$ | $\begin{pmatrix}1&0\\0&-1\end{pmatrix}$ | 相位翻轉 $\lvert1\rangle\to-\lvert1\rangle$ |
| $H$（Hadamard） | $\frac{1}{\sqrt2}\begin{pmatrix}1&1\\1&-1\end{pmatrix}$ | 製造疊加 |
| $S$ | $\begin{pmatrix}1&0\\0&i\end{pmatrix}$ | 相位 $\pi/2$ |
| $T$ | $\begin{pmatrix}1&0\\0&e^{i\pi/4}\end{pmatrix}$ | 相位 $\pi/4$ |

Hadamard 是最重要的單量子位元閘：

$$
H\lvert0\rangle=\frac{\lvert0\rangle+\lvert1\rangle}{\sqrt2}\equiv\lvert+\rangle,\qquad
H\lvert1\rangle=\frac{\lvert0\rangle-\lvert1\rangle}{\sqrt2}\equiv\lvert-\rangle .
$$

對 $n$ 個量子位元都作用 $H$，可從 $\lvert0\rangle^{\otimes n}$ 一步製造出所有 $2^n$ 個基底態的等權疊加：

$$
H^{\otimes n}\lvert0\rangle^{\otimes n}=\frac{1}{\sqrt{2^n}}\sum_{x=0}^{2^n-1}\lvert x\rangle .
$$

## 3.2 多量子位元閘：CNOT 與糾纏

**受控反閘（CNOT）**以第一個量子位元為控制、第二個為目標：

$$
\text{CNOT}=\begin{pmatrix}1&0&0&0\\0&1&0&0\\0&0&0&1\\0&0&1&0\end{pmatrix},\qquad
\text{CNOT}\,\lvert a,b\rangle=\lvert a,\,a\oplus b\rangle .
$$

CNOT 加上 Hadamard 即可製造糾纏。製備貝爾態的電路：先對控制位元施 $H$，再施 CNOT：

$$
\lvert00\rangle\xrightarrow{H\otimes I}\frac{\lvert00\rangle+\lvert10\rangle}{\sqrt2}
\xrightarrow{\text{CNOT}}\frac{\lvert00\rangle+\lvert11\rangle}{\sqrt2}=\lvert\Phi^{+}\rangle .
$$

另一個常用的三量子位元閘是 **Toffoli（CCNOT）**：當兩個控制位元皆為 $1$ 時才翻轉目標，$\lvert a,b,c\rangle\to\lvert a,b,\,c\oplus(a\wedge b)\rangle$。它本身就能可逆地實現古典通用邏輯。

## 3.3 通用性（universality）

並不需要無限多種閘。一組閘若能把任意 $n$ 量子位元的么正操作近似到任意精度，就稱為**通用閘集**。常見結論：

- $\{H,\,T,\,\text{CNOT}\}$ 是一組通用閘集。
- $\{$ 所有單量子位元閘 $+$ CNOT $\}$ 也是通用的。

**Solovay–Kitaev 定理**保證：用通用閘集近似任一單量子位元么正到誤差 $\varepsilon$，只需 $O\!\big(\log^{c}(1/\varepsilon)\big)$ 個閘（$c$ 為小常數），代價只是多項式對數級的開銷。

## 3.4 不可複製定理（No-Cloning）

不存在一個么正 $U$ 能對任意未知態做 $U(\lvert\psi\rangle\otimes\lvert0\rangle)=\lvert\psi\rangle\otimes\lvert\psi\rangle$。

**證明（線性）**：若對 $\lvert\psi\rangle$ 與 $\lvert\phi\rangle$ 都成立，取內積得 $\langle\phi\vert\psi\rangle=\langle\phi\vert\psi\rangle^2$，故 $\langle\phi\vert\psi\rangle\in\{0,1\}$——只有正交或相同的態才可能被複製，任意未知態則不行。這個定理深刻影響量子糾錯（不能單純「備份」）與量子密碼（竊聽必留痕跡）。

## 3.5 量子電路圖怎麼讀

- 每條水平線是一個量子位元，時間由左到右。
- 方塊代表單量子位元閘；實心點 $\bullet$ 連到 $\oplus$ 代表 CNOT（點為控制、$\oplus$ 為目標）。
- 末端的「儀表」符號代表測量，把量子資訊讀成古典位元。

---

[← 上一單元](02-foundations.md)　|　[回目錄](README.md)　|　[下一單元：密度算符 →](04-density-operator.md)
