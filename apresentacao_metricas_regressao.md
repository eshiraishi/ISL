---
marp: true
math: kate
theme: gaia
class:
    - invert
    - lead
size: 4:3
---

# Métricas para modelos de regressão

---

# MAE (*Mean Absolute Error*)

$$
    \text{MAE} = \frac 1 n \sum^n_{i=1}\left\|y_i-\hat y_i\right\|
$$

* Análogo à acurácia para valores contínuos
* Exemplos de teste com erros altos ou baixos posuem o mesmo peso o que gera baixa volatilidade

---

# MSE (*Mean Square Error*)

$$
    \text{MSE} = {\frac 1 n \sum_{i=1}^n (y_i - \hat f(x_i))^2}
$$

* Não tem as mesmas unidades do MAE (significados diferentes)
* Muito mais volátil a grandes diferenças entre predição e valor real
    * Boa função de custo (menos passos para atingir o mínimo global)

---

# RMSE (*Root Mean Square Error*)

$$
    \text{RMSE} = \sqrt {\text{MSE}}
$$

* Um modelo ideal possui MSE igual à variância e RMSE igual ao desvio padrão

---

# $R^2$

$$
    R^2 = 1 - \frac {\text{RSS}} {\text{TSS}} =
    \frac {\sum^n_{i=1}(Y_i - \hat f(X_i))^2} 
    {\sum^n_{i=1}Y_i^2}
$$

* Avalia quão bem um modelo explica a variância nos dados
* $R^2$ baixo pode indicar *underfitting* e $R^2$ alto pode indicar *overfitting* quando outras métricas não são satisfatórias

---

# $R^2$ Ajustado
$$
    R^2_{\text{aj}} = 1 - \left(\frac{\left(1-R^2\right)\left(n-1\right)}{n-k-1}\right)
$$

* $R^2$ depende da variância, logo quanto mais variáveis maior a variância total e mais satisfatório é seu valor, o que pode causar *overfitting*
* O $R^2$ ajustado pune modelos com variáveis excessivas que não explicam a variância dos dados