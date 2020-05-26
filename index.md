---
layout: default
title: Hep Web
---
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [['$','$'], ['\\(','\\)']],
      processEscapes: true
    },
    CommonHTML: { matchFontHeight: false },
    displayAlign: "left",
    displayIndent: "2em",
    TeX: {
      equationNumbers: { autoNumber: "AMS" },
    }
  });
</script>
<script async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.6/MathJax.js?config=TeX-AMS_CHTML"></script>



# 荷電粒子の振る舞い
荷電粒子が物質中を通過する際、原子核に束縛された電子と電磁相互作用を起こしながら通過していく。

## Photon interaction with materials
<img width="50%" src="fig/photon-energy-dependent-cross-sections.png"/>

エネルギーが上がっていくに従って、支配的な反応が変わっていく。

* 光電効果
* レイリー散乱
    * $$\gamma$$ 電子と弾性散乱を起こす。
* コンプトン散乱
    * $$\gamma$$ が原子核の電子と非弾性散乱を起こす。
* 対生成
    * $$\gamma$$ が電子や原子核と反応して、電子陽電子対を生成する。
    * 図から分かるように、最低でも1MeV以上のエネルギーが必要となる。

## Bethe-Blochの式
荷電粒子が物質中で失うエネルギーは、量子力学の補正を取り入れたBethe-Blochの式で表される。

$$
\frac{1}{\rho} \frac{dE}{dx} = D\frac{Z}{A}z^2\frac{1}{\beta^2} \left( \ln \left[ \frac{2mc^2\beta^2}{I(1-\beta^2)}\right] -\beta^2 - \frac{\delta}{2}\right)
$$

* 変数について
    * $$\rho$$：標的物質の密度
    * $$\beta=v/c$$：粒子の速度
    * $$D \simeq 0.3071$$：定数
    * $$Z$$：標的物質の原子番号
    * $$A$$：標的の質量数
    * $$z$$：電荷

* 粒子は
    * 速度が遅いと、よくエネルギーを落とす
    * 標的物質の原子番号が大きいと、よくエネルギーを落とせる
    * 標的物質の電荷が大きいと、よくエネルギーを落とせる

# HEP 検出器の基本
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
* http://www.nucl.phys.titech.ac.jp/presen/data/thesis/b/ay2008/okamura/Bthesis.pdf
