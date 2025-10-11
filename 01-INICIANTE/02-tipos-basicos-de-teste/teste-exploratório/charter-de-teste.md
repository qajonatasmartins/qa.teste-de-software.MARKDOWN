# Charter de Teste - Exploratory Testing

## O que é o Charter?

O **charter** é uma ferramenta fundamental na **Testagem Exploratória** (Exploratory Testing) para estruturar e orientar suas investigações. Ele serve como uma missão ou um lembrete para focar em um tipo específico de informação ou risco durante a exploração.

O objetivo final da criação de um charter é **descobrir informações de interesse e valor** para as partes interessadas (stakeholders). Um bom charter deve oferecer **direção sem especificar demais** as ações de teste.

### Definição

Um charter define o foco de uma sessão de exploração com tempo limitado (time-boxed session). Ele convida a diferentes tipos de exploração e orienta o testador.

Embora possa ser expresso de forma simples (ex: "Encontre maneiras pelas quais um cliente pode não conseguir concluir uma compra válida"), um charter geralmente segue um modelo de três partes essenciais:

1. **Alvo (Target):** Onde você está explorando (pode ser um recurso, um requisito ou um módulo).
2. **Recursos (Resources):** O que você trará consigo (pode ser uma ferramenta, um conjunto de dados, uma técnica, uma configuração, ou talvez um recurso interdependente).
3. **Informação (Information):** Que tipo de informação você espera descobrir (está buscando caracterizar segurança, desempenho, confiabilidade, usabilidade ou outro aspecto do sistema?).

## Quando Usar o Charter?

O chartering é um **processo contínuo** que deve ser integrado em todo o ciclo de desenvolvimento:

### Durante o Ciclo de Desenvolvimento

- **Desde o Início (Requisitos):** As discussões de requisitos são um momento ideal para começar a rascunhar charters. Começar cedo permite explorar ideias sobre o software antes mesmo que haja código implementado.

- **Em Sessões com Tempo Limitado:** Você estrutura seu tempo em uma série de sessões com tempo limitado (time-boxed) e estabelece um foco para cada sessão com antecedência através de um charter.

- **Ao Mapear o Terreno:** Ao explorar um sistema existente ou legado, um charter de reconhecimento (recon session) é usado para mapear o território, descobrir como o sistema funciona e determinar o escopo da exploração necessária.

- **Quando Sentir Dúvidas:** Se você começar a se sentir tentado a explorar em direções que estão "fora do charter" atual, isso é um sinal de que você precisa anotar charters adicionais para perseguir em sessões posteriores.

## Como Usar o Charter (Geração e Aplicação)

### Fontes para Geração de Charters

Os charters podem ser gerados a partir de diversas fontes:

#### 1. Requisitos e Discussões

Perguntas que revelam incerteza, ambiguidade ou dependências durante as discussões de requisitos são ótimas fontes. Você pode usar os charters para alinhar seus objetivos com as preocupações dos stakeholders.

#### 2. Expectativas Implícitas

Critérios de qualidade transversal (crosscutting quality criteria) como confiabilidade, escalabilidade, desempenho ou segurança devem ser capturados como charters.

#### 3. Perguntas dos Stakeholders

Preocupações sobre o que acontecerá no futuro ou sobre possíveis riscos podem formar a base de charters.

#### 4. O Jogo do Título de Pesadelo (The Nightmare Headline Game)

Uma técnica para imaginar uma falha catastrófica (um "título de pesadelo") e, em seguida, trabalhar de trás para frente para identificar os riscos que poderiam levar a essa falha. Esses riscos se transformam em charters.

#### 5. Artefatos Existentes

O banco de dados de bugs ou comentários no código-fonte também podem gerar ideias para charters.

### Durante a Execução

Durante a execução da exploração, o charter funciona como um guia. Por exemplo, um charter focado em segurança incentivará o testador a "canalizar seu hacker interior".

## Itens de Atenção ao Usar Charters

A eficácia dos charters depende de um equilíbrio e uma mentalidade fluida.

