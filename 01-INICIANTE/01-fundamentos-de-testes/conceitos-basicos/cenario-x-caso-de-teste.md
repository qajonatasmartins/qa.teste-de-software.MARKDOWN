# Cenário de Teste vs Caso de Teste: Diferenças Fundamentais

## 📋 Visão Geral

A diferença entre cenários de teste e casos de teste reside primariamente em seu **nível de detalhe** e sua **definição formal** dentro da disciplina de testes de software.

O termo "cenário de teste" (ou "condição de teste", que é o termo formalmente reconhecido) representa uma ideia ou aspecto do que deve ser testado, enquanto o "caso de teste" é o artefato detalhado que especifica exatamente como realizar esse teste.

## 🎯 Diferenças Conceituais

### Cenário de Teste (Condição de Teste)

O termo **cenário de teste** é uma terminologia que se popularizou na comunidade, mas **não possui uma fundamentação baseada na ISO 29119-1 ou no glossário da ISTQB**.

O que geralmente é popularizado como um cenário de teste é, formalmente, chamado de **Condição de Teste**.

#### Características da Condição de Teste:

1. **Conceito Central:** A condição de teste é uma **ideia do que testar**. É um aspecto testável de um componente ou sistema que é identificado com base na documentação do software disponível (base do teste).

2. **Natureza:** Representa uma **ideia de como avaliar** uma regra ou requisito. 
   - **Exemplo:** Se o requisito é "Transferência de valores entre clientes", uma condição de teste seria "Validar que o sistema é capaz de lidar com transferências inválidas".

3. **Hierarquia:** As condições de teste são criadas a partir de uma funcionalidade.

### Caso de Teste

#### Características do Caso de Teste:

1. **Conceito Central (ISTQB):** Um caso de teste é um artefato criado com base na condição de teste.

2. **Natureza:** Ele é uma **variação específica e detalhada** (combinação) de elementos (pré-condições, entradas, ações, etc.) que, quando executados, validam se a condição de teste funciona de maneira correta.

3. **Especificidade:** Um caso de teste é **específico**. Ele deve incluir os **dados exatos** a serem usados.
   - **Exemplo:** Para a condição "lidar com transferências inválidas", um caso de teste pode especificar: "Transferência para: não favorecido; saldo anterior: zero; limite do cheque especial: R$ 200,00; valor da transação: R$ 200,01".

## ⚠️ A Anomalia do Gherkin

Existe também uma confusão no mercado com a sintaxe **Gherkin** (usada em BDD), que utiliza a demarcação de "Cenário".

- Embora os cenários Gherkin (estruturados por *Dado que*, *Quando*, *Então*) possuam elementos que se assemelham aos casos de teste (pré-condições, ações e resultados esperados), **o uso de cenários Gherkin como casos de teste é considerado uma anomalia**.

- Os próprios criadores do BDD (incluindo Dan North e o criador do Cucumber) entendem que o Gherkin deve descrever **exemplos de regras**, e não casos de teste formais.

## 🏗️ Diferenças Estruturais

A principal diferença estrutural é que a Condição/Cenário de Teste é um **texto simples**, enquanto o Caso de Teste é um **documento estruturado e detalhado**.

### Estrutura do Cenário de Teste (Condição de Teste)

A condição de teste é tipicamente descrita como um **texto simples, um título ou um header**, representando a ideia do que testar.

**Exemplo:** 
- "Validar situações de transferência fazendo o uso de limite"

### Estrutura do Caso de Teste

Os casos de teste são artefatos que exigem um conjunto de componentes estruturados. Diferentes padrões e ferramentas definem o template do caso de teste de maneiras variadas.

| Fonte/Padrão | Componentes Estruturais |
|:-------------|:------------------------|
| **ISTQB** | Pré-condições, Entradas, Ações, Resultados Esperados e Pós-condições |
| **ISO 29119-3** | ID, Objetivo (Título), Prioridade, Rastreabilidade (à condição de teste), Pré-condições, Entradas e Resultados Esperados |
| **TestLink** | ID, Título, Resumo (que pode cobrir Ações e Entradas), Pré-condições, Status, Importância, Tipo de Execução, Tempo Estimado de Execução e Palavras-chave |

## 📝 Exemplo de Estrutura Detalhada (ISO 29119-3)

Um caso de teste, seguindo o padrão ISO 29119-3, deve conter:

### Componentes Obrigatórios:
- **ID:** Identificador único
- **Prioridade:** Define a ordem de execução se houver vários testes (Alta, Média, Baixa)
- **Rastreabilidade:** Indica qual Condição de Teste originou este Caso de Teste
- **Objetivo:** O título do caso de teste
- **Pré-condições:** Condições que devem ser atendidas antes da execução
- **Entradas:** Os dados ou passos a serem aplicados
- **Resultados Esperados:** O que deve acontecer após a ação

### Exemplo Prático:

**Condição de Teste:** "Validar transferências que excedem o limite disponível"

**Caso de Teste Derivado:**
- **ID:** CT001
- **Prioridade:** Alta
- **Rastreabilidade:** Condição_Transferencia_Limites
- **Objetivo:** Validar transferência que excede saldo + limite
- **Pré-condições:** Tenho saldo de R$ 5.000,01
- **Entradas:** Escolher um destinatário que não foi favorecido; transferir o valor de R$ 5.000,01
- **Resultados Esperados:** O usuário é avisado que o valor excede o limite e a transação não é realizada

## 🔍 Comparação Resumida

| Aspecto | Condição de Teste (Cenário) | Caso de Teste |
|---------|----------------------------|---------------|
| **Complexidade** | Simples (texto/título) | Complexo (estruturado) |
| **Objetivo** | Define "O QUE" testar | Define "COMO" testar |
| **Detalhamento** | Alto nível, abstrato | Específico, detalhado |
| **Dados** | Não especifica dados | Especifica dados exatos |
| **Estrutura** | Informal | Formal e padronizada |
| **Fundamentação** | Termo popular (não formal) | Baseado em ISTQB/ISO |
| **Execução** | Não executável diretamente | Executável |

## 📚 Conclusão

A diferença é **substancial**: a **Condição de Teste (Cenário)** é apenas a ideia resumida do que testar, enquanto o **Caso de Teste** é o conjunto detalhado e formalmente estruturado de passos e dados necessários para executar e validar essa ideia.

### Pontos Importantes:
- ✅ Use a terminologia correta: "Condição de Teste" em vez de "Cenário de Teste"
- ✅ Entenda que casos de teste derivam de condições de teste
- ✅ Gherkin descreve exemplos de regras, não casos de teste formais
- ✅ Casos de teste devem seguir padrões estruturados (ISTQB/ISO)

---

**📖 Referências Técnicas:**
- ISTQB Foundation Level Syllabus
- ISO/IEC/IEEE 29119-3 (Test Documentation)
- Glossário ISTQB de Termos de Teste
- [Descobrindo a Diferença entre Cenários de Testes e Casos de Testes](https://www.youtube.com/watch?v=bN4JvSxaYwQ)
- [Desvendando os Segredos de Cenários Práticos e Casos de Teste](https://www.youtube.com/watch?v=ay2MqCzYyvY&t=3s)