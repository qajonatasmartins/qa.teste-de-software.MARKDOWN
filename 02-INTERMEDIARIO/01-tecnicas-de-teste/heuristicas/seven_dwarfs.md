# Heurística Seven Dwarfs

**Criador:** Cassandra H. Leung

## O que é a Heurística Seven Dwarfs?

A heurística **Seven Dwarfs** é uma abordagem criada por **Cassandra H. Leung** (tester, entusiasta de UX, feminista interseccional, e speaker) que propõe uma alternativa às personas tradicionais utilizando os **sete anões da Disney** como **personas baseadas em estados mentais**.

### Conceito Principal

Uma **persona** é um personagem fictício criado para representar um tipo de usuário que pode utilizar um produto ou serviço de maneira semelhante. Tradicionalmente, personas focam em:
- Demografia (idade, salário, localização)
- Proficiência técnica
- Perfil profissional

### Problemas com Personas Tradicionais

Segundo Cassandra H. Leung, as personas tradicionais apresentam diversos problemas:

- **Inutilidade para Testes**: Não são projetadas para testes, fornecendo informações pouco úteis
- **Informação Vaga**: Apenas sugerem informações potencialmente úteis em vez de declará-las claramente
- **Foco Demográfico Estreito**: Concentram-se em demografia tradicional, ignorando outros fatores importantes
- **Generalização Excessiva**: Tentam cobrir muitos grupos diferentes em uma única persona
- **Complexidade Ignorada**: Pessoas são complexas e não podem ser reduzidas a uma única persona

### A Solução: Dwarf Personas

As **Dwarf Personas** focam nos **estados mentais dos usuários** ao invés de dados demográficos, reconhecendo que:
- Os usuários são complexos e não podem ser representados por uma única persona
- Uma pessoa pode incorporar diferentes "anões" em momentos distintos
- O estado mental influencia mais o comportamento do que a demografia

```
Insight Crucial: Os 'Dwarf Personas' são uma ferramenta que usa o estado mental do usuário (inspirado nos Sete Anões) para guiar testes. Ao invés de se basear em demografia, o foco está no estado mental do usuário em um dado momento – por exemplo, um usuário com pressa, estressado ou confuso. Essa abordagem garante que os testes cubram casos de borda que o produto pode induzir no usuário.
```

### Os Sete Anões como Personas

Cada anão representa um estado mental específico com características, prioridades e potenciais impactos bem definidos:

#### **Happy (O Temporário)**
- **Estado Mental**: Contente, mente aberta, perdoador
- **Comportamento**: Disposto a ignorar pequenas falhas, sem grandes expectativas
- **Prioridade**: Bom design, divertido de usar
- **Risco**: Baixo, a menos que seja empurrado para um estado mental diferente
- **Observação**: O humor pode mudar a qualquer momento

#### **Doc (O Exigente)**
- **Estado Mental**: Suspeito, difícil de impressionar, facilmente desinteressado
- **Comportamento**: Orientado a detalhes, prefere especificidade à ambiguidade
- **Prioridade**: Informação precisa e claramente apresentada
- **Risco**: Desconfiança leva à não adoção; confusão pode levar ao abandono
- **Exemplo de Impacto**: Desiste de usar e-mail seguro por falta de clareza

#### **Sneezy (O Distraído)**
- **Estado Mental**: Esquecido, errático, pouca atenção
- **Comportamento**: Multitarefa, não gosta de fluxos longos ou complicados
- **Prioridade**: Fluxo de trabalho rápido e simples; tempo suficiente para completar tarefas
- **Risco**: Reserva incompleta, erro na reserva, esgotamento do tempo da sessão
- **Exemplo de Impacto**: Viagem arruinada por reserva incompleta

#### **Dopey (O Confuso)**
- **Estado Mental**: Inseguro/sobrecarregado
- **Comportamento**: Busca conforto em padrões familiares e guias, propenso a erros
- **Prioridade**: Instruções claras e mensagens de aviso
- **Risco**: Ação errada (cliente cobrado demais), reclamações do cliente
- **Exemplo de Impacto**: Emprego em risco por erros no sistema

