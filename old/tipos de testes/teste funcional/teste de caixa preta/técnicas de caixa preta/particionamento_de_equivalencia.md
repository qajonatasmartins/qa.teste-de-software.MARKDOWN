# Partição de equivalência

A partição de equivâlencia é uma técnica de teste de caixa preta base para outras técnicas de testes. Ela se aplica a todos os níveis de testes.

A idéia é dividir um conjunto de condições de testes em grupos ou conjuntos que podem ser considerados iguais.

## **Passo a passo** para usar a partição de equivâlencia

- Identificar a **VARIÁVEL DE ENTRADA** da regra de negócio
  - **IMPORTANTE:** A variável de entrada precisa ser referenciada a um nome que generalize todos os valores que são usando
- Faça uma linha reta e informe o nome da variável de entrada definida
- Faça os riscos para separar variáveis válidas e inválidas
- Identifique os valores da partição de equivâlencia
- Informe os valores das partições
- Crie um teste para cada partição

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

> **Passo 4:**  Informe os valores das partições. Conforme a regra de negócio, pessoas com 18 anos ou mais podem beber (então é uma partição válida) e pessoas menores que 18 anos não podem beber (então menor que 18).

```
                               IDADE
                    _____________|________________
                      Inválidas  |    válidas     
                          <18    |      >=18
```

> **Passo 5:** Crie um teste para cada partição. Como possuímos somente duas partições, então temos somente 2 casos de testes para a **regra de negócio 1**.

```
                               IDADE
                    _____________|________________
                      Inválidas  |    válidas     
                          <18    |      >=18
```

- **Caso de Teste 1:** Inputar o valor 17
  - **Resultado:** Menor de idade, não beber bebida alcoólica
- **Caso de Teste 2:** Inputar o valor 20
  - **Resultado:** Maior de idade, pode beber bebida alcoólica

**Obs.:** Os valores informados nos casos de testes são valores que estão respeitando os valores da partição. No **caso do teste 1** poderia ser qualquer valor menor que 18 e no **caso de teste 2** poderia ser qualquer valor maior ou igual a 18.

______

### **Regra de negócio 2**

Em uma academia para ser um associado é necessário que a pessoa tenha idade entre 16 a 60 anos de idade.

> **Passo 1:** Identificar a variável de entrada, logo ao ler a regra de negócio identificamos que a variável de entrada é "**IDADE**".

> **Passo 2:** Faça uma linha reta e informe o nome da variável de entrada definida, no caso "**IDADE**"

```
                              IDADE
            _________________________________________

```

> **Passo 3:** Faça os riscos para separar variáveis válidas e inválidas.

```
                               IDADE
            _____________|________________|_____________
              Inválidas  |    válidas     |  Inválidas  

```

> **Passo 4:**  Informe os valores das partições. Conforme a regra de negócio, somente pessoas entre 16 a 60 anos podem ser associados na academia.
> Logo nossa váriavel válida é >=16 e <=60, inválidas < 16 e >60.

```
                               IDADE
            _____________|________________|_____________
              Inválidas  |    válidas     |  Inválidas  
                 <16     | >=16  e  <=60  |     >60  

```
Ou você pode cria-lá assim:
```
                               IDADE
            _____________|________________|_____________
              Inválidas  |    válidas     |  Inválidas  
               0 a 15    |    16 a 60     |  61 ou mais  

```

> **Passo 5:** Crie um teste para cada partição. Para a **regra de negócio 2** temos **3 casos de testes**.
```
                               IDADE
            _____________|________________|_____________
              Inválidas  |    válidas     |  Inválidas  
                 <16     | >=16  e  <=60  |     >60  

```
Ou você pode cria-lá assim:
```
                               IDADE
            _____________|________________|_____________
              Inválidas  |    válidas     |  Inválidas  
               0 a 15    |    16 a 60     |  61 ou mais  

```

- **Caso de Teste 1:** informar a idade igual a 10
  - **Resultado:** Cliente **não pode** ser associado.
- **Caso de Teste 2:** informar a idade igual a 20
  - **Resultado:** Cliente **pode** ser associado.
- **Caso de Teste 3:** informar a idade igual a 65
  - **Resultado:** Cliente **não pode** ser associado.

____

### **Regra de negócio 3**

O valor dos produtos da loja são sempre maiores que zero e nunca devem ultrapassar R$ 7.000,00.

> **Passo 1:** Identificar a variável de entrada, logo ao ler a regra de negócio identificamos que a variável de entrada é "**VALOR DO PRODUTO**".

> **Passo 2:** Faça uma linha reta e informe o nome da variável de entrada definida, no caso "**VALOR DO PRODUTO**"

```
                      VALOR DO PRODUTO
____________________________________________________________

```

> **Passo 3:** Faça os riscos para separar variáveis válidas e inválidas.

```
                            VALOR DO PRODUTO
            _____________|___________________|_____________
              Inválidas  |       válidas     |  Inválidas  

```

> **Passo 4:**  Informe os valores das partições. Conforme a regra de negócio
> os valores **válidos** é R$ 0,01 até R$ 7.000,00 e os valores **inválidos** são menores que R$ 0,00 e 
> R$ 7.000,01 ou mais.

```
                        VALOR DO PRODUTO
__________________|________________________|________________
      Inválidas   |       válidas          |  Inválidas  
Menor que R$ 0,00 | R$ 0,01 até R$ 7.000,00| R$ 7.000,01 ou maior 

```

> **Passo 5:** Crie um teste para cada partição. Para a **regra de negócio 3** temos **3 casos de testes**.

```
                       VALOR DO PRODUTO
__________________|________________________|________________
      Inválidas   |       válidas          |  Inválidas  
Menor que R$ 0,00 | R$ 0,01 até R$ 7.000,00| R$ 7.000,01 ou maior 

```

- **Caso de Teste 1:** informar o valor R$ 0,00
  - **Resultado:** Valor do produto inválido
- **Caso de Teste 2:** informar o valor R$ 531,11
  - **Resultado:** Valor do produto válido
- **Caso de Teste 3:** informar o valor R$ 7.345,11
  - **Resultado:** Valor do produto inválido.

## Referências

- [Técnica de Teste — Particionamento de Equivalência](https://medium.com/revista-tspi/t%C3%A9cnica-de-teste-particionamento-de-equival%C3%AAncia-d32a7d689d82)
- [Julio de lima - Alavanque sua carreira em testes de software e aumente seu salário em mais de 30%](https://programa.juliodelima.com.br/)
- [Mais dicas de particionamento de equivalência](https://www.toolsqa.com/software-testing/istqb/equivalence-partitioning/)
