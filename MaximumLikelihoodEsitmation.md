# 最尤推定（MLE:maximum likelihood esitmation）

## コイントスの例（二項分布）

コインを n 回投げると、表が k 回だった（結果・現象）。このコインの表になる（神のみぞ知る）真の確率 $p_0$ はいくらだったか？を考える。

もし、表率が $p$（現象を支配するパラメータ）ならば、この現象の確率は次の式で表せる（尤度：likelihood）。

尤度 ： $L(p)={}_nC_kp^k(1-p)^{n-k}$

この尤度が最大になるときの $p$ が $\hat{p}$ （推定値）であった。このとき、 $p_0=\hat{p}$ ではないか？

$\hat{p}=\arg\max L(p)$

⇒　以上の手法を「最尤推定」という。

対数をとって微分する。最大値を取るのは傾きが0の時。

**対数尤度** ：

$\log{L(p)}=\log({}_nC_kp^k(1-p)^{n-k})$

$=\log{p^k}+\log{(1-p)^{n-k}}+\log{{}_nC_k}$

$=k\log{p}+(n-k)\log{(1-p)}+\log{{}_nC_k}$

パラメータ $p$ で微分する（末尾に項は定数）。

$\displaystyle \frac{dL(p)}{dp}=\frac{k}{p}+\frac{(n-k)}{(1-p)}\times(-1)\to 0$

$\displaystyle \frac{k}{\hat{p}}=\frac{n-k}{1-\hat{p}}$ ⇒ 
$\hat{p}:(1-\hat{p})=k:(n-k)$

$\displaystyle \hat{p}=\frac{k}{n}$

## サイコロの例（多項分布）

サイコロを n 回振った。 $i\in\{1,2,3,4,5,6\}$ の目が出た回数を $k_i$ 、 $i$ が出た確率を $P_i$ と表記する。多項分布の確率密度関数より、

$L(p)=\frac{n!}{k_1!...k_6!}P^{k_1}_1...P^{k_6}_6$

対数尤度：

$\log L(p)=CONST+k_1\log{P_1}+...+k_6\log{P_6}$

まず $P_1$ で微分する。しかし $P_1+P_2+P_3+P_4+P_5+P_6=1$ であるので、 $P_1$ のみを変化させることは出来ず、二項分布のときのように微分することはできない。そこで $P_2,..,P_5$ を定数とし $P_6$ に全ての変化を押し付けて考える。

$k_6\log{P_6}=k_6\log{(1-P_1-P_2-P_3-P_4-P_5)}$

偏微分する。

$\displaystyle \frac{\partial L}{\partial P_1}=\frac{k_1}{P_1}-\frac{k_6}{1-P_1-P_2-P_3-P_4-P_5}$

$=\displaystyle\frac{k_1}{P_1}-\frac{k_6}{P_6}$

他の $P_i$ でも同様に偏微分すると、

$\displaystyle\frac{\partial L}{\partial P_i}=\frac{k_1}{P_i}-\frac{k_6}{P_6}$

$=0$ で最尤推定値なので、次の関係が成り立つ。

$\displaystyle\frac{k_1}{\hat{p_1}}=\frac{k_2}{\hat{p_2}}=...=\frac{k_6}{\hat{p_6}}$

すなわち

$\displaystyle\hat{p}_i=\frac{k_i}{n}$

【最尤推定の問題】

サイコロを6回振ったデータで最尤推定値を算出してみると明かであるが、 $n$ が少ない場合、 $\hat{p_i}$ はまったく信頼できな値となる。


