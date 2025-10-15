# Severidade vs Criticidade em Testes de Software

## Introdução

No contexto de teste de software, dois conceitos fundamentais frequentemente geram confusão entre profissionais iniciantes: **Severidade** e **Criticidade**. Embora ambos sejam usados para classificar defeitos e priorizar correções, eles representam perspectivas diferentes e complementares na gestão da qualidade de software.

Esta distinção é importante para testadores, desenvolvedores e gestores, pois permite uma comunicação mais precisa, priorização adequada de recursos e tomada de decisões mais eficientes no processo de desenvolvimento.

## Conceitos Fundamentais

### 1. Severidade (Severity)

**Definição:** A severidade refere-se ao **impacto técnico** que um defeito causa no funcionamento do software. É uma medida que indica quão grave é o problema do ponto de vista funcional, sem considerar fatores externos como contexto de negócio ou cronograma.

#### Características da Severidade:
- Foco no **impacto técnico** do defeito
- Classificação **objetiva** baseada no comportamento do sistema
- **Não muda** com o tempo ou contexto de negócio
- Definida pela **equipe técnica** (testadores/desenvolvedores)

#### Escala Típica de Severidade:

**Crítica (Critical):**
- Sistema completamente inoperante
- Perda de dados críticos
- Falhas de segurança graves

**Alta (High):**
- Funcionalidade principal não funciona
- Workaround complexo ou inexistente
- Impacto significativo na experiência do usuário

**Média (Medium):**
- Funcionalidade secundária afetada
- Workaround simples disponível
- Comportamento inesperado menor

**Baixa (Low):**
- Problemas cosméticos
- Funcionalidades opcionais afetadas
- Desvios menores da especificação

### 2. Criticidade (Priority)

**Definição:** A criticidade refere-se à **urgência de negócio** para corrigir um defeito. É uma medida que considera fatores como impacto nos usuários, cronograma de entrega, custos e objetivos estratégicos da organização.

#### Características da Criticidade:
- Foco no **impacto de negócio** do defeito
- Classificação **subjetiva** baseada em contexto empresarial
- **Pode mudar** conforme cronograma e prioridades
- Definida por **gestores/stakeholders** de negócio

#### Escala Típica de Criticidade:

**Urgente (Urgent):**
- Bloqueio total de release
- Impacto direto na receita
- Exposição pública negativa

**Alta (High):**
- Afeta funcionalidade principal do produto
- Impacto em usuários chave
- Pode atrasar release

**Média (Medium):**
- Deve ser corrigida em versão futura
- Impacto moderado nos usuários
- Não bloqueia release atual

**Baixa (Low):**
- Pode ser adiada
- Impacto mínimo
- Será tratada quando houver tempo

## Relação entre Severidade e Criticidade

### Matriz de Classificação

| Severidade | Criticidade Alta | Criticidade Média | Criticidade Baixa |
|------------|-----------------|-------------------|-------------------|
| **Crítica**    | Emergência      | Urgente          | Alta             |
| **Alta**       | Urgente         | Alta             | Média            |
| **Média**      | Alta            | Média            | Baixa            |
| **Baixa**      | Média           | Baixa            | Muito Baixa      |

### Cenários Comuns de Divergência

#### Cenário 1: Alta Severidade, Baixa Criticidade
```typescript
// Exemplo: Bug em funcionalidade raramente usada
class RelatorioAvancado {
    gerarRelatorioComplexo(): void {
        // DEFEITO: Crash ao gerar relatório com mais de 10.000 registros
        throw new Error("Memory overflow");
    }
}
```
- **Severidade:** Alta (sistema trava)
- **Criticidade:** Baixa (poucos usuários usam esta função)

#### Cenário 2: Baixa Severidade, Alta Criticidade
```typescript
// Exemplo: Erro de texto em tela principal
class TelaLogin {
    exibirMensagemBoasVindas(): string {
        // DEFEITO: Texto incorreto na tela principal
        return "Bem-vindos ao sistama";  // "sistama" em vez de "sistema"
    }
}
```
- **Severidade:** Baixa (apenas erro de texto)
- **Criticidade:** Alta (todos os usuários veem o erro)

## Exemplos Práticos por Contexto

### E-commerce

