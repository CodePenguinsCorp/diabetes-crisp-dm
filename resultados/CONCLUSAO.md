# Conclusão

**Ideia central.** Ordenar a convocação pela nota de risco, em vez da idade, encontra **3.910 casos a mais por ciclo** a cada 100.000 adultos com os mesmos 20.000 exames (ou os mesmos casos com **39% menos exames**): a gestão deve adotar a fila por risco e criar uma ação própria para os adultos de 18 a 44 anos, onde o modelo chama só 27% dos casos.

**Problema.** Com capacidade para examinar 20% da população, quem chamar primeiro para o exame de diabetes.

**Modelo.** Boosting (taxa 0,05; 31 folhas; L2 0), treinado só com respostas de questionário (sem exame de laboratório). Teste com 38.052 pessoas.

| Estratégia | Casos encontrados com 20% dos exames | Casos a cada 1.000 examinados |
|---|---:|---:|
| Aleatória | 19,5% | 139 |
| Regra por idade | 28,6% | 199 |
| Modelo | 56,6% | 395 |

Com 20% dos exames, o modelo é 2,83 vezes melhor que o acaso (IC95% 2,78 a 2,90). Para encontrar 80% dos casos, examinar 36,7% da população (regra por idade: 60,1%).

**Impacto (a cada 100.000 adultos, exame a R$ 1,85, tabela SUS).**

| Estratégia | Casos encontrados | Custo por caso |
|---|---:|---:|
| Aleatória | 2.715 | R$ 13,63 |
| Regra por idade | 3.981 | R$ 9,29 |
| Modelo | 7.892 | R$ 4,69 |

Casos a mais que a regra por idade: 3.910 por ciclo (IC95% 3.696 a 4.121). Para encontrar 80% dos casos: 23.400 exames a menos por ciclo (39%).

**Critérios de sucesso.**

- 1. Pelo menos 2 vezes melhor que o acaso: 2,83 vezes (sim)
- 2. Acha mais casos que a regra por idade: 56,6% contra 28,6% dos casos (sim)
- 3. Nenhum grupo com menos de 50% dos casos chamados: menor: 26,8% (18 a 44 anos) (não)

**Decisão recomendada.**

1. **Adotar a fila por risco** para a convocação: entre os 10% de maior risco, 47% têm diabetes ou pré-diabetes, contra 14% na média.
2. **Dimensionar a capacidade pela meta**: para encontrar 80% dos casos, contratar exames para cerca de **37%** da população (e não 60%).
3. **Criar uma ação para adultos de 18 a 44 anos** (busca ativa de quem tem IMC e pressão elevados), porque ali o modelo chama só **27%** dos casos.
4. **Acompanhar a cada ciclo**: casos encontrados por 1.000 exames (hoje o modelo faz 395), custo por caso, casos chamados por idade, sexo e renda, e quantos convocados comparecem.
5. **Retreinar com dados locais** antes de qualquer uso real.

**Limitações.** Dados dos Estados Unidos (2015), autodeclarados, alvo com pré-diabetes e corte transversal. A nota serve para ordenar, não para diagnosticar.
