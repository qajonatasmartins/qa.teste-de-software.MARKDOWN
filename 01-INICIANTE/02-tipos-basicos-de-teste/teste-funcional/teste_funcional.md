# Testes Funcionais: Conceitos e Aplicação Prática

## 📋 Definição

O **teste funcional** de um sistema envolve testes que avaliam as funções que o sistema deve executar. Os requisitos funcionais podem ser descritos em produtos de trabalho, como especificações de requisitos, de negócios, épicos, histórias de usuários, casos de uso ou especificações funcionais, podendo ainda não estarem documentados. 

As funções são **"o que"** o sistema deve fazer, focando no comportamento observável do software.

## 🎯 Características Principais

### Baseado em Especificações

- ✅ Verifica se o sistema atende aos requisitos funcionais
- ✅ Foca no comportamento externo (caixa-preta)
- ✅ Independe da implementação interna
- ✅ Testa a perspectiva do usuário final

### Conhecimento Especializado

O projeto e a execução de testes funcionais podem envolver habilidades ou conhecimentos especiais, como:
- 🏢 Conhecimento específico de um problema de negócios
- 🎯 Compreensão do papel que o software desempenha
- 📋 Domínio das regras de negócio aplicáveis

## 📊 Fundamentação Técnica (ISO 25010)

Os testes funcionais de um sistema avaliam a característica de **Adequação Funcional** descrita na norma ISO 25010. 

> **Importante**: Segundo a ISO 25010 atualizada, existem 9 características de qualidade de software: "Adequação funcional" corresponde ao teste funcional, enquanto as demais 8 características são os testes não funcionais.

