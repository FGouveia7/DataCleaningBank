# Data Cleaning - Bank Marketing

Projeto de limpeza e reformatação dos dados brutos de `bank_marketing.csv`, criando três arquivos
prontos para análise: `client.csv`, `campaign.csv` e `economics.csv`.

## Requisitos

Python 3.10 ou superior, com as seguintes bibliotecas:

    pandas
    numpy

Para instalar:

```bash
pip install pandas numpy
```

## Como executar

1. Certifique-se de que `bank_marketing.csv` está na raiz do projeto.
2. Abra o notebook `Project_DataCleaningBank.ipynb`.
3. Execute todas as células em ordem.
4. Os arquivos `client.csv`, `campaign.csv` e `economics.csv` serão gerados na pasta do projeto.

## Regras de limpeza

### client.csv

| Coluna           | Transformação                                        |
| ---------------- | ---------------------------------------------------- |
| `job`            | Substitui `.` por `_`                                |
| `education`      | Substitui `.` por `_`; converte `"unknown"` para NaN |
| `credit_default` | 1 se `"yes"`, caso contrário 0                       |
| `mortgage`       | 1 se `"yes"`, caso contrário 0                       |

### campaign.csv

| Coluna              | Transformação                                                            |
| ------------------- | ------------------------------------------------------------------------ |
| `campaign_outcome`  | 1 se `"yes"`, caso contrário 0                                           |
| `previous_outcome`  | 1 se `"success"`, caso contrário 0                                       |
| `last_contact_date` | Criada a partir de `day` + `month` + ano fixo 2022; formato `YYYY-MM-DD` |

### economics.csv

| Coluna                 | Transformação                      |
| ---------------------- | ---------------------------------- |
| `cons_price_idx`       | Mantido como float, sem alterações |
| `euribor_three_months` | Mantido como float, sem alterações |

## Observações

A função auxiliar `one_if(column, value)` centraliza a conversão de colunas categóricas para binário
(0/1), evitando repetição de lógica no notebook.

O ano 2022 é fixo na construção de `last_contact_date`. Caso os dados sejam de outro período, ajuste
o valor diretamente no notebook antes de executar.

Se alguma coluna esperada não for encontrada, verifique se os nomes no CSV de entrada correspondem
exatamente aos utilizados no notebook.
