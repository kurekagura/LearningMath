# 混同行列

<table>
<tr>
<td rowspan="2" colspan="2">調和平均（F値）で<br>注目したいのはTP↘</td>
<td colspan="2">予測値</td>
</tr>
<tr>
<td>Posi</td>
<td>Nega</td>
</tr>
<tr>
<td rowspan="2">正解値</td>
<td>Pos</td>
<td bgcolor="blue" style="color:white">TP</td>
<td>FN</td>
</tr>
<tr>
<td>Nega</td>
<td>FP</td>
<td bgcolor="blue" style="color:white">TN</td>
</tr>
</table>

<ins>※ 二文字目のP・Nは、予測値をさす。</ins>

**適合率（Precision）**

$\displaystyle=\frac{TP}{TP+FP}$ ・・・<ins>分母は **縦方向**。</ins>

**再現率（Recall）**

$\displaystyle=\frac{TP}{TP+FN}$ ・・・<ins>分母は **横方向**。</ins>

**F値（F-score）**

$\displaystyle=2\times\frac{Precision\times{Recall}}{Precision+Recall}$

$\displaystyle=\frac{1}{\displaystyle\frac{1}{Precision}+\frac{1}{Recall}}\times 2$

適合率と再現率はトレードオフの関係にあるので、この二つの指標の調和平均を算出し、F値という評価指標とする。

～　調和平均の解説　～

調和平均は **『比率率の平均』** である。分子／分母で構成された指標に対して、その分子を基準とする場合の平均と言える。

通常の平均の算出式と比べると逆のイメージで捉えるとよい（２で割るのではなく2を掛ける、逆数の足し算が分子ではなく分母に来ている、など）。<ins>F-Score は分子、この場合 TP に着目した指標と理解しておく。</ins>

例）時速は、距離/時間（km/h）の比率の指標である。この場合、調和和平均は距離を基準とした比率の平均となる。