#### **Sleepy (O Exausto)**
- **Estado Mental**: Mental ou fisicamente exausto
- **Comportamento**: Estressado, alta carga cognitiva, impaciente, baixa tolerância a problemas
- **Prioridade**: Funcionalidades autoexplicativas
- **Risco**: Fusos horários incertos, compromissos salvos no fuso errado
- **Exemplo de Impacto**: Reuniões perdidas, perda de trabalho/reputação

#### **Bashful (O Ansioso)**
- **Estado Mental**: Tímido, reservado, nervoso
- **Comportamento**: Preocupado em cometer erros, às vezes evita agir "por precaução"
- **Prioridade**: Localização (idioma nativo), gráficos úteis
- **Risco**: Informações mal traduzidas, blocos de texto como imagens
- **Exemplo de Impacto**: Pagamento incorreto de impostos por tradução ruim

#### **Grumpy (O Raivoso)**
- **Estado Mental**: Impaciente, irritado, frustrado
- **Comportamento**: Propenso a "rage clicking" e abandono após má experiência, resistente a mudanças
- **Prioridade**: Confiabilidade
- **Risco**: Aplicativo trava (perda de dados), longos tempos de processamento
- **Exemplo de Impacto**: Frustração, tempo perdido, abandono do produto
- **Observação**: Também pode ser visto como "O Insatisfeito" (Bad Actor / Ameaça de Segurança)

## Como Aplicar a Heurística

### 1. Criação de Personas Baseadas em Estados Mentais

**Processo:**
- Identifique o estado mental/emocional do usuário
- Desenvolva cenários situacionais específicos
- Considere objetivos do usuário naquele estado
- Explore fatores que influenciam esse estado

**Exemplo prático:**
```
Persona: Grumpy (Rabugento)
Estado: Frustrado após múltiplas tentativas de login falharam
Situação: Usuário tentando acessar sistema importante no trabalho
Objetivo: Fazer login rapidamente sem mais complicações
Fatores: Pressão do tempo, múltiplas senhas para lembrar
```

### 2. Análise de Inclusão e Exclusão

**Para cada anão, pergunte:**
- Como nosso produto atende esse estado mental?
- Que barreiras podem existir para usuários nesse estado?
- Como podemos ser mais inclusivos?

**Exemplo de análise:**

| Anão | Inclusão | Exclusão Potencial |
|------|----------|-------------------|
| **Sleepy** | Interface simples e clara | Textos longos, muitas etapas |
| **Bashful** | Processo privado, sem exposição | Compartilhamento forçado, perfis públicos |
| **Dopey** | Tutoriais e ajuda contextual | Interface complexa sem orientação |

### 3. Teste com Múltiplas Personas

**Reconheça que:**
- Um mesmo usuário pode estar em diferentes estados mentais
- Estados mentais mudam conforme a situação
- Uma pessoa pode ser representada por múltiplas personas

**Exemplo prático:**
```
João pela manhã = Doc (focado, analítico)
João após o almoço = Sleepy (menos energia)
João com deadline = Grumpy (estressado, impaciente)
```

## Metodologia de Aplicação

### Passo 1: Mapeamento de Estados
1. Liste os possíveis estados mentais dos usuários
2. Associe cada estado a um dos sete anões
3. Desenvolva cenários específicos para cada estado

### Passo 2: Análise de Experiência
1. Para cada anão, avalie a experiência atual do produto
2. Identifique pontos de exclusão ou dificuldade
3. Documente oportunidades de melhoria

### Passo 3: Design Inclusivo
1. Adapte interfaces para diferentes estados mentais
2. Crie fluxos alternativos quando necessário
3. Teste com usuários reais em diferentes estados

### Passo 4: Validação Contínua
1. Monitore como usuários se comportam em diferentes estados
2. Ajuste personas conforme aprendizado
3. Itere sobre melhorias identificadas

## Benefícios da Heurística

1. **Empatia aprimorada**: Foco em estados emocionais reais
2. **Design mais inclusivo**: Considera diversos contextos de uso
3. **Personas memoráveis**: Anões são facilmente lembrados pela equipe
4. **Flexibilidade**: Um usuário pode ser múltiplas personas
5. **Foco na experiência**: Estados mentais vs. dados demográficos

## Exemplos Práticos de Aplicação

### E-commerce
- **Grumpy**: Checkout rápido para usuários impacientes
- **Dopey**: Guias visuais para primeiros compradores
- **Sleepy**: Busca simplificada e categorização clara

