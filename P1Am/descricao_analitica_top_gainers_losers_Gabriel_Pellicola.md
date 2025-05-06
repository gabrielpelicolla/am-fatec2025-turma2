## Relatório de Análise de Ganhadores e Perdedores no Mercado Financeiro

### Introdução

Este relatório apresenta uma análise de dados financeiros com o objetivo de identificar padrões que diferenciam ativos ganhadores de perdedores no mercado. A análise foi realizada utilizando a API Alpha Vantage para coletar dados e técnicas de aprendizado de máquina para construir um modelo preditivo.

### Conclusões e Recomendações

#### Padrões de Ganhadores e Perdedores

A análise dos dados revelou padrões distintos entre ativos ganhadores e perdedores. Os ganhadores tendem a apresentar:

- *Média de retorno positiva (Mean)*  
- *Desvio padrão moderado (StdDev)*  
- *Preços (price) e volumes (volume) de negociação mais altos*  
- *Mudança percentual positiva (change_percentage)*  

Já os perdedores frequentemente exibem:

- *Média de retorno negativa*  
- *Desvio padrão potencialmente elevado*  
- *Preços e volumes de negociação menores*  
- *Mudança percentual negativa*  

#### Recomendações para Investidores

Com base nos padrões identificados, recomendamos as seguintes práticas para a tomada de decisão em investimentos:

1. *Priorizar ativos com média de retorno positiva e desvio padrão moderado.*  
2. *Considerar preço, volume e mudança percentual como indicadores de tendência.*  
3. *Monitorar o desvio padrão para gerenciar riscos.*  
4. *Utilizar o modelo Naive Bayes como ferramenta auxiliar na previsão do comportamento dos ativos, com cautela e acompanhamento constante.*  
5. *Combinar a análise estatística com outros indicadores, como fundamentos da empresa e notícias do mercado.*  
6. *Diversificar a carteira para reduzir riscos.*

### Análise das Técnicas e Implementações de Código

#### Obtenção e Preparação dos Dados

- A biblioteca requests foi utilizada para acessar a API Alpha Vantage e coletar dados.  
- A biblioteca pandas foi crucial para manipular e transformar os dados em DataFrames.  
- Funções como str.replace e astype foram empregadas para limpar e converter os dados.  

#### Análise Exploratória

- Bibliotecas como seaborn, matplotlib e plotly foram utilizadas para criar visualizações informativas.  
- A função describe() do pandas forneceu estatísticas descritivas dos dados.  

#### Pré-processamento

- StandardScaler foi aplicado para normalizar os dados.  
- train_test_split dividiu os dados em conjuntos de treinamento e teste.  

#### Modelagem e Avaliação

- O algoritmo GaussianNB foi utilizado para construir o modelo preditivo.  
- Métricas como accuracy_score, confusion_matrix e classification_report avaliaram o desempenho do modelo.  
- ConfusionMatrix do yellowbrick gerou uma visualização da matriz de confusão.  

#### Persistência e Exportação

- pickle foi utilizado para salvar o modelo e os dados pré-processados.  
- A funcionalidade de exportação para CSV do pandas poderia ser utilizada para salvar o dataset final.  

### Limitações e Soluções

Durante a execução da análise, foram encontradas limitações na versão gratuita da API Alpha Vantage, impactando principalmente o endpoint ANALYTICS_FIXED_WINDOW:

#### Limitação do Parâmetro SYMBOL

- A API limita a 5 symbols por requisição, enquanto eram necessários 6.  
- *Solução adotada*: Dividir as requisições em duas, uma para ganhadores e outra para perdedores.  
- Outras alternativas seriam reduzir o número de symbols, utilizar outra API ou ajustar a estratégia de coleta de dados.  

#### Agregação de Dados no Parâmetro RANGE

- A API retorna dados agregados para todo o período, limitando a quantidade de dados para treinamento.  
- *Soluções alternativas*:  
  - Ajustar o parâmetro RANGE para intervalos menores.  
  - Utilizar outro endpoint para obter dados diários.  
  - Criar features adicionais a partir dos dados agregados.  
  - Utilizar um modelo mais robusto.  

### Considerações Finais

As limitações da API Alpha Vantage impactaram a análise, mas foram contornadas com soluções alternativas. As conclusões e recomendações apresentadas fornecem insights valiosos para a tomada de decisão em investimentos, mas é crucial lembrar que o mercado financeiro é complexo e sujeito a diversos fatores. Portanto, este relatório deve ser utilizado como ferramenta auxiliar, combinado com outras análises e acompanhamento constante do mercado.
