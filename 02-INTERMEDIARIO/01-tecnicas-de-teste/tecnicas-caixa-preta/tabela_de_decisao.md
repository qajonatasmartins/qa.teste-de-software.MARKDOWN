# Decision Table Testing

Excelente para capturar e documentar regras de negócios complexas. Utiliza tabelas que cruzam combinações de condições de entrada com as ações esperadas do sistema.

## **Princípio básico**

As Tabelas de Decisão (Decision Tables) são uma excelente ferramenta para capturar requisitos e documentar o design interno de um sistema, representando regras de negócios complexas baseadas em um conjunto de condições. A estrutura divide-se em duas partes principais: **Condições** (que representam as várias entradas do sistema) e **Ações** (os processos que devem ser executados com base nessas entradas). Cada coluna na tabela é chamada de "Regra", e cada regra define uma combinação única de condições que resultará no disparo (*firing*) das ações associadas àquela regra.

## **Quando não usar**

Você não deve usar tabelas de decisão quando as ações do sistema dependerem de entradas anteriores ou do estado atual/histórico do sistema. Nestes casos em que o sistema precisa "lembrar" do que aconteceu antes ou possui uma ordem válida/inválida de operações, a técnica de Diagramas de Transição de Estado (*State-Transition Diagrams*) é a ferramenta adequada. Além disso, se o sistema não possuir regras de negócios complexas lógicas, a técnica pode ser desnecessária.

## **Quando usar**

O Teste de Tabela de Decisão deve ser usado sempre que o sistema precisar implementar **regras de negócios complexas**, desde que essas regras possam ser representadas como uma combinação de condições independentes e tenham ações discretas associadas a elas.

## **Como usar**

A utilização das tabelas de decisão para criar casos de teste é bastante direta:

