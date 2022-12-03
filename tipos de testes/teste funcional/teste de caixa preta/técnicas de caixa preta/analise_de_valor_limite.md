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

Se usarmos a técnica de particionamento de equivalência podemos achar ou não o problema, pois não necessáriamente iriámos informar um valor das extremidades o que é um problema.

Para solucionar esse problema, usamos a técnica de análise de valor limite que avalia as extremidades da nossa regra de negócio e dado a regra de negócio acima, o erro seria identificado e reportado ao desenvolvedor.