# 基本事項
## 正規分布

## 基礎知識

実験の測定値（$$x_1,x_2,...,x_n$$）は、真の値$X$の周りにふらつきを持って得られる。
究極的な目標は実験の精度を極限にまで高めて、真の値$X$を知ることである。

\subsubsection{平均 $\bar{x}$}
$n$点測定した結果を評価する時によく用いられるのが平均（算術平均or相加平均）である。

\begin{equation}
  \bar{x} = \frac{x_1 + x_2 + ... + x_n}{n}  = \frac{1}{n} \sum_{i=1}^{n} x_i
\end{equation}


\subsubsection{分散 $V$}
測定値がどれくらいばらついている（分散している）かの指標。平均値の周りにピッタリ分布していれば、
分散は小さくなり、平均値から大きかったり小さかったりすると、分散は大きくなる。

\begin{equation}
  V= \frac{1}{n}\sum_{i=1}^{n} (x_{i}-\bar{x})^{2} = \int (x-\bar{x})^2f(x)dx
\end{equation}

\subsubsection{偏差 $\sigma$}
分散の平方根を取ったもの
\begin{equation}
  \sigma = \sqrt{V}
\end{equation}

\subsubsection{期待値}
ある確率変数$X$に対する期待値は、$E[X]$と表される。 確率によって重み付けして平均を計算したもので、

\begin{equation}
  E[x] = \frac{p_1\times x_1+ p_2\times x_2+...+ p_n \times x_n}{n} = \frac{1}{n}\sum_{i=1}^{n} p_ix_i
\end{equation}

重要な性質として、実験結果$x=(x_1,x_2,...,x_n)$の期待値は、

\begin{equation}
  E[x] = \lim_{n\to\infty} = \frac{1}{n}\sum_{i=1}^{n} p_ix_i = \frac{1}{n}\sum_{i=1}^{n} p_ix_i
\end{equation}



\subsubsection{母集団と標本}
ある母集団から確率変数$X$を予想する場合。無限個のサンプル取得が可能であれば、 $X$の平均値（=期待値)は

\begin{equation}
  \mu = \bar{X} = \lim_{n\to\infty} \left(\frac{1}{n} \sum_{i=1}^{n} x_i \right)
\end{equation}

母平均の期待値 $E[\mu]$は、
\begin{equation}
  E[\mu] = \lim_{n\to\infty}\sum_{i=1}^{n}
\end{equation}

で表される。母集団から無限個のサンプルを取得すれば、真の値（母平均）を計算することができることを意味する。
また、母集団の分散（母分散）は

\begin{equation}
  V= \frac{1}{n}\sum_{i=1}^{n} (x_{i}-\mu)^{2}
\end{equation}

で表される。

実際には$n$の値は有限であり、母平均$\mu$や母分散$V$を計算することはできない。
ここで注意が必要である。
\subsubsection{標本分散}
\begin{equation}
  E((X-\bar{X})^2) = \sum_{i=1}^{n} (X_i - \bar{X})^2 = \sum_{i=1}^{n} \left(X_i - \frac{1}{n}\sum_{j=1}^{n} X_j \right)^2
  =
\end{equation}

% ====================================
## 確率分布}
\subsubsection{ポワソン分布}
\label{subsubsec:poisson}
平均 $\lambda$ 回発生する確率事象が、$x$ 回起こる確率

\begin{table}[h]
  \centering
  \begin{tabular}{lll}
    確率密度関数 & $f(x)=\frac{e^{\lambda}~\lambda^{x}}{x!}$   \\
    期待値      & $E(x)=\lambda$    \\
    分散        & $V(x)=\lambda$
  \end{tabular}
\end{table}

事象が起こる平均値$\lambda$が大きくなるほど、形がガウス分布に近づいていく。
十分に大きくなると$\mu=\lambda$、$V=\lambda$のガウス分布として近似できる。

