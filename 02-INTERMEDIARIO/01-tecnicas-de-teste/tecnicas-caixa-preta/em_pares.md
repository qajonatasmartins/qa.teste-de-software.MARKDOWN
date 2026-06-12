# Pairwise Testing

Empregado quando o sistema tem muitas variáveis e a combinação de todas elas geraria um número impossível de testes. Ele foca em testar todas as combinações em pares, reduzindo drasticamente o esforço de teste.

## **Princípio básico**

A técnica baseia-se na ideia de testar apenas as combinações de todos os *pares* possíveis de variáveis, em vez de tentar testar de forma exaustiva todas as combinações possíveis do sistema. Isso funciona porque a maioria dos defeitos de software costuma ser de "modo único" (uma funcionalidade falha independentemente) ou de "modo duplo" (a interação exclusiva entre duas funções ou módulos resulta na falha). Ao assegurar que cada par seja exercitado ao menos uma vez, é possível localizar a grande maioria dos problemas usando uma fração minúscula de esforço.

## **Quando não usar**

Você não deve depender exclusivamente de testes Pairwise se você ou os desenvolvedores tiverem consciência de que combinações específicas (mesmo triplas ou maiores) são muito utilizadas na prática ou envolvem riscos críticos. Por exemplo, uma configuração ou fluxo que acione um cenário do tipo "desligue o reator nuclear" deve obrigatoriamente funcionar. Caso as ferramentas de geração em pares não selecionem essas interações específicas no subconjunto, você não deve deixar de testá-las. A recomendação é usar o Pairwise e *adicionar manualmente* os casos de risco ou de uso frequente. Além disso, se o número de combinações for suficientemente pequeno, pode-se simplesmente testar tudo.

## **Quando usar**

A técnica deve ser usada em situações onde há múltiplas variáveis que assumem diversos valores diferentes e causam uma grande "explosão combinatória", resultando em uma quantidade de cenários impossível de se cobrir devidos às limitações de tempo e recursos da equipe.

## **Como usar**

O processo de criação de testes Pairwise geralmente envolve as seguintes etapas:

1. Identifique as variáveis do sistema e determine os possíveis valores/opções que cada uma pode assumir.
2. Como não é viável encontrar todos os pares de cabeça, utiliza-se métodos consolidados para gerar a lista de testes, como os **Arrays Ortogonais** (matrizes bidimensionais matemáticas prontas encontradas em catálogos), ou ferramentas computacionais de lógica desbalanceada baseadas no **Algoritmo Allpairs**.
3. Mapeie o seu problema do mundo real para dentro da matriz escolhida, substituindo as colunas pelas variáveis e os números internos pelos valores reais do software.
4. Se usar Arrays Ortogonais e a matriz ficar com "células sobrando", complemente com valores válidos para não perder a ortogonalidade.
5. Construa os casos de teste finais baseado nas linhas da tabela gerada. Note que a matriz fornece apenas os parâmetros de entrada; você, atuando como o "oráculo" de testes, precisará determinar o resultado esperado de cada cenário de teste.

## **Exemplos práticos**

Na prática, testadores evitam gerar combinações complexas sozinhos e se apoiam em ferramentas. Um analista poderia usar uma ferramenta da web, como o programa *Allpairs* de James Bach (onde se insere os dados numa planilha, exporta em .txt e o programa cospe apenas os testes a fazer), ou ferramentas focadas em Arrays Ortogonais (como o rdExpert ou o catálogo de Neil J.A. Sloane). Durante a utilização prática, o testador também precisa lidar com restrições lógicas do ambiente. Por exemplo, a matriz matemática pode pedir para testar um servidor IIS com o MacOS (incompatíveis). O testador mapeia essa restrição em ferramentas mais potentes (como rdExpert ou AETG) que irão gerar os pares de forma inteligente sem ferir as limitações físicas conhecidas do projeto.

### **Problema dos Navegadores Web**

Um site precisava ser testado com 8 navegadores, 3 plug-ins, 6 SOs clientes, 3 servidores web e 3 SOs de servidor, chegando a **1.296 combinações**. Utilizando a ferramenta de Arrays Ortogonais (usando um L64), os testes caíram para apenas **64** (redução de 95%). O mesmo problema jogado no Algoritmo Allpairs diminuiu ainda mais o conjunto, exigindo apenas **48 testes** (uma economia adicional de 25%).

> **Adaptação didática:** reduzimos a 4 variáveis com 3 valores cada (81 → 9 testes pairwise) para demonstrar a mecânica sem repetir 48 casos idênticos em markdown.

### Método

```typescript
interface ConfigWeb {
  browser: "chrome" | "firefox" | "safari";
  plugin: "flash" | "java" | "none";
  clientOs: "windows" | "mac" | "linux";
  server: "apache" | "nginx" | "iis";
}

function validarConfigWeb(config: ConfigWeb): boolean {
  if (config.server === "iis" && config.clientOs === "mac") return false;
  return true;
}
```

### Testes gerados (matriz all-pairs — 9 casos)

```typescript
const casosPairwiseWeb: ConfigWeb[] = [
  { browser: "chrome",  plugin: "flash", clientOs: "windows", server: "apache" },
  { browser: "chrome",  plugin: "java",  clientOs: "mac",     server: "nginx"  },
  { browser: "chrome",  plugin: "none",  clientOs: "linux",  server: "iis"    },
  { browser: "firefox", plugin: "flash", clientOs: "mac",     server: "nginx"  },
  { browser: "firefox", plugin: "java",  clientOs: "linux",  server: "iis"    },
  { browser: "firefox", plugin: "none",  clientOs: "windows", server: "apache" },
  { browser: "safari",  plugin: "flash", clientOs: "linux",  server: "iis"    },
  { browser: "safari",  plugin: "java",  clientOs: "windows", server: "nginx"  },
  { browser: "safari",  plugin: "none",  clientOs: "mac",     server: "apache" },
];

describe("validarConfigWeb — navegadores (pairwise)", () => {
  casosPairwiseWeb.forEach((config, i) => {
    it(`validar configuração web do caso pairwise ${i + 1}`, () => {
      const resultado = validarConfigWeb(config);

      expect(typeof resultado).toBe("boolean");
    });
  });
});
```

### Tabela all-pairs (amostra)

| Caso | Browser | Plugin | Client OS | Server |
|------|---------|--------|-----------|--------|
| 1 | chrome | flash | windows | apache |
| 2 | chrome | java | mac | nginx |
| 3 | firefox | none | linux | iis |
| … | … | … | … | … |

> 81 combinações exaustivas → **9 testes pairwise** (cada par de colunas aparece ao menos uma vez).

## Referências

- [A Practitioner's Guide to Software Test Design](https://amzn.to/4ejwIrl)
- [Testes em pares](https://bstqb.org.br/b9/doc/syllabus_ctal_ta_3.1.1br.pdf#page=39&zoom=100,53,134)