#### Defeito 1: Falha no Pagamento
```typescript
class ProcessadorPagamento {
    processarPagamento(valor: number): boolean {
        // DEFEITO: Sempre retorna false para valores acima de R$ 1000
        if (valor > 1000) {
            return false;
        }
        return true;
    }
}
```
- **Severidade:** Crítica (transação não funciona)
- **Criticidade:** Urgente (perda direta de receita)

#### Defeito 2: Cor do Botão Incorreta
```typescript
class BotaoComprar {
    renderizar(): void {
        // DEFEITO: Botão azul em vez de verde conforme design
        this.cor = "azul";  // Deveria ser "verde"
    }
}
```
- **Severidade:** Baixa (problema visual)
- **Criticidade:** Média (pode afetar conversão de vendas)

### Sistema Bancário

#### Defeito 3: Saldo Incorreto
```typescript
class ContaBancaria {
    calcularSaldo(): number {
        // DEFEITO: Cálculo incorreto em transferências
        return this.saldoAtual - this.valorTransferencia * 2;  // Multiplicando por 2 incorretamente
    }
}
```
- **Severidade:** Crítica (dados financeiros incorretos)
- **Criticidade:** Urgente (impacto financeiro direto)

#### Defeito 4: Logo Desatualizada
```typescript
class CabecalhoSistema {
    exibirLogo(): void {
        // DEFEITO: Logo antiga sendo exibida
        this.logo = "logo_2019.png";  // Deveria ser "logo_2024.png"
    }
}
```
- **Severidade:** Baixa (problema visual)
- **Criticidade:** Baixa (não afeta funcionalidade)

## Métricas Derivadas

### Métricas de Severidade

#### 1. Distribuição de Defeitos por Severidade
Esta métrica mostra como os defeitos estão distribuídos entre os diferentes níveis de severidade em um projeto. É fundamental para entender a qualidade geral do software e identificar padrões problemáticos.

**Como calcular:**
- Conte quantos defeitos existem em cada categoria de severidade
- Calcule a porcentagem de cada categoria em relação ao total
- Compare com benchmarks da indústria ou projetos anteriores

**Exemplo prático:**
- Total de defeitos: 100
- Crítica: 3 defeitos (3%)
- Alta: 15 defeitos (15%)
- Média: 50 defeitos (50%)
- Baixa: 32 defeitos (32%)

**Interpretação:** Uma alta concentração de defeitos críticos e de alta severidade pode indicar problemas estruturais no desenvolvimento ou testes insuficientes.

#### 2. Taxa de Defeitos Críticos
Esta métrica indica a porcentagem de defeitos que podem comprometer completamente o funcionamento do sistema.

**Fórmula:** (Defeitos Críticos / Total de Defeitos) × 100

**Benchmarks típicos:**
- **Excelente:** < 2%
- **Bom:** 2-5%
- **Aceitável:** 5-10%
- **Problemático:** > 10%

**Uso:** Indicador chave de qualidade e estabilidade do produto antes do lançamento.

#### 3. Tempo Médio de Resolução por Severidade
Mede quanto tempo, em média, leva para corrigir defeitos de cada nível de severidade.

**Tempos esperados:**
- **Crítica:** Máximo 4 horas (correção imediata)
- **Alta:** Máximo 24 horas (próximo dia útil)
- **Média:** Máximo 72 horas (dentro da semana)
- **Baixa:** Máximo 1 semana (quando houver capacidade)

**Importância:** Ajuda no planejamento de recursos e estabelecimento de SLAs (Service Level Agreements).

### Métricas de Criticidade

#### 1. Distribuição por Criticidade de Negócio
Mostra como os defeitos se distribuem conforme sua urgência empresarial, independentemente do impacto técnico.

**Categorias típicas:**
- **Urgente:** Defeitos que bloqueiam lançamentos ou causam perda de receita
- **Alta:** Defeitos que afetam funcionalidades principais ou usuários importantes
- **Média:** Defeitos que devem ser corrigidos em versões futuras
- **Baixa:** Defeitos que podem ser adiados sem impacto significativo

**Análise:** Uma alta concentração de itens urgentes pode indicar problemas no processo de desenvolvimento ou pressão excessiva de cronograma.

#### 2. Custo de Atraso por Criticidade
Estima o impacto financeiro de não corrigir defeitos dentro do prazo esperado.

**Categorização de impacto:**
- **Urgente:** Alto impacto financeiro imediato (perda de receita, multas contratuais)
- **Alta:** Impacto moderado no cronograma (atraso de entregas, retrabalho)
- **Média:** Impacto mínimo no projeto atual (pode afetar versões futuras)
- **Baixa:** Sem impacto financeiro significativo