### Aplicativo Bancário
- **Bashful**: Opções de privacidade para transações
- **Doc**: Dashboards detalhados para análise
- **Sneezy**: Recuperação fácil de sessões interrompidas

### Software Educacional
- **Happy**: Gamificação para usuários motivados
- **Grumpy**: Acesso direto ao conteúdo sem distrações
- **Dopey**: Tutoriais interativos e feedback constante

## Filosofia da Abordagem

> **"Não existe maneira 'certa' ou 'errada' - apenas 'útil' ou 'não útil'"**
> - Cassandra H. Leung

Esta flexibilidade permite que equipes adaptem a heurística às suas necessidades específicas e contextos de produto.

## Exemplo Prático Completo: Aplicativo de Entrega de Comida

Vamos aplicar a heurística Seven Dwarfs step-by-step em um aplicativo de entrega de comida para demonstrar como executar cada etapa da metodologia.

### Passo 1: Mapeamento de Estados

**1.1 Listando estados mentais dos usuários:**
- Usuário com fome e impaciente
- Usuário explorando opções com calma
- Usuário cansado querendo algo simples
- Usuário inseguro sobre pedidos online
- Usuário distraído (no trabalho/multitasking)
- Usuário inexperiente com apps
- Usuário experiente querendo controle total

**1.2 Associando cada estado a um anão:**

| Estado Mental | Anão | Característica |
|---------------|------|----------------|
| Impaciente e faminto | **Grumpy** | Quer rapidez, sem complicações |
| Explorando com prazer | **Happy** | Gosta de descobrir novidades |
| Cansado, quer simplicidade | **Sleepy** | Precisa de opções óbvias |
| Inseguro sobre pedidos | **Bashful** | Quer privacidade e segurança |
| Distraído/multitasking | **Sneezy** | Facilmente interrompido |
| Inexperiente com apps | **Dopey** | Precisa de orientação |
| Usuário experiente | **Doc** | Quer controle e informações |

**1.3 Desenvolvendo cenários específicos:**

**Grumpy (Rabugento):**
```
Cenário: Maria saiu tarde do trabalho, está com muita fome e quer algo rápido
Objetivo: Pedir comida no menor tempo possível
Frustração: Muitos cliques, cadastros longos, muitas opções
Estado mental: Impaciente, irritada, focada em velocidade
```

**Happy (Feliz):**
```
Cenário: João está em casa no fim de semana, quer experimentar algo novo
Objetivo: Descobrir restaurantes interessantes, explorar cardápios
Motivação: Prazer em descobrir, não tem pressa
Estado mental: Curioso, disposto a navegar e explorar
```

**Sleepy (Sonolento):**
```
Cenário: Ana chegou cansada em casa após um dia longo
Objetivo: Pedir algo familiar sem pensar muito
Necessidade: Interface simples, sugestões óbvias
Estado mental: Baixa energia, quer facilidade
```

### Passo 2: Análise de Experiência

**2.1 Avaliando experiência atual para cada anão:**

**Grumpy - Pontos Problemáticos:**
- ❌ Muitos passos no checkout
- ❌ Cadastro obrigatório antes do pedido
- ❌ Muitas opções de personalização obrigatórias
- ❌ Sem opção "repetir último pedido"

**Happy - Oportunidades:**
- ✅ Fotos atrativas dos pratos
- ❌ Falta sistema de descoberta/recomendação
- ❌ Não mostra avaliações de outros usuários
- ❌ Sem opção de favoritar restaurantes

**Sleepy - Desafios:**
- ❌ Interface complexa com muitas informações
- ❌ Sem sugestões baseadas em horário
- ❌ Categorização confusa
- ❌ Sem opção "mais pedidos" simples

**2.2 Identificando pontos de exclusão:**

| Anão | Exclusão Atual | Impacto |
|------|----------------|---------|
| **Grumpy** | Processo longo de pedido | Abandona o app, vai para concorrente |
| **Bashful** | Obriga criação de perfil público | Desiste por questões de privacidade |
| **Dopey** | Sem tutorial ou ajuda | Não consegue completar primeiro pedido |

### Passo 3: Design Inclusivo

**3.1 Adaptações para diferentes estados mentais:**

