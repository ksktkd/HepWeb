# HistFactory
RooFitやRooStatで処理を行っていくためには、RooWorkspaceを作成する必要がある。
簡単なチュートリアルレベルであればRooWorkspaceの作成は簡単な作業であるが、実際の解析ではかなり骨の折れる作業である。
そこでHistFactoryと呼ばれるパッケージがROOTでは提供されていて、これを用いることでユーザーは自分のヒストグラムから簡単にRooWorkspaceを計算して保存することができる。
RooWorkspace を一旦作ってしまえば（後述するが）、likelihood等を計算してくれる。

# イントロダクション
HistFactoryはパラメトライズされた確率密度関数(pdf)を計算するためのツールで、RooFit/RooStatsフレームワークに基づいている。
計算されるpdfは（パラメトライズされているため）近似的なものであるが、テンプレートのヒストグラムに基づいており多くの解析で使用することができる柔軟性を持ったpdfとなっている。
計算されたPDFはRooWorkspaceの形式で保存される。

## Preriminalies
まず初めに簡単な例を考える。信号事象のチャンネル（ex. 解析でいうと1レプトンチャンネル、2レプトンチャンネルの様な括りのこと）が1つ、背景事象となる過程も一つの場合を考え、
さらにdiscriminating variableの$x$には系統誤差が含まれないとする（統計誤差のみ）。
ここで、信号数は$S$、背景事象数は$B$として表記し、観測量$x$の確率密度関数をそれぞれ $f_S(x)$、$f_B(x)$ と定義する（$f(x)$ は信号／背景事象モデルで予想される観測量の振る舞いを表している。シグナルの運動量分布等を思い浮かべれば良い）。

$$
\int f_S(x) dx = 1
$$

が成り立つ様に規格化しているとする。
実際の計算では$x$（例えば運動量とか角度分布とか）のヒストグラムを描画して、それを規格化すれば簡単にf_{S,B}(x)が計算できる。
ROOT語で喋るなら

```python
hist = TH1D(...)
hist.Scale(1/hist.Integral())
```

程度の事。この確率密度関数は信号／背景事象の分布を表しているものでもあるので、「シェイプ」とも呼ばれたりする。
さらに信号強度 $\mu$を定義する。

- $\mu=0$：背景事象onlyの仮説
- $\mu=1$：信号事象+背景事象（新物理を予言する仮説）の仮説

を表しており Parameter of interest （POI）と呼ばれる。

ここで$n$点のデータを持ち、${x_1, x_2, ..., x_n}$ のデータセットがデータから得られた場合を考える（$e$ 番目のデータは $x_e$ という表記をする）。
以上の仮定の元に、このデータセットが得られる確率を計算する。ここでは次の2つの確率を考慮する必要がある。

- $\mu S+B$ の事象数が予想される場合に、データから $n$ 事象得られる確率（=ポワソン分布）
- $f_S(x)$ と $f_B(x)$ の分布に基づいて、$x_e$ が得られる確率

以上2点を一つの式で表したものが "marked poisson model"と呼ばれる確率密度関数である：

$$
  P({x_1,..,x_n}|\mu) =
  \mathrm{Pois}(n|\mu S+B) \times
  \left[ \prod_{e=1}^{n}\frac{\mu Sf_S(x_e)+Bf_B(x_e)}{\mu S+B} \right]
$$

第一項は、予想される $\mu S+B$ 事象のうち $n$ 事象が得られたときのシンプルなポワソン分布である。
第二項は積をバラして考えてみると、

$$
\frac{\mu Sf_S(x_1)+Bf_B(x_1)}{\mu S+B}
$$

marked poisson modelの数式に戻る。
データは既に取得して変化はないとすると、この式は $\mu$ にのみ依存し、likelihood function $L(\mu)$ に等しい。
両辺対数を取ると、"extended maximum likilihood fit"として使用される式を導出することができる。

$$
-\ln L(\mu) = -n\ln(\mu S+B) + (\mu S+B) + \ln n! - \sum_{e=1}^{n}\ln \left[ \frac{\mu Sf_S(x_e)+Bf_B(x_e)}{\mu S+B} \right]
$$

$$
-\ln L(\mu) = (\mu S+B) + \ln n! - \sum_{e=1}^{n}\ln[\mu Sf_S(x_e)+Bf_B(x_e)]
$$

`HistFactory`はヒストグラムから計算を行うため、ビン分けされた確率モデルを構築することが最も自然な発想となる。
信号／背景事象のヒストグラムを $\nu_b^{\rm{sig}}$、 $\nu_b^{\rm{bkg}}$ と表記し、添字 $b$ はビンの番号、$\nu_b$はそのビンの事象数を表す。
シェイプ $f(x)$ をヒストグラムで表すと、

$$
f_S(x_e) = \frac{\nu_{b_{e}}^{sig}}{S\Delta_{b_e}},~~~  f_B(x_e) = \frac{\nu_{b_{e}}^{bkg}}{S\Delta_{b_e}}
$$

となる。$b_e$ は $x_e$を含んでいるビンの番号（インデックス）、$\Delta_{b_e}$ はそのビンの幅を表している。
全ビンの内容を足し合わせると、信号数、背景事象数と等しくなる。

$$
S = \sum_{b} \nu_{b}^{sig},~~~ B = \sum_{b} \nu_{b}^{bkg}
$$

$$
\mathcal{P}(n_b|\mu) = \rm{Pois}(n_{\rm{tot}}|\mu S+B)\left[ \prod_{b}\right]
$$

# The Likelihood Template
## Index Convention
使用する添字について：

- $e \in$ イベント
- $b \in$ ビン
- $c \in$ チャンネル
- $s \in$ サンプル
- $p \in$ パラメーター

 さらに、

- $\mathbb{N} = \{\phi_p\}$：unconstrainedの規格化定数（ie. `NormFactor`）
- $\mathbb{S} = \{\alpha_p\}$：constrainedの条件を持っている系統誤差に関連するパラメーター群（ie. OverallSys, HistoSys）
- $\mathbb{\Gamma} =\{\gamma_{csb}\}$：ビンごとの系統誤差（ie. ShapeSys）

## The Template

実際にHistFactoryが計算する数式は次のものである。

$$
P(n_c,x_e,a_p|\phi_p,\alpha_p,\gamma_b) = \prod_{c}\left[\mathrm{Pois}(n_c|\nu_c) \prod_{e=1}^{n_c}f_c(x_e|\alpha) \right]
\times G(L_0|\lambda,\Delta_L)
\times \prod_{p\in\mathbb{S+\Gamma}} f_p(a_p|\alpha_p)
$$
