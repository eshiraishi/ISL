---
marp: true
size: 4:3
---

# O Dilema entre Viés e Variância

---
# Contexto

* Suponha que você quer otimizar um modelo de regressão.
* É preciso atribuir uma métrica de ajuste (MSE, MAE, RMSE, etc.) que significa maximizar / minimizar um valor arbitrário.
* **É possível provar que qualquer métrica desse tipo pode ser decomposta em dois termos: viés e variância.**

---
# Viés

* O viés representa a inabilidade de um modelo em capturar a verdadeira relação entre os dados.

* **É como se as estimativas com viés excessivo fossem incorretas porque o modelo faz assunções reducionistas sobre a complexidade dos dados.**
---
# Variância

* A variância representa a diferença de ajuste entre os *data sets* (avaliados por uma mesma métrica).
* **Para obter o melhor resultado possível na etapa de treino, o modelo com variância excessiva cria complexidades desnecessárias no modelo que não se provam verdadeiras fora dessa etapa.**

---

# Conclusão

* Porém para obter modelos mais ajustados é preciso encontrar o ponto ótimo entre viés e variância, através de métricas que fazem sentido naquele contexto.
* Métricas que podem ser decompostas em viés e variância sempre geram funções côncavas que podem ser otimizadas para achar a melhor opção.
---

![](https://www.ncbi.nlm.nih.gov/books/NBK543534/bin/463627_1_En_8_Fig3_HTML.jpg)