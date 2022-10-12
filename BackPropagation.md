# 表記

$\boxed{u_i^{l-1}|z_i^{l-1}}\xrightarrow{w^l_{ij}}\boxed{u_j^l\quad|z_j^l\quad}$  

$i$ は $l-1$ 層目の上から $i$ 番目のニューロン。  
$j$ は $l$ 層目の上から $j$ 番目のニューロン。

$u$ は重み付き線形和

$\displaystyle u^l_{j}=\sum_i w^l_{ij}z^{l-1}_i$

$u$ を活性化関数で処理した結果が $z$

$\displaystyle z^l_j=\varphi(u^l_j)=\varphi(\sum_i w^l_{ij}z^{l-1}_i)$

# 誤差逆伝播

$u$ は重み付け線形和の関数を表す。

$u^l_{ij}=u^l_{ij}(z^{l-1}_0,z^{l-1}_1,...,z^{l-1}_n)$

$(l-1)$ 層目の $n$ 個のニューロンから次の $l$ 層目の1番目のニューロン $\boxed{u|z}^l_1$ へ入力される際の例

$u^l_1=w^l_{11}z^{l-1}_1+w^l_{21}z^{l-1}_2+w^l_{31}z^{l-1}_3+...+w^l_{n1}z^{l-1}_n+b$

活性化関数 :

$z=\varphi^l(u)$

誤差関数 : ※ MSE。N=2のL2損失

$\displaystyle E=\frac{1}{N}\sum_i(y_i-\hat{y_i})^2$

～　最終層 L での話　～

$\quad\searrow$  
$\xrightarrow{w^L_{ij}}\boxed{u_j^L | z_j^L}$  
$\quad\nearrow$

誤差関数の ${w^L_{ij}}$ による偏微分 $\displaystyle\frac{\partial E}{\partial w^L_{ij}}$ を求める。

連鎖律より

$\displaystyle\frac{\partial E}{\partial w^L_{ij}} = \frac{\partial E}{\partial u^L_j} \frac{\partial u^L_j}{\partial w^L_{ij}}$

$\displaystyle\frac{\partial u^L_j}{\partial w^L_{ij}}$ は(L-1)層からの重み付け線形和を $w^L_{ij}$ で偏微分しているだけなので、１つの項、すなわち $[...+w^L_{ij}\times{z^{L-1}_i}+...]$ 以外は定数として消えて $=z^{L-1}_i$ となる。

$\displaystyle\frac{\partial E}{\partial w^L_{ij}} = \frac{\partial E}{\partial u^L_j} z^{L-1}_i$

次に $\displaystyle\frac{\partial E}{\partial u^L_j}=\delta^L_j$ とおく。

$z=\varphi(u)$ , $E(\varphi(u))$ の合成関数なので、

$\displaystyle\delta^L_j = \frac{\partial E}{\partial z^L_j} \frac{\partial z^L_j}{\partial u^L_{j}}$

活性化関数 $\varphi^L(u)$ が<ins>恒等関数の場合</ins>、 $z'(u)=1$ であるので、

$\displaystyle\delta^L_j = \frac{\partial E}{\partial z^L_j}\times1$

出力層の $z^L_j$ は $y_j$なので、誤差関数 $E$ を $y_j$ で偏微分していることになる。  
MSEの $y_j$ による偏微分では、一つだけ現れる $[...+(y_j-\hat{y_j})^2+...]$ 以外は定数として消え、

$\delta^L_j=y_j-\hat{y}_j$

以上より、誤差関数の ${w^L_{ij}}$ による偏微分が求まる。

**右辺は順伝播で得られる値であるので、最終層の勾配の値が求まる。**

$\displaystyle\frac{\partial E}{\partial w^L_{ij}} =(y_j-\hat{y}_j)\times z^{L-1}_i$

～　重みの更新　～

学習率 $\varepsilon$ を掛けて引く。

$ w^L_{ij} \gets w^L_{ij} - \varepsilon\times{(y_j-\hat{y}_j)z^{L-1}_i}$

～　中間層を考える　～

$\displaystyle\frac{\partial E}{\partial w^l_{ij}} = \frac{\partial E}{\partial u^l_j} \frac{\partial u^l_j}{\partial w^l_{ij}} = \delta^{l}_{j} z^{l-1}_i$

※ $z^{l-1}_i$ は順伝播で値が得られる。

$\displaystyle\delta^{l}_{j}=\frac{\partial E}{\partial u^l_j}=$