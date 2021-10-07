# Chapter 1

> Statistical learning refers to a set of tools for making sense of complex datasets.

- Boxplot é uma forma interessante de relacionar dados categóricos com dados numéricos de forma interpretável.

# Chapter 2

> In this setting, the advertising budgets are input variables while sales input variable is an output variable. The input variables are typically denoted using the symbol X, with a subscript to distinguish them. So X1 might be the TV budget, X2 the radio budget, and X3 the newspaper budget. The inputs go by different names, such as predictors, independent variables, features, predictor, independent variable, feature, or sometimes just variables. The output variable—in this case, sales—is often called the response or dependent variable, and is typically denoted response using the symbol Y. Throughout this book, we will use all of these terms interchangeably.

**Definição formal de um modelo estimativo:** Dados $X$ e $Y$ é possível definir diversos $Y = f(X) + \epsilon$ onde $\epsilon$ é o erro.

As principais motivações são obter predições (determinar a função que obtem as variáveis dependentes mais próximas possíveis do mundo real) e inferências (determinar o modelo que melhor descreve os dados e entender as características que fazem tal modelo a melhor opção).

## Regressão

$\epsilon$ é um valor otimizável usando a técnica de aprendizado estatístico correta mas não irredutível e existe uma prova matemática para determinar essa característica descrita na página 19. De forma resumida o exemplo mostra que determinar uma função onde não há erro inerente, no caso de uma regressão usando a qualidade de ajuste MSE, significa minimizar o valor esperado entre o quadrado da diferença dos valores reais e os valores preditos, valor que depende das funções mas também da variância do erro, um fator irredutível.

No caso de inferência, é preciso notar que muito frequentemente modelos que descrevem fielmente os dados não são simplesmente interpretáveis.

- Existem modelos compostos de funções contínuas que não são paramétricos (como interpolações e funções *spline*)

A forma de determinar o quão bem o modelo descreve os dados é preciso medir a qualidade de ajuste (*quality of fit*), que pode ser descrito de diversas formas e a mais adequada depende de análise do problema:
Em regressão um método muito comum é o MSE (erro da média quadrada) por ser diretamente proporcional ao erro.

$$
    MSE = \frac 1 n \sum_{i=1}^n (y_i - \hat f(x_i))^2
$$

Se essa métrica foi usada nos dados de treino é preciso chamar essa medida de *training MSE* porque é válida apenas nesse contexto. A métrica que precisa ser otimizada é o *test MSE*. Isso precisa ser feito ao testar os resultados com outro dataset, e não pode ser otimizado durante o treinamento dos dados porque durante o treinamento, a métrica utilizada será o *training MSE*, e os valores ótimos não estão necessariamente relacionados (*overfitting*).

Comparando a "flexibilidade" do modelo (conhecido mais formalmente como grau de liberdade da função, que pode ser interpretados como a flexibilidade de uma função como MSE) é possível ver que nem sempre o MSE mínimo em um conjunto é válido para o outro.

- Existem formas de estimar corretamente o test MSE usando dados de treino (cross-validation).

É possível provar matematicamente que o *test MSE* esperado pode ser decomposto sempre na soma da variância de $\hat f(x_0)$, quadrado do viés (bias) de $\hat f(x_0)$ e variância de $\epsilon$:

$$
    E(y_0 - \hat f(x_0))^2 = var(\hat f(x_0)) + [bias(\hat f(x_0))]^2 + var(\epsilon)
$$

Então minimizar o MSE de teste implica minimizar a variância e bias simultaneamente. Como os dois valores nunca são negativos, o menor valor possível é $var(\epsilon)$ como demonstrado antes.

* Variância: descrição quantitativa da mudança que ocorreria caso a função fosse estimada usando outro dataset.
* Bias: erro introduzido ao aproximar um problema da vida real. É necessário fazer assunções sobre o problema para gerar um modelo e por isso, existe viés inerente ao modelo. Por exemplo, se o modelo escolhido for linear e os dados polinomiais, bias será alto, mas se a função for polinomial, o bias será baixo.

De forma geral, quanto mais flexíveis os métodos menor o bias e maior a variância e vice versa (o que gera funções de MSE côncavas para baixo muito frequentemente). Otimizar apenas um parâmetro nunca atingirá o resultado ideal.

## Classificação

A qualidade do ajuste em classificação em geral é quantificada pela taxa de erro (fração de erros em comparação aos acertos):

$$
    \frac 1 n \sum^n_{i=1}I(y_i\neq \hat y_i)
$$

Um classificador de Bayes é um preditor que minimiza a taxa de erro de teste em média e pode ser demonstrado ao atribuir a classe mais provável matematicamente aos preditores dados. Vale notar que o erro minimizado nesse contexto é a taxa de erro bayesiano, que também é um parâmetro inerentemente não-nulo.

$$
    \epsilon_{\text{bayes}} = 1 - E(\max_j Pr(Y=j|X))
$$

Porém o classificador bayesiano é válido apenas quando se sabe a distribuição dos dados, e nem sempre essa informação é conhecida e o classificador bayesiano funciona mais como um ideal a ser atingido, já que o erro bayesiano é o menor erro factível.

KNN é um método que estima a probabilidade de forma condicional (analisando apenas os pontos mais próximos $N_0$):

$$
    Pr(Y=j|X=x_0) = \frac 1 K \sum_{i \in N_0} I(y_i=j)
$$
