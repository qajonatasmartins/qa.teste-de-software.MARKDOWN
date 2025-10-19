# Guia Completo: Desafios Técnicos para QAs

**Objetivo:** Este guia fornece dicas práticas e estruturadas para entregar desafios técnicos de qualidade em processos seletivos de QA.

## 📋 Índice

1. [Preparação Inicial](#preparação-inicial)
2. [Estrutura e Organização do Projeto](#estrutura-e-organização-do-projeto)
3. [Padrões de Desenvolvimento](#padrões-de-desenvolvimento)
4. [Arquitetura e Design Patterns](#arquitetura-e-design-patterns)
5. [Documentação](#documentação)
6. [Diferenciação e Valor Agregado](#diferenciação-e-valor-agregado)
7. [Checklist de Entrega](#checklist-de-entrega)
8. [Erros Comuns a Evitar](#erros-comuns-a-evitar)

---

## 🚀 Preparação Inicial

### Análise do Desafio

**Antes de começar a codar:**

1. **Leia completamente** o desafio técnico
2. **Identifique os requisitos** explícitos e implícitos
3. **Defina o escopo** - o que será testado?
4. **Escolha a tecnologia** adequada para o contexto
5. **Estime o tempo** necessário para cada etapa

### Planejamento da Estratégia

```
📝 Template de Planejamento:

□ Aplicação a ser testada: _______________
□ Tipos de teste necessários: ____________
□ Framework escolhido: __________________
□ Padrões a serem aplicados: ____________
□ Funcionalidades críticas: _____________
□ Tempo estimado: ______________________
```

---

## 🏗️ Estrutura e Organização do Projeto

### Convenção de Nomenclatura

**Padrão para nome do projeto:**
```
[sigla_empresa].[nome_aplicacao]-[finalidade].[framework_linguagem]
```

**Exemplos:**
- `MG.amazon-test.Cypress` 
- `XP.serasa-api-automation.RestAssured`
- `ITU.mercadolivre-mobile.Appium`
- `ABC.webapp-e2e.Playwright`

## 📝 Padrões de Desenvolvimento

### Arquivo de Code Review (CODE_REVIEW.md)

Crie um arquivo dedicado com padrões de desenvolvimento:

#### Nomenclatura de Métodos

**Para obter texto de elementos:**

[getText]+[Nome do mapeamento do elemento]

```javascript
// ✅ Padrão correto
getTextLblNameClient()
getTextLblTotalPrice()
getTextLblErrorMessage()

// ❌ Evitar
pegaNome()
getText()
obtemTextoCliente()
```

**Para preencher campos:**

[set]+[Nome do mapeamento do elemento]

```javascript
// ✅ Padrão correto
setInpNameCompany()
setInpEmailUser()
setInpPasswordLogin()

// ❌ Evitar
preencheCampo()
setText()
digitaNome()
```

**Para ações específicas:**

[click]+[Nome do mapeamento do elemento]

```javascript
// ✅ Padrão correto
clickBtnSubmit()
selectBtnOptionCountry()

// ❌ Evitar
clica()
seleciona()
espera()
```

#### Padrão de Escrita de Testes

```javascript
// ✅ Estrutura recomendada
describe('Login Functionality', () => {
    it('Deve exibir menssagem de sucesso com credenciais válidas', () => {
      // (Arrange)
      // (Act)  
      // (Assert)
    });
  
    it('Deve exibir menssagem de erro com credenciais inválidas', () => {
      // (Arrange)
      // (Act)  
      // (Assert)
    });
});
```

---

## 🏛️ Arquitetura e Design Patterns

### Page Object Model (POM)

- Estrutura básica

### App Actions Pattern

- Para aplicações complexas

### Fluent Page

- Para aplicações Java

### Screenplay Pattern

- Somente se solicitado em desafios, pois é uma abordagem que exige muito conhecimento em programação. Opte pelos outros padrões de projeto em desafios.

---

## 📚 Documentação

### README.md Completo

**Template estruturado:**

```markdown
# [Nome do Projeto] - Automação de Testes

## 📖 Sobre o Projeto
Breve descrição do que foi testado e objetivos.

## 🛠️ Tecnologias Utilizadas
- **Framework:** Cypress v12.0
- **Linguagem:** JavaScript (ES6+)
- **Pattern:** Page Object Model
- **CI/CD:** GitHub Actions
- **Reports:** Mochawesome

### Por que essas tecnologias?
- **Cypress:** Escolhido pela facilidade de debugging e execução em tempo real
- **JavaScript:** Linguagem nativa do Cypress, melhor performance
- **POM:** Facilita manutenção e reutilização de código

## 🏗️ Estrutura do Projeto
```
projeto/
├── cypress/
│   ├── e2e/           # Testes end-to-end
│   ├── pages/         # Page Objects
│   ├── fixtures/      # Dados de teste
│   └── support/       # Comandos customizados
```

## 🚀 Como Executar
```bash
# Instalar dependências
npm install

# Executar testes headless
npm run test

# Executar com interface gráfica
npm run test:open
```

## 📊 Relatórios
Os relatórios são gerados automaticamente em `/reports` após execução.

## 🎯 Cenários de Teste
- [ ] Login com credenciais válidas
- [ ] Login com credenciais inválidas  
- [ ] Validação de campos obrigatórios
- [ ] Logout do sistema

## 🏆 Funcionalidades Extras
- Pipeline CI/CD automatizado
- Análise de código com SonarQube
- Screenshots automáticos em falhas
- Relatórios HTML detalhados
```

### Documentação da Arquitetura

**ARCHITECTURE.md:**
```markdown
# Arquitetura do Projeto

## Design Patterns Utilizados

### Page Object Model
- **Localização:** `/cypress/pages/`
- **Responsabilidade:** Encapsular elementos e ações da página
- **Benefícios:** Reutilização, manutenibilidade, legibilidade

### Command Pattern  
- **Localização:** `/cypress/support/commands.js`
- **Responsabilidade:** Comandos customizados reutilizáveis
- **Exemplo:** `cy.login(email, password)`

## Estrutura de Dados
- **Fixtures:** Dados estáticos em JSON
- **Environment:** Configurações por ambiente
- **Config:** Configurações do framework
```

---

## 🌟 Diferenciação e Valor Agregado

### 1. Pipeline CI/CD

**GitHub Actions (.github/workflows/tests.yml):**

```yaml
name: E2E Tests
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - name: Install dependencies
        run: npm ci
      - name: Run tests
        run: npm run test:ci
      - name: Upload reports
        uses: actions/upload-artifact@v3
        if: always()
        with:
          name: test-reports
          path: reports/
```

### 2. Análise de Código (SonarQube)

**sonar-project.properties:**
```properties
sonar.projectKey=projeto-qa-teste
sonar.projectName=Projeto QA Teste
sonar.projectVersion=1.0
sonar.sources=cypress/
sonar.language=js
sonar.sourceEncoding=UTF-8
```

### 3. Relatórios Avançados

**Configuração Mochawesome:**
```javascript
// cypress.config.js
module.exports = {
  reporter: 'mochawesome',
  reporterOptions: {
    reportDir: 'reports',
    overwrite: false,
    html: true,
    json: true,
    charts: true
  }
}
```

### 4. Configuração Multi-ambiente

```javascript
// cypress.config.js
module.exports = {
  env: {
    staging: {
      baseUrl: 'https://staging.app.com'
    },
    production: {
      baseUrl: 'https://app.com'
    }
  }
}
```

---

## ✅ Checklist de Entrega

### Antes de Enviar

**Código e Estrutura:**
- [ ] Nome do projeto segue padrão estabelecido
- [ ] Estrutura de pastas organizada e lógica
- [ ] Padrões de nomenclatura consistentes
- [ ] Design pattern implementado (POM/App Actions)
- [ ] Idioma padronizado em todo projeto
- [ ] Código limpo e comentado quando necessário

**Documentação:**
- [ ] README.md completo e detalhado
- [ ] CODE_REVIEW.md com padrões de desenvolvimento
- [ ] Documentação da arquitetura
- [ ] Instruções de execução claras
- [ ] Explicação das tecnologias escolhidas

**Funcionalidades:**
- [ ] Testes executando sem erros
- [ ] Cenários de teste relevantes implementados
- [ ] Validações adequadas nos testes
- [ ] Tratamento de erros implementado
- [ ] Evidências de execução (screenshots/vídeos)

**Extras (Diferenciação):**
- [ ] Pipeline CI/CD configurado
- [ ] Análise estática de código (SonarQube)
- [ ] Relatórios HTML gerados
- [ ] Configuração multi-ambiente
- [ ] Comandos customizados úteis

**Segurança:**
- [ ] Nenhum dado sensível commitado
- [ ] Arquivos de configuração local no .gitignore
- [ ] Credenciais usando variáveis de ambiente
- [ ] Código próprio (não copiado da empresa atual)

---

## ❌ Erros Comuns a Evitar

### 1. Problemas de Segurança
```bash
# ❌ NUNCA commitar
config/secrets.json
.env
credentials.txt
company-specific-configs/

# ✅ Sempre no .gitignore
*.env
config/local.json
cypress.env.json
```

### 2. Estrutura Desorganizada
```
# ❌ Evitar
tests/
├── test1.js
├── test2.js
├── login.js
├── utils.js
└── data.json

# ✅ Preferir
tests/
├── pages/
├── specs/
├── fixtures/
└── utils/
```

### 3. Código Sem Padrão
```javascript
// ❌ Inconsistente
function login() { }
const clickButton = () => { }
var getTexto = function() { }

// ✅ Consistente
const loginUser = () => { }
const clickButtonSubmit = () => { }
const getTextWelcomeMessage = () => { }
```

### 4. Documentação Insuficiente
```markdown
# ❌ README básico
## Como usar
npm test

# ✅ README completo
## Sobre o Projeto
[Descrição detalhada]

## Tecnologias e Justificativas
[Lista com explicações]

## Como Executar
[Instruções passo a passo]

## Estrutura do Projeto
[Explicação de cada pasta/arquivo]
```

---

## 🎯 Dicas Finais de Ouro

### Para se Destacar:

1. **Demonstre Pensamento Crítico**
   - Justifique escolhas técnicas
   - Documente decisões de arquitetura
   - Explique trade-offs considerados

2. **Mostre Conhecimento de Mercado**
   - Use ferramentas modernas e relevantes
   - Implemente práticas de DevOps
   - Demonstre preocupação com qualidade de código

3. **Vá Além do Básico**
   - Adicione testes de diferentes tipos (E2E, API, Performance)
   - Configure ambientes diferentes
   - Implemente relatórios customizados

4. **Profissionalismo**
   - Código limpo e bem estruturado
   - Commits descritivos e organizados
   - Documentação como em projetos reais

### Cronograma Sugerido:

**Para desafio de 1 semana:**
- **Dia 1-2:** Análise e planejamento
- **Dia 3-4:** Desenvolvimento dos testes
- **Dia 5:** Documentação e extras
- **Dia 6:** Revisão e refinamentos
- **Dia 7:** Entrega e verificação final

**Lembre-se:** A qualidade é mais importante que a quantidade. É melhor entregar poucos cenários bem estruturados do que muitos cenários mal organizados. Sempre entregue o desafio independente se finalizou ou não.

---

> **💡 Dica Extra:** Após enviar, acompanhe se há feedback e esteja preparado para explicar suas escolhas técnicas durante possível apresentação do projeto.