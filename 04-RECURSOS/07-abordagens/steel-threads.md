# Abordagem do Steel Threads para Testes de Software

## 📋 Visão Geral

Imagine que você precisa testar um sistema complexo com centenas de funcionalidades. Por onde começar? O que é mais importante?

Um **Steel Thread** (Fio de Aço) é o caminho mais crítico que percorre todo o sistema, de ponta a ponta. É como uma linha forte de aço que conecta as partes mais importantes do sistema. Se esse caminho quebrar, o sistema não funciona.

**Definição:** Um Steel Thread é um conjunto de cenários logicamente agrupados que identifica um caminho de execução de ponta a ponta através do sistema para atingir objetivos de negócio e demonstrar que a arquitetura funciona.

## 🎯 O Que é um Steel Thread?

### Características Principais

1. **Foca apenas no fluxo principal** - Ignora cenários alternativos e de exceção
2. **Percorre todo o sistema** - De uma ponta até a outra, passando por todas as camadas
3. **Valida a arquitetura** - Prova que o sistema funciona antes de construir tudo
4. **Mitiga riscos** - Identifica e resolve problemas técnicos no início

### Objetivos

- ✅ **Mitigar riscos técnicos** - Validar tecnologias e integrações antes de construir tudo
- ✅ **Demonstrar funcionalidade crítica** - Provar que o essencial funciona
- ✅ **Estabelecer fundação sólida** - Criar base para o restante do sistema

## 🔍 Steel Threads vs. Requisitos

| Aspecto | Requisitos / Casos de Uso | Steel Threads |
| :------ | :------------------------ | :------------- |
| **Escopo** | Todas as funcionalidades (principal, alternativo, exceção) | Apenas fluxo principal |
| **Propósito** | Descrever "o que" o sistema faz | Validar arquitetura e riscos |
| **Detalhe** | Muito detalhado | Minimalista e focado |
| **Quando** | Todo o desenvolvimento | Início do projeto |

**Resumo:** Steel Threads são um subconjunto dos requisitos - os mais importantes que validam a arquitetura.

## 🏗️ Como Montar um Steel Thread

O processo de criação de um Steel Thread segue estes passos:

```mermaid
flowchart TD
    A[Identificar Riscos Técnicos] --> B[Definir Objetivos de Negócio]
    B --> C[Agrupar Cenários]
    C --> D[Validar Steel Thread]
    D --> E{Atende aos Objetivos?}
    E -->|Não| C
    E -->|Sim| F[Steel Thread Definido]
    
    A1[Integrações<br/>Performance<br/>Segurança<br/>Disponibilidade] -.-> A
    B1[Demonstrar funcionalidade básica<br/>Criar framework fundamental<br/>Validar integrações] -.-> B
    C1[Cenário 1 → Cenário 2 → Cenário 3<br/>Fluxo de ponta a ponta] -.-> C
```

### Passo a Passo

**1. Identificar Riscos Técnicos**
- Liste os principais riscos do projeto
- Exemplos: integração com sistemas externos, desempenho, segurança
- Pergunta: "O que pode dar errado tecnicamente?"

**2. Definir Objetivos de Negócio**
- O que o Steel Thread precisa demonstrar?
- Exemplos: "Cliente completa compra", "Sistema processa pagamento"
- Pergunta: "Qual funcionalidade crítica precisa funcionar?"

**3. Agrupar Cenários**
- Conecte cenários que formam um caminho completo
- Apenas fluxo principal, sem alternativas
- Exemplo: "Cliente faz pedido → Sistema calcula → Processa pagamento → Envia"

**4. Validar**
- O Steel Thread mitiga os riscos identificados?
- Demonstra a funcionalidade crítica?
- Se não, volte ao passo 3

## ⏰ Quando Usar?

**Use quando:**
- ✅ Início de projeto para validar arquitetura
- ✅ Sistema com integrações externas complexas
- ✅ Projetos com múltiplos fornecedores
- ✅ Alto risco técnico (performance, segurança, disponibilidade)