\begin{figure}[h]
  \centering
  \includegraphics[scale=0.5]{python/poisson_scan.pdf}
  \caption{異なる平均値を取ったときのポワソン分布。平均$\lambda$が大きくなるほど、ガウス分布のような形状になっていくのが分かる。}
\end{figure}

\subsubsection{正規分布（ガウス分布）}

\begin{table}[h]
  \centering
  \begin{tabular}{lll}
    確率密度関数 & $f(x)=\frac{1}{\sqrt{2\pi} \sigma}e^{-\left(\frac{(x-\mu)^2}{2\sigma^2}\right)}$   \\
    期待値      & $E(x)=\mu$    \\
    分散        & $V(x)=\sigma$
  \end{tabular}
\end{table}

\begin{itembox}[l]{ガウス分布の性質その1}
  確率変数$X$が$N(\mu,\sigma^2)$の正規分布に従うなら、$aX+b$は$N(a\mu+b,a^2\sigma^2)$の正規分布に従う
\end{itembox}




## 誤差論}
\subsubsection{誤差の伝播}
N点の計測（$x_1, x_2, ..., x_n$）を行う。測定値それぞれに誤差がついている場合（$x_1\pm\Delta x_1, x_2\pm\Delta x_2, ..., x_n\pm\Delta x_n$）、測定結果の合計、平均にはどのような誤差が付くか。

\subsubsection{合計の誤差}

\begin{equation}
  y=\Sigma_i~x_i=x_1+x_2+...+x_n=n\times\frac{1}{n}(x_1+x_2+...+x_n)=n\bar{x}
\end{equation}

誤差の和はｙに対して、

\begin{equation}
  \Delta y = \sqrt{\left(\frac{\partial}{\partial x_1}y \right)^2 \Delta x_1^2 + ... + } = \sqrt{\Sigma_{i=1}\left(\frac{dy}{dx_i}\right)^2\Delta x_i^2}
\end{equation}

として伝搬する(誤差伝搬の公式).
今の場合、
\begin{equation}
  \frac{\partial}{\partial x_1}n\times \frac{1}{n}(x_1+x_2+...+x_n)=1
\end{equation}

となるので、

\begin{equation}
  \Delta y=\sqrt(\Sigma(\Delta x_i)^2)
\end{equation}

測定値$x_{i}$の分散は、測定したn点から事前に計算される。
なので誤差の伝播の式を進めると、
\begin{equation}
  \Delta y=\sqrt{ns^2}=\sqrt{n}s
\end{equation}
となる。

\subsubsection{平均の誤差}
測定値の平均値には、
\begin{equation}
  \bar{x}=\frac{1}{n}\Sigma x_i
\end{equation}

誤差伝搬の式を適用して、
\begin{equation}
  \Delta \bar{x} = \sqrt{n\times\left(\frac{1}{n}\right)^2s^2}=\frac{1}{\sqrt{n}}
\end{equation}

この式は、平均値の誤差は測定点の数のルートN倍で小さくなっていくことを示している。測定を繰り返し行い、平均を得た場合にどのように誤差が小さくなっていくかを示している。

- 計数の誤差
- 計数$N$の統計誤差は$\sqrt{N}$で表される

\subsubsection{ヒストグラムにおける誤差}
ここまでの議論は、例えば粒子の不変質量を測定した場合に、あるイベントでは$m_1$[GeV]、あるイベントでは$m_2$[GeV]、...と測定した時に、その測定量に対してどれくらい誤差が付いているかを論じてきた。
議論をもう一度繰り返すと、$n$回測定した質量の平均値は、

\begin{equation}
  \bar{m}=\frac{1}{n}\Sigma m_i
\end{equation}

測定結果の分散は、

\begin{equation}
  V=\Sigma(m_i-\bar{\mu})・・・(☆)
\end{equation}

