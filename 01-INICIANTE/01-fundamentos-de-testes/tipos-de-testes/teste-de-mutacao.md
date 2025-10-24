# Teste de Mutação

## História e Origem

### Contexto Histórico

O teste de mutação tem suas raízes no início da década de 1970, durante um período de intensa pesquisa em engenharia de software. O conceito foi originalmente proposto por **Richard Lipton** em um trabalho de estudante em 1971 (**Hints onTest Data Selection: Helpfor the Practicing Programmer**). A ideia foi posteriormente desenvolvida e formalizada em uma série de publicações influentes no final da década de 1970 por **Richard A. DeMillo**, **Richard J. Lipton** e **Frederick G. Sayward**.

O marco que transformou a teoria em prática foi a primeira implementação de uma ferramenta de teste de mutação, realizada por **Timothy Budd** como parte de sua tese de doutorado na Universidade de Yale em 1980. Esse trabalho pioneiro demonstrou a viabilidade da geração e execução automatizada de mutantes.

### A Filosofia por trás do Conceito

O surgimento do teste de mutação não foi um evento isolado. Ele ocorreu em um contexto acadêmico onde a verificação formal de programas - o processo de provar matematicamente a correção de um software - era um campo de pesquisa proeminente, mas cada vez mais visto como impraticável para sistemas de grande escala.

**DeMillo** e **Lipton**, dois dos pioneiros do teste de mutação, também foram coautores de um artigo seminal de 1979, "Social Processes and Proofs of Theorems and Programs", que lançou uma crítica poderosa sobre a escalabilidade e a aplicabilidade da verificação formal no mundo real.

Este ceticismo em relação à prova de correção absoluta criou um vácuo filosófico e prático: **se não podemos provar que os programas são corretos, como podemos obter confiança em sua confiabilidade?** A resposta proposta foi o teste rigoroso.

### A Questão Central: "Quis custodiet ipsos custodes?"

A base filosófica do teste de mutação pode ser resumida pela antiga questão latina: **"Quem vigia os vigias?"**. No contexto de software, se os testes unitários são os "vigias" que protegem a qualidade e a integridade do código, o teste de mutação é o mecanismo que garante que esses vigias sejam competentes, alertas e eficazes.

Uma cobertura de código de 100% pode ser enganosa; ela apenas confirma que cada linha de código foi executada, mas não diz nada sobre a qualidade das assertivas ou a capacidade dos testes de detectar erros lógicos sutis.

## Teoria: As Duas Hipóteses Fundamentais

O teste de mutação baseia-se em duas hipóteses fundamentais sobre a natureza da programação e dos defeitos de software:

### 1. Hipótese do Programador Competente (HPC)

Esta hipótese postula que a maioria dos programadores é competente e, como tal, escreve programas que estão "próximos" de serem corretos. Isso não significa que o código esteja livre de erros, mas que os erros presentes são tipicamente **pequenos e sintáticos**, em vez de falhas lógicas massivas.

**Exemplos de erros típicos:**

- Usar `>` em vez de `>=`
- Usar `+` em vez de `-`
- Trocar `&&` por `||`

A HPC justifica a metodologia do teste de mutação: se os bugs do mundo real são pequenos, então a introdução de pequenas falhas sintáticas (mutantes) é uma forma eficaz de simular os tipos de erros que os programadores provavelmente cometerão.

### 2. Efeito de Acoplamento (Coupling Effect)

Esta hipótese afirma que **falhas complexas são "acopladas" a falhas mais simples**. Em outras palavras, uma suíte de testes que é sensível o suficiente para detectar erros simples (ou seja, matar mutantes de primeira ordem) também será, por extensão, eficaz em detectar bugs mais complexos e do mundo real.

O Efeito de Acoplamento é crucial porque justifica o valor prático do teste de mutação. Ele implica que o esforço computacionalmente intensivo de testar milhares de mutantes simples não é um exercício acadêmico, mas uma estratégia altamente eficaz para construir uma suíte de testes robusta.

**Relação Simbiótica:** Essas duas hipóteses formam uma relação simbiótica que sustenta toda a disciplina:

- A **HPC** fornece o método: justificativa para criar mutantes através de pequenas alterações sintáticas
- O **Efeito de Acoplamento** fornece o valor: garantia de que matar mutantes simples tem impacto real na capacidade da suíte

## O que é Teste de Mutação?

Imagine que você tem uma suíte de testes para seu código e gostaria de saber: **"Quão bons são meus testes?"**. É aí que entra o **Teste de Mutação**!

