# 誤差逆伝播

活性化関数 : ※ l : 層、L : 最終層

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
