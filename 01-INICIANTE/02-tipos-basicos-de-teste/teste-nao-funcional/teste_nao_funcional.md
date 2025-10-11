# Testes Não Funcionais: Conceitos e Aplicação Prática

## 📋 Definição

Os **testes não funcionais** de um sistema avaliam as características de qualidade de sistemas e softwares, como usabilidade, eficiência de performance ou segurança.

O teste não funcional responde à pergunta **"quão bem"** o sistema deve se comportar, enquanto o teste funcional responde **"o que"** o sistema deve fazer.

## 🎯 Características Principais

### Foco na Qualidade

- ✅ Avalia **como** o sistema funciona
- ✅ Mede características de qualidade
- ✅ Verifica requisitos não funcionais
- ✅ Testa atributos de qualidade

### Fundamentação Técnica (ISO 25010)

Segundo a **ISO 25010**, existem 9 características de qualidade de software:

- 1 característica = **Adequação Funcional** (testes funcionais)
- 8 características = **Testes Não Funcionais**

![ISO 25010](https://iso25000-com.translate.goog/images/figures/iso_25010_en.png?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc)

## 🚀 As 8 Características dos Testes Não Funcionais

## 1. ⚡ Eficiência de Desempenho

Essa característica representa o desempenho em relação à quantidade de recursos utilizados em condições declaradas.

### Sub-características:

#### Comportamento Temporal

**Definição**: Grau em que os tempos de resposta e processamento e as taxas de rendimento atendem aos requisitos.

**Exemplos Práticos**:

```
✅ Site de e-commerce deve carregar em menos de 3 segundos
✅ API deve responder em menos de 500ms
✅ Transação bancária deve processar em até 10 segundos
❌ Se demorar mais = problema de comportamento temporal
```

#### Utilização de Recursos

**Definição**: Grau em que as quantidades e tipos de recursos utilizados atendem aos requisitos.

**Exemplos Práticos**:

```
✅ App mobile deve usar no máximo 100MB de RAM
✅ Sistema deve usar no máximo 50% da CPU
✅ Backup deve usar no máximo 10GB de armazenamento
❌ Se exceder = problema de utilização de recursos
```

#### Capacidade

**Definição**: Grau em que os limites máximos de um produto ou parâmetro do sistema atendem aos requisitos.

**Exemplos Práticos**:

```
✅ Sistema deve suportar 10.000 usuários simultâneos
✅ Database deve armazenar até 1 milhão de registros
✅ Upload deve aceitar arquivos de até 50MB
❌ Se não suportar = problema de capacidade
```

## 2. 🔗 Compatibilidade

Grau em que um produto pode trocar informações com outros sistemas e executar suas funções enquanto compartilha o mesmo ambiente.

### Sub-características

#### Coexistência

**Definição**: Grau em que um produto pode executar suas funções eficientemente compartilhando ambiente com outros produtos.

**Exemplos Práticos**:
```
✅ Antivírus deve funcionar junto com navegadores
✅ App deve rodar junto com outros apps no celular
✅ Sistema deve funcionar com diferentes versões do Windows
❌ Se conflitar = problema de coexistência
```

#### Interoperabilidade

**Definição**: Grau em que sistemas podem trocar informações e usar as informações trocadas.

**Exemplos Práticos**:

```
✅ Sistema bancário deve integrar com Pix
✅ E-commerce deve integrar com correios
✅ CRM deve sincronizar com email marketing
❌ Se não integrar = problema de interoperabilidade
```

## 3. 👥 Capacidade de Interação (Interaction Capability)

Grau em que um produto pode ser usado por usuários especificados para atingir objetivos com eficácia, eficiência e satisfação em um contexto de uso especificado.

### Sub-características

#### Reconhecimento de Adequação

**Definição**: Grau em que os usuários podem reconhecer se um produto é apropriado para suas necessidades.

**Exemplos Práticos**:

```
✅ Interface do app deve deixar claro sua função
✅ Botões devem ter rótulos claros
✅ Menu deve mostrar opções disponíveis
❌ Se confundir = problema de reconhecimento
```

#### Aprendizagem

**Definição**: Grau em que usuários conseguem aprender a usar o produto com facilidade.

**Exemplos Práticos**:

```
✅ Tutorial interativo para novos usuários
✅ Interface intuitiva que não precisa manual
✅ Tooltips explicativos em funcionalidades complexas
❌ Se for difícil aprender = problema de aprendizagem
```

#### Operabilidade

**Definição**: Grau em que um produto possui atributos que facilitam a operação e o controle.

**Exemplos Práticos**:
```
✅ Atalhos de teclado para funções frequentes
✅ Interface responsiva (mobile-friendly)
✅ Navegação simples e intuitiva
❌ Se for difícil operar = problema de operabilidade
```

#### Proteção contra Erros do Usuário

**Definição**: Grau em que um sistema protege os usuários contra erros.

**Exemplos Práticos**:

```
✅ Confirmação antes de deletar dados importantes
✅ Validação de campos em tempo real
✅ Mensagens de erro claras e orientativas
❌ Se permitir erros críticos = problema de proteção
```

#### Estética da Interface

**Definição**: Grau em que uma interface permite uma interação agradável e satisfatória.

**Exemplos Práticos**:
```
✅ Design moderno e atrativo
✅ Cores e fontes que facilitam a leitura
✅ Layout organizado e limpo
❌ Se for visualmente ruim = problema estético
```

#### Acessibilidade (Inclusivity)

**Definição**: Grau em que um produto pode ser usado por pessoas com diversas características e capacidades.

**Exemplos Práticos**:
```
✅ Suporte a leitores de tela para deficientes visuais
✅ Contraste adequado para pessoas com baixa visão
✅ Navegação por teclado para quem não usa mouse
❌ Se excluir usuários = problema de acessibilidade
```

#### Engajamento do Usuário (User Engagement)

**Definição**: Grau em que a interface promove o interesse e motivação do usuário.

**Exemplos Práticos**:
```
✅ Interface atrativa que mantém o usuário envolvido
✅ Gamificação para incentivar uso contínuo
✅ Notificações relevantes que agregam valor
❌ Se o usuário não se engajar = problema de engajamento
```

#### Assistência ao Usuário (User Assistance)

**Definição**: Grau em que o produto fornece ajuda adequada aos usuários.

**Exemplos Práticos**:
```
✅ Sistema de help integrado e contextual
✅ Tutoriais e tours guiados para novas funcionalidades
✅ Chat de suporte ou FAQ acessível
❌ Se usuário ficar perdido = problema de assistência
```

#### Autodescritibilidade (Self-descriptiveness)

**Definição**: Grau em que o produto se explica por si mesmo sem necessidade de documentação externa.

**Exemplos Práticos**:
```
✅ Interface intuitiva com ícones universais
✅ Labels claros que explicam cada função
✅ Mensagens de status que informam o que está acontecendo
❌ Se precisar manual para entender = problema de autodescritibilidade
```

## 4. 🛡️ Confiabilidade

Grau em que um sistema executa funções especificadas sob condições especificadas por um período de tempo determinado.

### Sub-características

#### Maturidade

**Definição**: Grau em que um sistema atende às necessidades de confiabilidade em operação normal.

**Exemplos Práticos**:
```
✅ Sistema bancário deve ter 99.9% de disponibilidade
✅ E-commerce deve funcionar sem falhas críticas
✅ App não deve travar durante uso normal
❌ Se falhar frequentemente = problema de maturidade
```

#### Disponibilidade

**Definição**: Grau em que um sistema está operacional e acessível quando necessário.

**Exemplos Práticos**:

```
✅ Site deve estar no ar 24/7
✅ Sistema deve ter backup automático
✅ Redundância para evitar indisponibilidade
❌ Se ficar offline = problema de disponibilidade
```

#### Tolerância a Falhas

**Definição**: Grau em que um sistema opera conforme planejado, apesar da presença de falhas.

**Exemplos Práticos**:
```
✅ Sistema deve continuar funcionando se um serviço falhar
✅ Graceful degradation quando há sobrecarga
✅ Failover automático para servidor backup
❌ Se parar totalmente = problema de tolerância
```

#### Recuperabilidade

**Definição**: Grau em que um produto pode recuperar dados e restabelecer o estado desejado após falha.

**Exemplos Práticos**:
```
✅ Backup automático de dados importantes
✅ Restore rápido após falhas
✅ Auto-save de documentos em edição
❌ Se perder dados = problema de recuperabilidade
```

## 5. 🔒 Segurança

Grau em que um produto protege informações e dados, garantindo acesso apropriado conforme níveis de autorização.

### Sub-características

#### Confidencialidade

**Definição**: Grau em que dados são acessíveis apenas a quem está autorizado.

**Exemplos Práticos**:
```
✅ Dados pessoais devem ser criptografados
✅ Senhas não devem aparecer em logs
✅ Informações sensíveis devem ter acesso restrito
❌ Se vazar dados = problema de confidencialidade
```

#### Integridade

**Definição**: Grau em que um sistema impede acesso ou modificação não autorizada.

**Exemplos Práticos**:
```
✅ Dados não podem ser alterados sem autorização
✅ Checksum para validar integridade de arquivos
✅ Auditoria de todas as modificações
❌ Se dados forem corrompidos = problema de integridade
```

#### Não Repúdio

**Definição**: Grau em que ações podem ser comprovadas para que não possam ser negadas.

**Exemplos Práticos**:
```
✅ Log detalhado de todas as transações
✅ Assinatura digital em documentos importantes
✅ Rastreamento de ações por usuário
❌ Se não puder comprovar = problema de não repúdio
```

#### Prestação de Contas

**Definição**: Grau em que ações de uma entidade podem ser rastreadas exclusivamente à entidade.

**Exemplos Práticos**:
```
✅ Cada usuário deve ter login único
✅ Auditoria completa de ações por usuário
✅ Responsabilização por mudanças no sistema
❌ Se não rastrear = problema de prestação de contas
```

#### Autenticidade

**Definição**: Grau em que a identidade de um sujeito pode ser comprovada como a reivindicada.

**Exemplos Práticos**:
```
✅ Autenticação de dois fatores (2FA)
✅ Verificação de identidade por biometria
✅ Certificados digitais para verificação
❌ Se não autenticar = problema de autenticidade
```

## 6. 🔧 Capacidade de Manutenção (Maintainability)

Grau de eficácia e eficiência com que um produto pode ser modificado para melhorá-lo, corrigi-lo ou adaptá-lo.

### Sub-características

#### Modularidade

**Definição**: Grau em que um sistema é composto de componentes discretos com impacto mínimo entre si.

**Exemplos Práticos**:
```
✅ Código organizado em módulos independentes
✅ Alteração em um módulo não afeta outros
✅ Microserviços ao invés de monolito
❌ Se mudança quebrar tudo = problema de modularidade
```

#### Reutilização

**Definição**: Grau em que um ativo pode ser usado em múltiplos sistemas.

**Exemplos Práticos**:
```
✅ Bibliotecas de componentes reutilizáveis
✅ APIs que podem ser usadas por vários sistemas
✅ Templates que servem para diferentes projetos
❌ Se tiver que recriar tudo = problema de reutilização
```

#### Analisabilidade

**Definição**: Grau de facilidade para avaliar impacto de mudanças ou diagnosticar problemas.

**Exemplos Práticos**:
```
✅ Código bem documentado e comentado
✅ Logs detalhados para debugging
✅ Ferramentas de análise de impacto
❌ Se for difícil analisar = problema de analisabilidade
```

#### Modificabilidade

**Definição**: Grau em que um produto pode ser modificado sem introduzir defeitos.

**Exemplos Práticos**:
```
✅ Arquitetura que facilita mudanças
✅ Testes automatizados para validar alterações
✅ Código limpo e bem estruturado
❌ Se mudanças quebrarem = problema de modificabilidade
```

#### Testabilidade

**Definição**: Grau de facilidade para estabelecer critérios de teste e executá-los.

**Exemplos Práticos**:
```
✅ Código testável com baixo acoplamento
✅ Mocks e stubs para testes isolados
✅ Ambiente de teste dedicado
❌ Se for difícil testar = problema de testabilidade
```

## 7. 📦 Portabilidade


Grau de eficácia com que um sistema pode ser transferido de um ambiente para outro.

### Sub-características

#### Adaptabilidade

**Definição**: Grau em que um produto pode ser adaptado para diferentes ambientes.

**Exemplos Práticos**:
```
✅ App funciona em iOS e Android
✅ Sistema roda em Windows, Linux e Mac
✅ Responsivo para desktop e mobile
❌ Se só funcionar em um ambiente = problema de adaptabilidade
```

#### Instalabilidade

**Definição**: Grau de facilidade para instalar/desinstalar em um ambiente especificado.

**Exemplos Práticos**:
```
✅ Instalador automático e simples
✅ Desinstalação limpa sem deixar rastros
✅ Configuração mínima necessária
❌ Se for difícil instalar = problema de instalabilidade
```

#### Substituibilidade

**Definição**: Grau em que um produto pode substituir outro para a mesma finalidade.

**Exemplos Práticos**:
```
✅ Migração fácil entre sistemas similares
✅ Compatibilidade com formatos padrão
✅ Import/export de dados facilitado
❌ Se não puder substituir = problema de substituibilidade
```

## 8. ⚖️ Ausência de Risco (Freedom from Risk)

Grau em que um produto ou sistema mitiga o risco potencial para o status econômico, vida humana, saúde ou meio ambiente.

### Sub-características

#### Mitigação de Risco Econômico

**Definição**: Grau em que um produto reduz riscos relacionados a perdas financeiras.

**Exemplos Práticos**:
```
✅ Sistema bancário deve prevenir transações fraudulentas
✅ E-commerce deve proteger dados de cartão de crédito
✅ Backup automático para evitar perda de dados valiosos
❌ Se causar perdas financeiras = problema de risco econômico
```

#### Mitigação de Risco de Saúde e Segurança

**Definição**: Grau em que um produto reduz riscos à saúde e segurança das pessoas.

**Exemplos Práticos**:
```
✅ Software médico deve ter redundâncias de segurança
✅ Sistemas de controle industrial devem ter fail-safe
✅ Apps de saúde devem validar dados críticos
❌ Se colocar vidas em risco = problema de segurança crítica
```

#### Mitigação de Risco Ambiental

**Definição**: Grau em que um produto reduz riscos ao meio ambiente.

**Exemplos Práticos**:
```
✅ Software de controle de emissões deve ser preciso
✅ Sistemas de monitoramento ambiental devem ser confiáveis
✅ Otimização de energia para reduzir pegada carbono
❌ Se prejudicar meio ambiente = problema de risco ambiental
```

## 📊 Comparação: Funcional vs Não Funcional

| Aspecto | Teste Funcional | Teste Não Funcional |
|---------|----------------|---------------------|
| **Pergunta** | "O que o sistema faz?" | "Quão bem o sistema funciona?" |
| **Foco** | Funcionalidades | Qualidade |
| **Base** | Requisitos funcionais | Requisitos de qualidade |
| **Exemplo** | Login funciona corretamente? | Login é rápido e seguro? |
| **Resultado** | Passa/Falha | Métricas de qualidade |

## 📝 Exemplos Práticos para Iniciantes

### Teste de Performance (E-commerce)

``` text
Objetivo: Verificar tempo de resposta
Cenário: Black Friday com 50.000 usuários
Métrica: Página deve carregar em < 3 segundos
Resultado: Aprovado se atender, reprovado se não
```

### Teste de Usabilidade (App Bancário)

``` text
Objetivo: Verificar facilidade de uso
Cenário: Usuário idoso fazendo transferência
Métrica: Completar transferência em < 5 cliques
Resultado: Avaliar satisfação e dificuldades
```

### Teste de Segurança (Sistema de Pagamento)

``` text
Objetivo: Verificar proteção de dados
Cenário: Tentativa de acesso não autorizado
Métrica: Dados devem permanecer seguros
Resultado: Identificar vulnerabilidades
```

## 🛠️ Ferramentas Comuns

### Performance

- **JMeter**: Teste de carga e performance
- **LoadRunner**: Teste de performance enterprise
- **Artillery**: Teste de carga para APIs

### Segurança

- **OWASP ZAP**: Scanner de vulnerabilidades
- **Burp Suite**: Teste de segurança web
- **Nessus**: Scanner de vulnerabilidades

### Usabilidade

- **Hotjar**: Análise de comportamento do usuário
- **UserTesting**: Testes com usuários reais
- **Maze**: Testes de usabilidade

## 📚 Conclusão

Os testes não funcionais são fundamentais para garantir a qualidade completa do software. Eles complementam os testes funcionais, assegurando que o sistema não apenas funcione corretamente, mas também com qualidade adequada.

### Pontos-chave para iniciantes

- ✅ Testes não funcionais são sobre **qualidade**
- ✅ São baseados na **ISO 25010** (8 características não funcionais)
- ✅ Cada característica tem sub-características específicas
- ✅ Devem ser planejados desde o início do projeto
- ✅ Complementam os testes funcionais para cobertura completa

---

## 📖 Referências

- **ISTQB Foundation Level Syllabus v4.0** - [BSTQB](https://bstqb.online/files/syllabus_ctfl_4.0br.pdf)
- **ISO/IEC 25010:2011** - [ISO 25010 Portal](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010)
- [Diferença entre fases de teste, tipos de teste e formas de execução](https://www.zup.com.br/blog/fases-de-teste-tipos-de-teste)
- **ISTQB Glossary** - Definições oficiais de termos de teste