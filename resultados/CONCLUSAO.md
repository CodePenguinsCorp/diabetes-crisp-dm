# Conclusão

**Problema.** Com capacidade para examinar 20% da população, quem chamar primeiro para o exame de diabetes.

**Modelo.** HGB lr=0.05 folhas=31 l2=0.0, treinado só com respostas de questionário (sem exame de laboratório). Teste com 38052 pessoas.

| Estratégia | Casos encontrados com 20% dos exames | Casos a cada 1.000 examinados |
|---|---:|---:|
| Aleatória | 19.5% | 139 |
| Regra por idade | 28.6% | 199 |
| Modelo | 56.6% | 395 |

Lift do modelo: 2.83 (IC95% 2.78 a 2.90). Para encontrar 80% dos casos, examinar 36.7% da população (regra por idade: 60.1%).

**Critérios de sucesso.**

- 1. Lift@20% >= 2,0: 2.83 (sim)
- 2. Supera a regra por idade (captura@20%): 56.6% contra 28.6% (sim)
- 3. Nenhum subgrupo com cobertura abaixo de 50%: menor: 26.8% (idade: 18-44) (não)

**Decisão recomendada.**


1. Usar a nota de risco para ordenar a convocação. Os dois primeiros decis concentram a maior parte dos casos.
2. Se a meta do programa for encontrar 80% dos casos, dimensionar a capacidade para cerca de **37%** da população, e não para 60%.
3. Criar uma ação complementar para adultos de 18 a 44 anos (busca ativa de quem tem IMC e pressão elevados), porque ali o modelo cobre só **27%** dos casos.
4. Acompanhar a cobertura por idade, sexo e renda a cada ciclo e repetir o treino com dados locais antes de qualquer uso real.

**Limitações.** Dados dos Estados Unidos (2015), autodeclarados, alvo com pré-diabetes e corte transversal. A nota serve para ordenar, não para diagnosticar.
