# Template de Apoio à Atividade de Teste de Software
**Criado para o Exercício Final  da UC 13 - Executar Teste e Implantação de Aplicativos Computacionais**

---

## 1. Cenário geral do XXX (o quê será testado)
Apresente aqui uma visão geral do algoritmo, módulo ou do software que será testado. O que ele é? O que ele faz ou permite aos usuários fazerem? Quais são as principais funcionalidades? Ou quais funcionalidades serão testadas e consideradas aqui neste template? Ou quais módulos serão verificados?

---

O Simulador de Dados é um programa que permite aos usuários simular lançamentos de dados de diversos tipos e acompanhar os resultados de maneira interativa. Esse simulador é especialmente útil em jogos de RPG, onde os jogadores costumam usar dados com um número específico de faces para determinar ações e eventos. A interação do usuário é simples e amigável, com instruções e opções de forma sequencial, permitindo escolher o tipo de dado, a quantidade a ser lançada e exibindo o resultado. 

Funcionalidades Principais
O programa oferece as seguintes funcionalidades principais:

Escolha do Tipo de Dado : O usuário pode selecionar o tipo de dado que deseja lançar (D4, D6, D8, D10, D12, D20 ou D100), cada um com um número específico de faces.

Escolha da Quantidade de Dados : O usuário define quantos dados do tipo selecionado deseja lançar de uma só vez.

Lançamento e Exibição dos Resultados : Para cada dado lançado, o programa exibe o valor obtido e, em caso de múltiplos lançamentos, soma os resultados e exibe o total final.  

teste

Teste de Seleção de Tipo de Dado : Verifique se o programa permite a escolha correta do tipo de dado entre as opções oferecidas.

Teste de Quantidade de Dados : Validar se o programa aceita somente números inteiros positivos como quantidade de dados e trata entradas inválidas especificamente.

Teste de Lançamento de Dados : Confirmar que cada lançamento de dado retorna valores dentro do intervalo esperado (de 1 até o valor máximo)

---

## 2. Estratégia(s) de Teste (como será testado)
De acordo com o cenário/escopo daquilo que será testado, descreva quais atividades de teste serão conduzidas. Quais técnicas de teste serão usadas e com qual objetivo/finalidade? Qual ou quais critérios serão utilizados para cada técnica? Se alguma ferramenta for utilizada, descreva-a(s) aqui, de forma geral.

---

Planejamento dos Testes :

Definir os objetivos dos testes, escopo, recursos necessários e cronograma.
identificar as funcionalidades a serem testadas e os critérios de limites acessíveis.
Desenvolvimento de Casos de Teste :

Criar casos de teste baseados nos requisitos funcionais, abrangendo as funcionalidades principais do simulador, como seleção de tipo de dado, quantidade de dados, lançamento e soma de resultados.
Execução de Testes :

Conduzir a execução dos testes utilizando as técnicas seguidas, documentando os resultados e comportamentos observados.
Registro de Defeitos :

Documentar quaisquer falhas encontradas durante os testes, categorizando sua gravidade e impacto.
Reteste e Regressão :

Realizar retestes em funcionalidades corrigidas e testes de regressão para garantir que mudanças não introduzam novos problemas.
Relatório de Resultados :

Compilar um relatório detalhando os resultados dos testes, incluindo a cobertura das funcionalidades, defeitos encontrados e recomendações para melhorias.

Técnicas de Teste a Serem Usadas

teste funcional
teste estrutural
teste Mutação

Ferramentas Utilizadas

Estrutura de teste de unidade

vSCODE
pytest
colab

---

## 3. Projeto de Casos de Teste (como será testado)

Apresente, para cada técnica e critério considerados, quais são os casos de testes a serem utilizados (roteiro e/ou dados de entrada, resultados esperados).

*Exemplo*: Se usar Teste Funcional e Critério Análise do Valor Limite, apresente a tabela final considerando as variáveis de entrada, as classes de equivalência válidas e inválidas, bem como os casos considerando os limites.

---

teste funcional

