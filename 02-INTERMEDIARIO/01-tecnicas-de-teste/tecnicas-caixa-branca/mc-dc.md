
# MC/DC (Modified Condition/Decision Coverage)

## **Princípio básico**

A Cobertura de Condição/Decisão Modificada (MC/DC - *Modified Condition/Decision Coverage*) é uma métrica de cobertura estrutural de código exigida para softwares de altíssima confiabilidade. Ela aprimora o critério tradicional de cobertura de condição/decisão **exigindo que cada condição lógica seja demonstrada como afetando de forma independente o resultado da decisão na qual está inserida**.

Isso pode ser alcançado demonstrando que o resultado da decisão muda em consequência da alteração de uma única condição (abordagem de causa única) ou garantindo, por meio da lógica booleana, que as outras condições não estão influenciando no resultado (abordagem de mascaramento). **Para uma decisão com *n* entradas independentes, a cobertura MC/DC normalmente exige um mínimo de *n+1* casos de teste**, oferecendo uma alternativa prática e linear para o teste de todas as lógicas em comparação com um teste de condição múltipla (exaustivo) que precisaria de 2^n testes.

## **Quando não usar**

O MC/DC **não deve ser utilizado como um método de teste base, nem para derivar os cenários de testes inicialmente**. Se você tentar criar casos de teste a partir da estrutura do código-fonte, não conseguirá encontrar erros como requisitos não implementados e funções mal compreendidas (já que a referência utilizada é a própria implementação possivelmente incorreta). O MC/DC também **não precisa ser usado para softwares com níveis de menor criticidade** na aviação (níveis B, C ou D da DO-178B), uma vez que testes de cobertura de comando (*statement coverage*) ou decisão são suficientes nesses casos. Da mesma forma, se a quantidade de condições lógicas na função for incrivelmente pequena, realizar a cobertura múltipla exaustiva (2^n) pode ser mais fácil e direto do que analisar o MC/DC.

## **Quando usar**

A técnica **deve ser aplicada na validação de softwares considerados Nível A pela norma RTCA/DO-178B**, que compreende sistemas críticos de voo (computação de bordo da aviação) em que uma falha tem consequências catastróficas. Seu uso aplica-se principalmente para lidar com expressões booleanas complexas, comuns na indústria aeronáutica. O MC/DC deve atuar após o desenvolvimento dos casos de teste baseados em requisitos para funcionar como uma malha de confirmação: **ele garante que o rigor dos testes baseados em requisitos foi adequado e revela se existe alguma estrutura ou função não intencional oculta no código**.

## **Como usar**

A NASA propõe um método manual de 5 passos baseados na representação por portas lógicas para avaliar se os casos de teste cumprem o MC/DC:

1. **Criar uma representação do código fonte:** Modelar as expressões através de esquemas que conectam blocos lógicos básicos (portas AND, OR, XOR, NOT e comparadores numéricos).
2. **Identificar os dados de teste:** Mapear no esquema todos os casos de teste provenientes dos testes baseados em requisitos, assinalando Entradas (Verdadeiro/Falso) e verificando resultados intermediários em cada ramificação.
3. **Eliminar testes mascarados (*Masked tests*):** Descartar instâncias de testes cuja saída final na porta analisada é bloqueada (mascarada) por outras variáveis do circuito. Por exemplo: qualquer entrada "Falsa" em uma porta AND força o resultado daquela porta, ocultando e inutilizando a verificação do que ocorria com o restante das portas do bloco.
4. **Determinar o cumprimento do MC/DC:** Avaliar os testes válidos não mascarados contra as exigências para cada operador elementar.
5. **Confirmação da saída:** Analisar os resultados teóricos traçados no modelo esquemático e atestar se equivalem aos resultados práticos da documentação. Se divergirem, aponta falha ou defeito na codificação do software.

## **Exemplos práticos**

Na prática do método, cada "bloco de construção lógico" possui conjuntos de testes essenciais para atestar independência. Alguns exemplos simples incluem:

- **Porta AND (ex: 3 entradas):** O MC/DC requer um teste onde todas as entradas são *Verdadeiras* (comprovando que a porta opera) e *n* testes onde cada entrada assume exclusivamente a condição *Falsa* enquanto as outras se mantêm verdadeiras.
- **Porta OR (ex: 3 entradas):** O inverso se aplica. É necessário um caso base com todas as conexões em condição *Falsa* e testes suplementares onde cada componente torna-se *Verdadeiro* isoladamente.
- **Comparador lógico (ex: x > 2500):** O MC/DC exigiria logicamente dois testes, mas a prudência da engenharia requer três cenários nos testes baseados em requisitos: uma resposta que fica estritamente acima do limite, uma levemente inferior ao limite, e uma igual ao ponto de comparação em si para prevenir bugs de sintaxe `>= / >` ou limites de precisão da máquina.