- **Crie pelo menos um caso de teste para cada regra:** Cada coluna vertical da tabela se torna um caso de teste, onde as Condições especificam as entradas e as Ações especificam os resultados esperados. Para fazer isso, basta alterar os cabeçalhos da tabela, substituindo "Regra 1, Regra 2" por "Caso de Teste 1, Caso de Teste 2".
- **Tratamento de Condições:** Se a condição for binária (ex: Sim/Não), um único teste para cada combinação é suficiente. Se a condição for um intervalo de valores numéricos, recomenda-se combinar esta técnica com o Teste de Valor Limite (*Boundary Value Testing*), testando dados tanto na extremidade inferior quanto na superior do intervalo.
- **Evite Tabelas Colapsadas ("Don't Care"):** Frequentemente, analistas simplificam as tabelas agrupando condições que não afetam o resultado final e marcando-as como "DC" (*Don't Care* ou Não Importa). Embora seja bom para desenvolvedores escreverem menos código, **para testadores isso é perigoso**. O código pode ter sido escrito incorretamente, portanto, a tabela original (não-colapsada) deve ser sempre usada como base para a criação dos testes.

## **Exemplos práticos**

Na prática, o processo envolve transformar lógicas com múltiplos "If/Else" em uma matriz tabular. Se uma condição não for binária (por exemplo, "Idade < 5", "Idade = 5" ou "Idade > 7"), o testador não testa a palavra "Sim" ou "Não", mas seleciona **valores reais que satisfaçam a condição** (como 0, 5 ou 500) para criar seus casos de teste práticos e garantir que a ação correspondente seja disparada com precisão.

## 1. Descontos de Seguradora de Automóveis

Um exemplo introdutório onde uma seguradora dá descontos para motoristas baseados em duas condições binárias: *Casado?* (Sim/Não) e *Bom Estudante?* (Sim/Não). A combinação dessas condições gera 4 regras, cada uma disparando uma ação de desconto diferente ($60, $25, $50 ou $0).

### Método

```typescript
interface Motorista {
  casado: boolean;
  bomEstudante: boolean;
}

function calcularDescontoSeguro(motorista: Motorista): number {
  if (motorista.casado && motorista.bomEstudante) return 60;
  if (motorista.casado && !motorista.bomEstudante) return 25;
  if (!motorista.casado && motorista.bomEstudante) return 50;
  return 0;
}
```

### Testes gerados

```typescript
describe("calcularDescontoSeguro", () => {
  it("retornar desconto de $60 quando casado e bom estudante, regra 1", () => {
    const resultado = calcularDescontoSeguro({ casado: true, bomEstudante: true });

    expect(resultado).toBe(60);
  });

  it("retornar desconto de $25 quando casado e não bom estudante, regra 2", () => {
    const resultado = calcularDescontoSeguro({ casado: true, bomEstudante: false });

    expect(resultado).toBe(25);
  });

  it("retornar desconto de $50 quando solteiro e bom estudante, regra 3", () => {
    const resultado = calcularDescontoSeguro({ casado: false, bomEstudante: true });

    expect(resultado).toBe(50);
  });

  it("retornar desconto de $0 quando solteiro e não bom estudante, regra 4", () => {
    const resultado = calcularDescontoSeguro({ casado: false, bomEstudante: false });

    expect(resultado).toBe(0);
  });
});
```

### Tabela de decisão (não-colapsada)

| Condição / Ação | R1 | R2 | R3 | R4 |
|-----------------|----|----|----|----|
| Casado? | Sim | Sim | Não | Não |
| Bom Estudante? | Sim | Não | Sim | Não |
| **Desconto** | **$60** | **$25** | **$50** | **$0** |

---

## 2. Tabela Genérica com Condições Não-Binárias

Uma tabela abstrata mostrando o que fazer quando as opções não são apenas "Sim/Não". Por exemplo, a condição é avaliada em faixas matemáticas: "<5", "5", "6 ou 7", e ">7". Você deve extrair 4 casos de teste práticos atribuindo valores literais a essas faixas (como 0, 5, 50, 500) e checando as ações correspondentes.

### Método

```typescript
type FaixaValor = "abaixo" | "igual5" | "entre6e7" | "acima";

function classificarValor(valor: number): FaixaValor {
  if (valor < 5) return "abaixo";
  if (valor === 5) return "igual5";
  if (valor === 6 || valor === 7) return "entre6e7";
  return "acima";
}

function acaoPorFaixa(valor: number): string {
  const faixa = classificarValor(valor);
  switch (faixa) {
    case "abaixo": return "rejeitar";
    case "igual5": return "aceitar-nivel-1";
    case "entre6e7": return "aceitar-nivel-2";
    case "acima": return "aceitar-nivel-3";
  }
}
```

### Testes gerados

```typescript
describe("acaoPorFaixa", () => {
  it("rejeitar valor quando entrada é 0, representante da faixa <5, regra 1", () => {
    const resultado = acaoPorFaixa(0);

    expect(resultado).toBe("rejeitar");
  });

  it("retornar aceitar-nivel-1 quando entrada é 5, representante da faixa =5, regra 2", () => {
    const resultado = acaoPorFaixa(5);

    expect(resultado).toBe("aceitar-nivel-1");
  });

  it("retornar aceitar-nivel-2 quando entrada é 6, representante da faixa 6 ou 7, regra 3", () => {
    const resultado = acaoPorFaixa(6);

    expect(resultado).toBe("aceitar-nivel-2");
  });

  it("retornar aceitar-nivel-3 quando entrada é 500, representante da faixa >7, regra 4", () => {
    const resultado = acaoPorFaixa(500);

    expect(resultado).toBe("aceitar-nivel-3");
  });
});
```

### Tabela de decisão (não-colapsada)

| Condição / Ação | R1 | R2 | R3 | R4 |
|-----------------|----|----|----|----|
| Valor < 5 | Sim | Não | Não | Não |
| Valor = 5 | Não | Sim | Não | Não |
| Valor 6 ou 7 | Não | Não | Sim | Não |
| Valor > 7 | Não | Não | Não | Sim |
| **Representante** | **0** | **5** | **6** | **500** |
| **Ação** | **rejeitar** | **aceitar-nivel-1** | **aceitar-nivel-2** | **aceitar-nivel-3** |

---

## 3. Ordem de Compra de Ações (Estudo de Caso Brown & Donaldson - B&D)

Este exemplo foca na funcionalidade de aprovar uma ordem de compra na web. As condições são: *Símbolo Válido* (Sim/Não), *Quantidade Válida* (Sim/Não) e *Fundos Suficientes* (Sim/Não). A ação resultante é se o sistema deve executar a *Compra* (Sim/Não). Este exemplo é para demonstrar como as tabelas são "colapsadas" na programação usando condições de *Don't Care* (se o símbolo é inválido, não importa se há fundos, a compra será negada), alertando o testador para sempre testar a tabela com as 8 regras originais em vez da versão reduzida de 4 regras.

### Método

```typescript
interface ContextoCompra {
  simboloValido: boolean;
  quantidadeValida: boolean;
  fundosSuficientes: boolean;
}

function executarCompra(ctx: ContextoCompra): boolean {
  return ctx.simboloValido && ctx.quantidadeValida && ctx.fundosSuficientes;
}
```

### Testes gerados

```typescript
describe("executarCompra — tabela não-colapsada (8 regras)", () => {
  it("executar compra quando símbolo, quantidade e fundos são válidos, regra 1", () => {
    const resultado = executarCompra({ simboloValido: true, quantidadeValida: true, fundosSuficientes: true });

    expect(resultado).toBe(true);
  });

  it("rejeitar compra quando símbolo válido, quantidade válida e fundos insuficientes, regra 2", () => {
    const resultado = executarCompra({ simboloValido: true, quantidadeValida: true, fundosSuficientes: false });

    expect(resultado).toBe(false);
  });

  it("rejeitar compra quando símbolo válido, quantidade inválida e fundos suficientes, regra 3", () => {
    const resultado = executarCompra({ simboloValido: true, quantidadeValida: false, fundosSuficientes: true });

    expect(resultado).toBe(false);
  });

  it("rejeitar compra quando símbolo válido, quantidade inválida e fundos insuficientes, regra 4", () => {
    const resultado = executarCompra({ simboloValido: true, quantidadeValida: false, fundosSuficientes: false });

    expect(resultado).toBe(false);
  });

  it("rejeitar compra quando símbolo inválido, quantidade válida e fundos suficientes, regra 5", () => {
    const resultado = executarCompra({ simboloValido: false, quantidadeValida: true, fundosSuficientes: true });

    expect(resultado).toBe(false);
  });

  it("rejeitar compra quando símbolo inválido, quantidade válida e fundos insuficientes, regra 6", () => {
    const resultado = executarCompra({ simboloValido: false, quantidadeValida: true, fundosSuficientes: false });

    expect(resultado).toBe(false);
  });

  it("rejeitar compra quando símbolo inválido, quantidade inválida e fundos suficientes, regra 7", () => {
    const resultado = executarCompra({ simboloValido: false, quantidadeValida: false, fundosSuficientes: true });

    expect(resultado).toBe(false);
  });

  it("rejeitar compra quando símbolo inválido, quantidade inválida e fundos insuficientes, regra 8", () => {
    const resultado = executarCompra({ simboloValido: false, quantidadeValida: false, fundosSuficientes: false });

    expect(resultado).toBe(false);
  });
});
```

### Tabela de decisão (não-colapsada — 8 regras)

| Condição / Ação | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
|-----------------|----|----|----|----|----|----|----|-----|
| Símbolo Válido? | Sim | Sim | Sim | Sim | Não | Não | Não | Não |
| Quantidade Válida? | Sim | Sim | Não | Não | Sim | Sim | Não | Não |
| Fundos Suficientes? | Sim | Não | Sim | Não | Sim | Não | Sim | Não |
| **Executar Compra?** | **Sim** | **Não** | **Não** | **Não** | **Não** | **Não** | **Não** | **Não** |

> **Atenção:** Uma versão colapsada reduziria R5–R8 a "Símbolo inválido → Não compra (DC)". Teste sempre as 8 regras originais.

## Referências

- [A Practitioner's Guide to Software Test Design](https://amzn.to/4ejwIrl)