### 1. Evitar Extremos na Especificidade

**Charters muito específicos são problemáticos:**

- Se forem muito específicos, eles se tornam apenas uma maneira diferente de expressar testes individuais
- Isso leva a um tempo excessivo gasto em documentação com pouco benefício
- Perde-se a essência da exploração

**Charters muito amplos são problemáticos:**

- Eles correm o risco de não fornecer foco suficiente
- Se o alvo for muito grande, você nunca saberá quando terminou a exploração
- É melhor criar múltiplos charters, cada um focado em uma única área e/ou um tipo específico de risco

### 2. Manter a Fluidez e Evitar o Planejamento Excessivo

**Não planeje todos os charters com antecedência:**

- Se você estiver acostumado a planejar testes em larga escala, pode ser tentador mapear todos os charters antes de começar
- No entanto, o chartering é um processo fluido
- Você não pode saber que tipo de informação encontrará até começar a explorar
- A informação recém-descoberta deve permitir que você ajuste sua exploração

**Use o modelo como guia, não como camisa de força:**

- O modelo de três partes (Alvo, Recursos, Informação) é uma sugestão
- Não tente forçar ideias ricas e complexas em um formato simplista
- Concentre-se em capturar a **intenção** da sessão

### 3. Foco no Valor

**Calibre com as partes interessadas:**

- Garanta que a informação que você busca seja valorizada
- Se as partes interessadas não agirem sobre a informação que você descobrir, você está perdendo tempo
- Pergunte-lhes se eles valorizam a informação que o charter pode revelar

## Exemplos Práticos para o Dia a Dia

### Exemplo 1: Sistema de E-commerce

**Charter Simples:**

``` text
Explorar o fluxo de checkout para identificar maneiras pelas quais um cliente 
pode perder seu carrinho de compras.
```

**Charter com Estrutura de 3 Partes:**

``` text
Alvo: Fluxo de checkout (adicionar ao carrinho até confirmação de pagamento)
Recursos: Múltiplos navegadores, interrupções de rede, sessões simultâneas
Informação: Identificar cenários onde dados do carrinho são perdidos ou produtos não são salvos corretamente
```

**Como aplicar no dia a dia:**

1. Reserve 90 minutos no seu calendário
2. Configure diferentes navegadores (Chrome, Firefox, Safari)
3. Durante a exploração:
   - Adicione produtos ao carrinho e feche o navegador abruptamente
   - Abra o site em duas abas e manipule o carrinho simultaneamente
   - Simule perda de conexão durante o checkout
   - Teste com cookies desabilitados
4. Documente qualquer comportamento inesperado

### Exemplo 2: Aplicativo de Banco Mobile

**Charter:**

``` text
Alvo: Funcionalidade de transferência entre contas
Recursos: Dispositivos Android e iOS, diferentes versões do OS, conectividades variadas (4G, WiFi, modo avião)
Informação: Avaliar a confiabilidade e segurança das transações em condições adversas de rede
```

**Como aplicar no dia a dia:**

1. Tempo da sessão: 120 minutos
2. Prepare os cenários:
   - Inicie uma transferência e coloque o app em segundo plano
   - Inicie uma transferência e desligue o WiFi no meio do processo
   - Tente fazer múltiplas transferências rapidamente
   - Teste com valores limites (R$ 0,01, valor máximo permitido)
3. Anote perguntas que surgirem: "O que acontece se o app crashar durante a transferência?"
4. Crie novos charters baseados nas descobertas

### Exemplo 3: Sistema de Gestão de Usuários

**Charter:**

``` text
Alvo: Funcionalidade de reset de senha
Recursos: Diferentes tipos de usuários (admin, usuário comum, usuário bloqueado), email clients variados, links expirados
Informação: Identificar vulnerabilidades de segurança e problemas de usabilidade no fluxo de recuperação de senha
```

**Como aplicar no dia a dia:**

