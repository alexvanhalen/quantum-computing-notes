# 量子計算 Quantum Computing — 課程筆記

> 線上講義（Markdown + LaTeX）。GitHub 會原生渲染數學公式，因此本筆記的方程式可直接以漂亮的數學形式呈現。
> 授課教師：王和盛｜國立臺灣海洋大學 通訊與導航工程學系

---

## 課程簡介

本課程介紹量子計算與量子資訊的核心概念：如何用量子力學的疊加與糾纏進行計算，量子演算法為何能在某些問題上超越古典電腦，以及在有雜訊的真實世界裡，如何用量子糾錯保護量子資訊。課程從量子力學的數學語言出發，逐步建立量子位元、量子電路、量子演算法、開放系統與量子通道、糾錯碼，最後以量子資訊論作結。

**先備知識**：線性代數（向量空間、內積、特徵值與特徵向量、么正與厄米矩陣）、基礎機率，以及一點點古典計算理論。

---

## 單元目錄

1. [導論與總覽](01-introduction.md)
2. [量子力學基礎：態、測量與量子位元](02-foundations.md)
3. [量子閘與量子電路](03-circuits.md)
4. [密度算符與混合態](04-density-operator.md)
5. [量子演算法：從 Deutsch–Jozsa 到 QFT 與 Grover](05-quantum-algorithms.md)
6. [量子雜訊與量子操作](06-noise-and-operations.md)
7. [古典與量子糾錯碼](07-error-correction.md)
8. [熵與量子資訊論](08-entropy-and-information.md)

---

## 數學符號約定

| 記號 | 意義 |
| --- | --- |
| $\lvert\psi\rangle$ | 態向量（ket） |
| $\langle\psi\rvert$ | 對偶向量（bra），$\langle\psi\rvert = \lvert\psi\rangle^{\dagger}$ |
| $\langle\phi\vert\psi\rangle$ | 內積 |
| $\lvert\phi\rangle\langle\psi\rvert$ | 外積（算符） |
| $A^{\dagger}$ | 共軛轉置（厄米伴隨） |
| $\otimes$ | 張量積 |
| $\mathrm{tr}(\cdot)$ | 跡（trace） |
| $\rho$ | 密度算符 |

行內公式範例：一個量子位元的一般態為 $\lvert\psi\rangle=\alpha\lvert 0\rangle+\beta\lvert 1\rangle$，且 $\lvert\alpha\rvert^2+\lvert\beta\rvert^2=1$。

區塊公式範例：

$$
\lvert\psi\rangle=\cos\frac{\theta}{2}\,\lvert 0\rangle+e^{i\varphi}\sin\frac{\theta}{2}\,\lvert 1\rangle .
$$

如果上面這兩個式子在 GitHub 上顯示成漂亮的數學，就代表數學渲染正常運作。

---

## 如何上線（給維護者）

1. 在 GitHub 建一個新的 repository（例如 `quantum-computing-notes`），把本資料夾的檔案上傳。
2. GitHub 會自動以 MathJax 渲染 `.md` 檔中的 `$...$`（行內）與 `$$...$$`（區塊）公式，**不需要任何額外設定**。
3. （選用）若想要一個更像「課程網站」的版面：到 repo 的 **Settings → Pages**，選擇由 `main` 分支發佈，即可得到一個 GitHub Pages 網址；之後在 Google 協作平台的「量子計算」分頁，用連結指向各單元即可。
4. 在協作平台呈現方式：可在「量子計算」分頁，為每個單元放一個連結（指向對應的 `.md` 或 GitHub Pages 頁面）。

---

## 參考方向

本筆記為原創教學整理，涵蓋量子計算的標準主題。若需延伸閱讀，課程常見的經典參考包括 Nielsen & Chuang《Quantum Computation and Quantum Information》、John Preskill 的線上講義，以及 MIT 8.04 等量子力學課程；相關 PDF 講義另存於課程雲端資料夾。