**Para Grumpy (Rápido e Direto):**
```
✅ Implementar:
- Botão "Pedido Expresso" na home
- Checkout em 2 cliques máximo
- "Repetir último pedido" prominente
- Guest checkout (sem cadastro obrigatório)
- Filtro "Entrega rápida" (< 30min)
```

**Para Happy (Exploração e Descoberta):**
```
✅ Implementar:
- Feed de "Novidades" na home
- Sistema de recomendações personalizadas
- Galeria de fotos dos pratos
- Reviews e ratings visíveis
- "Surpreenda-me" com sugestão aleatória
```

**Para Sleepy (Simplicidade):**
```
✅ Implementar:
- Interface modo "simples" com menos opções
- Sugestões baseadas em horário ("Café da manhã", "Almoço")
- Grandes botões "Mais Pedidos da Região"
- Cardápio simplificado com apenas principais
- Auto-complete inteligente na busca
```

**3.2 Criando fluxos alternativos:**

**Fluxo Tradicional vs Fluxos Adaptativos:**

```
Fluxo Grumpy (Express):
Home → Último Pedido → Confirmar → Pagamento → Pronto
(2 cliques)

Fluxo Happy (Exploração):
Home → Feed Novidades → Restaurante → Galeria → Reviews → Cardápio → Personalizar → Pedido
(Navegação rica)

Fluxo Sleepy (Assistido):
Home → "Estou com fome" → Sugestão automática baseada em horário → Aceitar → Pronto
(1 clique + confirmação)
```

### Passo 4: Validação Contínua

**4.1 Métricas por Persona:**

**Grumpy:**
- Tempo médio de pedido (meta: < 2 minutos)
- Taxa de abandono no checkout
- Uso do "repetir pedido"
- NPS específico para velocidade

**Happy:**
- Tempo gasto explorando (quanto mais, melhor)
- Número de restaurantes visualizados por sessão
- Taxa de descoberta de novos restaurantes
- Engajamento com reviews

**Sleepy:**
- Taxa de conclusão do primeiro pedido
- Uso das sugestões automáticas
- Tempo de decisão (deve ser baixo)
- Satisfação com simplicidade

**4.2 Testes A/B por Estado Mental:**

```
Teste para Grumpy:
Versão A: Checkout tradicional (5 passos)
Versão B: Checkout express (2 passos)
Métrica: Taxa de conversão e tempo de pedido

Resultado esperado: Versão B deve ter maior conversão para usuários identificados como "Grumpy"
```

**4.3 Monitoramento e Iteração:**

**Indicadores de Estado Mental:**
- Velocidade de cliques (rápido = Grumpy)
- Tempo navegando (longo = Happy)
- Horário de uso (noite = Sleepy)
- Primeira visita (Dopey)

**Adaptação Dinâmica:**
```
if (clicks_per_minute > 20 && time_on_page < 30s) {
    show_express_mode = true; // Usuário Grumpy detectado
}

if (time_browsing > 5min && pages_visited > 10) {
    show_discovery_features = true; // Usuário Happy detectado
}
```

### Resultados Esperados

**Métricas de Sucesso:**
- **Grumpy**: Redução de 50% no tempo de pedido
- **Happy**: Aumento de 30% no tempo de sessão e descoberta
- **Sleepy**: 80% dos usuários completam pedido com sugestões automáticas
- **Bashful**: Redução de 40% no abandono por questões de privacidade
- **Dopey**: 90% de conclusão do primeiro pedido com tutorial
- **Doc**: Aumento de uso de filtros avançados em 60%
- **Sneezy**: Redução de 35% em sessões interrompidas

### Lições Aprendidas

1. **Um usuário = múltiplas personas**: João pode ser Happy no domingo (explorando) e Grumpy na segunda (com pressa)
2. **Context matters**: O mesmo usuário tem necessidades diferentes em momentos diferentes
3. **Inclusive design**: Atender diferentes estados mentais beneficia todos os usuários
4. **Mensurável**: Cada persona pode ter métricas específicas de sucesso

## Prompt para QAs: Aplicando Seven Dwarfs em Testes

### Template de Prompt para Análise

Use este prompt como guia para aplicar a heurística Seven Dwarfs em seus testes. Substitua `[SEU_PRODUTO]` pelo sistema que você está testando.

