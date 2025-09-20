# lab_iqr_relatorio

Relatório textual de EDA com IQR/Tukey, normalidade heurística (e Shapiro-Wilk opcional), e sumários para variáveis numéricas e categóricas.

## Como instalar/usar no Colab

1. Envie `lab_iqr_relatorio.py` para o seu ambiente (ou copie o conteúdo deste arquivo).
2. Importe e use:

```python
import pandas as pd
from lab_iqr_relatorio import generate_report

df = pd.read_csv("meus_dados.csv")
texto = generate_report(
    df,
    dataset_name="meus_dados",
    normality_tests=True,                  # usa Shapiro se n<=5000 e SciPy disponível
    include_examples_in_report=False,
    save_path="relatorio_meus_dados.txt"   # salva o relatório
)
print(texto[:1000])
```

## Dados usados na demonstração

Dataset sintético com 1000 linhas: `idade` (normal), `salario` (log-normal), `categoria` (A/B/C desbalanceada),
`score` (Beta escalado para 0-100) e `data_cadastro` (série diária). Foram inseridos faltantes intencionais em `salario` e `categoria`.

## Principais achados do demo

- `salario`: assimetria positiva, cauda longa; outliers por Tukey são esperados.
- `score`: concentrado em valores baixos (Beta com α<β), desvia da normalidade.
- `idade`: tende a simétrica; pode atender os critérios de normalidade (ver relatório).
- `categoria`: alta concentração em 'A' (~50%), diversidade moderada.
- Faltantes: presentes (imputar/remover conforme objetivo).

## Saídas geradas
- `relatorio_eda_demo.txt`: relatório textual do dataset de demonstração.