1. Sessão de 60 minutos
2. Explore:
   - Solicite reset para email inexistente
   - Clique no link de reset após expiração
   - Tente usar o mesmo link múltiplas vezes
   - Solicite múltiplos resets consecutivos
   - Teste com senhas fracas vs senhas fortes
3. Pergunte-se: "Um atacante poderia abusar deste fluxo?"

### Exemplo 4: API REST de Produtos

**Charter:**

``` text
Alvo: Endpoints de criação e atualização de produtos (POST /products, PUT /products/{id})
Recursos: Postman/Insomnia, dados válidos e inválidos, tokens de autenticação variados
Informação: Validar tratamento de erros, validações de dados e comportamento sob requisições mal formadas
```

**Como aplicar no dia a dia:**

1. Sessão de 90 minutos
2. Experimente:
   - Envie campos obrigatórios vazios
   - Envie tipos de dados incorretos (string onde espera número)
   - Teste com payloads muito grandes
   - Use tokens expirados ou inválidos
   - Faça requisições concorrentes para o mesmo recurso
3. Documente as respostas de erro - estão claras e úteis?

## Template Prático para Criar Seus Charters

```markdown
# Charter: [Nome descritivo]

**Data:** [Data da sessão]
**Testador:** [Seu nome]
**Duração Planejada:** [90 minutos, por exemplo]

## Objetivo

[Descrição breve do que você pretende investigar]

## Estrutura

**Alvo (Target):** [Recurso, módulo ou área que será explorada]

**Recursos (Resources):** [Ferramentas, dados, configurações, técnicas que você usará]

**Informação (Information):** [Que tipo de informação você busca descobrir - bugs, riscos, comportamentos, etc.]

## Perguntas Orientadoras

- [Pergunta 1 que você quer responder]
- [Pergunta 2 que você quer responder]
- [Pergunta 3 que você quer responder]

## Notas da Sessão

[Durante a exploração, anote suas observações, bugs encontrados, 
 novos charters que surgirem, etc.]

## Resultados

**Bugs encontrados:** [Número e IDs]
**Novos charters gerados:** [Liste aqui]
**Riscos identificados:** [Liste aqui]
**Áreas que precisam mais exploração:** [Liste aqui]
```

## Dicas para Iniciantes

### Como Começar com Charters no Seu Dia a Dia

1. **Comece Pequeno**
   - Crie seu primeiro charter para uma funcionalidade que você já conhece
   - Reserve apenas 60 minutos para a primeira sessão
   - Não se preocupe em fazer perfeito - a prática leva à melhoria

2. **Faça Perguntas**
   - Antes de criar um charter, pergunte ao Product Owner: "Qual é sua maior preocupação com esta feature?"
   - Use essas preocupações como base para seus charters

3. **Documente de Forma Simples**
   - Não gaste mais tempo documentando do que explorando
   - Use bullet points, seja conciso
   - Foque em capturar insights e bugs, não em escrever um relatório bonito

4. **Aprenda com Cada Sessão**
   - Após cada sessão, reflita: "O charter me deu o foco necessário?"
   - Ajuste seu estilo de escrita de charters com base no que funcionou

5. **Compartilhe com o Time**
   - Mostre seus charters para desenvolvedores e outros testadores
   - Peça feedback sobre os alvos que você está escolhendo
   - Use charters como ferramenta de comunicação sobre cobertura de testes

### Erros Comuns a Evitar

```
❌ Erro: Criar charters muito detalhados como "Clicar no botão X, depois Y, depois Z"

✅ Correto: "Explorar o fluxo de onboarding identificando pontos onde usuários podem ficar confusos"
```

```
❌ Erro: Criar um charter vago como "Testar o sistema"
✅ Correto: "Explorar a funcionalidade de busca avançada com foco em performance com grandes volumes de dados"
```

```
❌ Erro: Planejar 50 charters antes de começar a testar
✅ Correto: Criar 3-5 charters iniciais e deixar que a exploração guie os próximos
```

```
❌ Erro: Seguir o charter religiosamente mesmo quando descobrir algo interessante fora do escopo
✅ Correto: Anotar rapidamente a descoberta "fora do charter" e criar um novo charter para explorá-la depois
```

