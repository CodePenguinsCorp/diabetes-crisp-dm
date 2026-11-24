# Roteiro de apresentação (cerca de 8 minutos)

Abra o notebook no Colab com as saídas já executadas. Não precisa rodar nada ao vivo.

| Tempo | Fase / técnica | O que mostrar e dizer |
|---|---|---|
| 0:00-0:45 | **1. Negócio** | Seção 1. O problema: um programa só examina 20% da população, então quem chamar primeiro? Diga os três critérios de sucesso, definidos antes de modelar. |
| 0:45-2:15 | **2. Dados (EDA)** | Figuras 01 e 02. 253 mil respostas de uma pesquisa dos EUA, 14% com diabetes ou pré-diabetes. A prevalência sobe com a idade, e pressão alta, saúde geral e IMC aparecem forte. Cuidado: fatores "protetores" são associação, não causa. |
| 2:15-3:15 | **3. Preparação (ETL)** | Seção 3. Remoção do ID, IMC limitado, nova variável com o número de condições de saúde, divisão 70/15/15. Decisão: manter as linhas repetidas e tratar o desbalanceamento na métrica, não reamostrando. |
| 3:15-4:15 | **4. Modelagem** | Tabela de validação. Comparei base, regra por idade, regressão logística, floresta aleatória e boosting de árvores. A regressão logística fica perto; o escolhido é o de maior AUC-PR. |
| 4:15-5:45 | **5. Avaliação** | Figura 04 (quantos casos aparecem conforme se avança na fila). Com 20% dos exames, o modelo encontra 56,6% dos casos; a regra por idade, 28,6%; o acaso, 19,5%. Mostre o intervalo de confiança e a tabela de critérios. |
| 5:45-6:15 | **5. Avaliação (honestidade)** | Figura 05. O critério 3 falhou: entre 18 e 44 anos, o modelo chama só 27% dos casos. Diga isso antes que perguntem. |
| 6:15-7:45 | **6. Impacto e storytelling** | Figura 06 (painel de impacto). Comece pela ideia central em uma frase. Depois os três números: **+3.910 casos** a mais por ciclo a cada 100 mil adultos, **39% menos exames** para achar 80% dos casos, **R$ 4,69 contra R$ 9,29** de exame por caso encontrado (tabela SUS, R$ 1,85 por exame). Diga com franqueza que a economia em reais é pequena (cerca de R$ 43 mil por ciclo) e que o ganho real é encontrar quase o dobro de casos com a mesma capacidade. Feche com o plano de ação. |
| 7:45-8:00 | Fechamento | Limites: dados dos EUA, custo só do exame (sem logística) e benefício clínico não estimado. O modelo ordena, não diagnostica. |

**Dica de narrativa:** a plateia é o professor, então fale como se o público fosse um gestor de saúde. Abra pelo problema e pelo impacto, não pelo modelo. Evite gastar tempo com décimos de AUC.

## Perguntas que o professor pode fazer

- **Por que não usar acurácia?** Com 14% de positivos, "ninguém tem diabetes" acerta 86%. Por isso uso a AUC-PR (precisão média) e a parcela de casos encontrados no topo da fila.
- **Por que manter linhas repetidas?** O ID é um contador e as variáveis são em maioria binárias; duas pessoas diferentes podem responder igual. Remover enviesaria quem tem perfil comum.
- **Houve vazamento de dados?** O teste só foi usado uma vez, no fim, e a seleção do modelo foi na validação. Todas as variáveis vêm de questionário, sem o diagnóstico.
- **Por que os casos incluem pré-diabetes?** É assim que a base é distribuída (a classe 1 reúne as duas condições).
- **O modelo vale para o Brasil?** Não diretamente: os dados são dos EUA. Precisaria de validação e treino com dados locais.