O teste de mutação é uma técnica que **testa seus testes**, não o código em si. Ele cria versões "defeituosas" do seu código (chamadas de **mutantes**) e verifica se seus testes conseguem detectar esses defeitos artificiais.

### Analogia do Mundo Real

Pense no teste de mutação como um **simulado de emergência**:

- **Hospital:** Faz simulados de incêndio para testar se os procedimentos de evacuação funcionam
- **Teste de Mutação:** Introduz "bugs" artificiais para testar se seus testes conseguem detectá-los

Se o alarme de incêndio não tocar durante o simulado, há um problema no sistema de segurança. Se seus testes não falharem com bugs artificiais, há um problema na qualidade dos seus testes!

## Como Funciona?

### O Processo Básico

1. **Código Original:** Seu código de teste funcionando normalmente
2. **Criação de Mutantes:** Ferramenta modifica pequenas partes do código de teste
3. **Execução dos Testes:** Roda todos os testes contra cada mutante
4. **Análise dos Resultados:**
   - **Mutante "Morto":** Teste falhou (BOM! Teste detectou o problema)
   - **Mutante "Sobrevivente":** Teste passou (RUIM! Teste não detectou o problema)

### Exemplo Prático: Sistema de Login

**Código Original:**
```typescript
export function validarIdade(idade: number): boolean {
    if (idade >= 18) {  // Pessoa maior de idade
        return true;
    }
    return false;
}
```

**Mutantes Gerados:**
```typescript
// Mutante 1: Operador alterado
if (idade > 18) { ... }  // >= virou >

// Mutante 2: Valor alterado  
if (idade >= 21) { ... }  // 18 virou 21

// Mutante 3: Lógica invertida
if (idade < 18) { ... }  // >= virou <
```

**Teste Atual:**
```typescript
import { validarIdade } from './validarIdade'

test('Idade maior ou igual a 18', () => {
    expect(validarIdade(25)).toBe(true); // Passa para todos os mutantes
});
```

### Problema Detectado!

Nosso teste só verifica um caso (25 anos). Vamos ver o que acontece:

- **Mutante 1** (`> 18`): Passa (25 > 18 = true)
- **Mutante 2** (`>= 21`): Passa (25 >= 21 = true)  
- **Mutante 3** (`< 18`): Passa (25 < 18 = false, mas esperamos true!)

**Todos os mutantes sobreviveram!** Isso indica que nosso teste é insuficiente.

### Melhorando os Testes

```typescript
import { validarIdade } from './validarIdade'

test('Validação de idade com casos limite', () => {
    // Casos limite importantes
    expect(validarIdade(18)).toBe(true);    // Exatamente 18 - mataria Mutante 1
    expect(validarIdade(17)).toBe(false);   // Menor que 18 - mataria Mutante 3
    expect(validarIdade(19)).toBe(true);    // Maior que 18 - mataria Mutante 2
});
```

Agora sim! Com esses testes, todos os mutantes morreriam.

## Tipos de Mutações

### 1. Mutação de Operadores

**Operadores Aritméticos:**
```typescript
// Original
let resultado = a + b;

// Mutantes
resultado = a - b;  // + para -
resultado = a * b;  // + para *
resultado = a / b;  // + para /
```

**Operadores Relacionais:**
```typescript
// Original
if (x > 5) { /* ... */ }

// Mutantes  
if (x >= 5) { /* ... */ }  // > para >=
if (x < 5) { /* ... */ }   // > para <
if (x <= 5) { /* ... */ }  // > para <=
if (x === 5) { /* ... */ } // > para ==
```

### 2. Mutação de Valores

**Constantes Numéricas:**
```typescript
// Original
let limite = 100;

// Mutantes
limite = 101;  // 100 para 101
limite = 99;   // 100 para 99
limite = 0;    // 100 para 0
```

**Valores Booleanos:**
```typescript
// Original
return true;

// Mutante
return false;  // true para false
```

### 3. Mutação de Declarações

**Remoção de Linhas:**
```typescript
// Original
let x = calcularValor();
x = x + 10;  // Esta linha pode ser removida
return x;

// Mutante
let x = calcularValor();
// x = x + 10;  // Linha removida
return x;
```

## Exemplo Completo: Sistema de Desconto

### Código a ser Testado

```typescript
export class CalculadoraDesconto {
    calcularDesconto(valor: number, tipoCliente: string): number {
        if (valor <= 0) {
            return 0;
        }

        if (tipoCliente === "VIP") {
            return valor * 0.20;  // 20% de desconto
        } else if (tipoCliente === "PREMIUM") {
            return valor * 0.10;  // 10% de desconto
        }

        return 0;  // Cliente normal, sem desconto
    }
}
```