で表される。しかし、これらの議論はヒストグラムの場合には少し特殊な議論となる。よく不変質量の分布をヒストグラムにしたりして議論を進めていくが、この時によく「ヒストグラムにエラーバーを付けて」と言われるが、このエラーバーはここまでの誤差とは若干違っている。(☆)の誤差は不変質量の測定値に付くものであって、ヒストグラムのそれぞれのビンにつくものではない。

\subsection{ビンにつく誤差}
「ヒストグラムのエラー」は、そのビンにいる統計数に対して考える。よくみるヒッグス粒子の不変質量を例に取ってみよう。（☆）の議論はヒッグス質量125GeVに対して$125GeV \pm \sigma_{H}$ という形で付くものである。これは強いて言うなら下図の横方向(x軸方向)に対しての誤差である、

![](https://cds.cern.ch/record/2684923/files/LP2019_Higgs_figure1b.png?subformat=icon-640)

では、図に示されている縦方向の誤差は一体なんでしょうか？これこそが高エネ実験領域でよく耳にする「統計誤差」というものである。

\subsubsection{考え方}
例えば1番目のビンに注目する。このビンでカウントされている事象数を仮に460事象と読み取ることにする。
これを「とある確率分布に従う事象を観測し、平均値460事象観測した」と捉える。よく用いられる確率分布はポワソン分布である(\ref{subsubsec:poisson}節)。
簡単に分散$V=460$、$\sigma=\sqrt{460}$と求めることができる。これがヒストグラムの計量の際の誤差である。感覚的には、縦方向に（各ビンに）ある確率分布があって、それらの平均値をつなぐようにしてヒッグス質量分布が計算されているとすればいい。

\subsubsection{誤差はどうなっていくか}
統計量が溜まってくると、1ビン〜10000事象とかがあるかもしれない。こういうときにポワソン分布でヒストグラムのエラーバーを考えていいのか？という疑問が湧いてくる。答えは**ガウス分布**を使う、が、「考え方」は変わらないということである。

- 二項分布→ポワソン分布
- 二項分布において$\lambda$を一定にして、$n$を大きく、$p$を小さくするとポワソン分布になる
- ポワソン分布→ガウス分布
- ポワソン分布で$\lambda$を大きくすると、期待値$\lambda$、分散$\lambda$のガウス分布になる
- 二項分布→ガウス分布
- 期待値$np$、分散$np(1-p)$の両方が大きい場合、期待値$np$、$分散np(1-p)$のガウス分布になる

上記の関係性を思い出せば、1ビンあたりの統計量（＝１ビンで観測したイベントの期待数）が大きくなっても、結局は分散$\lambda$のガウス分布に従っているので、ヒストグラムのエラーバーはやはり$\sqrt{N}$になる。

つまりヒストグラムのエラーバーは、

$N\pm\sqrt{N}$

の関係で成り立っている（ポワソン分布orガウス分布に由来するものであることに留意）。


\subsection{「誤差は$\frac{1}{\sqrt{N}}$で小さくなっていく」の真実}
誤差の大きさそのものが$\frac{1}{\sqrt{N}}$なのではなく、ここで言っている誤差は「XX\%」の誤差に相当するものである。ヒストグラムの誤差は、

\begin{equation}
  N\pm\sqrt{N}
\end{equation}

で付くものだったから、1ビンに対する誤差は

\begin{equation}
  \frac{\sqrt{N}}{N}\times 100 = \frac{1}{\sqrt{N}} \%
\end{equation}

である。つまり、1ビンに入る統計数が多くなればなるほど、統計量が増えれば増えるほど、誤差は、$\frac{1}{\sqrt{N}}$で小さくなっていきます。
なので、できる限り統計量を貯める、という至極まっとうな感想が生まれてきます。

ちなみに、例えばあるビンの統計数が1事象だった場合の誤差は、

\begin{equation}
  1\pm 1
\end{equation}

で、「なんだ、誤差の大きさは1じゃん、小さいじゃん」と思うかもしれないが、

\begin{equation}
  \frac{\sqrt{1}}{1}\times 100 = 100 \%
\end{equation}

の誤差が付いているという事実を忘れてはならない。ちなみに100事象貯めれば、

\begin{equation}
  \frac{\sqrt{100}}{100}\times 100 = 10 \%
\end{equation}

10\%の誤差にまで削減することができるのである。



# Pythonと学ぶ統計}
## 最小二乗法 (least square)}
python/chi\_square.py
$N$組のデータ$(x_i,y_i)$を測定した($i=1,...,N$)。これらを尤もらしく表すことができる関数$y=f(x)$を求めたい。
想定する状況は、実験者が$x_i$を固定して、$y_i$を測定していく、というもの。
各$y_i$はとある平均値の周りにふらつきを持って測定される。以下では簡単に線形近似の場合を考える。
\begin{equation}
  y = ax + b
\end{equation}
の係数を実験データから求めたい。そこで次のような値を考える。

\begin{equation}
  \Phi(a,b) = \sum_{i=1}^{N} w_i r_i^{2} = \sum_{i=1}^{n} w_i[f(x_i)-y_i]^2
\end{equation}

$r_i$は残差（residual）と呼ばれる値であり、データ点とモデル曲線との差を表している。
$w_i$は各データ点に対する重みであり、分散の逆数に比例した値を持つ。
仮に$w_i$が$1/\sigma_i^2$に全く等しい場合、$\Phi$は$\chi^2$に等しくなるため、最小二乗フィットはカイ自乗フィットとも呼ばれる。


誤差を含むような実験データ値から、もっともらしい関数の形を決定する時に用いられる手法。
$n$個のデータ点$(x_1,y_1), (x_2,y_2), ... (x_n, y_n)$をフィットする際に（関数の形は経験的に決定する）指標として用いる。

## カイ自乗検定}

\begin{equation}
  \chi^2 = \frac{(x_1-\mu_1)}{\sigma_1^2} + \frac{(x_2-\mu_2)}{\sigma_2^2} + ... + \frac{(x_n-\mu_n)}{\sigma_n^2} = \sum_{i=1}^{n} \frac{(x_i-\mu_i)}{\sigma_i^2}
\end{equation}

カイ自乗の確率関数

\begin{figure}[h]
  \centering
  \includegraphics[scale=0.5]{python/ChiSquareDistribution.pdf}
  \caption{$\chi^2$の確率分布。$chi^2$が大きくなるに従って、関数の形が右へシフトしていく。}
\end{figure}


\subsection{どうやってフィットの妥当性を評価するか？}
異なる実験で$Z$ボソンの質量が測定された。これらの実験結果を尤もらしく一つの数値で表現することはできるだろうか？

\begin{table}
  \centering
  \begin{tabular}{lll}
    L3        & $91.161 \pm 0.013$   \\
    OPAL      & $91.174 \pm 0.011$    \\
    Aleph       & $91.186 \pm 0.013$ \\
    Delphi      & $91.188 \pm 0.013$
  \end{tabular}
\end{table}

# 検定}
真の値が$X$である量を$N$回測定して、$N$点のデータが得られたとする。
そこから真の値を推定するにはどうすればよいか。

# HEP統計}
素粒子実験では目当ての事象をカウントして、そのカウント数$s$で理論モデルの検証を行っていく。
その際には背景事象もあるカウント数$b$だけ含まれてしまうことから、たとえ信号事象を観測できたとしてもノイズに埋もれてしまったら発見にはつながらない。
そこで、最終的には$b$に対して$s$が優位に大きいかどうかを議論する必要があるのだが、この手法にはいくつかの種類があり

\begin{itemize}
  \item カウンティング
  \item シェイプフィット
\end{itemize}

が主な手法である。大層な名前がついているが特に難しいわけではないのでじっくり考えれば理解できるはず。
信号の発見を行うには、$s=0$の仮説の$p-value$を計算することが一般的である。

これは、目的の新物理は世の中に存在しない場合（$s=0$）に、実験で得られたイベント数がどれくらい普通に起きるかの目安となる。

## p-value}

\begin{equation}
  p = \int_{\alpha}^{\infty} f(x)dx
\end{equation}

例えばガウス分布であれば、p値が小さければ小さいほど起こり得ない事象であると理解できる。
高エネ業界では専ら、p値を標準化された正規分布におけるsignificance $Z$ に焼き直して議論する。
\begin{equation}
  Z = \Phi^{-1}(1-p)
\end{equation}
$p=0.5$のときに$Z=0$、$p=0.05$のときに$Z=1.64$、$p=2.9\times 10^{-7}$の時$Z=5$となる。
つまり、標準化された正規分布の平均値から何$\sigma$離れた場所に位置しているかの指標となる。

## $S/\sqrt{B}$の導出}
背景事象$B$に対して信号事象$S$がどれだけ優位に多いかを表す指標であり、発見感度の議論の仕方としては最も基本的なものの一つである。
ポワソン分布の平均値$\lambda$が大きいときにガウス分布で近似できる性質を使う。
素粒子実験においてポワソン分布の平均値とは、「実験で観測できるとされる事象数 $s+b$」を意味する。
ゆえに十分な統計を溜めることのできる実験では以下の近似式を用いることができる。

\begin{equation}
  f(x)
  = \frac{1}{\sqrt{2\pi}\sigma} e^{\frac{(x-\mu)^2}{2\sigma^2}}
  = \frac{1}{\sqrt{2\pi(s+b)}} e^{\frac{{x-(s+b)}^2}{2(s+b)^2}}
\end{equation}

ここでポワソン分布は、 $\mu = s+b$、$\sigma = \sqrt{s+b}$
のパラメータを持つガウス分布で記述されている。

この近似式を用いた場合に、信号事象がゼロの仮説（background only hypothesis）に対するp値は次のように計算できる（$s=0$）。

\begin{equation}
  p = 1 - \Phi \left(\frac{x-\mu}{\sigma} \right) = 1 - \Phi \left(\frac{x-b}{\sqrt{b}} \right)
\end{equation}

ここから、予想されるsignificance を求めることができて、
\begin{equation}
  \Phi \left(\frac{x-b}{\sqrt{b}} \right) = 1-p \\
\end{equation}

\begin{equation}\label{eq:signigicance_Z}
  \frac{x-b}{\sqrt{b}} = \Phi^{-1} (1-p) = Z
\end{equation}

（\ref{eq:signigicance_Z}）式より、$x=s+b$の場合に予想されるsiginificanceは、

\begin{equation}
  \mathrm{med}[Z|s] = \frac{s}{\sqrt{b}}
\end{equation}

この式は信号事象の優位性を議論する時に広く用いられているものである。

\begin{figure}[h]
  \centering
  \includegraphics[scale=0.8]{python/discovery_significance.pdf}
  \caption{予想されるsiginificanceの分布。赤線は$Z=s/\sqrt{b}$、青線は$Z=\sqrt{2\left((s+b)\log\left({1+\frac{s}{b}}\right)-s)}$から見積もった曲線。Asimov siginificanceの方が背景事象が少なくなってくる領域でも正しくexpected limitを見積もることが可能である。基本的には$s/\sqrt{b}$はそのような領域ではoverestimationになっているだけで、$s/\sqrt{b}$同士で比較する分には多少の意味はある。}
\end{figure}


## Statistical test}

\begin{equation}
  \lambda(s) = \frac{L(s,\hat{\hat{\theta}}(s))}{L(\hat{s},\hat{\theta})}
\end{equation}


## Asymptotic formulae}
\subsection{導入}
ある確率変数$x$を測定して$N$ビンのヒストグラムを作成した（$n_1,n_2,...,n_N$）。
$i$番目のビン内のイベント数の期待値は次のように表される。
\begin{equation}
E[n_i] = \mu s_i + b_i
\end{equation}
ここで$s_i$と$b_i$は$i$番目のビンにおける信号数と背景事象数の平均値である。
\begin{eqnarray}
 s_i = s_{tot}\int_{\mathrm{bin}~i}f_s(x;\theta_s)dx \\
 b_i = b_{tot}\int_{\mathrm{bin}~i}f_b(x;\theta_b)dx
\end{eqnarray}
$f(x;\theta)$は各モデルの確率密度関数を表しており、積分することで注目するビンに事象が得られる確率を計算することができる。また、$\mu$は信号強度であり、$\mu=0$の時にはbacground only hypothesis、$\mu=1$のときには信号を含んだ仮説を表現することができる。
$\theta$は確率密度関数の形状を決めるパラメーターで、$(\theta_s,\theta_b,b_{tot})$をまとめてnuisance parameter として扱う。

\subsection{likelihood}
作成したヒストグラムに対する尤度関数は、とあるビンに事象が観測される確率（ポワソン分布）の積で表すことができる。
\begin{equation}
    L(\mu, \theta) = \Pi_{\j=1}^{N} \frac{(\mu s_j + b_j)^{n_j}}{n_j!}e^{-(\mu s_j + b_j)}
\end{equation}
さらに、control regionを定義した解析では、CRにおける尤度関数も式に含めることができる。

\subsection{Profile likelihood ratio}
信号強度$\mu$を試験するために、profile likelihood ratio $\lambda(\mu)$を用いる。
\begin{equation}
  \lambda(\mu) = \frac{L(\mu,\hat{\hat{\theta}})}{L(\hat{\mu},\hat{\theta})}
\end{equation}
分母はLikelihoodの最大値、分子は$\mu$をとある値に固定した時にLikelihoodが最大となるように求めた$\theta$を用いたときの値。
尤度関数を最大にするパラメータの組み合わせは$(\hat{\mu},\hat{\theta})$であるため、常に分子は分母より小さいか分母に等しくなるので、$0<\lambda<1$が成り立つ。
$\lambda=1$はデータと$\mu$がよく一致することを表していて、0に近づくほど実験データと乖離している（$\mu$を仮定した理論では実験データを説明できない、棄却される対象となる）ことが表される。

\subsection{test statistic $t_\mu=-2\ln\lambda$}
statistical testを行う際には、$\lambda$をさらに次の様に変換して用いることが多い。
\begin{equation}
  t_\mu=-2\ln\lambda(\mu) = -2 \left(\ln L(\mu,\hat{\hat{\theta}}) -  L(\hat{\mu},\hat{\theta} ) \right)
\end{equation}
先程の$\lambda$の範囲の議論より、$t_\mu$は$-2<t_\mu<0$の範囲を動く。
よって0に近いほど（値が大きくなるほど）、データと$\mu$の整合性が取れないことを表している。
\begin{equation}
p_\mu = \int_{t_{\mu,obs}} ^{\infty} f(t_\mu|\mu) dt_\mu
\end{equation}
$t_{\mu,obs}$は実験データから見積もった値、$f(t_\mu|\mu)$は$t_\mu$が得られる確率密度関数を表している。

\subsection{Test statistics $t_\mu$ for $\mu > 0$}
一般的に信号モデルは、既存のモデルに対してさらに数イベント信号が観測できると予測する。
そのため信号強度は正の値をとる。その場合を試験量も記述しておく。$\mu>0$の領域では今まで通りのlikelihood ratioを用いて、0以下の領域では$\mu$の値を0に固定したlikelihood ratioを定義しておく。

\subsection{Test statistics $q_\mu,q_0$}
高エネ実験では新物理$\mu=1$を探している。
実際の統計処理では$\mu=0$のbackground only hypothesisを棄却する方向で計算を進めていく\footnote{ここが少し混乱の元。示したいのは信号を含んだモデルが存在することであるが、統計処理では「信号を含まないモデル$H_0$では実験データを説明できない$\to$新しいモデルが必要となる」というロジックで進んでいく。}。
よって方針は、$\mu=0$のtest statisticsを正しく評価していくこととなる。
（で、問題は）ここから定義した$t_\mu$をさらにいろいろ条件を変えたときの式として、$q_\mu$に置き換えて議論していくので、本書もそれに倣う\footnote{
式の形は$t_\mu$の議論の時に示したとおりだが、$q_\mu$と明記したときには「$\mu$の値に関して条件を掛けて立式していきますよ」という意思表示だと思ってもらえればいい。}。

\begin{euation}
  q_0 = -2\ln\lambda(0) : \hat{\mu} > 0
\end{equation}
\begin{euation}
  q_0 = 0 : \hat{\mu} < 0
\end{equation}

\begin{euation}
  q_\mu = -2\ln\lambda(\mu) : \hat{\mu} < \mu
\end{equation}
\begin{euation}
  q_\mu = 0 : \hat{\mu} > \mu
\end{equation}

## Profile likelihood ratio の近似式}
信号強度$\mu$を試験する場合を考え、データ点は$\mu'$に従って分布しているとする。
\begin{equation}
-2\ln\lambda(\mu) = \frac{(\mu-\hat{\mu})^2}{\sigma^2} + O(1/\sqrt{N})
\end{equation}
ここで、$\hat{\mu}$はmean $\mu'$、標準偏差$\sigma$のガウス分布に従う。$N$はサンプル数を表す。
\sigmaは共分散から簡単に求めることができて、
\begin{equation}
  V_{ij} = \mathrm{cov}[\hat{\theta_i}, \hat{\theta_j}]
\end{equation}

## カウンティング（1ビンフィット）}
ポワソン分布に従う事象を$n$事象観測して、1ビンのヒストグラムで評価する場合を考える。
SRにおける期待値は
\begin{equation}
E[n] = \mu s + b
\end{equation}
$s$は信号モデルから予想される信号事象数の平均値、$b$は背景事象数の期待値、$\mu$は信号強度を表す。
$b$はnuisance parameter \footnote{nuisanceとは迷惑なこと、厄介なこと、の意味を持つ単語。高エネの人が真に興味があるのは信号数なので、まぁ背景事象数は邪魔だということか。}であり、CRにおける背景事象数の分布から制限をかけることができる。
CRにおける背景事象の期待値は、SRとCRにおける背景数の違いを表す scale factor を$\tau$で表すと、
\begin{equation}
E[m] = \tau b
\end{equation}
と記述することができる。
実際の解析ではこの$\tau$もnuisance parameterとしてフィットから求める手順を踏むが、
ここでは簡単のために既知の値として話を進める。

実験から得られる値はSRの事象数$n$、CRにおける自少数$m$、興味のあるパラメータ（parameter of intereset; POI）$\mu$、そしてnuisance parameter $b$である。
ポワソン分布に従うような場合に、$\mu$と$b$に対して実験結果から次のような尤度関数を定義することができる。


## シェイプフィット}
1ビンではなく、分布の形を反映した統計処理を行いたい場合、こちらの手法を用いる。
俗語的に
\begin{itemize}
  \item シェイプフィット
  \item シェイプでフィットした
\end{itemize}
とか呼ばれる。

## CLs法}
以下で定義する$CL_s$と呼ばれる量をtest statisticとして用いて解析感度を評価する手法。

\begin{equation}
CL_s = \frac{CL_{s+b}}{CL_b}
\end{equation}

$CL_{x}$はたどっていくと$\mu$に依存する。
よく用いられるのは95$\%$CLsであり、$CL_s=0.05$となる$\mu$の値を探してそれを$\mu_{up}$として
解釈し、最終的に断面積の上限値設定に使用する手法である。

# RooFitで学ぶ統計処理}
https://twiki.cern.ch/twiki/bin/view/Main/LearningRoostats
## ジャーゴン}
\begin{itemize}
  \item フロートにする：定数として扱わないこと。MLEの時に、何を変数として扱って、何を定数として固定するかに関する話題でよく出る。setConstant(0);
\end{itemize}
## 関数}



# HistFactory}
RooFitやRooStatで処理を行っていくためには、RooWorkspaceを作成する必要がある。
簡単なチュートリアルレベルであればRooWorkspaceの作成は簡単な作業であるが、実際の解析ではかなり骨の折れる作業である。
そこでHistFactoryと呼ばれるパッケージがROOTでは提供されていて、これを用いることでユーザーは自分のヒストグラムから簡単にRooWorkspace(＝確率密度関数)を計算して保存することができる。

## 使い方}
ROOTにはhist2workspaceというコマンドが用意されていて\footnote{ローカルでROOTを触っている人はインストールしていないかもしれない。ROOTを自分の環境でビルドしたときのことを思い出しましょう。}、これに「どのヒストグラムをどういう設定で使用するか」を記したXMLファイルを食わせることでRooWorkspaceがアウトプットされる。

## marked Poisson model}
marked poisson modelと呼ばれる確率密度関数をヒストグラムの情報から計算する。
ヒストグラムのビンの情報はシグナル数$S$と背景事象数$B$との間に次の関係を定義する。
$\nu_{b}^{sig}$は着目する$b$番目のビンに含まれるイベント数で、次の等式が成り立つ（単にビンを端から端まで足し合わせたら全イベント数になるということを言っている）。
\begin{equation}
  S = \sum_{b} \nu_{b}^{sig}
\end{equation}
\begin{equation}
  B = \sum_{b} \nu_{b}^{bkg}
\end{equation}

シグナルと背景事象の"shape"は$f_S(x_e)$、$f_B(x_e)$で表現する。
ヒストグラムをhist->Scale(1/hist->Integral())することと等しく、そのイベントがどのような確率で出現するかを表すことができる。
\begin{equation}
  f_S(x_e) = \frac{\nu_b_{e}^{sig}}{S\Delta_{b_e}}
\end{equation}

\begin{equation}
  f_B(x_e) = \frac{\nu_b_{e}^{bkg}}{S\Delta_{b_e}}
\end{equation}
以上の定義した式を用いて次のmarked poisson modelを計算する。
\begin{equation}
  P({x_1,..,x_n}|\mu) = \mathrm{Pois}(n|\mu S+B) \left[ \prod_{e=1}^{n}\frac{\mu Sf_S(x_e)+Bf_B(x_e)}{\mu S+B} \right]
\end{equation}
この式は、イベント数やその他のパラメータが固定（観測からわかっていれば）であれば、$\mu$にのみ依存し、これはまさしくLikelihoodを表している。

## HistFactoryのレンプレート}
はじめに使用する添字について簡単な説明を行う。
\begin{itemize}
  \item e：イベント
  \item b：ビン
  \item c：チャンネル
  \item s：サンプル
  \item p：パラメーター
\end{itemize}

さらに、
\begin{itemize}
  \item ${\phi_p}$：パラメーター毎の規格化定数（NormFactor）
  \item ${\alpha_p}$：系統誤差に関連するパラメーター、それ自身は事前にCR等で見積もっておくもの（OverallSys, HistoSys）
  \item ${\gamma_{csb}}$：ビンごとの系統誤差（ShapeSys、）
\end{itemize}
を定義する。 実際にHistFactoryが計算する数式は次のものである。
\begin{equation}
  P(n_c,x_e,a_p|\phi_p,\alpha_p,\gamma_b) = \prod_{c}\left[\mathrm{Pois}(n_c|\nu_c) \prod_{e=1}^{n_c}f_c(x_e|\alpha) \right]
  \times G(L_0|\lambda,\Delta_L)
  \times \prod_{p} f_p(a_p|\alpha_p)
\end{equation}








\end{document}