```
🧪 APLICANDO SEVEN DWARFS EM TESTES - [SEU_PRODUTO]

## 1. MAPEAMENTO DE PERSONAS POR ESTADO MENTAL

Para cada anão, identifique:

### 😊 HAPPY (O Temporário)
**Estado Mental:** Contente, mente aberta, perdoador
**Comportamento:** Disposto a ignorar pequenas falhas, sem grandes expectativas
**Prioridade:** Bom design, divertido de usar
**Cenário de teste:** _[Situação onde usuário está explorando com humor positivo]_
**Risco/Falha:** _[Como o sistema pode empurrá-lo para outro estado mental?]_
**Observação:** O humor pode mudar a qualquer momento

### 🧑‍⚕️ DOC (O Exigente)
**Estado Mental:** Suspeito, difícil de impressionar, facilmente desinteressado
**Comportamento:** Orientado a detalhes, prefere especificidade à ambiguidade
**Prioridade:** Informação precisa e claramente apresentada
**Cenário de teste:** _[Situação onde usuário analisa detalhes do sistema]_
**Risco/Falha:** Desconfiança leva à não adoção; confusão pode levar ao abandono
**Exemplo:** Desiste de usar e-mail seguro por falta de clareza

### 🤧 SNEEZY (O Distraído)
**Estado Mental:** Esquecido, errático, pouca atenção
**Comportamento:** Multitarefa, não gosta de fluxos longos ou complicados
**Prioridade:** Fluxo rápido e simples; tempo suficiente para completar tarefas
**Cenário de teste:** _[Situação de multitasking ou interrupções constantes]_
**Risco/Falha:** Reserva incompleta, erro na reserva, esgotamento do tempo da sessão
**Exemplo:** Viagem arruinada por reserva incompleta

### 🤔 DOPEY (O Confuso)
**Estado Mental:** Inseguro/sobrecarregado
**Comportamento:** Busca conforto em padrões familiares e guias, propenso a erros
**Prioridade:** Instruções claras e mensagens de aviso
**Cenário de teste:** _[Situação de primeiro uso ou complexidade elevada]_
**Risco/Falha:** Ação errada (cliente cobrado demais), reclamações do cliente
**Exemplo:** Emprego em risco por erros no sistema

### 😴 SLEEPY (O Exausto)
**Estado Mental:** Mental ou fisicamente exausto
**Comportamento:** Estressado, alta carga cognitiva, impaciente, baixa tolerância a problemas
**Prioridade:** Funcionalidades autoexplicativas
**Cenário de teste:** _[Situação de uso em horários extremos ou sob estresse]_
**Risco/Falha:** Fusos horários incertos, compromissos salvos no fuso errado
**Exemplo:** Reuniões perdidas, perda de trabalho/reputação

### 😳 BASHFUL (O Ansioso)
**Estado Mental:** Tímido, reservado, nervoso
**Comportamento:** Preocupado em cometer erros, às vezes evita agir "por precaução"
**Prioridade:** Localização (idioma nativo), gráficos úteis
**Cenário de teste:** _[Situação onde usuário tem medo de errar ou expor dados]_
**Risco/Falha:** Informações mal traduzidas, blocos de texto como imagens
**Exemplo:** Pagamento incorreto de impostos por tradução ruim

### 👿 GRUMPY (O Raivoso)
**Estado Mental:** Impaciente, irritado, frustrado
**Comportamento:** Propenso a "rage clicking" e abandono, resistente a mudanças
**Prioridade:** Confiabilidade
**Cenário de teste:** _[Situação de pressão, falhas anteriores, ou stress]_
**Risco/Falha:** Aplicativo trava (perda de dados), longos tempos de processamento
**Exemplo:** Frustração, tempo perdido, abandono do produto
**Observação:** Pode ser "O Insatisfeito" (Bad Actor / Ameaça de Segurança)

## 2. CASOS DE TESTE POR PERSONA

Para cada anão, crie pelo menos 3 casos de teste específicos:

### Exemplo de Estrutura:
**CT001 - Grumpy: Login Rápido Sob Pressão**
- **Pré-condição:** Usuário já cadastrado, tentou login 2x sem sucesso
- **Passos:** [1] Acessar login [2] Tentar credenciais incorretas [3] Usar "Esqueci senha"
- **Resultado esperado:** Processo de recuperação deve ser rápido e claro
- **Critério de falha:** Se processo levar mais de 2 cliques ou não for intuitivo

## 3. MATRIZ DE COBERTURA DE TESTES

| Funcionalidade | Grumpy | Happy | Sleepy | Bashful | Sneezy | Dopey | Doc |
|----------------|--------|--------|---------|----------|---------|--------|-----|
| Login          | ⚠️ Testado | ✅ OK | ❌ Não testado | ✅ OK | ⚠️ Testado | ❌ Não testado | ✅ OK |
| Cadastro       | | | | | | | |
| Navegação      | | | | | | | |
| Checkout       | | | | | | | |

## 4. QUESTÕES PARA ANÁLISE

**Inclusão vs Exclusão:**
- Quais personas são bem atendidas pelo sistema atual?
- Quais personas enfrentam barreiras ou exclusão?
- Que melhorias poderiam tornar o sistema mais inclusivo?

**Priorização:**
- Quais personas são mais críticas para o negócio?
- Quais cenários de falha têm maior impacto?
- Onde investir esforços de teste primeiro?

**Cenários de Transição:**
- Como o sistema se comporta quando um usuário muda de estado mental?
- Ex: Doc (analisando) → Grumpy (com pressa) durante a mesma sessão

## 5. MÉTRICAS DE VALIDAÇÃO

Para cada persona, defina métricas mensuráveis:

**Grumpy:**
- Tempo médio para completar tarefa crítica: ___
- Taxa de abandono por impaciência: ___%
- Número de cliques para tarefa principal: ___

**Happy:**
- Tempo de exploração antes de converter: ___
- Número de funcionalidades descobertas: ___
- Taxa de engajamento com conteúdo: ___%

[Continue para todas as personas...]

## 6. PLANO DE TESTE FINAL

**Prioridade Alta:** [Liste cenários críticos identificados]
**Prioridade Média:** [Liste cenários importantes mas não críticos]
**Prioridade Baixa:** [Liste cenários nice-to-have]

**Recursos necessários:**
- Tempo estimado: ___
- Ferramentas: ___
- Ambientes: ___

**Cronograma:**
- Fase 1 (Grumpy + Doc): [data]
- Fase 2 (Happy + Sleepy): [data]
- Fase 3 (Bashful + Sneezy + Dopey): [data]
```