**Uso prático:** Auxilia na justificativa de investimentos em qualidade e priorização de recursos.

### Métricas Combinadas

#### 1. Índice de Risco do Projeto
Combina severidade técnica com criticidade de negócio para criar uma pontuação única de risco.

**Sistema de pontuação:**
- Severidade: Crítica (4), Alta (3), Média (2), Baixa (1)
- Criticidade: Urgente (4), Alta (3), Média (2), Baixa (1)
- **Risco = Severidade × Criticidade**

**Interpretação dos resultados:**
- **16 pontos:** Risco extremo - ação imediata necessária
- **12 pontos:** Risco alto - prioridade máxima
- **6-9 pontos:** Risco moderado - incluir no próximo sprint
- **1-4 pontos:** Risco baixo - backlog de melhorias

#### 2. Matriz de Priorização de Defeitos
Ferramenta visual que combina ambas as dimensões para facilitar decisões de priorização.

**Benefícios da abordagem combinada:**
- **Visão holística:** Considera tanto aspectos técnicos quanto de negócio
- **Decisões balanceadas:** Evita focar apenas em um critério
- **Comunicação melhorada:** Linguagem comum entre equipes técnicas e de negócio
- **Otimização de recursos:** Direciona esforços para máximo impacto

**Exemplo de uso:** Um defeito cosmético (baixa severidade) na tela de login pode ter alta criticidade se afeta a percepção da marca durante um lançamento importante.

## Processo de Classificação

### Etapas de Classificação

#### 1. Identificação e Documentação do Defeito
Antes de classificar um defeito, é essencial documentá-lo adequadamente com todas as informações necessárias.

**Informações essenciais:**
- **ID único:** Para rastreamento e referência
- **Título descritivo:** Resume o problema em poucas palavras
- **Descrição detalhada:** Explica o comportamento observado
- **Passos para reproduzir:** Sequência clara para replicar o problema
- **Resultado esperado:** O que deveria acontecer
- **Resultado atual:** O que realmente acontece
- **Evidências:** Screenshots, logs, vídeos quando aplicável

#### 2. Análise Técnica para Determinação da Severidade
A equipe técnica avalia o impacto funcional do defeito no sistema.

**Critérios de avaliação:**
- **Impacto funcional:** Quais funcionalidades são afetadas?
- **Extensão do problema:** O defeito afeta apenas uma função ou múltiplas áreas?
- **Disponibilidade de workarounds:** Existe forma alternativa de realizar a tarefa?
- **Estabilidade do sistema:** O defeito causa travamentos ou comportamento instável?
- **Perda de dados:** Há risco de perda ou corrupção de informações?

**Perguntas-chave:**
- O sistema continua operacional?
- Os usuários conseguem completar suas tarefas principais?
- Existe risco para a integridade dos dados?
- Quantas funcionalidades são impactadas?

#### 3. Análise de Negócio para Determinação da Criticidade
A equipe de negócio ou gestores avaliam a urgência empresarial da correção.

**Fatores de negócio:**
- **Impacto nos usuários:** Quantos usuários são afetados e com que frequência?
- **Cronograma de entrega:** O defeito pode atrasar lançamentos planejados?
- **Custos envolvidos:** Qual o custo de manter o defeito vs. corrigi-lo?
- **Reputação da empresa:** O defeito pode afetar a imagem da organização?
- **Conformidade regulatória:** Há implicações legais ou regulamentares?

**Perguntas-chave:**
- Este defeito bloqueia o lançamento do produto?
- Quantos clientes podem ser impactados?
- Há riscos financeiros ou regulatórios?
- Qual o custo de oportunidade de não corrigir imediatamente?

#### 4. Validação e Consenso
Etapa crucial para alinhar expectativas e garantir classificação adequada.

**Processo de consenso:**
- **Revisão multidisciplinar:** Envolver representantes técnicos e de negócio
- **Discussão aberta:** Permitir questionamentos e diferentes perspectivas
- **Documentação das justificativas:** Registrar os motivos das decisões
- **Aprovação formal:** Confirmar a classificação com stakeholders responsáveis
- **Comunicação clara:** Informar todas as partes interessadas sobre as decisões

**Pontos de atenção:**
- Evitar classificações baseadas em emoções ou pressões
- Considerar o contexto atual do projeto
- Manter consistência com classificações anteriores
- Estar aberto a reclassificações quando necessário