| **Módulo**   | **Descrição**                           | **Roteiro**                                             | **Resultado Esperado**                                    | **Comentário**                                                           | **Resultado do Teste** |
|--------------|-----------------------------------------|---------------------------------------------------------|-----------------------------------------------------------|--------------------------------------------------------------------------|-------------------------|
| `lanca_dado` | Teste de lançamento de um único dado D6 | Lançar um dado com `tipo=6` e `quantidade_de_dados=1`   | Resultado dentro do intervalo `[1, 6]`                    | Verifica se o lançamento de um dado único retorna um valor válido        | Passou                  |
| `lanca_dado` | Teste de lançamento de múltiplos dados D10 | Lançar 3 dados com `tipo=10` e `quantidade_de_dados=3` | Resultado é uma lista de 3 valores entre `[1, 10]`, e a soma dos valores | Verifica se múltiplos lançamentos retornam valores válidos e soma correta | Passou                  |
| `execute`    | Teste de escolha de não lançar dados    | Escolher "Não (2)" na primeira pergunta do método `execute` | Exibe "ok" e encerra o programa                           | Testa se o programa encerra corretamente quando o usuário opta por não lançar dados | Passou         |

---

teste estrutural

| Módulo              | Descrição                                        | Roteiro                                            | Resultado Esperado                                    | Comentário                                                                                   | Resultado do Teste |
|---------------------|--------------------------------------------------|----------------------------------------------------|------------------------------------------------------|---------------------------------------------------------------------------------------------|---------------------|
| `lanca_dado`        | Testa o lançamento de múltiplos dados D6.        | 1. Instanciar a classe `SimuladorDados`.           | O resultado deve ser uma lista de 3 valores entre 1 e 6. | Verifica se a função `lanca_dado` retorna uma lista correta para múltiplos lançamentos.    | Passou             |
| `execute`           | Testa o fluxo de execução quando o usuário escolhe não lançar o dado. | 1. Simular a resposta `2` na primeira pergunta do método `execute`. | O loop deve terminar, exibindo apenas a mensagem "ok". | Testa se o programa encerra corretamente quando o usuário opta por não lançar o dado.      | Passou             |
| `soma_resultado`    | Testa o comportamento com uma lista vazia.       | 1. Instanciar a classe `SimuladorDados`. 2. Chamar `soma_resultado` com uma lista vazia. | O método deve retornar `0`.                            | Verifica se a função `soma_resultado` retorna `0` para uma lista vazia, o que é esperado. | Passou             |


---
teste mutação 

| Caso de Teste                                         | Status   | Mutantes Mortos | Mutantes Sobreviventes |
|-------------------------------------------------------|----------|------------------|------------------------|
| Teste da função `soma_resultado`                      | Sucesso  | 1                | 0                      |
| Teste do intervalo de sorteio de valores dos dados    | Sucesso  | 1                | 0                      |
| Teste da estrutura de controle do loop `while`        | Sucesso  | 1                | 0                      |
| Teste do valor padrão `quantidade_de_dados = 0`       | Sucesso  | 1                | 0                      |


---

## 4. Execução (quando e como será testado)
Detalhes sobre a execução: explique como o teste foi executado. Foi utilizada alguma ferramenta, mesmo que não tenha sido apresentada no curso? Para os casos de teste considerados anteriormente, especifique o resultado retornado (resultado do teste), descrição dos erros (caso tenham ocorrido).

teste funcional 

Teste Funcional: Lançamento de um Único Dado (D6)
Objetivo : Verificar se o programa permite lançar um dado de 6 lados e retornar um valor no intervalo correto.
Inserir o nome do jogador quando solicitado.
Escolha "Sim (1)" para lançar um dado.
Selecione o dado D6.
Defina a quantidade de dados para 1.
Resultado Esperado : O programa retorna um valor entre 1 e 6 e exibe o resultado do lançamento, como "Você lançou 1 D6 e obteve X como resultado", onde X está entre 1 e 6.

---

