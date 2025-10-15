# WWWWWHKE - Heurística para Análise de Requisitos

**Criador:** Darren Mc Millan

## O que é a Heurística WWWWWHKE?

A heurística WWWWWHKE (pronuncia-se como "Wiki") é uma ferramenta mnemônica criada por Darren Mc Millan para análise estruturada de requisitos de software. Esta técnica utiliza uma série de perguntas fundamentais combinadas com conhecimento e experiência do testador para identificar lacunas, ambiguidades e problemas potenciais em documentações de requisitos.

O acrônimo representa as perguntas em inglês que devem ser feitas durante a análise:
- **W**ho (Quem)
- **W**hat (O que) 
- **W**hen (Quando)
- **W**here (Onde)
- **W**hy (Por que)
- **H**ow (Como)
- **K**nowledge (Conhecimento)
- **E**xperience (Experiência)

## Detalhamento de Cada Componente

### **W - Who (Para Quem)**
Identifica os usuários, stakeholders e responsáveis pelo sistema.

**Perguntas a fazer:**
- Quem são os usuários finais deste sistema?
- Quem irá implementar esta funcionalidade?
- Quem é responsável por aprovar esta feature?
- Quem será impactado por esta mudança?
- Quem pode fornecer feedback sobre este requisito?

**Exemplo Prático - Sistema de E-commerce:**
```
Requisito: "O sistema deve permitir login"

Perguntas Who:
• Quem fará login? (Clientes, administradores, vendedores?)
• Quem pode redefinir senhas? 
• Quem tem acesso a dados de login?
• Quem irá desenvolver esta funcionalidade?
• Quem testará diferentes tipos de usuário?

Resultado: Descobrimos que existem 3 tipos de usuário com permissões diferentes.
```

### **W - What (O Que)**
Define exatamente o que precisa ser implementado.

**Perguntas a fazer:**
- O que exatamente esta funcionalidade deve fazer?
- O que acontece em caso de erro?
- O que constitui sucesso nesta operação?
- O que não está incluído neste requisito?
- O que pode dar errado?

**Exemplo Prático - Upload de Arquivos:**
```
Requisito: "Usuários podem fazer upload de documentos"

Perguntas What:
• O que são "documentos"? (PDF, DOC, imagens?)
• O que é o tamanho máximo permitido?
• O que acontece se o upload falhar?
• O que fazer com arquivos corrompidos?
• O que é exibido durante o upload?

Resultado: Especificação mais clara sobre tipos, tamanhos e tratamento de erros.
```

### **W - When (Quando)**
Estabelece timing, sequência e condições temporais.

**Perguntas a fazer:**
- Quando esta funcionalidade deve estar disponível?
- Quando ela deve ser executada?
- Quando ela não deve funcionar?
- Quando expira ou é invalidada?
- Quando deve notificar usuários?

**Exemplo Prático - Sistema de Notificações:**
```
Requisito: "Enviar notificação de promoção para usuários"

Perguntas When:
• Quando enviar? (Horário específico, evento específico?)
• Quando não enviar? (Fins de semana, feriados?)
• Quando parar de enviar? (Usuário optou por sair?)
• Quando reenviar se falhar?
• Quando considerar a notificação expirada?

Resultado: Definição de cronograma e regras de negócio para envios.
```

### **W - Where (Onde)**
Identifica localização, contexto e ambiente.

**Perguntas a fazer:**
- Onde esta funcionalidade será usada?
- Onde os dados serão armazenados?
- Onde ocorre o processamento?
- Onde podem ocorrer falhas?
- Onde estão as dependências?

**Exemplo Prático - Sistema de Pagamentos:**
```
Requisito: "Processar pagamentos com cartão"

Perguntas Where:
• Onde os dados do cartão são processados? (Local, cloud?)
• Onde são armazenados? (Criptografados onde?)
• Onde ocorre a validação? (Frontend, backend?)
• Onde estão os logs de transação?
• Onde ficam as configurações de segurança?

Resultado: Mapeamento da arquitetura e fluxo de dados seguros.
```