### Testes Iniciais (Insuficientes)

```typescript
import { CalculadoraDesconto } from './CalculadoraDesconto'

test('Desconto VIP', () => {
    const calc = new CalculadoraDesconto();
    const desconto = calc.calcularDesconto(100.0, "VIP");
    expect(desconto).toBeCloseTo(20.0, 2);
});
```

### Mutantes Gerados e Problemas

```typescript
// Mutante 1: Operador alterado
if (valor < 0) { ... } // <= virou <

// Mutante 2: Percentual alterado  
return valor * 0.25;  // 0.20 virou 0.25

// Mutante 3: String alterada
if (tipoCliente === "VIPP") { ... } // VIP virou VIPP

// Mutante 4: Condição invertida
if (tipoCliente !== "VIP") { ... }
```

**Problema:** Nosso teste atual passa para quase todos os mutantes! Precisamos de mais testes.

### Testes Melhorados

```typescript
import { CalculadoraDesconto } from './CalculadoraDesconto'

test('Descontos completos', () => {
    const calc = new CalculadoraDesconto();

    // Testa valor zero - mata Mutante 1
    expect(calc.calcularDesconto(0.0, "VIP")).toBeCloseTo(0.0, 2);

    // Testa VIP com valores diferentes - mata Mutante 2
    expect(calc.calcularDesconto(100.0, "VIP")).toBeCloseTo(20.0, 2);
    expect(calc.calcularDesconto(50.0, "VIP")).toBeCloseTo(10.0, 2);

    // Testa PREMIUM - mata Mutante 3
    expect(calc.calcularDesconto(100.0, "PREMIUM")).toBeCloseTo(10.0, 2);

    // Testa cliente normal - mata Mutante 4
    expect(calc.calcularDesconto(100.0, "NORMAL")).toBeCloseTo(0.0, 2);

    // Testa valor negativo
    expect(calc.calcularDesconto(-10.0, "VIP")).toBeCloseTo(0.0, 2);
});
```

## Métricas do Teste de Mutação

### Pontuação de Mutação

```
Pontuação de Mutação = (Mutantes Mortos / Total de Mutantes) x 100%
```

**Exemplo:**
- Total de mutantes gerados: 100
- Mutantes mortos pelos testes: 85
- Mutantes sobreviventes: 15
- **Pontuação: 85%**

### Interpretação das Pontuações

| Pontuação (%) | Qualidade dos Testes    | Ação Recomendada                        |
|:-------------:|:-----------------------|:----------------------------------------|
| 0–30          | Muito baixa             | Reescreva grande parte dos testes       |
| 31–60         | Baixa                   | Adicione muitos testes novos            |
| 61–80         | Moderada                | Melhore testes existentes               |
| 81–95         | Boa                     | Foque nos mutantes sobreviventes        |
| 96–100        | Excelente               | Mantenha a qualidade atual              |

## Ferramentas Populares

### Java: PIT (Pitest)

**Configuração Maven:**
```xml
<plugin>
    <groupId>org.pitest</groupId>
    <artifactId>pitest-maven</artifactId>
    <version>1.15.7</version>
    <configuration>
        <targetClasses>
            <param>com.exemplo.*</param>
        </targetClasses>
        <targetTests>
            <param>com.exemplo.testes.*</param>
        </targetTests>
    </configuration>
</plugin>
```

**Executar:**
```bash
mvn org.pitest:pitest-maven:mutationCoverage
```

### JavaScript: Stryker

**Instalação:**
```bash
npm init stryker@latest
```

**Executar:**
```bash
npx stryker run
```

### Python: mutmut

**Instalação:**
```bash
pip install mutmut
```

**Executar:**
```bash
mutmut run
```

**Ver resultados:**
```bash
mutmut results          # Lista sobreviventes
mutmut show 5           # Mostra mutante específico
mutmut apply 5          # Aplica mutação para criar teste
```

## Vantagens do Teste de Mutação

### 1. **Qualidade Real dos Testes**
- Vai além da cobertura de código
- Mede se os testes realmente detectam problemas
- Identifica "testes fake" que sempre passam

### 2. **Encontra Pontos Fracos**
- Mostra exatamente onde seus testes são insuficientes
- Cada mutante sobrevivente = oportunidade de melhoria
- Guia objetivo para escrever novos testes

### 3. **Confiança no Código**
- Alta pontuação = alta confiança na detecção de bugs
- Reduz medo de fazer mudanças (refatoração)
- Garante que regressões serão detectadas