## Boas Práticas

### Para Testadores

#### 1. Documentação Clara e Completa
A qualidade da documentação impacta diretamente na eficácia da classificação.

**Elementos essenciais do relatório:**
- **Identificação única:** Código ou número para rastreamento
- **Severidade justificada:** Explicar por que foi classificada daquela forma
- **Criticidade contextualizada:** Relacionar com objetivos de negócio
- **Impacto detalhado:** Descrever consequências específicas
- **Evidências anexadas:** Screenshots, logs, gravações quando necessário

**Exemplo de boa documentação:**
"Severidade: Alta - Sistema trava completamente ao processar pedidos acima de R$ 1000, impedindo conclusão de transações. Criticidade: Urgente - Afeta 15% dos pedidos durante período de promoção, com impacto direto na receita."

#### 2. Critérios Objetivos e Consistentes
**Estratégias para manter objetividade:**
- **Checklists de classificação:** Criar guias rápidos para cada nível
- **Exemplos de referência:** Manter biblioteca de casos já classificados
- **Calibração regular:** Revisar classificações antigas para manter consistência
- **Treinamento contínuo:** Atualizar conhecimento sobre critérios
- **Revisão por pares:** Validar classificações com outros testadores

#### 3. Comunicação Efetiva
- Usar linguagem clara e não técnica ao comunicar com stakeholders de negócio
- Explicar impactos em termos de experiência do usuário
- Fornecer estimativas realistas de esforço para correção
- Manter atualizações regulares sobre status dos defeitos

### Para Gestores

#### 1. Priorização Estratégica
**Fatores para decisão equilibrada:**
- **Combinar dimensões:** Nunca priorizar baseado apenas em severidade ou criticidade
- **Recursos disponíveis:** Considerar capacidade atual da equipe de desenvolvimento
- **Impacto no cronograma:** Avaliar efeito nas entregas planejadas
- **Custo-benefício:** Comparar esforço de correção vs. impacto de manter o defeito
- **Dependências:** Identificar defeitos que podem bloquear outras atividades

#### 2. Monitoramento e Governança
**Práticas de acompanhamento:**
- **Métricas regulares:** Revisar distribuição de defeitos semanalmente
- **Tendências históricas:** Identificar padrões que indicam problemas sistêmicos
- **SLA de correção:** Estabelecer e monitorar tempos de resposta por severidade
- **Comunicação com stakeholders:** Manter transparência sobre status e prioridades
- **Ajustes dinâmicos:** Estar preparado para reclassificar conforme contexto muda

#### 3. Liderança e Cultura
- **Fomentar colaboração:** Promover diálogo construtivo entre equipes técnicas e de negócio
- **Evitar culpabilização:** Focar na resolução, não na atribuição de responsabilidade
- **Investir em prevenção:** Usar dados de defeitos para melhorar processos
- **Reconhecer boas práticas:** Valorizar equipes que mantêm alta qualidade

## Ferramentas de Apoio

### Sistemas de Gerenciamento de Defeitos

#### Ferramentas Populares
**Jira (Atlassian):**
- Campos customizáveis para severidade e criticidade
- Workflows automatizados baseados em classificação
- Dashboards para visualização de métricas
- Integração com ferramentas de desenvolvimento

**Azure DevOps (Microsoft):**
- Work items com classificação de prioridade e severidade
- Rastreabilidade completa do ciclo de vida
- Relatórios automáticos de distribuição
- Integração com pipelines de CI/CD

**Bugzilla (Mozilla):**
- Campos nativos de priority e severity
- Sistema robusto e gratuito
- Customizações avançadas disponíveis
- Comunidade ativa de suporte

**GitHub Issues:**
- Sistema de labels para classificação
- Templates customizáveis para reports
- Integração nativa com código
- Boa opção para projetos open source

#### Características Essenciais
**Funcionalidades indispensáveis:**
- **Campos obrigatórios:** Garantir que severidade e criticidade sejam sempre informadas
- **Workflows automatizados:** Direcionar defeitos para pessoas certas baseado na classificação
- **Notificações inteligentes:** Alertar stakeholders sobre defeitos críticos imediatamente
- **Relatórios customizáveis:** Gerar métricas específicas para diferentes audiências
- **Histórico de mudanças:** Rastrear alterações de classificação ao longo do tempo

### Guias de Classificação