**Não use quando:**
- ❌ Projeto muito simples
- ❌ Sistema já em produção e estável
- ❌ Refatorações menores

## 📝 Exemplos Práticos

### Exemplo 1: Livraria Online

**Risco:** Integração com sistemas externos (faturamento, pagamento, envio)

**Fluxo Completo de Compra:**

```mermaid
flowchart TD
    Start([Cliente acessa livraria]) --> CheckAccount{Cliente tem conta?}
    CheckAccount -->|Não| CreateAccount[Cria nova conta]
    CreateAccount --> BrowseBooks[Navega e seleciona livros]
    CheckAccount -->|Sim| BrowseBooks
    
    BrowseBooks --> AddToCart[Adiciona livros ao carrinho]
    AddToCart --> CheckStock{Verifica estoque}
    CheckStock -->|Sem estoque| StockError([Erro: Produto sem estoque])
    CheckStock -->|Com estoque| ProceedCheckout[Prossegue para checkout]
    
    ProceedCheckout --> ValidateAddress{Valida endereço de entrega}
    ValidateAddress -->|Endereço inválido| AddressError([Erro: Endereço inválido])
    ValidateAddress -->|Endereço válido| MakeOrder[Cliente faz pedido de livros]
    
    MakeOrder --> BillingSystem[Sistema de faturamento calcula conta final]
    BillingSystem --> PaymentSystem{Sistema de cartão de crédito processa pagamento}
    PaymentSystem -->|Pagamento recusado| PaymentError([Erro: Pagamento recusado])
    PaymentSystem -->|Erro na conexão| PaymentNetworkError([Erro: Falha na conexão com gateway])
    PaymentSystem -->|Pagamento aprovado| ShippingSystem[Sistema de envio recebe notificação]
    ShippingSystem --> Dispatch[Despacha os itens]
    Dispatch --> Success([Pedido concluído com sucesso])
```

**Steel Thread Identificado (Caminho Principal em Vermelho):**

O Steel Thread para este fluxo de compra é apenas o **caminho de sucesso** que valida todas as integrações críticas:

```mermaid
flowchart TD
    Start([Cliente acessa livraria]) --> BrowseBooks[Navega e seleciona livros]
    BrowseBooks --> AddToCart[Adiciona livros ao carrinho]
    AddToCart --> MakeOrder[Cliente faz pedido de livros]
    MakeOrder --> BillingSystem[Sistema de faturamento calcula conta final]
    BillingSystem --> PaymentSystem{Sistema de cartão de crédito processa pagamento}
    PaymentSystem -->|Pagamento aprovado| ShippingSystem[Sistema de envio recebe notificação]
    ShippingSystem --> Dispatch[Despacha os itens]
    Dispatch --> Success([Pedido concluído com sucesso])
    
    style Start fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style BrowseBooks fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style AddToCart fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style MakeOrder fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style BillingSystem fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style PaymentSystem fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style ShippingSystem fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style Dispatch fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style Success fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
```

**Steel Thread:**
1. Cliente acessa livraria
2. Navega e seleciona livros
3. Adiciona livros ao carrinho
4. Cliente faz pedido de livros
5. Sistema de faturamento calcula conta final
6. Sistema de cartão de crédito processa pagamento (aprovado)
7. Sistema de envio recebe notificação
8. Despacha os itens
9. Pedido concluído com sucesso

**O que é ignorado (não faz parte do Steel Thread):**
- ❌ Criação de nova conta
- ❌ Verificação de estoque
- ❌ Validação de endereço de entrega
- ❌ Tratamento de erro de pagamento recusado
- ❌ Tratamento de erro de conexão com gateway
- ❌ Tratamento de erro de estoque insuficiente

**Por quê?** Valida todas as integrações críticas de uma vez (faturamento, pagamento e envio) sem se preocupar com validações e tratamentos de erro que podem ser implementados depois.

