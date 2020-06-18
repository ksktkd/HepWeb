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

# 統計処理
## フィット

```cpp
TH1::Fit()
```

デフォルトでは各ビンの $\chi^2$の値を計算してそれが最小となるようにパラメータを推定する（$\chi^2$フィット）。

$$
\chi^2 = \frac{(y_i-f(y_i))^2}{}
$$
