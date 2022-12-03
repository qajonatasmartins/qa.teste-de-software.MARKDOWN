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

**Regra de negócio 1:** No Brasil somente pessoas com 18 anos ou mais podem beber.

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