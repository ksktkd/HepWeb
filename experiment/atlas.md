# ATLAS実験
## なぜ？

- 陽子・陽子衝突なのはなぜか？


## 検出原理

ATLAS実験で検出できる粒子は

- 電子
- ミューオン
- 光子
- 中性子
- ハドロンジェット

の5種類である。これらを、検出器の配置と特性を活かして識別する必要がある。

<img width="50%" src="../fig/atlas/detector.jpg"/>

## 特徴的な2種類の磁石
ATLAS検出器では2種類の磁石を用いて、荷電粒子の運動量測定を行っている。内部秘跡検出器のためのソレノイド磁場と、ミューオン検出位のためのトロイダル磁場について説明する。

### ソレノイド磁石
ソレノイド磁石は直径2.4mの大きさで、内部秘跡検出器を包み込むように設置されている。
そのため内部秘跡検出器（以下ID）では、その磁場を用いて荷電粒子の運動量を測定することができる。

<img width="50%" src="../fig/atlas/id_momentum.png"/>

荷電粒子の磁場中の運動は、

$$
\frac{mv^2}{R} = evB \\
mv = \frac{eB}{R} \\
p = \frac{eB}{R} \\
$$

そのため、軌道の半径 $$R$$が分かれば粒子の運動量を求めることができる。
さらに近似手法を用いることでより実験的に測定のしやすい関係式を導出する。図中の黄色の直角三角形に着目して三平方の定理より、

$$
R^2 = (R-s)^2 + \left( \frac{L}{2} \right)^2 \\
R^2 = R^2 - 2Rs + s^2 + \frac{L^2}{4} \\
R = \frac{s}{2} + \frac{L^2}{8s} 
$$

ここで、実際の軌道では$$s << L$$が成り立つので

$$
R \simeq \frac{L^2}{8s} 
$$

この曲率半径を用いることで、最初に導入した式を変形することができ、


$$
p = \frac{eB}{R} = \frac{eB8s}{L^2}
$$

ここから運動量を求めることができる。

### トロイダル磁石

## 内部秘跡検出器
### IBL
### Pixel
### SCT
### TRT
## カロリメーター
粒子のエネルギーを測定する。
→ bremsstrahlung を起こしてエネルギーを落とす +$$\gamma$$ を放出する
Definition: 
The radiation length of a material is the mean length (in cm) to reduce the energy of an electron by the factor 1/e.   

Physical explanation: 
An electron arriving in the vicinity of an atom will be affected by the electromagnetic field produced by the electrons of this atom. Because of this interaction, the electron will emit photons which will reduce its energy. This is called the Bremsstrahlung radiation. It is clear that this interaction will depend on the number of electrons of the atom (atomic number Z) but also the size of the atom, represented by its atomic weight A.  

### 電磁カロリメーター
入射粒子は物質中の核子と電磁相互作用をして軌道を曲げられる。
電子、光子を放出させて電磁シャワーを観測する。
基本的に入射粒子のエネルギーが大きいほど、測定誤差は小さくなる。

[ターゲット]
* $$e$$
    * 核子による電磁相互作用で軌道を曲げて制動放射（Bremsstrahlung）を起こし、測定する
* $$\gamma$$
    * 核子との相互作用で対生成を起こさせて、電子の生成
    * 生成された電子が制動放射で#gammaを放出。。。を繰り返し（カスケードシャワーを発生させて）検知する

[Key point]
* $$X_0$$：Radiation length、放射長
    * 入射粒子のエネルギーが 1/e （〜超ざっくり半分）になる距離
    * 半分、と考えるとX0は各反応点から反応点までの距離に相当
* $$E_C$$：Critical energy
    * 電子が$$\gamma$$を放出し始めるエネルギー。
    * 入射高エネルギー粒子のエネルギーが$$E_C$$になるまでシャワー生成が続く（それを下回ると生成が終わる）
* RM：Moliere radius 
    * 横方向（transverse）シャワーサイズ。

$$
\frac{\sigma(E_0)}{E_0} = \frac{a}{\sqrt{E_0}} \oplus \frac{b}{E_0} \oplus c
$$

* a：stocastic term
    * 統計的なゆらぎによる誤差（サンプリングカロリメーターだと、aが大きい）
* b：noise term
    * ノイズ・パイルアップ
* c：constant term
    * 物質の不均一性、キャリブレーションの精度、shower の漏れ (leakage)

* カロリメーターは
    * 入射粒子のエネルギーが大きいほど、分解能がよくなる

### ハドロンカロリメーター
ハドロンシャワーを起こさせてエネルギーを測定する。 入射ハドロンが核と反応を起こす (QCD反応, 核をぶっ壊す)

* Elastic scattering: h+nucleus -> h + nucleus
* Inelastic scattering: h+nucleus -> π+ + π- + πο + ...+ nucleus
* Absorption and capture
* Secondary hadrons and muons in the shower
* Secondary neutrinos (not detectable) 

## ミューオン検出器


# Reference

- https://cds.cern.ch/record/1457044/files/ATLAS%20fact%20sheet.pdf
