# Análise de valor limite

A análise de valor limite é uma extensão do particionamento de equivalência, mas só pode ser usada quando a partição é ordenada, consistindo em dados **numéricos ou sequenciais**.

A análise de valor limite pode ser aplicada em todos os níveis de teste. Essa técnica é geralmente usada para testar requisitos que exigem um **intervalo de números (incluindo datas e horas).**

## Qual é a diferença entre **análise de valor limite** e **particionamento de equivalência**?

- A análise de valor limite avalia os **limites dos seus valores**.
- Já o particionamento de equivalência avalia um valor de cada partição, não sendo necessáriamente um valor da extremidade da partição.

### Exemplo

#### **Regra de negócio**

Se o usuário digitar uma idade maior ou igual a 18 deve ser impresso a palavra 'Adulto'.

#### Código do desenvolvedor

``` 
if(idade>18){
    return "Adulto"
} else {
    return "Não é adulto"
}
```

#### Problema

Dado a regra de negócio, se o usuário da aplicação informar o valor 18 para o código desenvolvido acima, o sistema retorna a mensagem "Não é adulto" o que é incorreto.

Se usarmos a técnica de particionamento de equivalência podemos achar ou não o problema, pois não necessáriamente iriámos informar um valor das extremidades.

Para solucionar esse problema, usamos a técnica de análise de valor limite que avalia as extremidades da nossa regra de negócio e dado a regra acima, o erro seria identificado e reportado ao desenvolvedor.

## **Passo a passo** para usar a análise de valor limite

- Identificar a **VARIÁVEL DE ENTRADA** da regra de negócio
  - **IMPORTANTE:** A variável de entrada precisa ser referenciada a um nome que generalize todos os valores que são usando
- Faça uma linha reta e informe o nome da variável de entrada definida
- Faça os riscos para separar variáveis válidas e inválidas
- Identifique os valores da regra de negócio para a técnica de análise de valor limite.
  - Lembre-se somente valores **numéricos ou sequenciais**.
- Informe os valores válidos no risquinho da partição.
- Identifique o valor que está abaixo e acima dos valores válidos informados nos risquinhos da partição.
- Informe os valores abaixo das partições válidas
- Informe os valores acima das partições válidas
- Crie os casos de testes dos limites e do valor válido da partição.

## **Exemplos**

### **Regra de negócio 1**

No Brasil somente pessoas com 18 anos ou mais podem beber.

> **Passo 1:** Identificar a variável de entrada, logo ao ler a regra de negócio identificamos que a variável de entrada é "**IDADE**".

> **Passo 2:** Faça uma linha reta e informe o nome da variável de entrada definida, no caso "**IDADE**"

```
                              IDADE
            _________________________________________

```

> **Passo 3:** Faça os riscos para separar variáveis válidas e inválidas.

```
                               IDADE
                    _____________|________________
                      Inválidas  |    válidas     

```

> **Passo 4:** Identifique os valores da regra de negócio para a técnica de análise de valor limite. Dado a regra de negócio o valor válido é todos os valores de **18** ou mais anos de idade.

> **Passo 5:** Informe os valores válidos no risquinho da partição. No caso o primeiro valor válido é 18 e será esse o valor atribuído no risquinho da tabela de análise de valor limite.

```
                               IDADE
                    _____________|________________
                      Inválidas  |    válidas     
                                 |         
                                 18

```

> **Passo 6:** Identifique o valor que está abaixo e acima dos valores válidos informados nos risquinhos da partição.

- Valor inferior(abaixo) ao valor válido: 17
- Valor superior(acima) ao valor válido: 19

```
                               IDADE
                    _____________|________________
                      Inválidas  |    válidas     
                                 |         
                                 18

```

> **Passo 6:** Informe os valores abaixo das partições inválidas. No caso o valor "17"

```
                               IDADE
                    _____________|________________
                      Inválidas  |    válidas     
                                 |         
                            17   18  

```

> **Passo 7:** Informe os valores acima das partições válidas. No caso o valor "19"

```
                               IDADE
                    _____________|________________
                      Inválidas  |    válidas     
                                 |         
                            17   18  19

```

> **Passo 8:** Crie os casos de testes dos limites e do valor válido da partição.

```
                               IDADE
                    _____________|________________
                      Inválidas  |    válidas     
                                 |         
                            17   18  19

```

- **Caso de Teste 1:** Informar a idade 17
  - **Resultado:** Menor de idade, não beber bebida alcoólica
- **Caso de Teste 2:** Informar a idade 18
  - **Resultado:** Maior de idade, pode beber bebida alcoólica
- **Caso de Teste 3:** Informar a idade 19
  - **Resultado:** Maior de idade, pode beber bebida alcoólica

## Referências

- [Mais dicas de análise de valor limite](toolsqa.com/software-testing/istqb/boundary-value-analysis/)
- [Julio de lima - Alavanque sua carreira em testes de software e aumente seu salário em mais de 30%](https://programa.juliodelima.com.br/)
- [Análise de valor limite - Teste de Software](https://www.youtube.com/watch?v=a8eYjuz9RUA)
