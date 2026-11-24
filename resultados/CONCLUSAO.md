# Conclusão

**Ideia central.** Ordenar a convocação pela nota de risco, em vez da idade, encontra **3.910 casos a mais por ciclo** a cada 100.000 adultos com os mesmos 20.000 exames (ou os mesmos casos com **39% menos exames**): a gestão deve adotar a fila por risco e criar uma ação própria para os adultos de 18 a 44 anos, onde o modelo cobre só 27% dos casos.

**Problema.** Com capacidade para examinar 20% da população, quem chamar primeiro para o exame de diabetes.

**Modelo.** HGB lr=0.05 folhas=31 l2=0.0, treinado só com respostas de questionário (sem exame de laboratório). Teste com 38052 pessoas.

| Estratégia | Casos encontrados com 20% dos exames | Casos a cada 1.000 examinados |
|---|---:|---:|
| Aleatória | 19.5% | 139 |
| Regra por idade | 28.6% | 199 |
| Modelo | 56.6% | 395 |

Lift do modelo: 2.83 (IC95% 2.78 a 2.90). Para encontrar 80% dos casos, examinar 36.7% da população (regra por idade: 60.1%).

**Impacto (a cada 100.000 adultos, exame a R$ 20, hipótese).**

| Estratégia | Casos encontrados | Custo por caso |
|---|---:|---:|
| Aleatória | 2.715 | R$ 147 |
| Regra por idade | 3.981 | R$ 100 |
| Modelo | 7.892 | R$ 51 |

Casos a mais que a regra por idade: 3.910 por ciclo (IC95% 3.696 a 4.121). Para encontrar 80% dos casos: 23.400 exames a menos por ciclo (39%).

**Critérios de sucesso.**

- 1. Lift@20% >= 2,0: 2.83 (sim)
- 2. Supera a regra por idade (captura@20%): 56.6% contra 28.6% (sim)
- 3. Nenhum subgrupo com cobertura abaixo de 50%: menor: 26.8% (idade: 18-44) (não)

**Decisão recomendada.**

1. **Adotar a fila por risco** para a convocação: o primeiro decil tem 47% de diabetes, contra 14% na média.
2. **Dimensionar a capacidade pela meta**: para encontrar 80% dos casos, contratar exames para cerca de **37%** da população (e não 60%).
3. **Criar uma ação para adultos de 18 a 44 anos** (busca ativa de quem tem IMC e pressão elevados), porque ali o modelo cobre só **27%** dos casos.
4. **Acompanhar a cada ciclo**: casos encontrados por 1.000 exames (hoje o modelo faz 395), custo por caso, cobertura por idade, sexo e renda, e quantos convocados comparecem.
5. **Retreinar com dados locais** antes de qualquer uso real.

**Limitações.** Dados dos Estados Unidos (2015), autodeclarados, alvo com pré-diabetes e corte transversal. A nota serve para ordenar, não para diagnosticar.
