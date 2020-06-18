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

# MCシミュレーション
## 反応断面積

$$
\sigma(pp\to t\bar{t}) = \sum_{ab}\int  \times \sigma(ab\to t\bar{t}) \times dx_1 dx_2 f_a(x_1, \mu_F) f_b(x_2, \mu_F)
$$

- parton level cross section：$\sigma(ab\to t\bar{t})$
  - 陽子の中のクォーク $a$ とクォーク $b$ が反応してトップクォーク対を生成する確率。
  - matrix elementから計算する
- パートン密度関数：$f_a(x)$
  - 陽子の中にクォーク $a$ がmomentum fraction $x$を持って存在している確率に相当する。
  - ここでの $\mu_F$は低エネルギーと高いエネルギーの運動を識別するためのスケールファクターである。

## 断面積

$$
\sigma = \frac{1}{F}\int dx^n |M_{fi}|^2
$$

- $dx^n$
  - すべての位相空間での積分（ここでは $n$次元とした）
- $F$
  - フラックスファクター
- $|M_{fi}|^2$
  - matrix element squared
  - Matrix elementは遷移振幅（遷移確率）を表していて、$a+b\to c+d$の状態に行く確率を表現している 
  - ファインマン図から計算される物理モデルを表しているもの


# Event generator

- Pythia
- Herwig
- Sherpa
