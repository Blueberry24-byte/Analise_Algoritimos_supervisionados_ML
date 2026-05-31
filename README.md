 Diagnóstico de Câncer de Mama: KNN vs. Naive Bayes 

Uma análise preditiva focada em otimização de métricas clínicas e redução de Falsos Negativos na detecção de tumores.

 📌 Sobre o Projeto
Este projeto aplica algoritmos de Machine Learning supervisionado para classificar tumores de mama como Benignos ou Malignos (base `Breast Cancer Wisconsin`). Mais do que apenas instanciar modelos, o foco desta análise está na **regra de negócio e no impacto clínico**: num contexto oncológico, o custo de um Falso Negativo (classificar um tumor maligno como benigno) é incalculável. Portanto, a métrica alvo para otimização foi a **Sensibilidade (Recall)** da classe minoritária.

 ## Desafios Técnicos e Pipeline de Dados
Durante a análise exploratória (EDA) e pré-processamento, lidamos com desafios reais de dados estruturados:
* **Remoção de Multicolinearidade:** Variáveis geométricas (como raio, área e perímetro) possuem alta correlação matemática. Removemos atributos com correlação `> 0.90` para manter um espaço de features enxuto, estritamente informativo e evitar distorções estatísticas.
* **Balanceamento de Classes (SMOTE):** Para evitar que o modelo ficasse enviesado para a classe majoritária (tumores benignos), utilizamos SMOTE **estritamente no conjunto de treino**, garantindo que os dados de teste se mantivessem fiéis à distribuição do mundo real.
* **Feature Scaling:** Aplicação de `StandardScaler` para garantir que o cálculo de distância do KNN não fosse dominado por atributos com escalas de grandeza muito maiores.

## Modelagem e Otimização
Comparamos dois modelos preditivos fundamentais, com busca exaustiva de hiperparâmetros via `GridSearchCV` e validação cruzada (`cv=5`):
1. **Gaussian Naive Bayes** (ajuste do `var_smoothing`)
2. **K-Nearest Neighbors - KNN** (ajuste de `n_neighbors`, `weights` e `metric`)

## 🏆 Conclusão Clínica
O modelo **KNN Otimizado** apresentou uma performance superior e consideravelmente mais segura para o contexto médico. 

O Naive Bayes assume independência estrita entre os atributos, o que limitou seu poder preditivo, dado que as proporções geométricas de um tumor possuem dependências naturais. O KNN, por outro lado, operando num espaço multidimensional devidamente escalonado, conseguiu mapear a similaridade estrutural dos casos críticos com maior precisão, reduzindo o número de Falsos Negativos.

## Como Executar

1. Clone este repositório:
git clone [https://github.com/ArthurStuker05/Analise_Algoritimos_supervisionados_ML.git](https://github.com/ArthurStuker05/Analise_Algoritimos_supervisionados_ML.git)ker05/Analise_Algoritimos_supervisionados_ML.git)

2. Abra o arquivo .ipynb na sua IDE favorita (VS Code, Jupyter) ou diretamente no Google Colab.
3. O dataset é importado nativamente pela biblioteca scikit-learn, portanto não é necessário baixar arquivos CSV externos. Basta executar as células sequencialmente.

Desenvolvido como aplicação prática de Análise e Visualização de Dados no escopo do bacharelado em Tecnologia da Informação para Negócios Digitais. 



