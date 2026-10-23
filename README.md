# CredAIR | Desafio 1 — Análise de Crédito

Projeto educacional desenvolvido para o **Fast Track AI**. O objetivo é investigar os fatores associados à inadimplência e treinar uma **Regressão Logística**, utilizando dados sintéticos de propostas de empréstimo.

## Organização do repositório

```text
fast-track-ai-analise-de-credito/
├── dados/credito.csv                         # dados originais (sintéticos)
├── dados/desafios/analise-credito/README.md  # enunciado do desafio de analise de crédito
├── notebooks/analise_credito.ipynb           # análise completa, do entendimento à conclusão
├── .gitignore
├── requirements.txt                          # bibliotecas implementadas no projeto
└── README.md
```

## Como executar

1. Instale o Python 3.10 ou superior.
2. A partir da pasta principal do projeto, crie e ative um ambiente virtual (recomendado).
3. Instale as dependências com `pip install -r requirements.txt`.
4. Execute `jupyter lab`, abra `notebooks/analise_credito.ipynb` e selecione **Run All**.
5. Confirme que todas as células executam sem erro e que os gráficos e resultados aparecem.

O notebook funciona tanto se executado a partir da raiz quanto de `notebooks/`. O arquivo bruto é preservado.

## Método e decisões

1. **Entendimento do problema:** classificação supervisionada binária; `inadimplente` é a resposta.
2. **EDA:** distribuição da resposta, estatísticas e relação com score, renda e dívidas.
3. **Limpeza:** exclusão das 19 duplicatas exatas, padronização de estados e marcação de valores inválidos como ausentes.
4. **Engenharia de atributos:** `multiplo_renda_solicitado = valor_solicitado / renda_mensal`.
5. **Preparação:** divisão estratificada treino/teste 80/20 e pré-processamento dentro do Pipeline.
6. **Modelagem:** Regressão Logística versus DummyClassifier (classe majoritária).
7. **Avaliação:** acurácia, precision, recall, F1, ROC-AUC, matriz de confusão e importância por permutação.
8. **Conclusão:** resultados, riscos, limitações e cuidados necessários para uso real.

## Resultados de referência

Com a semente de aleatoriedade `42` e os tratamentos documentados:

| Modelo | Acurácia | Precision (inadimplente) | Recall (inadimplente) | F1 | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| DummyClassifier | 65,6% | 0% | 0% | 0% | 0,500 |
| Regressão Logística | 73,3% | 66,2% | 45,8% | 54,1% | 0,766 |

Os valores acima são da avaliação sobre o conjunto de teste; não representam desempenho garantido em ambiente real.