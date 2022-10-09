# 重み付け線形和

入力層に２つ、１層目に２つのニューロンを想定する。  
このとき１層目の１つめのニューロンへの入力と２つ目のニューロンへの入力は、  

１つ目

$u^1_1 = w_{11}\times x_1 + w_{21}\times x_2$

２つ目

$u^1_2 = w_{12}\times x_1 + w_{22}\times x_2$

**一般化**

$u^l_j = w^l_{1j}z_1^{l-1}+w^l_{2j}z_2^{l-1}+..$

$^l$ : layer  
$w_{ij}$ : i 番目ニューロンから j 番目ニューロンへの重み

# 三角関数の微分公式

$(sinx)' = cosx$

$(cosx)' = -sinx$

$(tanx)' = -\frac{1}{cos^2x}$


# 偏差値
**※「標準偏差値」という用語は無い。**

$偏差値=\frac{x-\mu}{\sigma}\times 10 + 50$

平均との差に対して、分散（ばらつき）が小さいほど影響を大きく（ずば抜けて...）、分散が大きいほど影響を小さくしたいので、分散が分母にくる。

$\sigma$ : 標準偏差（standard deviation）= $\sqrt{分散}$

$\sigma^2$ : 分散（variance）

# 確率変数（Stochastic Variable）
具体的な値のこと。確率変数を $X$、実現値を $x$ で表す。

確率(密度)関数とは「具体的な値から確率を得る関数 $f(X)$」のこと。  
e.g.)正規分布、一様分布

# 期待値
確率変数が取る値を、確率によって重み付けした**加重平均値**。期待値の定義は離散型確率変数と連続型確率変数とで扱いが異なる。

離散型  
$E[X]=\sum_i{x_if(x_i)}$

連続型  
$E[X]=\int^{\infty}_{-\infty}{xf(x)dx}$

# 平均値と期待値の関係
平均値は次の式で求められる。

$\displaystyle\overline{x}=\sum_{i}\frac{x_iN_i}{N}$

※${N_i}$は${x_i}$が発生した回数。$\frac{N_i}{N}$を**相対度数**という。

標本数 $N$ が $\infty$ では、$相対度数\space\frac{N_i}{N}=p_i$ となり、$\bold{平均\space\overline{x}=期待値\space\mu}$ となる。  

$\displaystyle\mu=\sum_{i}x_ip_i$

<u>**M**</u>EAN（平均）の頭文字Mのギリシャ文字が $\mu$ (mu) であり、期待値は $\mu$ で表記される。

# 確率変数の分散の公式
通常の分散

$\displaystyle\sigma^2=\frac1n\sum^n_{i=1}(x_i-\overline{x})^2$

標本数$N$、${x_i}$が発生する度数を$N_i$ とする確率で理解すると、

$\displaystyle\sum^n_{i=1}(x_i-\overline{x})^2\frac{N_i}{N}$

$N$ が $\infty$ では、相対度数 $\frac{N_i}{N}=p_i$（確率）となり、平均値と期待値は等しくなる（$\overline{x}=\mu$）。

確率変数の分散を次のように定義している。

$\displaystyle\sigma^2=V[X]=\sum^n_{i=1}(x_i-\mu)^2p_i$

# ベルヌーイ分布
ベルヌーイ試行を１回行う場合に確率変数$X$が従う分布をベルヌーイ分布（$Be(p)$）という。$X\backsim Be(p)$と表記する。

確率変数 $X$ は$失敗=0$ 又は、$成功=1$ の何れかとなる。
