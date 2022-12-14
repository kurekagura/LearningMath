# 平均二乗誤差（mean squared error）

$\displaystyle MSE=\frac{1}{N}\sum^N_{n=1}(y_n-t_n)^2$
$\qquad t_n$ : 正解値（=平均値であれば分散となる）

これを最小化する　⇒　最小二乗法

ちなみに、

$\quad\enspace\displaystyle \sigma^2=\frac{1}{N}\sum^N_{n=1}(y_n-\overline{y})^2$
$\qquad\overline{y}$ : 平均値

# 交差エントロピー誤差

## 多クラス分類

$\displaystyle L=-\frac{1}{N}\sum^N_{n=1}\sum^K_{k=1}t_n^k\log{y_{nk}}$

<img src="./img/交差エントロピー誤差(多クラス分類).png" width="50%">

## ２クラス分類

$\displaystyle L=-\sum^N_{n=1}\lbrace t_n\log{y_n}+(1-t_n)\log(1-y_n)\rbrace$

正解値（ $t_n=1\space or\space t_n=0$ ）と予測値が一致すると $\lbrace \rbrace$ の中は ゼロ になる。

正解（ $t_n=1$ ）と不正解（ $t_n=0$ ）の場合で、左右の項を別々のグラフで表すと理解しやすい。

<img src="./img/交差エントロピー誤差(2クラス分類).png" width="50%">

尤度（関数）：

もっともらしい（あてはまりの良さ）ほうが大きな値になる。

マイナスを付ける理由：

最適化は損失（誤差）を最小化する方向として理解するほうが自然なので、尤度関数をマイナスにする。

対数とする理由：

小数点の掛け算を繰り返すと値がどんどん小さくなっていく。そこで、対数を導入し掛け算を足し算とする方が都合が良い。
