# 標準理論

%
% ----- 表:物理定数 ------
\begin{table}[h]
 \caption{場の量子論の発展}
 \label{table:SpeedOfLight}
 \centering
  \begin{tabular}{cll}
   \hline
   西暦 & 発見者 & コメント \\
   \hline \hline
   1926 & Schrodinger & 非相対論的なシュレーディンガー方程式を導く\\
   & & Schrodinger方程式を相対論的に拡張したクラインゴルドン方程式が考案されるも、負のエネルギー・確率密度が出てくるので、発展せず。\\
   1928 & Dirac & ディラック方程式を基礎方程式とする特殊相対論的量子力学を創設。\\
   1930 & Pauli & ベータ崩壊に伴うエネルギー保存則の破れを解決するために、ニュートリノを提唱\\
   \hline
  \end{tabular}
\end{table}


1964 年
CP 対称性の破れはJ. H. Cristenson らによって初めて発見。
ストレンジ クォークを含む中性 K 中間子がストレンジクォークを含まない π 中間子へ崩壊する、CP 対 称性で禁止されている崩壊過程が存在することが確認された

物質優勢宇宙を説明するためには、標準理論が説明する既存のCP対称性の破れだけでは、不十分（小さすぎる）
既存のCP対称性の破れは、クォーク世代間の混合によるもの



https://www-he.scphys.kyoto-u.ac.jp/seminar/

# 言葉の定義

- スカラー：軸性ベクトル同士の内積、空間反転で符号を変えない
- 擬スカラー：軸性ベクトルと極性ベクトルの内積、空間反転で符号を変える
- 極性ベクトル（ベクトル）：空間反転で符号を変える
- 軸性ベクトル（擬ベクトル）：空間反転で符号を変えない
- パリティ保存：ある物理現象が、空間反転した物理現象と対等に起こる。パリティが保存しているということは、その現象を支配するハミルトニアンの中で、空間反転によって符号を変える項が禁止されることを意味する（符号を変えてしまっては対等に起こらなくなる）。
- ディラック方程式：１粒子が満たす相対論的波動方程式
- スピノル：ベクトルやテンソルの様に数学的な概念で、特に任意のスピンの状態を指す量（くらいに理解しとけば困らないはず）。


# ディラック方程式
シュレーディンガー方程式が考案された2年後に、さらにそれを相対論的な運動をする粒子を記述するために拡張された概念がディラック方程式である。

ディラック場 $\psi(x)$ は、ディラックスピノルと呼ばれたりする。
自由電子を記述するために導入したハミルトニアンは、

$$
H=\alpha \vec{p} + \beta m = -i \alpha \vec{\nabla} + \beta m
$$

と表される。この$\alpha$、$\beta$は$4\times4$のディラック行列 (ディラック行列の定義はいろいろパターンがある。どういう考察をしたいかで使い分ければよいのだが、特に高エネルギー領域（相対論的な領域、$E,\vec{p}\gg m$）ではカイラル表示を使うのが便利だそうだ。)と呼ばれる行列で（数学的に証明できる、ワイル粒子なら $2\times2$ 行列で良いらしい）、$4\times4$行列なのでそれゆえディラックスピノルも4成分を持つ。

$$
\psi =
\left(
    \begin{array}{c}
\psi_1\\
\psi_2\\
\psi_3\\
\psi_4\\
    \end{array}
  \right)
$$

ここで、上２成分を $\psi_L$（Left-handed spinor）、下２成分を $\psi_R$（Right-handed spinor）と呼ぶ。
左・右で分けることは、のちのち弱い力を議論するときに便利。

ディラックスピノルを左成分と右成分に射影（＝分解）することのできる演算子があれば便利と言えるだろう。
そこで、まずガンマ行列なるものを定義する。

$$
\gamma^0 = \beta, \gamma^i = \beta\alpha_i (i=1,2,3)
$$

ここでアルファ、ベータは、一番最初にディラック方程式のハミルトニアンを定義した際に用いたディラック行列である。
こう定義しておけば、（あとは計算するだけで）

$$
\frac{1}{2}\left( \vec{I} - \gamma^5 \right)\psi = \left(
    \begin{array}{c}
\psi_L\\
0
    \end{array}
  \right)
