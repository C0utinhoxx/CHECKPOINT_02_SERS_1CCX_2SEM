# CHECKPOINT_02_SERS_1CCX_2SEM
# Avaliação — APIs, Energias Renováveis e Aprendizado de Máquina

## Objetivo

Desenvolver duas tarefas independentes de aprendizado de máquina utilizando dados obtidos de APIs públicas:

- Classificação da fonte renovável de empreendimentos de geração.
- Regressão da radiação solar em Petrolina (PE).

Foram treinados e comparados três algoritmos para cada tarefa.

## Fontes dos dados

### SIGA — ANEEL

Fonte:  
https://dadosabertos.aneel.gov.br/dataset/siga-sistema-de-informacoes-de-geracao-da-aneel

Utilizado para a tarefa de classificação.

Variáveis utilizadas:

- `potencia_kw`
- `latitude`
- `longitude`

Variável alvo:

- `fonte`

As classes consideradas são Solar (`UFV`), Eólica (`EOL`) e Hidráulica (`UHE`, `PCH`, `CGH`).

### Open-Meteo

Fonte:  
https://open-meteo.com/en/docs/historical-weather-api

Dados históricos para Petrolina (PE), nas coordenadas aproximadas `-9,39, -40,50`, no fuso `America/Recife`.

Período:

**01/04/2025 a 30/06/2025**

Foram utilizadas as horas locais entre 7h e 17h.

Variáveis utilizadas:

- `temperatura_c`
- `umidade_pct`
- `nuvens_pct`
- `vento_kmh`
- `hora`

Variável alvo:

- `radiacao_w_m2`

A variável `data_hora` foi utilizada para ordenar os dados e separar treino e teste, mas não foi utilizada como entrada do modelo.

## Tarefa 1 — Classificação

Foi realizada uma análise dos dados, incluindo quantidade de registros, valores ausentes, distribuição das classes e características das variáveis de entrada.

Os dados foram divididos em 80% para treinamento e 20% para teste, utilizando divisão estratificada e `random_state=42`.

Foram treinados três classificadores:

- Logistic Regression
- K-Nearest Neighbors (KNN)
- Random Forest

Os modelos foram comparados utilizando:

- Accuracy
- Precision
- Recall
- F1-score

Para Precision, Recall e F1-score foi utilizada média `macro`.

Também foram geradas matrizes de confusão para os três modelos.

### Resultados

| Modelo | Accuracy | Precision | Recall | F1 |
|---|---:|---:|---:|---:|
| Logistic Regression | [RESULTADO] | [RESULTADO] | [RESULTADO] | [RESULTADO] |
| KNN | [RESULTADO] | [RESULTADO] | [RESULTADO] | [RESULTADO] |
| Random Forest | [RESULTADO] | [RESULTADO] | [RESULTADO] | [RESULTADO] |

### Interpretação

[INSERIR A INTERPRETAÇÃO DAS CLASSES MAIS CONFUNDIDAS E AS LIMITAÇÕES DE PREVER A FONTE UTILIZANDO APENAS POTÊNCIA E LOCALIZAÇÃO.]

## Tarefa 2 — Regressão

Foi realizada uma análise dos dados, incluindo variáveis utilizadas, valores ausentes e visualizações das características dos dados.

Os dados foram ordenados por `data_hora` e divididos temporalmente, utilizando as primeiras 80% das horas para treinamento e as últimas 20% para teste.

Foram treinados três regressores:

- Linear Regression
- Random Forest Regressor
- Gradient Boosting Regressor

Os modelos foram comparados utilizando:

- MAE
- MSE
- R²

Também foi gerado um gráfico de valores reais versus valores previstos.

### Resultados

| Modelo | MAE (W/m²) | MSE ((W/m²)²) | R² |
|---|---:|---:|---:|
| Linear Regression | [RESULTADO] | [RESULTADO] | [RESULTADO] |
| Random Forest | [RESULTADO] | [RESULTADO] | [RESULTADO] |
| Gradient Boosting | [RESULTADO] | [RESULTADO] | [RESULTADO] |

### Interpretação

A variável `hora` foi utilizada como entrada por representar o comportamento diário da radiação solar.

A radiação solar estimada não representa diretamente a geração de energia elétrica, pois a geração depende também de fatores como potência instalada, eficiência dos equipamentos, orientação e inclinação dos painéis, temperatura, sombreamento e perdas do sistema.

## Execução

Criar o ambiente virtual:

```bash
python3 -m venv .venv
```

Ativar o ambiente virtual:

```bash
source .venv/bin/activate
```

Instalar as dependências:

```bash
pip install -r requirements.txt
```

Executar o notebook:

```bash
jupyter notebook
```

Abrir o notebook localizado em:

```text
notebooks/avaliacao_energias.ipynb
```

Executar as células na ordem.

## Dados

O repositório contém os arquivos:

```text
dados/aneel_classificacao_orange.csv
dados/meteo_regressao_orange.csv
```

Os dados também podem ser reproduzidos utilizando as APIs públicas indicadas neste README.

Não são utilizadas ou publicadas senhas ou tokens.