### **W - Why (Por Que)**
Compreende a motivação e valor de negócio.

**Perguntas a fazer:**
- Por que esta funcionalidade é necessária?
- Por que agora?
- Por que esta abordagem foi escolhida?
- Por que não usar alternativas existentes?
- Por que este é um problema que precisa ser resolvido?

**Exemplo Prático - Feature de Chat:**
```
Requisito: "Adicionar chat em tempo real"

Perguntas Why:
• Por que usuários precisam de chat? (Suporte? Vendas?)
• Por que tempo real é importante?
• Por que não usar email ou telefone?
• Por que implementar internamente vs. usar soluções prontas?
• Por que esta é uma prioridade agora?

Resultado: Validação do valor de negócio e justificativa para investimento.
```

### **H - How (Como)**
Detalha a implementação e o funcionamento.

**Perguntas a fazer:**
- Como esta funcionalidade funcionará?
- Como os usuários irão interagir?
- Como será integrado com sistemas existentes?
- Como será testado?
- Como será mantido?

**Exemplo Prático - Sistema de Busca:**
```
Requisito: "Implementar busca avançada de produtos"

Perguntas How:
• Como usuários inserem critérios de busca?
• Como os resultados são ordenados?
• Como funciona com produtos em promoção?
• Como é a performance com muitos produtos?
• Como funciona busca por voz?

Resultado: Especificação técnica detalhada da implementação.
```

### **K - Knowledge (Conhecimento)**
Aplica conhecimento técnico e de domínio.

**Perguntas baseadas em conhecimento:**
- Que tecnologias são adequadas para isto?
- Que padrões de design se aplicam?
- Que regulamentações devem ser consideradas?
- Que melhores práticas existem?
- Que limitações técnicas podem existir?

**Exemplo Prático - Sistema Bancário:**
```
Requisito: "Transferência internacional de dinheiro"

Perguntas Knowledge:
• Que regulamentações bancárias se aplicam?
• Que protocolos de segurança são obrigatórios?
• Que taxas de câmbio devem ser consideradas?
• Que limites regulamentares existem?
• Que validações de compliance são necessárias?

Resultado: Requisitos técnicos e legais mais completos.
```

### **E - Experience (Experiência)**
Utiliza experiência prévia com projetos similares.

**Perguntas baseadas em experiência:**
- Que problemas similares já enfrentamos?
- Que soluções funcionaram bem no passado?
- Que armadilhas comuns devemos evitar?
- Que feedback de usuários já recebemos?
- Que lições aprendidas se aplicam?

**Exemplo Prático - Sistema de Relatórios:**
```
Requisito: "Gerar relatórios mensais automaticamente"

Perguntas Experience:
• Que problemas tivemos com relatórios anteriores?
• Que formatos os usuários realmente usam?
• Que horários causam menos impacto no sistema?
• Que falhas de email já ocorreram?
• Que reclamações sobre relatórios já recebemos?

Resultado: Implementação que evita problemas conhecidos.
```

## Aplicação Prática Passo a Passo

### Exemplo Completo: Funcionalidade de Reset de Senha

**Requisito Original:** "Usuários devem poder redefinir suas senhas"

#### Aplicando WWWWWHKE:

**WHO - Quem:**
- Quem pode redefinir senhas? → Usuários finais, administradores
- Quem aprova esta redefinição? → Sistema automaticamente, ou requer aprovação?
- Quem recebe notificações? → Usuário, equipe de segurança

**WHAT - O que:**
- O que constitui uma senha válida? → Critérios de complexidade
- O que acontece com a senha antiga? → Invalidada imediatamente
- O que fazer se email não for entregue? → Processo alternativo

**WHEN - Quando:**
- Quando o link de reset expira? → 1 hora, 24 horas?
- Quando notificar sobre tentativas? → Imediatamente
- Quando bloquear tentativas excessivas? → Após quantas tentativas?

**WHERE - Onde:**
- Onde o usuário inicia o processo? → Tela de login, perfil
- Onde são enviados os emails? → Email principal, secundário
- Onde ficam armazenados os tokens? → Banco de dados, cache