### Exemplo 2: Sistema de Controle de Tráfego Aéreo (ATC)

**Riscos identificados:**
- Sistema pode não atender expectativas dos controladores
- Alta disponibilidade requerida (menos de 5 minutos de downtime por ano)
- Concorrência (até 2400 aeronaves simultâneas)
- Múltiplos fornecedores desenvolvendo componentes

**Steel Threads criados:**
- **ST1:** Aquisição de dados de radar e visualização na tela
- **ST2:** Transferência de controle entre setores
- **ST3:** Funcionalidade de replay (valida logging)
- **ST4:** Arquivamento quando aeronave sai da área

**Fluxo Completo - ST1: Aquisição de Dados de Vigilância:**

```mermaid
flowchart TD
    Start([Sistema inicializado e em operação]) --> MonitorRadar[Monitora dados dos equipamentos de vigilância]
    MonitorRadar --> CheckData{Dados detectados?}
    CheckData -->|Erro de comunicação| CommError([Erro: Falha na comunicação com equipamento])
    CheckData -->|Dados inválidos| InvalidData([Erro: Dados inválidos recebidos])
    CheckData -->|Sim| ProcessData[Processa dados de vigilância]
    
    ProcessData --> CheckFailover{Failover necessário?}
    CheckFailover -->|Sim| SwitchToSecondary[Falha para host secundário]
    SwitchToSecondary --> ProcessData
    CheckFailover -->|Não| DisplayRadar[Exibe dados na tela em vista de plano]
    
    DisplayRadar --> CheckFlightPlan{Plano de voo disponível?}
    CheckFlightPlan -->|Não| DisplayRadarOnly[Exibe apenas dados de radar]
    CheckFlightPlan -->|Sim| DisplayWithPlan[Exibe dados de radar e plano de voo]
    
    DisplayWithPlan --> ControllerAccess[Controlador acessa plano de voo]
    ControllerAccess --> MonitorSeparation[Controlador monitora separação segura]
    
    MonitorSeparation --> CheckSectorChange{Aeronave muda de setor?}
    CheckSectorChange -->|Sim| MigrateData[Migra dados para exibição do setor correspondente]
    MigrateData --> MonitorSeparation
    
    CheckSectorChange -->|Não| CheckAreaExit{Aeronave sai da área?}
    CheckAreaExit -->|Sim| ArchiveData[Arquiva dados da aeronave]
    ArchiveData --> RemoveDisplay[Remove da exibição do controlador]
    CheckAreaExit -->|Não| MonitorSeparation
```

**Steel Thread Identificado - ST1 (Caminho Principal em Vermelho):**

O Steel Thread para aquisição de dados de vigilância é apenas o **caminho de sucesso** que valida a arquitetura básica:

```mermaid
flowchart TD
    Start([Sistema inicializado e em operação]) --> MonitorRadar[Monitora dados dos equipamentos de vigilância]
    MonitorRadar --> ProcessData[Processa dados de vigilância]
    ProcessData --> DisplayRadar[Exibe dados na tela em vista de plano]
    DisplayRadar --> DisplayWithPlan[Exibe dados de radar e plano de voo]
    DisplayWithPlan --> ControllerAccess[Controlador acessa plano de voo]
    ControllerAccess --> MonitorSeparation[Controlador monitora separação segura]
    
    style Start fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style MonitorRadar fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style ProcessData fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style DisplayRadar fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style DisplayWithPlan fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style ControllerAccess fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style MonitorSeparation fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
```

**Steel Thread ST1:**
1. Sistema inicializado e em operação
2. Monitora dados dos equipamentos de vigilância
3. Processa dados de vigilância
4. Exibe dados na tela em vista de plano
5. Exibe dados de radar e plano de voo
6. Controlador acessa plano de voo
7. Controlador monitora separação segura

