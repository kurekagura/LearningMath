# AdaBoost（アダ・ブースト）

学習データに重み付けによる変化を与え、一つづつ順番に弱学習器（弱分類器）を生成し、直列につなげる。前の弱学習器の間違い・誤差に応じてデータを調整し（重み付けし）、次の弱学習器を生成するので、適応的と名付けられている（<ins>Ada</ins>ptive Boosting）。前回モデルで、不正解（誤差の大きかった）データに対する重みを大きくし、次のモデルを学習させる。

【注】
AdaBoostはアンサンブル学習の一つ。但し、アンサンブル学習の他のアプローチ（ランダムフォレスト、バギング、スタッキング）とは独立した『ブースティング』に分類される。ブースティングにはもう一つ『勾配（Gradient）ブースティング』がある。

# 仕組み

① 最初のモデルの重みを $\displaystyle w^{1}_i=\frac{1}{N}$ に設定（ $N$ : 標本数）

② $m=1,...,M$ （モデル数）で、以下を繰り返す

②-1 モデル $m$ の誤差と信頼度の算出

誤差：

$E_m=\frac{\displaystyle\sum_i^N w_i^m I(y_m(x_i)\ne{t_i})}{\displaystyle\sum_i^N w_i^m}$

$I$ : 予測が正解の場合 0、不正解の場合 1 を戻す（0か1を返す関数）。

データ $i$ が不正解の場合、 $I\to 1$ が加重加算されるので、 $E$ は大きくなる。

$E$ が最小になるような 分岐 $y_m$ を決定する。

⇒ $E_m$ が定まる。

信頼度：

$\displaystyle \alpha_m=\log(\frac{1-E_m}{E_m})$

※ $\frac{1}{E_m}-1$ : $0\lt E_m\lt 1$

※ $E_m= 0$ の時 $\alpha_m=\infty$ とする。

<img src="./img/AdaBoostモデル信頼度α.png" width="50%">

②-2 重み更新

$w^{m+1}_i=w^m_i\exp{\alpha_m I(y_m(x_i)\ne{t_i})}$

正解の $i$ では $\exp{(\alpha_m\times{0})}=1$ となり更新されない。不正解の $i$ に対してのみ更新される。

次のモデル( $m+1$ )に関して ②-1 から繰り返す。

④ 完成するモデル

$y(x)=\displaystyle sgn(\sum^M_{m=1}\alpha_my_m(x))$

※ $\to 0$ or $1$

各弱学習器に、$\times{貢献度 \alpha}$ されている。すなわち、最終予測値は重み付き多数決によって決定される。

# 多クラス分類の場合

<ins>AdaBoostは２クラス分類に対する手法である。</ins> 多クラス分類に応用する場合、クラス数-1の数のモデルを用意するなどの工夫が必要となる。

例えば、A,B,Cの３クラス分類問題に適用するには、Aとそれ以外、Bとそれ以外、の２つの学習モデルを準備する。

# 参考

- [Adaboostの仕組みを解説＋重みの可視化をしてみよう！ -
 K_DM【機械学習 x Python】](https://youtu.be/1K-h4YzrnsY?list=PLq7HV4kcWdgOuNZ2zgS6tTz3eRAafyVlK)
- [【機械学習-理論】バカでもわかるAdaBoost(アダブースト)の考え方 - 
へちやぼらけ・データサイエンティスト](https://youtu.be/_oG7ZAAKx-c)
- [[機械学習]Adaboostの理論をまとめてみた](https://qiita.com/renesisu727/items/b2162ddef0759f16b09e)
- [統計的学習の基礎10章：ブースティグとは〈AdaBoost～GradientBoosting（勾配ブースティング）](https://qiita.com/Mark-N/items/1f0dd4c8b9473610eaa7)

# 未読

[多クラスAdaBoostを用いた3次元腹部CT像における腹部血管領域への血管名自動命名手法に関する研究：血管名識別器における検討](https://nagoya.repo.nii.ac.jp/record/21554/files/110009481674.pdf)
