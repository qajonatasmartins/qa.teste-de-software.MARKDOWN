# Guia Completo: Entrevistas para QA

**Objetivo:** Este guia prepara você para entrevistas de QA com perguntas comuns, respostas modelo e estratégias de apresentação.

## 📋 Índice

1. [Preparação Estratégica](#-preparação-estratégica)
2. [Metodologias Ágeis](#-metodologias-ágeis)
3. [Fundamentos de Teste](#-fundamentos-de-teste)
4. [Automação e Ferramentas](#-automação-e-ferramentas)
5. [Testes Mobile](#-testes-mobile)
6. [Perguntas Comportamentais](#️-perguntas-comportamentais)
7. [Dicas de Apresentação](#-dicas-de-apresentação)
8. [Checklist Pré-Entrevista](#-checklist-pré-entrevista)


## 🎯 Preparação Estratégica

### Antes da Entrevista

**Pesquisa sobre a empresa:**
- [ ] Modelo de negócio e produtos
- [ ] Stack tecnológico utilizado
- [ ] Metodologia de desenvolvimento
- [ ] Cultura organizacional
- [ ] Desafios atuais do mercado

**Preparação técnica:**
- [ ] Revise fundamentos de teste
- [ ] Pratique explicar conceitos com exemplos
- [ ] Prepare histórias de projetos anteriores
- [ ] Atualize conhecimentos sobre ferramentas

## 🔄 Metodologias Ágeis

### Perguntas Frequentes

#### **"Você sabe me falar um pouco sobre como é o processo de teste no ciclo de desenvolvimento?"**

**Resposta Estruturada:**
```
No contexto ágil, o processo de teste é contínuo e integrado:

1. **Refinamento:** Momento onde é feito a quebra de atividades, respondido dúvidas, levantamento de questionamento se é o que realmente devemos fazer, momento onde pode ser pontuado as atividades também e essas atividades refinadas podem ser aceitas ou não, caso de aceite, entram para próxima sprint.
2. **Planning:** Participação na definição de critérios de aceite, pontuação das atividades, quebras das atividades que não foram refinadas, levantamento de como fazer e planejamento da sprint a ser desenvolvida.
3. **Durante Sprint:** 
   - Testes exploratórios conforme desenvolvimento
   - Automação de cenários críticos
   - Criação de casos de testes
   - Acompanhamento de métricas do DEV TEAM
   - Validação de histórias com Product Owner
   - Análise de riscos
   - Comunicação
4. **Daily:** Comunicação sobre impedimentos e progresso das atividades
5. **Review:** Demonstração de funcionalidades desenvolvidas durante a sprint e aceite ou não das atividades pelo Product Owner, stakeholders, business analyst e outras partes interessadas.
6. **Retrospectiva:** Melhoria contínua do processo de qualidade, onde é discutido os pontos positivos e negativos da sprint, como o time pode melhorar, quais iniciativas serão executadas para garantir o crescimento e evolução do DEV TEAM.

Princípio: "Testar cedo e frequentemente" (Shift Left Testing)
```

#### **"Como você prioriza as tarefas em um contexto ágil?"**

**Modelo de Resposta:**
```
Utilizo matriz de priorização baseada em:

1. **Valor de Negócio** (Alto/Médio/Baixo)
2. **Risco Técnico** (Alto/Médio/Baixo)  
3. **Complexidade** (Alta/Média/Baixa)

Prioridade 1: Alto valor + Alto risco
Prioridade 2: Alto valor + Baixo risco
Prioridade 3: Médio valor + Alto risco

Considerações adicionais:
- Dependências entre funcionalidades
- Prazo de release
- Disponibilidade de ambiente
- Feedback de usuários
```

#### **"Quando é a hora de parar de testar?"**

**Critérios de Saída:**
```
Paro de testar quando:

✅ **Critérios Funcionais:**
- Todos casos de teste críticos executados
- Cenários de aceite validados
- Bugs críticos e altos resolvidos

✅ **Critérios de Qualidade:**
- Cobertura de código adequada (>80%)
- Performance dentro dos SLAs
- Segurança básica validada

✅ **Critérios de Negócio:**
- Prazo de release
- Orçamento disponível
- Risco aceitável pelo negócio

⚠️ **Nunca paro por:** "Não encontrei mais bugs"
```

#### **"Como é o ciclo de vida do bug em um contexto ágil?"**

**Fluxo do Bug:**
```
1. **Descoberta** → Log imediato no backlog
2. **Triagem** → Priorização em Daily/Planning
3. **Atribuição** → Dev assume na mesma sprint (se crítico)
4. **Correção** → Fix + unit test
5. **Validação** → Reteste pelo QA
6. **Fechamento** → Confirma resolução

Ágil vs Tradicional:
- Comunicação direta (menos documentação)
- Correção rápida (dentro da sprint)
- Validação imediata
- Menos burocracia
```

## 🧪 Fundamentos de Teste

### Conceitos Essenciais

#### **"O que é Teste funcional vs não funcional?"**

**Resposta Comparativa:**
```
TESTES FUNCIONAIS:
✅ O que o sistema FAZ
✅ Validam requisitos de negócio
✅ Baseados em especificações

Exemplos:
- Login com credenciais válidas
- Cálculo de impostos
- Fluxo de compra e-commerce

TESTES NÃO FUNCIONAIS:
✅ COMO o sistema se comporta
✅ Qualidades do sistema
✅ Baseados em atributos de qualidade

Exemplos:
- Performance (tempo de resposta)
- Segurança (autenticação)
- Usabilidade (facilidade de uso)
- Compatibilidade (browsers/devices)
```

#### **"Explique sobre partição de equivalência e análise de valor limite"**

**Partição de Equivalência:**
```
Técnica: Dividir dados em grupos que se comportam similarmente

Exemplo - Campo "Idade" (válido: 18-65):
┌─────────────────┬─────────────────┬─────────────────┐
│   INVÁLIDA      │     VÁLIDA      │   INVÁLIDA      │
│    < 18         │    18-65        │    > 65         │
└─────────────────┴─────────────────┴─────────────────┘

Teste: 1 valor de cada partição (ex: 10, 30, 70)
```

**Análise de Valor Limite:**
```
Técnica: Testar valores nas "bordas" das partições, usado mais para valores númericos, datas e etc.

Exemplo - Campo "Idade" (válido: 18-65):
Valores de teste:
- 17 (inválido - limite inferior)
- 18 (válido - limite)  
- 19 (válido - limite superior)
- 64 (válido - limite inferior)
- 65 (válido - limite)
- 66 (inválido - limite superior)

Regra: Bugs aparecem mais frequentemente nas bordas
```

#### **"O que é smoke test vs sanity test?"**

**Comparativo:**
```
SMOKE TEST:
🔍 "O sistema está funcionando basicamente?"
📦 Teste após build/deploy
🎯 Funcionalidades críticas principais
⚡ Rápido e superficial
📝 Subset dos testes de regressão

Exemplo: Login, homepage carrega, menu principal

SANITY TEST:
🔍 "A funcionalidade específica está funcionando?"
📦 Teste após bug fix específico
🎯 Funcionalidade específica em detalhes
⚡ Focado e profundo
📝 Subset dos testes funcionais

Exemplo: Após fix no carrinho, testar todo fluxo de compra
```

#### **"Me fale sobre a pirâmide de Testes"**

**Estrutura da Pirâmide:**
```
         /\
        /UI\     ← Poucos, caros, lentos
       /____\      Interface do usuário
      /      \
     /INTEGR.\   ← Moderados, médio custo
    /__AÇÃO___\    Testes de integração
   /          \
  /   UNIT     \  ← Muitos, baratos, rápidos
 /______________\   Testes unitários

PRINCÍPIOS:
- Base ampla de testes unitários (70%)
- Camada média de integração (20%)  
- Topo pequeno de UI/E2E (10%)

BENEFÍCIOS:
- Feedback rápido
- Menor custo de manutenção
- Maior confiabilidade
```

## 🤖 Automação e Ferramentas

### Estratégia de Automação

#### **"Como priorizar o que será automatizado?"**

**Critérios de Priorização:**
```
🏆 ALTA PRIORIDADE:
- Testes executados frequentemente
- Cenários críticos de negócio
- Testes estáveis (pouca mudança)
- Regressão de funcionalidades core
- Smoke tests

🎯 MÉDIA PRIORIDADE:
- Testes de integração API
- Validações de dados
- Fluxos alternativos importantes

⚠️ BAIXA PRIORIDADE:
- Testes exploratórios
- Validações visuais complexas
- Funcionalidades instáveis
- Cases únicos/raros

FÓRMULA: Frequência × Criticidade × Estabilidade = Prioridade
```

#### **"Page Objects - o que é e para que serve?"**

**Conceito e Implementação:**
```
DEFINIÇÃO:
Pattern que encapsula elementos e ações de uma página em uma classe

BENEFÍCIOS:
✅ Reutilização de código
✅ Manutenção centralizada
✅ Legibilidade dos testes
✅ Redução de duplicação

ESTRUTURA:
┌─────────────────┐
│   Test Class    │ ← Cenários de teste
└─────────────────┘
         │
┌─────────────────┐
│   Page Object   │ ← Elementos + Ações
└─────────────────┘
         │
┌─────────────────┐
│   Web Driver    │ ← Interação com browser
└─────────────────┘

EXEMPLO:
// LoginPage.js
class LoginPage {
  get emailField() { return $('#email'); }
  get passwordField() { return $('#password'); }
  
  login(email, password) {
    this.emailField.setValue(email);
    this.passwordField.setValue(password);
    this.loginButton.click();
  }
}
```

#### **"Quais frameworks você conhece? Web, Mobile, API?"**

**Por Categoria:**
```
WEB AUTOMATION:
🔧 Selenium (Java, C#, Python, JS)
🔧 Cypress (JavaScript) - Modern, fast
🔧 Playwright (Multi-browser, multi-language)
🔧 WebDriverIO (JavaScript/TypeScript)

MOBILE AUTOMATION:
📱 Appium (Cross-platform)
📱 Espresso (Android nativo)
📱 XCUITest (iOS nativo)
📱 Detox (React Native)

API AUTOMATION:
🌐 Rest Assured (Java)
🌐 Postman/Newman
🌐 SuperTest (Node.js)
🌐 Requests (Python)

ESCOLHA BASEADA EM:
- Stack da empresa
- Experiência da equipe
- Tipo de aplicação
- Recursos disponíveis
```

### Ferramentas e Tecnologias

#### **"Quais ferramentas de CI/CD você conhece?"**

**Ferramentas por Categoria:**
```
CI/CD PLATFORMS:
🔄 Jenkins (Open source, flexível)
🔄 GitLab CI (Integrado ao GitLab)
🔄 GitHub Actions (Integrado ao GitHub)
🔄 Azure DevOps (Microsoft ecosystem)
🔄 CircleCI (Cloud-native)

IMPLEMENTAÇÃO DE TESTES:
1. Trigger: Push/PR no repositório
2. Build: Compilar código + testes
3. Test: Executar suíte automatizada
4. Report: Gerar relatórios
5. Deploy: Se testes passarem

PIPELINE EXEMPLO:
Code → Build → Unit Tests → Integration Tests → E2E Tests → Deploy
```

#### **"Ferramentas de gestão que você usa?"**

**Categorias de Ferramentas:**
```
GESTÃO DE PROJETOS:
📊 Jira (Atlassian) - Tickets, sprints
📊 Azure DevOps - Microsoft ecosystem  
📊 Trello - Kanban simples
📊 Asana - Gestão de tarefas

DOCUMENTAÇÃO:
📝 Confluence (Wiki)
📝 Notion (All-in-one)
📝 GitBook (Documentação técnica)

COMUNICAÇÃO:
💬 Slack (Chat)
💬 Microsoft Teams (Colaboração)
💬 Discord (Comunidades)

VERSIONAMENTO:
🔧 Git (Distributed)
🔧 SVN (Centralized)
🔧 TFS (Team Foundation Server)
```

## 📱 Testes Mobile

### Estratégias Mobile

#### **"O que é importante testar em um aplicativo mobile?"**

**Checklist Mobile:**
```
📱 FUNCIONALIDADES:
- Navegação e usabilidade
- Gestos touch (tap, swipe, pinch)
- Orientação (portrait/landscape)
- Campos de entrada (teclado virtual)

🔋 PERFORMANCE:
- Tempo de inicialização
- Consumo de bateria
- Uso de memória/CPU
- Tamanho do app

🌐 CONECTIVIDADE:
- Funcionamento offline
- Sincronização ao voltar online
- Diferentes tipos de rede (2G/3G/4G/5G/WiFi)
- Mudança de rede durante uso

🔔 INTEGRAÇÕES:
- Notificações push
- Câmera e galeria
- GPS e localização
- Sensores (acelerômetro, giroscópio)

📊 COMPATIBILIDADE:
- Múltiplos dispositivos
- Diferentes versões do SO
- Diferentes tamanhos de tela
```

#### **"Como escolher dispositivos de teste?"**

**Estratégia de Seleção:**
```
DADOS PARA ANÁLISE:
📊 Analytics do app atual (Firebase, App Store Connect)
📊 Market share por região
📊 Público-alvo específico

MATRIZ DE DISPOSITIVOS:
┌─────────────┬─────────────┬─────────────┐
│   SO        │ Mais Usado  │ Crítico     │
├─────────────┼─────────────┼─────────────┤
│ Android     │ Samsung S23 │ Xiaomi      │
│ iOS         │ iPhone 14   │ iPhone SE   │
└─────────────┴─────────────┴─────────────┘

CRITÉRIOS:
- Top 5 dispositivos mais usados
- Dispositivos com menor/maior tela
- Versões mínimas suportadas
- Dispositivos problemáticos conhecidos
```

#### **"Nativo vs Web vs Híbrido?"**

**Comparativo Técnico:**
```
APLICATIVO NATIVO:
✅ Performance máxima
✅ Acesso completo às APIs do SO
✅ UX otimizada para plataforma
❌ Desenvolvimento separado (iOS/Android)
❌ Maior custo de desenvolvimento

APLICATIVO WEB:
✅ Único código para todas plataformas
✅ Facilidade de atualização
✅ Menor custo de desenvolvimento
❌ Performance limitada
❌ Acesso limitado às APIs do device

APLICATIVO HÍBRIDO:
✅ Código compartilhado
✅ Acesso às APIs nativas (via plugins)
✅ Deploy nas app stores
❌ Performance intermediária
❌ Dependência de frameworks terceiros

FERRAMENTAS:
- Nativo: Swift/Kotlin
- Web: React/Angular/Vue
- Híbrido: React Native, Flutter, Ionic
```

## 🗣️ Perguntas Comportamentais

### Estratégias de Resposta

#### **"Qual foi o seu principal desafio na carreira?"**

**Estrutura de Resposta (STAR):**
```
SITUAÇÃO:
"Em um projeto de e-commerce, tínhamos prazo apertado e equipe reduzida..."

TAREFA:
"Precisava garantir qualidade sem atrasar o go-live..."

AÇÃO:
"Implementei estratégia de risk-based testing, priorizei automação dos fluxos críticos..."

RESULTADO:
"Entregamos no prazo com 95% de cobertura dos cenários críticos e zero bugs críticos em produção"

APRENDIZADO:
"Aprendi a importância da priorização e comunicação com stakeholders"
```

#### **"Um projeto que atuou e usa como referência?"**

**Template de Resposta:**
```
CONTEXTO DO PROJETO:
- Tipo: [E-commerce/Mobile/API]
- Duração: [6 meses]
- Equipe: [5 pessoas - 2 devs, 1 QA, 1 PO, 1 SM]

RESPONSABILIDADES:
- Estratégia de testes end-to-end
- Automação com [Framework escolhido]
- Implementação de CI/CD

CONTRIBUIÇÕES ESPECÍFICAS:
- Reduzi tempo de regressão de 8h para 2h
- Implementei 150 casos automatizados
- Criei framework de dados de teste

RESULTADOS MENSURÁVEIS:
- 40% redução de bugs em produção
- 60% economia de tempo em regressão
- 95% de satisfação da equipe com processo

TECNOLOGIAS:
[Lista as tecnologias relevantes para a vaga]
```

#### **"O que você agregaria para a equipe de Qualidade?"**

**Proposta de Valor:**
```
CONHECIMENTO TÉCNICO:
- Experiência em [tecnologias relevantes]
- Visão de arquitetura de testes
- Práticas de DevOps/CI-CD

SOFT SKILLS:
- Comunicação efetiva com stakeholders
- Mentalidade analítica para encontrar edge cases
- Colaboração próxima com desenvolvimento

MELHORIAS PROCESSUAIS:
- Implementação de shift-left testing
- Estratégias de test data management
- Métricas e KPIs de qualidade

INOVAÇÃO:
- Exploração de novas ferramentas
- Automação de processos manuais
- Cultura de qualidade na equipe
```

#### **"Está estudando algo no momento?"**

**Estrutura de Resposta:**
```
ESTUDO ATUAL:
"Estou estudando [tecnologia específica]"

MOTIVAÇÃO:
"Porque percebo que o mercado está caminhando para..."

APLICAÇÃO:
"Já implementei um projeto pessoal que..."

PRÓXIMOS PASSOS:
"Planejo aplicar esse conhecimento em..."

EXEMPLOS ATUAIS (2024):
- IA/ML para testes (test data generation)
- Testes de performance com K6
- Contract testing com Pact
- Accessibility testing
- Security testing
```

## 🎭 Dicas de Apresentação

### Como se Comportar na Entrevista

#### **Antes da Entrevista**
```
📝 PREPARAÇÃO:
- Revisar CV e projetos mencionados
- Preparar perguntas sobre a empresa
- Testar equipamentos (câmera, áudio)
- Escolher ambiente silencioso

🎯 MINDSET:
- Confiança sem arrogância
- Curiosidade genuína sobre a vaga
- Foco em contribuição, não só benefícios
```

#### **Durante a Entrevista**
```
💬 COMUNICAÇÃO:
- Seja claro e objetivo
- Use exemplos práticos
- Desenhe diagramas se necessário
- Admita quando não souber algo

🧠 ESTRATÉGIAS:
- Use a técnica STAR para exemplos
- Conecte respostas com a vaga
- Mostre evolução e aprendizado
- Faça perguntas inteligentes
```

#### **Perguntas para Fazer ao Entrevistador**
```
SOBRE O PROCESSO:
- "Como é o processo de desenvolvimento aqui?"
- "Qual o nível de automação atual?"
- "Como vocês medem qualidade?"

SOBRE A EQUIPE:
- "Como é a estrutura da equipe de QA?"
- "Quais são os principais desafios técnicos?"
- "Qual stack tecnológico vocês usam?"

SOBRE CRESCIMENTO:
- "Quais oportunidades de desenvolvimento existem?"
- "Como vocês apoiam aprendizado contínuo?"
- "Qual a perspectiva para a área de QA?"
```

---

## ✅ Checklist Pré-Entrevista

### 24h Antes da Entrevista

**Preparação Técnica:**
- [ ] Revisar fundamentos de teste
- [ ] Praticar explicar projetos anteriores
- [ ] Preparar exemplos com método STAR
- [ ] Revisar tecnologias da empresa

**Preparação Prática:**
- [ ] Testar setup técnico (câmera, áudio, internet)
- [ ] Preparar ambiente silencioso
- [ ] Imprimir/ter acesso ao CV
- [ ] Preparar perguntas para o entrevistador

**Preparação Mental:**
- [ ] Dormir bem na noite anterior
- [ ] Chegar 10-15 min antes (presencial/online)
- [ ] Ter água por perto
- [ ] Respirar fundo e relaxar

### Durante a Entrevista

**Comunicação:**
- [ ] Manter contato visual (câmera)
- [ ] Falar de forma clara e pausada
- [ ] Usar gestos naturais
- [ ] Sorrir quando apropriado

**Estratégias:**
- [ ] Ouvir completamente a pergunta
- [ ] Pedir esclarecimento se necessário
- [ ] Estruturar resposta antes de falar
- [ ] Dar exemplos concretos

### Pós-Entrevista

**Immediately After:**
- [ ] Anotar impressões e feedback
- [ ] Enviar thank you note (se apropriado)
- [ ] Refletir sobre pontos de melhoria

**Follow-up:**
- [ ] Aguardar prazo informado
- [ ] Se necessário, enviar follow-up educado
- [ ] Continuar estudando independente do resultado


## 💡 Dicas Finais de Ouro

### Para se Destacar Positivamente

**1. Demonstre Paixão pela Qualidade**
- Fale sobre iniciativas próprias de melhoria
- Mostre preocupação com experiência do usuário
- Cite exemplos de quando foi além do esperado

**2. Prove Pensamento Analítico**
- Decomponha problemas complexos
- Use dados para justificar decisões
- Mostre raciocínio lógico nas respostas

**3. Evidencie Aprendizado Contínuo**
- Mencione cursos/certificações recentes
- Fale sobre experimentação com novas tecnologias
- Demonstre adaptabilidade a mudanças

**4. Mostre Soft Skills**
- Dê exemplos de colaboração efetiva
- Demonstre comunicação clara
- Evidencie resolução de conflitos

### Red Flags a Evitar

**❌ Nunca diga:**
- "Não tenho experiência com isso" (sem complementar)
- "Na minha empresa anterior fazíamos tudo errado"
- "Não gosto de trabalhar com [tecnologia/pessoa]"
- "Só quero fazer automação" (para vaga mista)

**✅ Alternativas positivas:**
- "Não tenho experiência direta, mas estudei sobre..."
- "Em experiências anteriores, identifiquei oportunidades de melhoria..."
- "Prefiro [tecnologia X] por [motivos técnicos], mas sou adaptável"
- "Vejo valor tanto na automação quanto nos testes manuais..."

### Fechamento Forte

**Última impressão:**
- Reitere interesse genuíno na vaga
- Resuma suas principais qualificações
- Agradeça pelo tempo dedicado
- Seja profissional e entusiasmado

## Extras

1. **Conceitos ágil**
   1. Você sabe me falar um pouco sobre como é o processo de teste no ciclo de desenvolvimento?
   2. Como você prioriza as tarefas em um contexto ágil?
   3. Quando é a hora de parar de testar?
   4. Como é o ciclo de vida do bug em um contexto ágil?
   5. Fale um pouco sobre o conceito de Scrum, Kanban (papéis, cerimônias)?
2. **Outros tópicos**
   1. Como é a sua metodologia de trabalho?
   2. Qual foi o seu principal desafio na carreira?
   3. Um projeto que atuou e usa como referência? No que contribuiu?
   4. Um projeto que atuou e não deu certo? Qual foi o problema?
   5. O que você agregaria para a equipe de Qualidade?
   6. Na área(testes e qualidade de software) cita algo que gosta de fazer e algo que não gosta de fazer...
   7. Está estudando algo nesse momento, pode citar o que/motivo...
3. **Conceitos gerais**
   1. O que é Teste funcional?
   2. O que é Teste não funcional?
   3. Cite exemplos de testes funcionais e não funcionais?
   4. Explique sobre a técnica de partição de equivalência?
   5. Explique sobre a técnica de análise de valor limite?
   6. O que é smoke test?
   7. O que é sanity test?
   8. O que é teste unitário, como é feito e porque quem é feito?
   9. O que é testes de integração?
   10. O que é testes de interface do usuário?
   11. Me fale sobre a pirâmide de Testes (conceito, como funciona)?
   12. O que é teste de mutação?
   13. Explique como escrever um caso de teste?
   14. Casos de Teste (estrutura dos casos de teste)?
   15. O que é BDD(estrutura, ferramentas e o que é gherkin) ?
   16. Conhece TDD ou ATDD, fale sobre?
   17. Sobre mock (para que serve, como funciona, quando utilizar)?
   18. Bug report (o que deve conter na descrição de um bug)?
   19. Como priorizar os bugs (como categorizar um bug) ?
   20. Quais heurísticas de testes você conhece? Fale sobre ela?
   21. CI x CD (para que serve, como deve ser implementado)?
   22. Sobre testes de API (quais ferramentas utilizadas, para que serve, status code, verbos HTTP)?
   23. O que deve conter em um relatório de testes (o que deve conter, quando gerar)?
   24. Métricas de testes (quais métricas utilizar)?
4. Ferramentas
   1. Como priorizar o que será automatizado?
   2. Qual é a importância da automação de testes?
   3. Page Objects (o que é, para que serve, como é estruturado no código)?
   4. Quais frameworks de testes automatizados você conhece? web, mobile e api?
      1. Exemplo: Selenium, WebDriverIO, robot framework, Protactor, Watir, Appium, Espresso, XCUITest, etc
   5. Quais ferramentas de gestão de dependências você já usou? (ex.: Maven, package.json, gemfile)
   6. Ferramentas de gerenciamento? (azure, jira, trello e etc..)
   7. Localizadores de elemento (quais existem, qual é mais performático)?
   8. Qual biblioteca de assertion vc já usou/usa (qual biblioteca utiliza, exemplos de assertion que utiliza no projeto, como validar os testes)
   9. O que é o cucumber, para que serve?
   10. O que é Data driven?
   11. Quais ferramentas de controle de versão (ex.: Git, SVN, TFS, etc) você conhece?
   12. Quais ferramentas de virtualização você conhece (ex.: Docker, Podman) ? já usou ou estudou qual? Para que usou?
   13. Ferramenta de CI (ex.: Jenkins, Gitlab, CircleCI, Bitrise, etc)
   14. Ferramenta de bugtracking (ex.: JIRA, Bugzilla, Mantis, etc)
   15. Device farm/Multi Browser (ex.: Browserstack, AWS Device Farm, Saucelabs, Firebase)
   16. Ferramentas controle mobile (Firebase, Testflight, Crashlytics, Bitrise)
   17. Quais bancos de dados você conhece (ex. Oracle, SQL, Mongo, Dynamo, Postgresql e ect..)?
   18. Fale um pouco sobre testes multi browser/multi devices?
       1. Exemplos de situações:
          1. Quando um determinado elemento demora para aparecer na tela, como tratar? (Exemplo de resposta: utilizar waits ao invés de esperas fixas (Thread.sleep())
          2. Como fazer um teste que o cadastro de cliente é único por CPF? (Exemplo de respostas: pode utilizar libs de geração de dados randômicos; pode excluir o registro logo antes/após o cadastro)
          3. Como fazer o teste da exclusão de um registro para que ele seja independente dos outros? (Exemplo de resposta: ter uma query ou chamada que cadastre primeiro o registro antes de excluí-lo)
5. Conceitos testes mobile
   1. O que é importante testar em um aplicativo mobile?
   2. Como escolher os dispositivos de teste? (exemplo: verificar quais são os devices mais utilizados através firebase ou outros.)
   3. Conceito de aplicativo nativo, web e híbrido?
   4. Me diga quais ferramentas para automação mobile você conhece? Como você faz para testar ios e android (faz separado ou em um mesmo projeto? Como foi montado a arquitetura do projeto?)



---

> **🎯 Lembre-se:** A entrevista é uma conversa de duas vias. Você está avaliando a empresa tanto quanto ela está avaliando você. Seja autêntico, prepare-se bem, e mostre seu valor de forma confiante mas humilde.