**O que é ignorado (não faz parte do Steel Thread):**
- ❌ Failover para host secundário
- ❌ Tratamento de erro de comunicação com equipamentos
- ❌ Validação de dados inválidos
- ❌ Migração de dados entre setores
- ❌ Arquivamento quando aeronave sai da área
- ❌ Processamento de todas as aeronaves (apenas algumas são processadas)

**Por quê?** Cada Steel Thread valida um aspecto crítico da arquitetura. O ST1 demonstra funcionalidade básica e cria o framework fundamental para aquisição e visualização de dados.

### Exemplo 3: Visualizando o Steel Thread em um Fluxograma

Este exemplo mostra como identificar o Steel Thread em um fluxo de autenticação. O diagrama abaixo apresenta **todo o fluxo** (incluindo alternativas e exceções), mas o **Steel Thread** é destacado como o caminho principal que valida a arquitetura.

**Fluxo Completo de Autenticação:**

```mermaid
flowchart TD
    Start([Abre o app]) --> FillEmail[Preenche campo de email]
    FillEmail --> CheckFormat{Formato válido?}
    CheckFormat -->|Não| ErrorFormat([Erro de formato de login inválido])
    CheckFormat -->|Sim| FillPassword[Preenche o campo de senha]
    
    FillEmail --> ForgotPassword[Clicka em 'esqueci a senha']
    ForgotPassword --> FillEmailRecovery[Preenche campo de email]
    FillEmailRecovery --> FillCode[Preenche o código recebido no email]
    FillCode --> FillNewPassword[Preenche o campo de nova senha]
    FillNewPassword --> SavePassword[Salva a nova senha]
    
    FillPassword --> ClickLogin[Clicka em 'Login']
    ClickLogin --> CheckCredentials{Credenciais válidas?}
    CheckCredentials -->|Erro de rede?| NetworkError([Mensagem de falha na conexão])
    CheckCredentials -->|Não| ErrorCredentials([Erro de credenciais inválidas])
    ErrorCredentials --> FillPassword
    CheckCredentials -->|Sim| Success([Redireciona para a Home])
```

**Steel Thread Identificado (Caminho Principal em Vermelho):**

O Steel Thread para este fluxo de autenticação é apenas o **caminho de sucesso** que valida a arquitetura básica de login. Este é o caminho crítico destacado:

```mermaid
flowchart TD
    Start([Abre o app]) --> FillEmail[Preenche campo de email]
    FillEmail --> CheckFormat{Formato válido?}
    CheckFormat -->|Sim| FillPassword[Preenche o campo de senha]
    FillPassword --> ClickLogin[Clicka em 'Login']
    ClickLogin --> CheckCredentials{Credenciais válidas?}
    CheckCredentials -->|Sim| Success([Redireciona para a Home])
    
    style Start fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style FillEmail fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style CheckFormat fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style FillPassword fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style ClickLogin fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style CheckCredentials fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
    style Success fill:#ff0000,stroke:#000000,stroke-width:2px,color:#fff
```

**Análise do Steel Thread:**

**Steel Thread:**
1. Abre o app
2. Preenche campo de email (formato válido)
3. Preenche campo de senha
4. Clica em 'Login'
5. Credenciais válidas → Redireciona para a Home

**O que é ignorado (não faz parte do Steel Thread):**
- ❌ Fluxo de "esqueci a senha" (recuperação de senha)
- ❌ Validação de formato inválido
- ❌ Tratamento de erro de credenciais inválidas
- ❌ Tratamento de erro de rede
- ❌ Loops de retry

**Por quê este é o Steel Thread?**
- ✅ Valida o fluxo principal de autenticação de ponta a ponta
- ✅ Demonstra que a arquitetura de login funciona
- ✅ Prova que o sistema consegue autenticar um usuário válido
- ✅ Ignora cenários alternativos (recuperação de senha) e exceções (erros)

Este exemplo mostra claramente a diferença entre o **fluxo completo** (com todos os caminhos) e o **Steel Thread** (apenas o caminho crítico que valida a arquitetura).

## 🧪 Como Usar em Testes

### Para QA Junior