$$

$$
\frac{1}{2}\left( \vec{I} +\gamma^5 \right)\psi = \left(
    \begin{array}{c}
0\\
\psi_R\\
    \end{array}
  \right)
$$

が得られる。ここで、 $\gamma^5 = i\gamma^0\gamma^1\gamma^2\gamma^3$。
また、ガンマ行列を用いることで、冒頭で定義したディラック方程式をより綺麗な形式に書き下すことが出来る。

$$
\left( i\gamma^{\mu}\partial_{\mu} - m \right) \psi
$$

## まとめ
自由電子に対する波動方程式を相対論領域にまで拡張したのが、ディラック方程式である。ディラック方程式を満たす波動関数はディラック場、もしくはディラックスピノルと言って4成分ある。
このディラックスピノルを２成分ずつ分解したのがleft-handed spinor、right-handed spinorで弱い力を議論するときに登場する。また、より簡潔にディラック方程式と、その周りの性質を書き下すためにガンマ行列を導入している\footnote{と、大まかにこれくらいを押さえておけばディラック方程式に関する知識のまとめには十分じゃないだろうか。あとは、余力のある限り実際に計算して手を動かせばよい}。

http://www.th.phys.titech.ac.jp/~muto/lectures/INP02/INP02\_chap08.pdf

# 標準模型
現在確立されている標準模型では説明のつかない事象が多数見受けられ、新物理があることは確定している。

\begin{itemize}
\item 物質優勢宇宙：粒子、反粒子の数の差の説明がつけられない
\item 暗黒物質候補となる粒子がSM内には無い
\item フェルミオン（レプトン、クォーク）の電荷の構造の差
\item 質量ヒエラルキーがなぜ存在するか
\end{itemize}

\section{対称性}
SU(2)の2はダブレット、つまりアップ・ダウンの組み合わせを表現している（topとbottom, charmとstrange, upとdown）。

\section{疑問}
とりあえず箇条書き。
\begin{itemize}
\item なぜFlavour-Changing-Neutral-CurrentはSMにないのか？
\item なぜB中間子は長生き？
\begin{itemize}
\item bクォークが崩壊ということは、そのフレーバーを変えるのだが、まずSMではFCCN反応は禁止されているので同じダウン型（電荷の変わらない組み合わせである）$b \to s$に崩壊することは無い。ということは、bの崩壊先はトップクォークか、チャームクォークになる。トップクォークは173GeVであり、bクォークの4.18GeVより遥かに大きく崩壊先としては抑制される。また、$b\to c$も可能であるが抑制されるため、B中間子は比較的長生きになる（ATLAS実験ではsecondary vertexを生成することとなる）。
\item スカラー粒子とベクトル粒子のラグランジアン的な違いは？
\end{itemize}
\end{itemize}

\input{./Stat/Stat.tex}



\documentclass[a4paper,8pt]{jreport} % A4,11pt標準
%\usepackage{sty/soturon}
\usepackage{comment}
\usepackage{lineno}
\usepackage{amsmath}
%\pagewiselinenumbers

% コマンド類
\newcommand{\lumi}{$\times10^{34} \rm \ cm^{-2} s^{-1}$ }
\newcommand{\fb}{$\rm fb^{-1}$}
\newcommand{\pT}{$p_{\rm T}$}
\newcommand{\ET}{$E_{\rm T}$}
\newcommand{\MET}{$E_{\rm T}^{\rm miss}$}

\include{NewCommand/NewCommand}

%
\begin{document}

% 表紙
%\input{Title/Title.tex}
%x

% abstract
%\input{Abstract/Abstract.tex}
%

% 目次
\newpage
\pagenumbering{roman}
\setcounter{page}{1}
\setcounter{tocdepth}{1}
\tableofcontents
%


% 本文
\newpage
\pagestyle{headings}
\pagenumbering{arabic}
\setcounter{page}{1}
%
\include{src/spin}
\include{src/symmetry}
\include{src/gamma_interaction}
\include{src/quark}
%

\end{document}

\chapter{対称性とクォーク}
\section{対称性と群}
\begin{itemize}
\item ユニタリー演算子：$X^{\dagger}X=XX^{\dagger}=E$
\item ユニタリ行列：$U^{\dagger}U=UU^{\dagger}=E$
\item エルミート演算子：$X^{\dagger}=X$
\end{itemize}

