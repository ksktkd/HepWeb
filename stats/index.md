# 統計処理の基礎
## p-value

p-valueは次式で定義される。

$$
p=\int_{x}^{\infty}
$$

ここで$$f(x)$$は仮説$$H_0$$の確率密度関数を表しており、p-valueが小さいことは観測値が$$H_0$$の範囲では滅多に起きない事象であることを示している。

- eveidence : p-value=0.003
- discovery  : p-value=0.000003

## test statistics
統計処理の大きな主題の一つは何で評価するか、つまりtest statisticsをどう選ぶかとうことである。
### Likelihood ratio
$$
\lambda = \frac{L(\theta, \hat{\mu})}{L(\hat{\theta}, \hat{\mu})}
$$