## Como Integrar Charters em Metodologias Ágeis

### Durante a Sprint

- **Planning:** Identifique 2-3 áreas de risco e crie charters preliminares
- **Durante Desenvolvimento:** Execute sessões de 60-90 minutos quando features ficarem prontas
- **Daily:** Compartilhe brevemente descobertas importantes das sessões de exploração
- **Review:** Apresente insights obtidos através dos charters
- **Retrospective:** Discuta se os charters estão ajudando a encontrar bugs importantes

### Exemplo de Rotina Semanal

**Segunda-feira:**

- Revisar user stories da sprint
- Criar 3-5 charters baseados em riscos identificados

**Terça a Quinta:**

- Executar 1-2 sessões de charter por dia (90 min cada)
- Documentar descobertas
- Reportar bugs encontrados
- Criar novos charters baseados em descobertas

**Sexta-feira:**

- Revisar charters executados na semana
- Consolidar aprendizados
- Planejar charters para próxima sprint

## Benefícios dos Charters

- ✅ **Foco e Direção:** Evita exploração aleatória sem propósito
- ✅ **Comunicação:** Facilita explicar ao time o que você está testando
- ✅ **Cobertura:** Ajuda a garantir que diferentes aspectos do sistema sejam explorados
- ✅ **Documentação Leve:** Fornece registro do que foi testado sem burocracia excessiva
- ✅ **Flexibilidade:** Permite adaptação baseada em descobertas
- ✅ **Aprendizado:** Ajuda a desenvolver intuição sobre onde focar esforços de teste

## Ferramentas de Apoio

Você pode gerenciar seus charters usando:

- **Ferramentas Simples:**
  - Markdown files (como este)
  - Notion, Confluence ou Wiki do time
  - Trello ou Jira boards
  - Planilhas Google Sheets

- **Ferramentas Especializadas:**
  - Test Collab
  - qTest
  - TestRail (com customizações)

O importante não é a ferramenta, mas a **consistência e disciplina** em usar charters para guiar sua exploração.

## Evoluindo Sua Prática

À medida que você ganha experiência com charters:

1. **Nível Iniciante (1-3 meses):**
   - Use o template de 3 partes religiosamente
   - Foque em charters de funcionalidades óbvias
   - Execute sessões mais curtas (60 min)

2. **Nível Intermediário (3-9 meses):**
   - Experimente formatos diferentes de charter
   - Explore aspectos não-funcionais (performance, segurança)
   - Combine charters com técnicas específicas (boundary value, pairwise)

3. **Nível Avançado (9+ meses):**
   - Crie charters baseados em modelos de risco
   - Use charters para guiar testes de integração complexos
   - Ensine outros sobre chartering

## Conclusão

Os charters são uma ponte entre a estrutura necessária para trabalho produtivo e a liberdade necessária para exploração criativa. Eles não são scripts rígidos, mas sim convites para investigação focada.

Lembre-se: **o melhor charter é aquele que gera informação valiosa para seu time e stakeholders**. Comece simples, pratique regularmente e ajuste sua abordagem com base no feedback e resultados.

## 📖 Referências

- **HENDRICKSON, Elisabeth. Explore It!: Reduce Risk and Increase Confidence with Exploratory Testing. 1st ed. Raleigh, NC: Pragmatic Bookshelf, 2013.**
- **WHITTAKER, James; ARBON, Jason; CAROLLO, Jeff. How Google Tests Software. Boston: Addison-Wesley, 2012.**
  - Discute como Google usa exploratory testing e charters em larga escala

- **KANER, Cem; BACH, James; PETTICHORD, Bret. Lessons Learned in Software Testing. New York: Wiley, 2001.**
  - Lições sobre como estruturar testes exploratórios

- **Session-Based Test Management (SBTM)** - Desenvolvido por James e Jon Bach
  - Framework que usa charters como componente central
  - Website: https://www.satisfice.com/download/session-based-test-management
