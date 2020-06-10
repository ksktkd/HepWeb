# 統計処理
最終的に解析で選別したものは、統計処理を行い素粒子物理学的に意味のある数字にする必要がある。

## リミットを引く

## HistFactory
RooFitやRooStatで処理を行っていくためには、RooWorkspaceを作成する必要がある。
簡単なチュートリアルレベルであればRooWorkspaceの作成は簡単な作業であるが、実際の解析ではかなり骨の折れる作業である。
そこでHistFactoryと呼ばれるパッケージがROOTでは提供されていて、これを用いることでユーザーは自分のヒストグラムから簡単にRooWorkspace(＝確率密度関数)を計算して保存することができる。

### 使い方
ROOTにはhist2workspaceというコマンドが用意されていて\footnote{ローカルでROOTを触っている人はインストールしていないかもしれない。ROOTを自分の環境でビルドしたときのことを思い出しましょう。}、これに「どのヒストグラムをどういう設定で使用するか」を記したXMLファイルを食わせることでRooWorkspaceがアウトプットされる。

#### maarked Poisson model
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

          #### HistFactoryのレンプレート
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