**WHY - Por que:**
- Por que permitir reset? → Usuários esquecem senhas
- Por que não usar pergunta secreta? → Menos seguro
- Por que email é o método escolhido? → Verificação de identidade

**HOW - Como:**
- Como validar identidade? → Email + token único
- Como gerar tokens seguros? → Algoritmo específico
- Como integrar com email? → Serviço SMTP, API de email

**KNOWLEDGE - Conhecimento:**
- Que padrões de segurança aplicar? → OWASP, criptografia
- Que regulamentações considerar? → LGPD, GDPR
- Que ataques prevenir? → Brute force, credential stuffing

**EXPERIENCE - Experiência:**
- Que problemas já tivemos? → Emails na spam, tokens expirados
- Que feedback recebemos? → Processo muito complexo
- Que melhorias implementamos? → Interface mais clara

### Resultado da Análise:
```
Requisito Refinado:
"Usuários finais podem solicitar redefinição de senha através da tela de login, 
recebendo um email com link válido por 1 hora. O sistema deve:
- Validar complexidade da nova senha
- Invalidar a senha anterior imediatamente
- Registrar todas as tentativas para auditoria
- Bloquear após 3 tentativas em 1 hora
- Notificar sobre atividade suspeita
- Funcionar com provedores de email principais
- Ser acessível em dispositivos móveis"
```

## Quando Aplicar WWWWWHKE

### **Cenários Ideais:**
- **Análise de novos requisitos**
- **Revisão de especificações**
- **Refinamento de user stories**
- **Preparação para estimativas**
- **Sessões de brainstorming**

### **Momento da Aplicação:**
- Durante reuniões de refinamento
- Antes de iniciar desenvolvimento
- Em revisões de design
- Durante análise de impacto
- Em sessões de planning

## Dicas Práticas para Iniciantes

### 1. **Comece Simples**
- Use um requisito por vez
- Anote todas as perguntas que surgirem
- Não tente responder tudo de uma vez
- Foque nas perguntas mais importantes primeiro

### 2. **Colabore com a Equipe**
- Aplique em grupo sempre que possível
- Diferentes perspectivas enriquecem a análise
- Documente as descobertas
- Compartilhe insights com stakeholders

### 3. **Pratique Regularmente**
- Use em requisitos existentes para praticar
- Desenvolva intuição sobre que perguntas fazer
- Crie checklists personalizados para seu domínio
- Refine sua abordagem com base na experiência

### 4. **Adapte ao Contexto**
- Nem todas as perguntas se aplicam a todos os requisitos
- Priorize com base no risco e complexidade
- Adapte a profundidade da análise ao tempo disponível
- Use conhecimento específico do domínio

## Exemplo de Checklist para Aplicação

```
□ WHO - Identifiquei todos os stakeholders?
□ WHAT - O requisito está claro e completo?
□ WHEN - Timing e condições estão definidos?
□ WHERE - Contexto e ambiente estão claros?
□ WHY - A justificativa faz sentido?
□ HOW - A implementação é viável?
□ KNOWLEDGE - Apliquei conhecimento técnico relevante?
□ EXPERIENCE - Considerei lições aprendidas?
□ Documentei todas as descobertas?
□ Identifiquei próximos passos?
```

## Limitações e Cuidados

### **Limitações:**
- Não substitui conhecimento técnico profundo
- Pode ser demorada para requisitos simples
- Requer experiência para fazer boas perguntas
- Pode gerar análise excessiva (analysis paralysis)

### **Cuidados:**
- **Balance profundidade vs. tempo:** Nem todo requisito precisa análise completa
- **Foque no valor:** Priorize perguntas que agregam valor real
- **Documente decisões:** Registre por que certas perguntas não se aplicam
- **Iterate:** Refine a análise conforme aprende mais sobre o sistema

## Referências

- [Artigo original - "Wiki" (WWWWWH/KE) requirements testing mnemonic](https://www.bettertesting.co.uk/content/?p=857) - Darren Mc Millan