数学上の定義で、"群"とは何かを定義されている。
\begin{itemize}
  \item n次元ユニタリ群（n次元のユニタリ行列の集合）：$U(n)$
  \item n次元特殊ユニタリ群（行列式が1であるn次元のユニタリ行列の集合）：$SU(n)$
  \item 直行特殊群（行列式が1であるようなn次元の直交行列）：$SO(n)$
\end{itemize}


\chapter{スピン}
スピン角運動量$s$、軌道角運動量$\ell$を合成すると、全角運動量$j=\ell+s$が定義できる。

\begin{table}[htb]
  \begin{center}
    \begin{tabular}{|c|c|} \hline
      $\ell=0$ & s状態（s軌道） \\ \hline
      $\ell=1$ & p状態（p軌道） \\ \hline
      $\ell=2$ & d状態（d軌道） \\ \hline
      $\ell=3$ & f状態（f軌道） \\ \hline
    \end{tabular}
  \end{center}
\end{table}

\section{シュテルン・ゲルラッハの実験}
銀原子($Z=47$)を不均一な磁場中に打ち込んで、古典論系と、量子論的な系の差を考える契機となった。
磁場中に銀原子を打ち込む時、考えられる相互作用は
\begin{itemize}
  \item ローレンツ力：$F=q \bf{v}\times \bf{B}$
  \item 磁気モーメントが磁場から作用：$V_{int}=-\bf{\mu}・\bf{B}$
\end{itemize}
ローレンツ力は入射方向に対して横向きに働き、実験結果のz方向への影響にはなりえない。
磁場がz方向のみとし、磁気モーメントの相互作用を微分すると、

\begin{align}
  V&=-\mu_{z}B_{z} \\
  dV&=-\mu_{z}\cfrac{dB_{z}}{dz}dz \\
  F&=\mu_{z}\cfrac{dB_{z}}{dz}
\end{align}

実験結果と比較して、磁気モーメントのz成分が正負の2つだけ取るとすれば説明できる。
その値を

\begin{equation}
  \mu_{z}=\pm \mu_{B}
\end{equation}

とする。$\mu_{B}$はボーア磁子と呼ばれ

\begin{equation}
  \mu_{B}=\cfrac{eh}{2m}=9.274\times10^{-24}\mathrm{[JT^{-1}]}
\end{equation}

ここでmは電子の質量である。電子が2成分のみの磁気モーメントを持つと考えれば実験結果を説明することが出来る。
この電子の磁気モーメントは電子に固有のもので、軌道角運動量に起因するものではない。
すなわち電子は固有のスピン角運動量を持っていて$s$、磁気モーメントはスピン角運動量に比例し、

\begin{equation}
  \bf{\mu}=g\bf{s}
\end{equation}
スピン角運動量は量子化されて、z成分は2つの値だけ取れる。
角運動量の大きさがJであるときは、そのz成分は$2L+1$個だけ考えることが出来る。










\chapter{クォーク}

クォーク模型
自然界の粒子は全て白色（カラー1重項）でしか存在できない事を要請する。
量子電磁力学は$\alpha$の値が小さく、摂動級数の収束が早い。
光子の放出・吸収の確率は$\sqrt{\alpha}$に比例し、vertex1個につき$\sqrt{\alpha}$が相当！

\eq{\alpha=\cfrac{e^{2}}{4\pi}}

なので、光子を放出・吸収する反応確率は

\eq{{(\sqrt{\alpha}\sqrt{\alpha})}^{2} = \alpha^{2}}
で記述できる。


\section{電磁相互作用}
仮想光子の放出・吸収で相互作用を記述できる。
仮想光子の運動量ベクトルは正負の値を取るので、引力・斥力を記述できる。
光子は電荷を持たないので、グルーオンの様に自己相互作用しない。

\section{}


\chapter{γ線と物質の相互作用}

\section{光電効果}
\section{コンプトン散乱}
\subsection{コンプトン波長}
$\lambda=\frac{h}{mc}$
\section{電子対生成}
\section{トムソン散乱}