### Exemplo de Aplicação do Prompt

**Produto:** Sistema de Internet Banking

```
🧪 APLICANDO SEVEN DWARFS EM TESTES - INTERNET BANKING

## 1. MAPEAMENTO DE PERSONAS POR ESTADO MENTAL

### 👿 GRUMPY (Usuário Frustrado/Impaciente)
**Contexto:** Cliente precisa fazer transferência urgente, já teve problema com app
**Cenário de teste:** Transferência PIX em horário de pico com timeout de sessão
**Comportamentos esperados:** Vai direto ao PIX, quer fazer transferência em < 1 min
**Pontos de falha:** Logout automático, muitas confirmações, steps desnecessários

### 😊 HAPPY (Usuário Satisfeito/Explorador)
**Contexto:** Cliente satisfeito explorando novos produtos do banco
**Cenário de teste:** Navegação por produtos de investimento no fim de semana
**Comportamentos esperados:** Explora dashboards, lê informações, compara produtos
**Pontos de falha:** Informações incompletas, links quebrados, simuladores com erro

### 😴 SLEEPY (Usuário Cansado/Baixa Energia)
**Contexto:** Cliente acessando app tarde da noite para pagar conta
**Cenário de teste:** Pagamento de boleto depois das 22h
**Comportamentos esperados:** Quer pagar rápido sem pensar muito
**Pontos de falha:** Interface complexa, muitas opções, falta de sugestões automáticas

[Continua para todos os anões...]

## 2. CASOS DE TESTE POR PERSONA

**CT001 - Grumpy: PIX Urgente com Timeout**
- **Pré-condição:** App com sessão prestes a expirar
- **Passos:** [1] Login [2] PIX [3] Inserir dados [4] Confirmar antes do timeout
- **Resultado esperado:** Transferência deve ser concluída ou sessão deve ser estendida automaticamente
- **Critério de falha:** Se usuário perde dados inseridos por timeout

**CT002 - Sleepy: Pagamento Boleto Noturno**
- **Pré-condição:** Usuário logado às 23h
- **Passos:** [1] Pagamentos [2] Escanear código barras [3] Confirmar valor [4] Pagar
- **Resultado esperado:** Processo deve ser intuitivo com mínimos cliques
- **Critério de falha:** Se requer mais de 4 cliques ou decisões complexas
```