### 4. **Educação da Equipe**
- Ensina a escrever testes melhores
- Desenvolve pensamento crítico sobre qualidade
- Cultura de teste mais madura

## Desafios e Soluções

### 1. **Performance**
**Problema:** Pode ser lento (muitos mutantes x muitos testes)

**Soluções:**
- **Execução seletiva:** Roda apenas testes que cobrem a linha mutada
- **Execução paralela:** Usa múltiplas threads/cores
- **Amostragem:** Testa apenas uma porcentagem dos mutantes

### 2. **Mutantes Equivalentes**
**Problema:** Mutações que não mudam o comportamento

```typescript
// Original
if (x > 5) { return true; }

// Mutante equivalente para números inteiros
if (x >= 6) { return true; }  // Mesmo comportamento!
```

**Solução:** Marcar como equivalente e ignorar nas métricas

### 3. **Custo Computacional**
**Problema:** Muitos mutantes = muito tempo de execução

**Estratégias:**
- **Execução noturna:** Roda análise completa durante a noite
- **Análise de diff:** Só testa código que mudou no PR
- **Quality gates:** Falha CI se pontuação diminuir

## Conceitos Avançados

### Mutação Forte vs. Fraca

- **Mutação Forte (tradicional):** Exige que a saída final do programa seja diferente
- **Mutação Fraca:** Exige apenas que o estado interno seja diferente imediatamente após a mutação

### Mutantes de Ordem Superior (HOMs)

Mutantes criados pela aplicação de múltiplos operadores de mutação simultaneamente, resultando em uma única versão do programa com várias falhas. Desafia a premissa do Efeito de Acoplamento.

## Boas Práticas para Iniciantes

### 1. **Comece Pequeno**
- Execute em um módulo pequeno primeiro
- Aprenda a interpretar os relatórios
- Ganhe experiência antes de expandir

### 2. **Foque nos Sobreviventes**
- Não se obceque com a pontuação final
- Cada mutante sobrevivente é uma lição
- Escreva teste específico para matá-lo

### 3. **Configure Timeouts**
```bash
# Evita loops infinitos
mutmut run --timeout-factor 2.0
```

### 4. **Use Configuração Incremental**
- Comece com operadores básicos
- Adicione complexidade gradualmente
- Monitore impacto na performance

### 5. **Integre com CI/CD**
```yaml
# GitHub Actions exemplo
- name: Mutation Testing  
  run: |
    npm run test:mutation
    # Falha se pontuação < 80%
```

## Quando NÃO Usar Teste de Mutação

### Situações Inadequadas:
- Projeto em fase inicial (código muito instável)
- Deadline muito apertado
- Testes muito lentos (sem otimização)
- Equipe sem experiência em testes básicos

### Momentos Ideais:
- Código estável com testes existentes
- Refatoração importante (garantir que testes protegem)
- Code review (verificar qualidade dos novos testes)
- Preparação para release crítico

## Exemplo Prático: E-commerce

### Cenário: Validação de Carrinho

```typescript
export type Item = {
    nome: string;
    preco: number;
    quantidade: number;
};

export class CarrinhoCompras {
    private valorMinimo: number = 50.0;

    podeFinalizarCompra(itens: Item[] | null): boolean {
        if (!itens || itens.length === 0) {
            return false;
        }

        let total = 0;
        for (const item of itens) {
            if (item.preco <= 0) {
                return false; // Item inválido
            }
            total += item.preco * item.quantidade;
        }

        return total >= this.valorMinimo;
    }
}
```

### Mutantes Típicos

```typescript
// Mutante 1: Valor mínimo alterado
private valorMinimo: number = 51.0; // 50.0 para 51.0

// Mutante 2: Operador de comparação
if (item.preco < 0) { /* ... */ } // <= para <

// Mutante 3: Operador final
return total > this.valorMinimo;  // >= para >

// Mutante 4: Condição de lista
if (!!itens || itens.length === 0) { /* ... */ } // && para ||
```

### Testes Completos

