# Origem dos dados

- Conjunto: **CDC Diabetes Health Indicators** (arquivo `diabetes_binary_health_indicators`).
- Fonte primária: pesquisa BRFSS 2015 (Behavioral Risk Factor Surveillance System), dos Centros de Controle e Prevenção de Doenças dos Estados Unidos (CDC).
- Repositório: UCI Machine Learning Repository, conjunto 891.
- Página: https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators
- Download usado: https://archive.ics.uci.edu/static/public/891/data.csv
- DOI: https://doi.org/10.24432/C53919
- Acesso: 24/11/2026.
- Licença: conforme a página do conjunto na UCI (conjuntos da UCI costumam usar Creative Commons Attribution 4.0). Confira a licença na página antes de redistribuir.
- SHA-256 do CSV: `9f71fda9d4ae5f4878c99b9233b6a16accfa9a17c194116a6b78100540934964`.

`raw/diabetes_binary_health_indicators.csv` é a cópia sem alteração do arquivo da UCI: 253.680 linhas e 23 colunas (`ID`, o alvo `Diabetes_binary` e 21 variáveis de questionário). O alvo vale 1 para diabetes ou pré-diabetes e 0 para ausência de diabetes.

Os dados representam a população dos Estados Unidos e não foram coletados pelo autor deste trabalho. As transformações (remoção do ID, limite do IMC em 60 e a variável derivada `n_condicoes`) acontecem em memória no notebook; o arquivo bruto não é alterado.
