# Questão Pipeline

Clique: ► [Preview no Github p/ melhor visualização](https://github.com/11joao44/Quest-o-pipeline)

## Questão 1

### Tema: Conceito de Pipeline

O texto compara o pipeline com uma linha de montagem de automóveis. Com base
nessa analogia e no conceito apresentado, qual é o principal objetivo da utilização de
pipeline na arquitetura de computadores?

☐ a) Aumentar a capacidade de armazenamento da memória cache
☐ b) Reduzir o consumo de energia do processador
✅ c) Aumentar o desempenho na execução de instruções através do paralelismo
☐ d) Simplificar o conjunto de instruções do processador
☐ e) Eliminar completamente a necessidade de ciclos de clock

## Questão 2

### Tema: Conflito de Recursos

Em um pipeline com os estágios F, D, E, M e W, ocorre um conflito de recursos quando:

☐ a) Duas instruções tentam acessar a mesma posição de memória simultaneamente
✅ b) O pipeline tenta utilizar o mesmo componente por mais de uma instrução ao mesmo tempo
☐ c) Uma instrução depende do resultado de outra instrução que ainda não foi concluída
☐ d) Uma instrução de desvio condicional altera o fluxo de execução do programa
☐ e) O ciclo de clock é insuficiente para a execução de um estágio do pipeline

## Questão 3

### Tema: Forwarding

A técnica de forwarding (bypassing) consiste em:

☐ a) Inserir bolhas no pipeline para resolver conflitos de dados
☐ b) Prever se os desvios condicionais serão tomados ou não
✅ c) Fornecer o resultado de uma instrução diretamente como entrada para outra antes do
término de sua execução completa
☐ d)Adiar a execução de instruções de salto para evitar conflitos
☐ e) Reordenar as instruções para evitar dependências de dados

## Questão 4

### Tema: Problemas no Pipeline

Quais são os três principais problemas que podem ocorrer na execução de um pipeline,
conforme apresentado no texto?

✅ a) Conflito de recursos, conflito de dados e conflito de controle
☐ b) Conflito de memória, conflito de registradores e conflito de execução
☐ c) Conflito de busca, conflito de decodificação e conflito de escrita
☐ d) Conflito de hardware, conflito de software e conflito de firmware
☐ e) Conflito de ciclo, conflito de estágio e conflito de instrução

## Questão 5

### Tema: Conceito e Funcionamento do Pipeline

Explique o conceito de pipeline na arquitetura de computadores, utilizando a analogia
da linha de montagem de automóveis apresentada no texto. Descreva como o
paralelismo é aplicado na execução de instruções e por que isso resulta em aumento de
desempenho em comparação com a execução sequencial.

**Resposta:**

> Como em uma fábrica de carros tem varias etapas enquanto um carro é pintado, o próximo já recebe o motor no processador é igual cada instrução passa por estágios diferentes ao mesmo tempo, então tudo anda em paralelo e o trabalho acaba bem mais rápido que fazer uma instrução de cada vez.

## Questão 6

### Tema: Conflito de Recurso

Descreva detalhadamente o que é um conflito de recursos em um pipeline de
instruções. Apresente um exemplo concreto desse tipo de conflito, explicando como ele
ocorre e uma possível solução para resolvê-lo.

**Resposta:**

> Conflito de recursos acontece quando duas instruções tentam usar o mesmo espaço no hardware ao mesmo tempo memória, banco de registradores, barramento, ULA e etc.
> Ex.: o add quer gravar no banco de registradores enquanto, no mesmo ciclo, a sub tenta ler desse banco ele não faz leitura e escrita simultâneas, então uma das duas precisa esperar para solucionar isso podemos duplicar/separar o recurso (memória de instruções distinta da de dados) ou usar a primeira metade do ciclo de 6ns para escrever e a segunda metade pra ler, eliminando a briga sem parar o pipeline.

## Questão 7

### Tema: Conflito de Dados

Explique o que é um conflito de dados em um pipeline e como ele afeta a execução das
instruções. Utilizando o exemplo do texto com as instruções "add $8, $9, $10" e "sub
$11, $12, $8", demonstre como a técnica de forwarding (bypassing) pode ser aplicada
para resolver esse conflito, detalhando seu funcionamento.

**Resposta:**

> Conflito de dados aparece quando a instrução seguinte precisa de um resultado que a anterior ainda não terminou de produzir no caso add `$8, $9, $10 → sub $11, $12, $8`, a sub precisa do valor de $8, mas ele só sai no estágio WB da add se nada fosse feito, teríamos bolhas (stalls) até lá Forwarding resolve desviando o resultado direto da saída da ALU da add para a entrada da ALU da sub no ciclo seguinte, antes da escrita no registrador. Assim o pipeline segue fluindo sem inserir bolhas extras.

## Questão 8

### Tema: Cálculo do Tempo Total de Execução

Explique como é calculado o tempo total (Tk) para executar n instruções em um pipeline
sem ocorrência de saltos. Utilizando a equação Tk = k + (n-1), onde k é o número de
estágios do pipeline, demonstre o cálculo do tempo total para executar 8 instruções em
um pipeline de 5 estágios.

**Resposta:**

> A priemira instrução leva k ciclos pra atravessar todos os 5 estágios cada nova instrução acrescenta só 1 ciclo porque pega a fila já andando. Então: Tk = 5 + (8 - 1) = 12 ciclos de clock pra terminar as 8 instruções.

## Questão 9

### Tema: Comparação entre Técnicas de Pipeline

Com base no texto, compare as técnicas de pipeline convencional, superpipeline e
pipeline superescalar. Explique as principais diferenças entre elas, como cada uma
busca melhorar o desempenho e quais são os desafios específicos de implementação de
cada abordagem.

**Resposta:**

> Convencional: linha de 5 estágios emite 1 instrução/ciclo.
> Superpipeline – corta cada estágio em dois e dobrando o número de estágios clock fica mais rápido e há mais instruções dentro da linha, mas cresce o overhead de registradores e controle.
> Superescalar – replica os estágios para despachar 2 ou mais instruções no mesmo ciclo obtém o maior througput, porém exige lógica extra para dependencias e pode travar se faltar paralelismo.