#### Template de Severidade
**Crítica - Sistema Inoperante:**
- Sistema completamente fora do ar
- Perda ou corrupção de dados críticos
- Falhas graves de segurança
- Exemplo: "Usuários não conseguem acessar o sistema"

**Alta - Funcionalidade Principal Comprometida:**
- Funcionalidade principal não funciona
- Sem workaround disponível
- Impacto significativo na experiência
- Exemplo: "Checkout não finaliza compras"

**Média - Funcionalidade Secundária Afetada:**
- Funcionalidade secundária com problemas
- Workaround simples disponível
- Impacto moderado na experiência
- Exemplo: "Filtro de busca não funciona corretamente"

**Baixa - Problemas Menores:**
- Problemas cosméticos ou de usabilidade
- Funcionalidades opcionais afetadas
- Desvios menores da especificação
- Exemplo: "Botão com cor ligeiramente diferente do design"

#### Template de Criticidade
**Urgente - Bloqueio Crítico:**
- Impede lançamento de produto
- Perda direta de receita
- Exposição pública negativa
- Exemplo: "Bug descoberto 1 hora antes do lançamento"

**Alta - Impacto Significativo:**
- Afeta usuários principais
- Pode atrasar entregas importantes
- Impacto na satisfação do cliente
- Exemplo: "Funcionalidade usada por 80% dos usuários"

**Média - Impacto Moderado:**
- Deve ser corrigida em versão futura
- Impacto limitado nos usuários
- Não bloqueia release atual
- Exemplo: "Melhoria solicitada por alguns usuários"

**Baixa - Impacto Mínimo:**
- Pode ser adiada indefinidamente
- Impacto quase imperceptível
- Será tratada quando houver capacidade
- Exemplo: "Ajuste cosmético em tela pouco acessada"

## Casos de Estudo

### Caso 1: Sistema de Saúde

#### Contexto
Sistema hospitalar para gerenciamento de pacientes

#### Defeito Encontrado
```typescript
class AgendamentoPaciente {
    agendarConsulta(pacienteId: string, data: Date): boolean {
        // DEFEITO: Permite agendar consultas em datas passadas
        return this.salvarAgendamento(pacienteId, data);
    }
}
```

#### Classificação
- **Severidade:** Alta (funcionalidade principal comprometida)
- **Criticidade:** Urgente (impacto direto no atendimento ao paciente)
- **Justificativa:** Embora seja um problema de validação, afeta diretamente o cuidado com pacientes

### Caso 2: Aplicativo de Delivery

#### Contexto
App de entrega de comida durante período de promoção

#### Defeito Encontrado
```typescript
class CalculadoraDesconto {
    aplicarPromocao(valorPedido: number): number {
        // DEFEITO: Desconto sendo aplicado incorretamente
        return valorPedido - (valorPedido * 0.50);  // 50% em vez de 15%
    }
}
```

#### Classificação
- **Severidade:** Alta (cálculo incorreto afeta transações)
- **Criticidade:** Urgente (perda financeira durante promoção)
- **Justificativa:** Impacto financeiro direto durante evento promocional

## Conclusão

A distinção clara entre severidade e criticidade é fundamental para:

### Benefícios da Classificação Adequada
- **Comunicação eficaz** entre equipes técnicas e de negócio
- **Priorização otimizada** de recursos de desenvolvimento
- **Gestão de riscos** mais precisa
- **Tomada de decisões** baseada em dados objetivos
- **Melhoria contínua** dos processos de qualidade

### Pontos-Chave para Iniciantes
1. **Severidade** = Impacto técnico (objetivo)
2. **Criticidade** = Urgência de negócio (subjetivo)
3. **Ambos são importantes** para priorização
4. **Podem divergir** conforme contexto
5. **Métricas derivadas** auxiliam na gestão

### Recomendações Finais
- Estabelecer critérios claros e documentados
- Treinar equipe para classificação consistente
- Revisar periodicamente as classificações
- Usar métricas para monitorar qualidade
- Manter comunicação aberta entre áreas

## Referências

- ISTQB Foundation Level Syllabus - International Software Testing Qualifications Board
- IEEE 829-2008 - Standard for Software and System Test Documentation
- ISO/IEC 25010:2011 - Systems and software Quality Requirements and Evaluation
- "Software Testing: A Craftsman's Approach" - Paul C. Jorgensen
- "Agile Testing: A Practical Guide" - Lisa Crispin & Janet Gregory