### Dicas para QAs

1. **Começe com 2-3 anões** mais relevantes para seu produto
2. **Use dados reais** de comportamento do usuário se disponível
3. **Combine com outras técnicas** como boundary testing e equivalence partitioning
4. **Documente descobertas** sobre exclusão/inclusão para compartilhar com UX
5. **Itere regularmente** - estados mentais e contextos mudam
6. **Reconheça a complexidade** - uma pessoa pode ser todos os anões em momentos diferentes
7. **Foque em casos de estresse** - as situações são baseadas em casos reais de estresse
8. **Teste também para usuários indesejados** - considere atores mal-intencionados (Grumpy como Bad Actor)

### Pessoas vs Roles vs Personas

É fundamental entender as diferenças:

| Característica | Papéis (Roles) | Personas Tradicionais | Dwarf Personas |
| :--- | :--- | :--- | :--- |
| **Foco** | Usuários em relação ao software; permissões (Ex.: admin, líder) | Demografia, profissão, ambiente | Estados mentais e comportamentais |
| **Formato de Uso** | "Como um [papel], eu quero X para que Y." | "Como [persona tradicional] responderia a esta funcionalidade?" | "Como o produto impacta usuários no estado [anão]?" |
| **Componentes** | Permissões, responsabilidades | Demografia, Proficiência Técnica, Psicografia | Estado Mental, Comportamentos, Situação, Prioridade, Impacto |
| **Complexidade** | Um usuário pode ter múltiplos papéis | Tenta cobrir tudo em uma persona | Uma pessoa pode ser todos os anões |

### Recomendações da Heurística

O documento original encoraja:

1. **Quebrar o paradigma das demografias tradicionais**
2. **Basear personas em pessoas reais**, em vez de generalizações
3. **Realizar testes como se fosse cada persona**
4. **Pensar em como o produto pode despertar cada estado mental nos usuários**
5. **Ter personas também para usuários que você NÃO deseja** (atores mal-intencionados)

### Filosofia Central

> **"Não existe maneira 'certa' ou 'errada' - apenas 'ÚTIL' ou 'INÚTIL'"**
> - Cassandra H. Leung

## Pergunta-Chave

> **"Como nosso produto atende (ou exclui) usuários em diferentes estados mentais?"**

### Casos de Estresse Inspirados em Situações Reais

As situações de exemplo para estas personas são inspiradas em **casos reais** que a autora vivenciou, sendo consideradas **"casos de estresse"**, mas **não incomuns**. Isso torna a heurística mais realista e prática para testes.

## Informações Adicionais

### Sobre a Autora

**Cassandra H. Leung** se identifica como:
- Tester
- Entusiasta de UX (Experiência do Usuário)
- Feminista interseccional
- Speaker

### Contexto da Criação

O documento original é uma apresentação intitulada **"(Mis)Using Personas with The Seven Dwarfs"** (Mal/Bom Uso de Personas com os Sete Anões), que explora o conceito de personas de usuário, critica as personas tradicionais e propõe esta abordagem alternativa.

### Licença Criativa

As **Dwarf Personas** são inspiradas, com **licença criativa**, nos anões da Disney, focando nos **estados mentais dos usuários** como alternativa às abordagens tradicionais.

## Referências

- [Palestra: (Mis)Using Personas with the Seven Dwarfs - Ministry of Testing](https://www.ministryoftesting.com/dojo/lessons/mis-using-personas-with-the-seven-dwarfs-cassandra-h-leung)
- [Blog Post: (Mis)Using Personas with the Seven Dwarfs - Cassandra HL](https://www.cassandrahl.com/blog/misusing-personas-with-the-seven-dwarfs/)
- [PDF da Apresentação](https://www.cassandrahl.com/wp-content/uploads/2019/09/MisUsing-Personas-with-The-Seven-Dwarfs.pdf)
- TestBash Germany 2019 - Apresentação original