**O que fazer:**
1. Pergunte: "Qual é o fluxo mais crítico que precisa funcionar?"
2. Desenhe o Steel Thread de ponta a ponta do fluxo principal
3. Execute esses testes primeiro - se falharem, pare tudo

**Perguntas em refinamento:**
- "Qual é o caminho mais crítico para entregar valor?"
- "Se este fluxo quebrar, o sistema ainda funciona?"
- "Este é o fluxo que devemos testar primeiro?"

### Para QA Pleno

**O que fazer:**
1. Use Steel Threads como base para testes de sistema e integração
2. Organize testes por Steel Thread, não por funcionalidade
3. Priorize bugs que quebram Steel Threads

**Estratégia:**
- Steel Threads devem ser o coração dos seus testes principais
- Falha em Steel Thread = prioridade máxima
- Use para decidir o que corrigir primeiro

### Para QA Senior

**O que fazer:**
1. Use Steel Threads para definir estratégia de testes
2. Monitore se os Steel Threads continuam representando os riscos críticos
3. Revise periodicamente e ajuste conforme necessário

**Governança:**
- "Todos os Steel Threads passando" = sistema saudável
- Revise a cada release ou sprint
- Adicione novos quando novos riscos surgirem

## 🤝 Como Usar em Refinamentos

### Mentalidade

**Pergunta central:** "Qual é o caminho mais crítico e de maior risco que precisa funcionar para entregar valor?"

### Técnicas

**1. Análise de Riscos**
- Para cada história: "Qual é o maior risco técnico?"
- Se risco alto → pode ser parte de um Steel Thread
- Priorize histórias que mitigam riscos arquiteturais

**2. Mapeamento de Dependências**
- Identifique histórias dependentes
- Steel Thread forma uma cadeia de dependências
- Use para priorizar ordem de desenvolvimento

**3. Perguntas Úteis**

**Para entender fluxo crítico:**
- "Se entregássemos apenas uma funcionalidade, qual seria?"
- "O que precisa funcionar para o cliente usar o sistema?"

**Para identificar riscos:**
- "Qual parte tem maior chance de quebrar?"
- "Há integração externa? Como validamos?"

**Para priorizar:**
- "Esta história faz parte do fluxo crítico?"
- "Podemos entregar valor sem esta história?"

## ⚠️ Armadilhas Comuns

### Armadilha 1: Escolher Cenários Instáveis

**Problema:** Escolher fluxos difíceis de testar ou que não representam riscos reais.

**Como evitar:** Escolha fluxos estáveis que realmente validem riscos arquiteturais.

### Armadilha 2: Incluir Cenários Alternativos

**Problema:** Tentar incluir todos os cenários possíveis.

**Como evitar:** Lembre-se - Steel Threads focam apenas no fluxo principal. Alternativas testam separadamente.

### Armadilha 3: Não Revisar

**Problema:** Definir no início e nunca mais olhar.

**Como evitar:** Revise periodicamente (a cada release ou sprint). Ajuste conforme o projeto evolui.

### Armadilha 4: Confundir com História de Usuário

**Problema:** Tratar cada história como um Steel Thread separado.

**Como evitar:** Steel Thread geralmente envolve múltiplas histórias. É o "fio" que conecta várias funcionalidades.

### Boas Práticas

✅ Foque no essencial - minimalista e focado  
✅ Valide riscos reais - mitiga riscos arquiteturais verdadeiros  
✅ Comunique claramente - todos devem entender os Steel Threads  
✅ Documente - mantenha claro por que foram escolhidos  
✅ Revise periodicamente - ajuste conforme necessário

**📖 Referências:**

- Narayanappa, S., Alkobaisi, S., Bae, W. D., & Debnath, N. (2009). Steel Threads: Framework for Developing Software System Architecture. Disponível em: [https://www.cs.du.edu/~snarayan/sada/docs/steelthreads.pdf](https://www.cs.du.edu/~snarayan/sada/docs/steelthreads.pdf)