```typescript
import { CarrinhoCompras, Item } from './CarrinhoCompras'

describe('CarrinhoCompras', () => {
    let carrinho: CarrinhoCompras;

    beforeEach(() => {
        carrinho = new CarrinhoCompras();
    });

    test('Lista nula - mata Mutante 4', () => {
        expect(carrinho.podeFinalizarCompra(null)).toBe(false);
    });

    test('Lista vazia', () => {
        expect(carrinho.podeFinalizarCompra([])).toBe(false);
    });

    test('Item com preco zero - mata Mutante 2', () => {
        const itensInvalidos: Item[] = [
            { nome: 'Produto', preco: 0.0, quantidade: 1 }
        ];
        expect(carrinho.podeFinalizarCompra(itensInvalidos)).toBe(false);
    });

    test('Total exatamente no limite - mata Mutante 1 e 3', () => {
        const itensLimite: Item[] = [
            { nome: 'Produto', preco: 50.0, quantidade: 1 }
        ];
        expect(carrinho.podeFinalizarCompra(itensLimite)).toBe(true);
    });

    test('Total abaixo do limite', () => {
        const itensInsuficientes: Item[] = [
            { nome: 'Produto', preco: 49.99, quantidade: 1 }
        ];
        expect(carrinho.podeFinalizarCompra(itensInsuficientes)).toBe(false);
    });

    test('Total acima do limite', () => {
        const itensOk: Item[] = [
            { nome: 'Produto', preco: 75.0, quantidade: 1 }
        ];
        expect(carrinho.podeFinalizarCompra(itensOk)).toBe(true);
    });
});
```

## Integração com Pipelines de CI/CD

### Estratégias Comuns

**Execuções Noturnas:**
- Executar análise completa no branch principal durante a noite
- Fornece relatório diário sobre a saúde da suíte de testes

**Análise de Diferenças (Diff Analysis):**
- Configurar ferramenta para gerar mutantes apenas no código alterado
- Fornece feedback rápido e focado em pull requests

**Portões de Qualidade (Quality Gates):**
- Definir limite mínimo de pontuação de mutação
- Falha pipeline se pontuação diminuir em relação ao branch principal

### Interpretando Pontuações e Definindo Metas

Não existe um número mágico para uma "boa" pontuação de mutação. Embora 80% seja frequentemente citada como meta razoável, o valor real não está em atingir um número específico, mas em usar a análise como motor para melhoria contínua.

- **Pontuação baixa (30%):** Indica problemas sistêmicos na cultura de testes
- **Pontuação alta (95%):** Indica suíte de testes muito robusta
- **Foco principal:** Sempre na análise dos mutantes sobreviventes

## Conclusão

O teste de mutação é uma ferramenta muito boa, consequentemente, a confiabilidade do seu software.

**Principais takeaways:**

1. **Objetivo:** Testa a qualidade dos testes, não do código
2. **Funcionamento:** Cria bugs artificiais e verifica se testes os detectam  
3. **Métrica:** Pontuação de mutação (% de mutantes mortos)
4. **Valor real:** Cada mutante sobrevivente aponta uma melhoria específica
5. **Performance:** Ferramentas modernas são otimizadas e práticas

**Para QAs iniciantes:**

- Comece com projetos pequenos
- Foque em entender os mutantes sobreviventes
- Use como ferramenta de aprendizado, não apenas métrica
- Integre gradualmente no processo de desenvolvimento

O teste de mutação não substitui outros tipos de teste, mas **complementa** sua estratégia de qualidade, fornecendo uma visão única sobre a eficácia dos seus testes.

Lembre-se: **Um código com 100% de cobertura pode ter 0% de qualidade de testes**. O teste de mutação ajuda a distinguir cobertura real de cobertura ilusória!

## Referências

1. **DeMillo, R. A., Lipton, R. J., & Sayward, F. G. (1978).** "Hints on test data selection: Help for the practicing programmer." Computer, 11(4), 34-41.

2. **Budd, T. A. (1980).** "Mutation analysis of program test data." Tese de Doutorado, Universidade de Yale.

3. **Jia, Y., & Harman, M. (2011).** "An analysis and survey of the development of mutation testing." IEEE Transactions on Software Engineering, 37(5), 649-678.

4. **Howden, W. E. (1982).** "Weak mutation testing and completeness of test sets." IEEE Transactions on Software Engineering, (4), 371-379.

5. **DeMillo, R. A., Lipton, R. J., & Perlis, A. J. (1979).** "Social processes and proofs of theorems and programs." Communications of the ACM, 22(5), 271-280.

6. **PIT Mutation Testing:** https://pitest.org/

7. **Stryker Mutator:** https://stryker-mutator.io/

8. **mutmut - Python Mutation Tester:** https://mutmut.readthedocs.io/

9. **Mutation Testing - Wikipedia:** https://en.wikipedia.org/wiki/Mutation_testing

10. **"Java Mutation Testing Explained" - BellSoft:** https://bell-sw.com/blog/a-comprehensive-guide-to-mutation-testing-in-java/