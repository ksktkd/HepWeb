# RooStats, RooFit
CERN ROOTに付随する、より高度な統計処理を行うためのRooStats, RooFitと呼ばれるパッケージについての説明です。
個人的にヒストグラムを手軽に描画するときにはPyROOTを使っていますが、RooStats系を使うときにはC++を使っています（型、名前空間、引数の渡し方を明示したいので）。
もちろんPyROOTのAPIもあります（が、いざfitする時には動作速度を担保したくなるので、C++の方が良いかと。）。

## RooWorkspaceの基本のキ
ガウス分布に従った乱数を振って、描画する方法です。
RooWorkspaceにはfactoryメソッドと呼ばれる、便利な関数が用意されているのでそれを使いましょう。

<img width="30%" src="fig/roostats/gauss.png">

```cpp
void gaussian()
{
    // RooWorkspaceの作成、名前を"ws"としている
    RooWorkspace ws("ws");

    // factoryメソッドを使って、一気に"MyGauss"という名前のガウス分布を定義している
    ws.factory("Gaussian::MyGauss(x[-10,10], mean[0], sigma[1])");
    
    // 乱数の生成
    RooDataSet* data = ws.pdf("MyGauss")->generate(*ws.var("x"), 1000);

    // ヒストグラムの作成
    // 乱数によるデータ点と、ガウス分布の理論線を描画しています
    RooPlot *frame   = ws.var("x")->frame();
    data             ->plotOn(frame);
    ws.pdf("MyGauss")->plotOn(frame);
    frame->Draw();
}
```

上に示しているように、`factory`メソッドで定義した変数は`ws.var("変数名")`で取ってくることができます。
変数の定義の部分の記法について、

```cpp
    ws.factory("Gaussian::MyGauss(x[-10,10], mean[0], sigma[1])");
    // x[-10, 10] : -10〜10までの範囲の変数。名前が「x」となる（勿論x1とかmy_xとかの名前でも大丈夫です）
    // mean[0]    : mean  = 0 の定数。名前が「mean」のRooRealVar。
    // sigma[1]   : sigma = 1 の定数。名前が「sigma」のRooRealVar。
```

ちなみにfactoryメソッドを使わなければ、以下のようにRooRealVarを変数分定義しなければならないのでより煩雑になる。

```cpp
void gaussian()
{
    RooRealVar  x("x","x",-10,10);
    RooRealVar  mean("mean","mean",0);
    RooRealVar  sigma("sigma","sigma",1);
    RooGaussian MyGauss("MyGauss","MyGauss",x,mean,sigma);

    RooDataSet* data = MyGauss.generate(x, 1000);
    RooPlot* frame = x.frame();
    data->plotOn(frame);
    frame->Draw();
}
```

## RooWorkspaceの使い方
単純なフィットであればROOTの範疇でやっていけるが、最尤法などを用いてパラメーター推定を本格的にやり始めるとRooStatsを使いたくなると思います。

```cpp
void workspace() 
{
    //construct the model
    RooWorkspace w("w");

    w.factory("Gaussian::constraint_b(nuisance_b[41.7,0,100],41.7,4.6)");          //constrained b to be positive - "truncated gaussian"
    w.factory("Gaussian::constraint_acc(nuisance_acc[0.71,0,1],0.71,0.09)");       //constrained acc in range 0-1
    w.factory("Gaussian::constraint_lumi(nuisance_lumi[5.0,0.0,10.0],5.0,0.195)"); //constrained lumi from 0 to 10.0
    w.factory("prod::s(sigma[0,100],nuisance_lumi,nuisance_acc)");
    w.factory("sum::mean(s,nuisance_b)");
    w.factory("Poisson::pois(n[61,0,100],mean)");
    w.factory("PROD::model(pois,constraint_b,constraint_lumi,constraint_acc)");
```

# Profile likelihood fit
nuisance parameter（$$\simeq$$興味のないパラメーター、以下NP）も含めてフィットする手法。
NPとは具体的には背景事象数やルミノシティ等、直接は探索感度に関係ないパラメーターを指す。

```cpp
void profile_gauss()
{
   RooWorkspace* ws = new RooWorkspace("ws", "ws");

   ws->factory("Gaussian::constrain_gauss(Bkg[50, 0,100], mean[25, 0, 100], sigma[3, 0,5])");
   ws->factory("prod::Sig(SigXsecOverSM[0,10],S[10])");
   ws->factory("sum::sum(Sig,Bkg)");
   ws->factory("Poisson::poisson(n[10,0,100], sum)");
   ws->factory("PROD::template(poisson, constrain_gauss)");

   ws->defineSet("poi", "SigXsecOverSM");
```











