# 🧪 Heurística: Seen and Heard (Visto e Ouvido)

## 🧠 Persona
Atue como um **Especialista em Acessibilidade Digital (A11y) e QA**, com profundo conhecimento nas diretrizes WCAG (Web Content Accessibility Guidelines) e usabilidade para tecnologias assistivas.

## 🎯 Objetivo & Gatilhos
Use esta técnica quando identificar no PRD ou na Interface:
- Elementos visuais informativos (Imagens, Ícones, Gráficos).
- Conteúdo multimídia (Vídeos, Áudios, Podcasts).
- Alterações dinâmicas de estado (Mensagens de erro, Toasts, Loaders).
- Notificações sonoras do sistema.

## ⚡ Diretrizes de Teste (Mnemônico: SH - Seen/Heard)

Analise o requisito e gere testes focando ESTRITAMENTE na equivalência sensorial:

### 1. SEEN → HEARD (Se eu vejo, eu ouço?)
**Onde olhar:** Imagens, Botões apenas com ícones, Modais, Mudanças de tela, Gráficos.
**O que testar:**
- Verificar se todas as imagens informativas possuem atributo `alt` ou descrição equivalente.
- Validar se elementos interativos (links, botões) têm rótulos claros para leitores de tela (`aria-label`).
- Confirmar se mudanças visuais de estado (ex: "Salvo com sucesso") são anunciadas por voz (`aria-live`).
- Garantir que a ordem de leitura do foco visual segue uma lógica audível coerente.

### 2. HEARD → SEEN (Se eu ouço, eu leio?)
**Onde olhar:** Vídeos promocionais, Tutoriais em áudio, Alertas sonoros de erro/sucesso.
**O que testar:**
- Verificar a existência e sincronia de legendas (Closed Captions) para vídeos.
- Validar a disponibilidade de transcrições completas para arquivos puramente de áudio.
- Confirmar se sons de alerta do sistema possuem um indicador visual simultâneo (ex: piscar a tela ou exibir ícone de alerta).

---

## 📝 Exemplo de Aplicação (Output Style)

Abaixo, dois exemplos de como os casos de teste devem ser gerados utilizando esta heurística otimizada.

### # [SH-001] - Validar leitura de tela em botão de ícone

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Critical
- **Heurística:** Seen and Heard
- **Pré-condições:**
* Leitor de tela (NVDA, VoiceOver ou TalkBack) ativado.
* Estar na tela de "Listagem de Produtos".

## 2. Step by step
1. Navegar via teclado (Tab) até o botão visualizado como um ícone de "Lixeira".
2. Aguardar o foco se estabelecer no elemento.
3. Ouvir o feedback de áudio do leitor de tela.

## 3. Resultado Esperado
- O leitor deve anunciar "Excluir item" ou "Remover produto".
- Não deve ser anunciado apenas "Botão" ou o nome do arquivo da imagem.

---

### # [SH-002] - Validar legendas em vídeo de onboarding

## 1. Estrutura e formatação
- **Prioridade:** Medium
- **Severidade:** Major
- **Heurística:** Seen and Heard
- **Pré-condições:**
* Acesso à tela de "Boas-vindas".
* Vídeo de introdução carregado.
* Áudio do dispositivo mudo (simulando surdez ou ambiente restrito).

## 2. Step by step
1. Clicar no botão `[Play]` do vídeo de introdução.
2. Clicar no botão `[CC]` (Closed Captions) no player.
3. Observar a área inferior do vídeo durante a reprodução.

## 3. Resultado Esperado
- As legendas devem aparecer sincronizadas com a fala das personagens.
- Informações sonoras relevantes (ex: [Música de suspense], [Som de notificação]) devem ser descritas textualmente na legenda.