![ISO 25010](https://iso25000-com.translate.goog/images/figures/iso_25010_en.png?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc)

## 🔍 Adequação Funcional (ISO 25010)

Essa característica representa o grau em que um produto ou sistema fornece funções que atendem às necessidades declaradas e implícitas quando usadas em condições especificadas.

### Sub-características

#### 1. Completude Funcional

**Definição**: Grau em que o conjunto de funções abrange todas as tarefas e objetivos do usuário especificados.

**Exemplo Prático**

```
Sistema de E-commerce deve ter:
✅ Cadastro de produtos
✅ Carrinho de compras  
✅ Processo de pagamento
✅ Acompanhamento de pedidos
❌ Se faltar qualquer função, há problema de completude
```

#### 2. Correção Funcional

**Definição**: Grau em que um produto ou sistema fornece os resultados corretos com o grau de precisão necessário.

**Exemplo Prático**:

```
Calculadora deve:
✅ 2 + 3 = 5 (correto)
❌ 2 + 3 = 6 (incorreto - problema de correção)

Sistema bancário deve:
✅ Transferência de R$ 100,00 debita exatamente R$ 100,00
❌ Se debitar R$ 99,99 ou R$ 100,01 = problema de correção
```

#### 3. Adequação Funcional

**Definição**: Grau em que as funções facilitam a realização de tarefas e objetivos especificados.

**Exemplo Prático**:
```
Sistema de vendas deve ter:
✅ Busca rápida de produtos
✅ Filtros úteis (preço, categoria, marca)
✅ Comparação entre produtos
❌ Se for difícil encontrar produtos = problema de adequação
```

## 📝 Exemplos Práticos para Iniciantes

### Exemplo 1: Sistema de Login

**Funcionalidades a testar**:

``` text
Cenário: Login com credenciais válidas
Dado que: Usuário cadastrado existe
Quando: Inserir email e senha corretos
Então: Sistema deve autenticar e direcionar ao painel

Cenário: Login com senha incorreta  
Dado que: Usuário cadastrado existe
Quando: Inserir email correto e senha incorreta
Então: Sistema deve exibir "Credenciais inválidas"
```

### Exemplo 2: Carrinho de Compras

**Funcionalidades a testar**:

``` text
Teste: Adicionar produto
Entrada: Produto ID=123, Quantidade=2
Resultado Esperado: Carrinho mostra 2 unidades do produto

Teste: Calcular total
Entrada: Produto R$ 50,00 x 2 unidades  
Resultado Esperado: Total = R$ 100,00

Teste: Aplicar desconto
Entrada: Total R$ 100,00 + Cupom 10%
Resultado Esperado: Total final = R$ 90,00
```

## 🛠️ Técnicas de Teste Funcional

### 1. Particionamento de Equivalência

**Conceito**: Divide dados em grupos que devem ter comportamento similar.

**Exemplo**:

``` text
Campo "Idade" (aceita 18-65 anos):
• Classe válida: 18 ≤ idade ≤ 65
• Classe inválida 1: idade < 18  
• Classe inválida 2: idade > 65

Testes: 17 (inválida), 25 (válida), 70 (inválida)
```

### 2. Análise de Valor Limite

**Conceito**: Testa valores nas bordas das classes.

**Exemplo**:

``` text
Para campo "Idade" (18-65):
Valores limite: 17, 18, 19, 64, 65, 66
```

### 3. Tabela de Decisão

**Conceito**: Mapeia condições para ações.

**Exemplo - Aprovação de Empréstimo**:

| Renda > R$ 5000 | Score > 600 | Resultado |
|:----------------:|:-----------:|:---------:|
| Sim | Sim | Aprovado |
| Sim | Não | Análise manual |
| Não | Sim | Negado |
| Não | Não | Negado |

## ✅ Vantagens dos Testes Funcionais

- 🎯 **Perspectiva do usuário**: Testa como o usuário realmente usa
- 📋 **Baseado em requisitos**: Verifica especificações documentadas  
- 🔄 **Reproduzível**: Pode ser executado múltiplas vezes
- 🏷️ **Rastreável**: Liga defeitos aos requisitos específicos

## ⚠️ Limitações dos Testes Funcionais

- 🚫 **Não testa estrutura interna**: Não verifica qualidade do código
- 🚫 **Não testa performance**: Não avalia velocidade ou carga
- 🚫 **Não testa usabilidade**: Não verifica facilidade de uso
- 🚫 **Não testa segurança**: Não foca em vulnerabilidades

## 🔗 Tipos de Teste Funcional por Nível

### Teste de Unidade (Funcional)

- Testa funções/métodos individuais
- **Exemplo**: Testar função `calcularImposto(valor)`

### Teste de Integração (Funcional)

- Testa interação entre módulos
- **Exemplo**: Testar integração Carrinho + Pagamento

### Teste de Sistema (Funcional)

- Testa o sistema completo
- **Exemplo**: Testar fluxo completo de compra

### Teste de Aceite (Funcional)

- Verifica se atende necessidades do usuário
- **Exemplo**: Cliente valida se sistema atende suas regras de negócio

## 📚 Conclusão

Os testes funcionais são essenciais para verificar se o software faz o que deveria fazer. Eles garantem que as funcionalidades atendem aos requisitos especificados e proporcionam a experiência esperada pelo usuário.

### Pontos-chave para iniciantes:

- ✅ Foque no comportamento externo do sistema
- ✅ Use os requisitos como base para criar testes
- ✅ Teste tanto cenários positivos quanto negativos
- ✅ Documente claramente os casos de teste
- ✅ Combine com testes não funcionais para cobertura completa

---

## 📖 Referências

- **ISTQB Foundation Level Syllabus v4.0** - [BSTQB](https://bstqb.online/files/syllabus_ctfl_4.0br.pdf)
- **ISO/IEC 25010:2011** - [ISO 25010 Portal](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010)
- [Diferença entre fases de teste, tipos de teste e formas de execução](https://www.zup.com.br/blog/fases-de-teste-tipos-de-teste)
- **ISTQB Glossary** - Definições oficiais de termos de teste
