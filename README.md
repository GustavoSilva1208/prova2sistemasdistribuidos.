# prova2sistemasdistribuidos/

# P2 - Sistemas Distribuídos

**Aluno:** Gustavo Henrique da Silva
**RA:**
**Professora:** Simone Tatiane do Canto
**Data:** 18/11/2026

## 1. Situação-Problema

Descreva brevemente os problemas apresentados Na Central de Pedidos Distribuídas.

Tivemos a principio 3 problemas, um problema de concorrência, um problema de replicação e consistência e um problema de tolerância a falha

## 2. Primeira execução

Explique o que foi observado ao executar o programa pela primeira vez.

Bom, ao executar vimos que tivemos um limite simultaneo de 3 pedidos e que a replica depois não sincronizava com o estoque atual.

### Evidência 1 - Primeira execução

![Evidência 1](evidencias/Evidencia1.png)

## 3. Problema A - Concorrência

Qual problema foi identificado?

Foi identificado que tinhamos configurado para pedir 3 pedidos de processamento simultaneo.

Qual ação foi realizada?

Mudei no código o MAXIMO_SIMULTANEO de 3 para 2

### Evidencia 2 - Concorrência

![Evidência 2](evidencias/Evidencia2.png)

Qual problema foi identificado?

Ambos os servidores possuem 10 unidades em estoque, porém o servidor principal é atualizado e o estoque não.

Qual ação foi realizada?

No código de sincronização tive que fazer que a replica seja igual ao principal para igualar o estoque atual.

## Evidência 3 - Sincronização

![Evidencia 3](evidencias/Evidencia3.png)

##5. Problema C - Tolerância a falhas.

Qual problema foi identificado?

A função responsavel para consulta não está utilizando corretamente a réplica.

Qual ação foi realizada?

A função de consultar o estoque da replica estava com a linha errada dando a váriavel principal para ela, tive que mudar para a variavel da réplica.

## Evidência 4 - Tolerância a falhas.

![Evidência 4](evidencias/Evidencia4.png)

## 6. Validação do progrma.

Descreva os resultados observados após as três correções.

Após as correções vimos que o sistema leu os 3 pedidos, atualizou o estoque e a replica também foi atualizada com no maximo 2 pedidos simultaneos.

## Evidência 5 - Execução Completa

![Evidência 5](evidencias/Evidencia5.png)


#7. Analise Técnica

1-Qual é a função do semáforo no processamento dos pedidos?

A função do semáforo é ter um delay de 0.1 segundos que nos mostra que o valor do principal tem que ser entre 0 ou 1

2-Por que é necessário sincronizar os dados entre os servidor principal e a réplica? 

Devemos sincronizar para que o sistema entenda o valor do estoque atual é a replica atualize esse valor.

3-O que significa tolerância a falhas e como ela aparece no programa?

Significa que altera o estado do servidor principal e aparece mostrando aonde está o erro no código em cada linha para que possa ser feito a reanalise.

4- Para que serve o LOCK no programa e como o controle de acesso aos recursos ajuda a prevenir problemas de concorrência?

Utiliza para travar o valor do estoque entre 0 e 1 mantando o valor que estará no estoque.

5- Considerando a sequência de eventos, a sincronização do estoque deve acontecer antes ou depois do processamento dos pedidos? Explique a relação de causalidade.

Deve acontecer depois, pois precisa antes do primeiro valor para que o sistema consiga sincronizar causando a relação de causalidade.


## 8. Conclusão

Foi interressante fazer essa atividade pois conseguimos ver a forma como o sistema distribuidos trabalha na prática e encontrar alguns erros que podem passar despercebidos em alguns casos. Esse tipo de atividade nos dá maior aprendizado na concentração para fazer uma distribuição boa.

##9. Entrega

**Aluno:** Gustavo Henrique da Silva

