# Triagem de diabetes com CRISP-DM

Atividade de Ciência de Dados: as seis fases do CRISP-DM aplicadas a um problema de saúde, com ETL, EDA, análise preditiva e data storytelling para chegar a uma decisão.

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/CodePenguinsCorp/diabetes-crisp-dm/blob/main/Diabetes_CRISP-DM.ipynb)

**Instituição:** Católica de Santa Catarina

**Disciplina:** Ciência de Dados

**Professor:** Claudinei Dias (Ney)

**Autor:** José Henrique Brühmüller

## Trabalho principal

Abra **[Diabetes_CRISP-DM.ipynb](Diabetes_CRISP-DM.ipynb)**. O notebook contém a documentação, o código em Python e as saídas da execução (gráficos e tabelas), organizados nas seis fases do CRISP-DM.

**Problema:** um programa de saúde só consegue examinar uma parte da população por ciclo. Com capacidade para **20% das pessoas**, quem chamar primeiro para o exame de diabetes para encontrar o maior número de casos?

| Fase CRISP-DM | Seção do notebook | Técnica |
|---|---|---|
| 1. Entendimento do negócio | 1 | Problema, decisão e critérios de sucesso definidos antes da modelagem |
| 2. Entendimento dos dados | 2 | EDA |
| 3. Preparação dos dados | 3 | ETL |
| 4. Modelagem | 4 | Análise preditiva |
| 5. Avaliação | 5 | Teste, intervalos de confiança, subgrupos |
| 6. Implantação | 6 | Data storytelling e decisão |

## Dados e metodologia

- Fonte: [CDC Diabetes Health Indicators, UCI](https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators), pesquisa BRFSS 2015 dos Estados Unidos. Detalhes, licença e hash em [data/README.md](data/README.md).
- 253.680 respostas e 21 variáveis de questionário (pressão alta, IMC, saúde geral, idade, renda e outras), sem exames de laboratório. O alvo é diabetes ou pré-diabetes (13,9% da base).
- **ETL:** remoção do ID, limite do IMC em 60, variável `n_condicoes` (condições de saúde relatadas) e divisão estratificada em 70% treino, 15% validação e 15% teste. As 24.206 linhas repetidas foram mantidas, com justificativa no notebook.
- **Modelagem:** base ingênua, regra simples por idade, regressão logística, random forest e HistGradientBoosting (oito configurações). Seleção pela AUC-PR na validação; modelo escolhido reajustado em treino e validação e avaliado uma vez no teste.
- **Métrica de decisão:** captura de casos entre os 20% de maior risco e lift, porque o uso é ordenar uma fila. A acurácia não serve com 14% de positivos.

## Resultados no teste

Teste com 38.052 pessoas. Modelo escolhido: HistGradientBoosting (taxa de aprendizado 0,05, 31 folhas).

| Estratégia | Casos encontrados com 20% dos exames | Casos a cada 1.000 examinados |
|---|---:|---:|
| Seleção aleatória | 19,5% | 139 |
| Regra simples por idade | 28,6% | 199 |
| **Modelo** | **56,6%** | **395** |

- AUC-PR de 0,421 (IC95% 0,408 a 0,435) contra 0,139 da seleção aleatória. Lift@20% de 2,83 (IC95% 2,78 a 2,90).
- Para encontrar **80% dos casos**, o modelo precisa examinar 36,7% da população; a regra por idade precisa de 60,1%, cerca de 39% mais exames.
- Variáveis que mais pesam: IMC, saúde geral autoavaliada, número de condições de saúde e idade.

![Ganho acumulado e decis de risco](resultados/04_ganho_decis.png)

## Decisão para a gestão

1. Ordenar a convocação pela nota de risco.
2. Dimensionar a capacidade pela meta: cerca de 37% da população para encontrar 80% dos casos, e não 60%.
3. Criar uma ação complementar para adultos de 18 a 44 anos: nessa faixa o modelo cobre só 27% dos casos.
4. Acompanhar a cobertura por idade, sexo e renda e retreinar com dados locais antes de qualquer uso real.

**O que não deu certo:** dos três critérios de sucesso fixados antes da modelagem, dois foram atendidos (lift acima de 2,0 e ganho sobre a regra por idade). O terceiro, cobertura mínima de 50% em todos os subgrupos, não foi: adultos jovens (27%) e renda alta (42%) ficam sub-representados. Está discutido no notebook.

**Limitações:** dados dos Estados Unidos (2015) e autodeclarados, alvo que reúne diabetes e pré-diabetes, estudo de corte transversal. O modelo ordena risco; não diagnostica nem prova causa.

## Executar no Google Colab

1. Clique no botão **Abrir no Colab** acima.
2. Execute todas as células em ordem (**Ambiente de execução > Executar tudo**). Sem o CSV local, o notebook baixa os dados da UCI automaticamente.
3. A execução leva poucos minutos. A pasta `resultados/` criada na sessão pode ser baixada.

## Executar localmente

Com Python 3.10 ou superior, em um terminal na pasta do projeto:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m ipykernel install --user --name diabetes-crisp-dm --display-name "Diabetes CRISP-DM"
```

Abra o notebook no VS Code ou no Jupyter, selecione o kernel **Diabetes CRISP-DM** e execute todas as células. O ambiente da execução de referência está em `resultados/metadados.json`; o `requirements.txt` define faixas compatíveis, sem garantir resultados idênticos entre versões.

## Arquivos

| Arquivo/pasta | Conteúdo |
|---|---|
| `Diabetes_CRISP-DM.ipynb` | Trabalho completo e executável, com resultados salvos |
| `data/raw/` | CSV original da UCI, sem alteração |
| `data/README.md` | Fonte, licença e integridade dos dados |
| `resultados/CONCLUSAO.md` | Resumo e decisão recomendada |
| `resultados/*.png` | Cinco figuras da EDA e da avaliação |
| `resultados/*.csv` | Métricas, decis, subgrupos, importância e capacidade necessária |
| `resultados/modelo.joblib` | Modelo final, variáveis e corte usado na função `priorizar()` |
| `resultados/metadados.json` | Versões, semente, partições e métricas |
| `roteiro_apresentacao.md` | Roteiro de 8 minutos para a apresentação |
