# Roteiro de apresentação (cerca de 8 minutos)

A apresentação é um caminho de nove perguntas. Em cada parada: **faça a pergunta, mostre a evidência, responda em uma frase e use a frase de passagem** para chegar à próxima. No notebook, cada parada está marcada com "Parada N de 9".

Abra o notebook no Colab com as saídas já executadas. Não precisa rodar nada ao vivo. Comece mostrando a tabela **"O caminho"**, no topo, para o professor saber para onde vai.

| Tempo | Parada | Mostre | Responda | Frase de passagem |
|---|---|---|---|---|
| 0:00-0:40 | **1. Que decisão precisamos tomar?** (Negócio) | Seção 1 e os três critérios de sucesso | Quem chamar primeiro quando só cabem exames para 20% das pessoas. | "Antes de responder: dá para confiar nos dados?" |
| 0:40-1:10 | **2. Dá para confiar nos dados?** (EDA) | Seções 2.1 e 2.2 | Sim: 253 mil respostas, sem valores vazios, 13,9% com diabetes ou pré-diabetes. São autodeclaradas e dos EUA. | "Se eu só posso examinar alguns, o primeiro critério que vem à cabeça é a idade." |
| 1:10-1:45 | **3. Basta chamar os mais velhos?** (EDA) | Figura 01 | A idade ajuda (3,0% até 39 anos, 19,7% com 60 ou mais), mas cerca de 8 em 10 idosos não têm o diagnóstico. | "Então o que mais distingue quem tem?" |
| 1:45-2:40 | **4. Que outros sinais existem?** (EDA) | Figuras 02 e 03 | Pressão alta, IMC, saúde percebida e renda. Nenhum basta sozinho. São associações, não causas. | "Dá para juntar tudo isso em uma só ordem de prioridade?" |
| 2:40-3:20 | **5. Como preparar sem enganar o resultado?** (ETL) | Seção 3 | Uma função única de tratamento, linhas repetidas mantidas e 15% separados para o teste final. | "Com os dados prontos: juntar os sinais ajuda mesmo?" |
| 3:20-4:10 | **6. Juntar os sinais ajuda?** (Modelagem) | Tabela de validação, seção 4 | Sim: AUC-PR de 0,197 (idade) para 0,420 (logística) e 0,441 (boosting). O salto vem de combinar os sinais. | "Mas isso vale para quem o modelo nunca viu?" |
| 4:10-5:10 | **7. Funciona com pessoas novas?** (Avaliação) | Figura 04 | Com 20% dos exames: 56,6% dos casos, contra 28,6% pela idade e 19,5% ao acaso. | "A média está boa. Mas está boa para todo mundo?" |
| 5:10-6:00 | **8. Para quem funciona mal?** (Avaliação) | Figura 05 | De 18 a 44 anos, só 27% dos casos são chamados. Um dos três critérios não foi atendido. | "Sabendo onde acerta e onde falha: vale usar?" |
| 6:00-7:30 | **9. O que muda e o que fazer?** (Storytelling) | Figura 06, a ideia central e o plano de ação | +3.910 casos a cada 100 mil adultos, 39% menos exames para achar 80% dos casos, e R$ 4,69 contra R$ 9,29 de exame por caso. | "Isso responde à pergunta inicial, e abre outras." |
| 7:30-8:00 | **Fim do caminho** | "O percurso em uma página" e "O próximo trecho" | Usar para ordenar a fila, com ação própria para os jovens. Falta validar no Brasil, medir o comparecimento e o benefício clínico. | |

## Cuidados

- **Siga a ordem.** Não antecipe o resultado do modelo nas paradas 3 e 4: a graça é o professor sentir por que ele é necessário.
- **Seja franco sobre o dinheiro.** No SUS (R$ 1,85 por exame), a economia é pequena, cerca de R$ 43 mil por ciclo. O ganho real é achar quase o dobro de casos com a mesma capacidade.
- **Fale como para um gestor de saúde** e não gaste tempo com décimos de AUC.

## Perguntas que o professor pode fazer

- **Por que não usar acurácia?** Com 14% de positivos, "ninguém tem diabetes" acerta 86%. Por isso uso a AUC-PR (precisão média) e a parcela de casos encontrados no topo da fila.
- **Por que manter linhas repetidas?** O ID é um contador e as variáveis são em maioria binárias; duas pessoas diferentes podem responder igual. Remover enviesaria quem tem perfil comum.
- **Houve vazamento de dados?** O teste só foi usado uma vez, no fim, e a seleção do modelo foi na validação. Todas as variáveis vêm de questionário, sem o diagnóstico.
- **Por que a pressão alta pesa pouco no modelo?** Parte da informação dela está dentro do número de condições de saúde.
- **Por que os casos incluem pré-diabetes?** É assim que a base é distribuída (a classe 1 reúne as duas condições).
- **O modelo vale para o Brasil?** Não diretamente: os dados são dos EUA. Precisaria de validação e treino com dados locais.
