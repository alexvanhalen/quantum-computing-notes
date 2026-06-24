# 4. 密度算符與混合態

[← 上一單元](03-circuits.md)　|　[回目錄](README.md)　|　[下一單元：量子演算法 →](05-quantum-algorithms.md)

---

態向量 $\lvert\psi\rangle$ 只能描述「純態」。當我們對狀態有古典上的不確定性（混合態），或想描述一個糾纏系統的某個子系統時，就需要更一般的工具：**密度算符** $\rho$。

## 4.1 定義與性質

若系統以機率 $p_i$ 處於純態 $\lvert\psi_i\rangle$，其密度算符為

$$
\rho=\sum_i p_i\,\lvert\psi_i\rangle\langle\psi_i\rvert .
$$

任一密度算符滿足三個條件：

1. **厄米**：$\rho=\rho^{\dagger}$。
2. **跡為一**：$\mathrm{tr}(\rho)=1$。
3. **半正定**：$\langle\varphi\rvert\rho\lvert\varphi\rangle\ge0$ 對所有 $\lvert\varphi\rangle$。

**純態判據**：$\rho$ 為純態 $\iff \mathrm{tr}(\rho^2)=1$；混合態則 $\mathrm{tr}(\rho^2)<1$。量 $\mathrm{tr}(\rho^2)$ 稱為純度（purity）。

## 4.2 期望值與演化

可觀測量 $A$ 的期望值：

$$
\langle A\rangle=\mathrm{tr}(\rho A).
$$

么正演化：$\rho\to U\rho U^{\dagger}$。測量結果 $m$ 的機率：$P(m)=\mathrm{tr}(M_m^{\dagger}M_m\,\rho)$，測後態 $\rho\to M_m\rho M_m^{\dagger}/P(m)$。

## 4.3 Bloch 向量（單量子位元）

任一單量子位元密度算符可寫成

$$
\rho=\frac{1}{2}\big(I+\vec r\cdot\vec\sigma\big)
=\frac{1}{2}\big(I+r_xX+r_yY+r_zZ\big),\qquad \lvert\vec r\rvert\le1 .
$$

$\lvert\vec r\rvert=1$ 為純態（落在 Bloch 球面上）；$\lvert\vec r\rvert<1$ 為混合態（球內部）；$\vec r=0$ 給出**最大混合態** $\rho=I/2$，代表完全無資訊。

## 4.4 約化密度算符與偏跡

複合系統 $AB$ 的狀態 $\rho_{AB}$，其子系統 $A$ 的狀態由**偏跡（partial trace）**給出：

$$
\rho_A=\mathrm{tr}_B(\rho_{AB}).
$$

關鍵洞見：即使 $AB$ 整體是純態，子系統 $A$ 仍可能是混合態——這正是**糾纏**的特徵。例如貝爾態 $\lvert\Phi^{+}\rangle=\frac{1}{\sqrt2}(\lvert00\rangle+\lvert11\rangle)$：

$$
\rho_{AB}=\lvert\Phi^{+}\rangle\langle\Phi^{+}\rvert,\qquad
\rho_A=\mathrm{tr}_B(\rho_{AB})=\frac{1}{2}\big(\lvert0\rangle\langle0\rvert+\lvert1\rangle\langle1\rvert\big)=\frac{I}{2}.
$$

整體是「最有資訊」的純態，局部卻是「最無資訊」的最大混合態——糾纏把資訊藏在了關聯裡。

## 4.5 純化（purification）

反過來，任一混合態 $\rho_A$ 都可看成某個更大系統純態的約化：存在 $\lvert\Psi\rangle_{AB}$ 使 $\rho_A=\mathrm{tr}_B(\lvert\Psi\rangle\langle\Psi\rvert)$。也就是說，「混合」永遠可以理解成「與環境糾纏」。這個觀點是第 6 章量子通道與第 8 章量子熵的基礎。

---

[← 上一單元](03-circuits.md)　|　[回目錄](README.md)　|　[下一單元：量子演算法 →](05-quantum-algorithms.md)