Teste Funcional: Lançamento de Múltiplos Dados (D10)
Objetivo : Testar se o programa permite lançar múltiplos dados (D10) e soma corretamente os valores.
Insira o nome do jogador.
Escolha "Sim (1)" para lançar um dado.
Selecione o dado D10.
Defina a quantidade de dados para 3.
Resultado Esperado : O programa deve mostrar três valores de lançamentos entre 1 e 10, e a soma desses valores, como "Você lançou 3 D10 e obteve Y como resultado", onde Y é a soma dos três lançamentos.

---

Teste Funcional: Escolha de Não Lançar Dados
Objetivo : Testar o fluxo do programa quando o usuário escolhe não lançar dados.
Insira o nome do jogador.
Escolha "Não (2)" quando questionado se deseja lançar um dado.
Resultado Esperado : O programa deve exibir a mensagem "ok" e encerrar sem outras perguntas ou lançamentos.

---


teste estrutural

Teste  estrutural: foi feito no pytest, foi testado o lançamento de múltiplos dados D6 O teste instanciou a classe SimuladorDados e chamou a função lanca_dado com tipo=6 e quantidade_de_dados=3, O teste confirmou que a função retornou uma lista correta com os valores esperados. 

---
Teste Estrutural: Teste do Loop de Execução com Escolha de Não Lançar
Objetivo : Testar o fluxo de execução principal quando o usuário opta por não lançar o dado.
Passos :
Substitua inputpor uma simulação para retornar o valor 2na primeira pergunta do método execute("Você quer lançar um dado?").
Execute o método executee verifique se o loop foi finalizado imediatamente.
Espera-se : Que o programa exiba a mensagem "ok" e encerre sem fazer outras perguntas.

---

Teste Estrutural: Teste do Método soma_resultadocom uma Lista Vazia
Objetivo : Verificar o comportamento do método soma_resultadoao receber uma lista vazia.
Passos :
Instância de uma classe SimuladorDados.
Chama o método soma_resultadopassando por uma lista vazia ( []).
Verifique se o método retorna 0.
Espera-se : Que o método retorne 0, já que a soma de uma lista vazia deve ser zero.

---

teste mutação

Mutação: O teste de mutação foi feito utilizando a ferramenta colab, Resultado Esperado: A soma deve ser o total dos elementos, mas com o mutante o resultado será negativo.
Resultado do Teste: O teste detecta a falha, pois o resultado é incorreto e não corresponde ao esperado, Mutante 1: Mudar soma = soma + int(i) para soma = soma - int(i)

---

Mutação: Alteração do intervalo de sorteio de valores dos dados
Modificação: Altere o intervalo de random.randint(1, valor_max)para random.randint(1, valor_max - 1)em lanca_dado.
Objetivo: Verifique se o programa detecta quando o dado não gera o valor máximo possível, um erro comum que pode ocorrer se o intervalo estiver incorreto.

---
Mutação: Modificar a estrutura de controle do loop whileno métodoexecute
Modificação: Altere a linha while lancar == True:para while lancar == False:.
Objetivo: Testar se o loop principal do jogo se comporta corretamente e encerra quando o usuário escolhe parar.

---
Mutação: Alterar o valor padrão quantidade_de_dadospara 0 no métodolanca_dado
Modificação: Nenhum método lanca_dado, altere quantidade_de_dados: int = 1para quantidade_de_dados: int = 0.
Objetivo: Verificar como o programa reage ao tentar lançar zero dados e se há algum tratamento para impedir lançamentos inválidos.

---

## 5. Análise dos Resultados e Próximos Passos
Após o teste, que conclusão você chegou? Outras técnicas ou ferramentas são necessárias? Tendo mais tempo para realizar os testes, quais seriam os próximos passos que poderiam ser realizados?

Após a realização dos testes do Simulador de Dados, a conclusão é que o programa atende aos requisitos funcionais esperados, com os testes funcionais, estruturais e mutacionais. No entanto, alguns pontos podem ser considerados para melhorar ainda mais a robustez do software

Se tivéssemos mais tempo, os próximos passos incluiriam:
1 documentação
2 Feedback de Usuários
3 Avaliação de Segurança
4 melhoria