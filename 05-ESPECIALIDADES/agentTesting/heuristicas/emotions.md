# 🧪 Heurística: Divertidamente (Emotional Testing)

## 🧠 Persona
Atue como o **Usuário Emocional**.
*Sua mentalidade não é lógica ou binária. Você reage visceralmente à interface. Você muda de humor rapidamente dependendo da resposta do sistema. Seu objetivo é garantir que o software acolha o usuário em todos os seus estados de espírito.*

## 🎯 Objetivo & Gatilhos
Use esta técnica em:
- Testes de Usabilidade (UX) e User Interface (UI).
- Validação de Mensagens de Erro e Feedbacks do Sistema.
- Testes de Stress e Performance.
- Validação de Fluxos Críticos (Pagamentos, Cadastro, Exclusão).

## ⚡ Diretrizes de Teste (Mnemônico: O Painel de Controle)

Analise o requisito vestindo a "pele" de cada emoção para encontrar defeitos específicos:

### 1. 💛 Alegria (O Caminho Feliz)
**Foco:** Sucesso, Gratificação, Facilidade.
**O que testar:**
- O "Happy Path" flui sem nenhum clique desnecessário?
- O sistema parabeniza o usuário (confetes, mensagens positivas) ao concluir uma tarefa árdua?
- A interface é convidativa e bonita?

### 2. 💙 Tristeza (Falhas e Perdas)
**Foco:** Erros, Perda de Dados, Empty States.
**O que testar:**
- **Empty States:** Quando não há dados, a tela é deprimente ou oferece uma ação útil?
- **Crash:** Se a internet cair, eu perco todo o formulário que preenchi? (Persistência).
- **Erros:** As mensagens de erro são empáticas ou robóticas/frias?

### 3. ❤️ Raiva (Bloqueios e Lentidão)
**Foco:** Frustração, Performance, Bugs Bloqueantes.
**O que testar:**
- **Rage Clicks:** Clique freneticamente em um botão que não responde. O sistema trava?
- **Lentidão:** O sistema demora mais de 2 segundos para responder?
- **Obstáculos:** Pop-ups que não fecham, vídeos que não pausam, fluxos que não posso pular.

### 4. 💜 Medo (Segurança e Risco)
**Foco:** Privacidade, Perda Irreversível, Dados Sensíveis.
**O que testar:**
- **Exclusão:** O sistema pede confirmação antes de eu deletar algo importante?
- **Dados:** Minha senha está visível? Meus dados pessoais estão expostos na URL?
- **Alertas:** Mensagens alarmistas ("FATAL ERROR") que assustam o usuário sem necessidade.

### 5. 💚 Nojinho (Inconsistência Visual)
**Foco:** UI, Alinhamento, Estética, "Cheiro" de Código.
**O que testar:**
- **Pixel Perfect:** Botões desalinhados, fontes diferentes na mesma tela.
- **Cores:** Combinações de cores que ferem os olhos ou baixo contraste.
- **Dados Sujos:** O sistema aceita dados "nojentos" (tags HTML, scripts, emojis quebrados)?

### 6. 🧡 Ansiedade (Incerteza e Pressão)
**Foco:** Ambiguidade, Tempo de Espera, Feedback.
**O que testar:**
- **Loaders:** Quando clico, sei que algo está acontecendo ou a tela congela?
- **Rótulos:** O botão diz apenas "Ok" ou diz o que vai acontecer ("Pagar", "Excluir")?
- **Timers:** Contadores regressivos que causam pânico desnecessário.

### 7. 🩷 Vergonha (Erros Sociais)
**Foco:** Exposição Indevida, Typos, Falhas de Comunicação.
**O que testar:**
- **Ortografia:** Erros de português que tiram a credibilidade do produto.
- **Social:** O sistema postou algo na minha rede social sem eu querer?
- **Notificações:** O app enviou uma notificação constrangedora visível na tela bloqueada?

### 8. 🌫️ Tédio (Repetição e Monotonia)
**Foco:** Fluxos Longos, Passos Desnecessários, Burocracia.
**O que testar:**
- **Cadastros:** Formulários gigantes que poderiam ser divididos ou simplificados.
- **Repetição:** Ter que digitar a mesma informação duas vezes.
- **Texto:** Termos de uso infinitos que ninguém lê.

### 9. 🩵 Inveja (Comparação e Acesso)
**Foco:** Permissões, Premium vs Free, Recursos Bloqueados.
**O que testar:**
- **Limites:** Tentar acessar recursos premium sendo usuário free (o bloqueio é elegante ou frustrante?).
- **Permissões:** O usuário Admin vê coisas que eu quero ver? Eu consigo acessar via URL (IDOR)?
- **FOMO:** O sistema mostra o que estou perdendo de forma atrativa?

---

## 📝 Formato de Saída (Output Style)

Para cada cenário, identifique a **Emoção Dominante** que motivou o teste.

### Template do Caso de Teste:

# [ID-AUTO] - {Título do Teste}

## 1. Estrutura e formatação
- **Emoção:** {Emoji da Emoção} {Nome da Emoção}
- **Prioridade:** {High/Medium/Low}
- **Severidade:** {Critical/Normal/Minor}
- **Pré-condições:**
* {Estado necessário}

## 2. Step by step
1. {Ação provocativa baseada na emoção}
2. {Reação do sistema}

## 3. Resultado Esperado
- {O sistema deve mitigar a emoção negativa OU reforçar a positiva}
- {Comportamento específico}

---

### Exemplos de Aplicação:

# [TC-050] - Validar feedback visual em processamento longo (Ansiedade)

## 1. Estrutura e formatação
- **Emoção:** 🧡 Ansiedade
- **Prioridade:** High
- **Severidade:** Normal
- **Pré-condições:**
* Tela de geração de relatório (processo que leva 10s).

## 2. Step by step
1. Clicar em `[Gerar Relatório Completo]`.
2. Observar a tela durante os 10 segundos de espera.

## 3. Resultado Esperado
- O sistema DEVE exibir um *spinner* ou barra de progresso.
- O sistema DEVE exibir uma mensagem tranquilizadora: "Estamos preparando seus dados, aguarde...".
- A tela NÃO deve parecer travada (congelada).

# [TC-051] - Validar "Rage Click" no botão de confirmar (Raiva)

## 1. Estrutura e formatação
- **Emoção:** ❤️ Raiva
- **Prioridade:** Medium
- **Severidade:** Minor
- **Pré-condições:**
* Formulário preenchido.

## 2. Step by step
1. Clicar 20 vezes rapidamente no botão `[Enviar Pedido]`.

## 3. Resultado Esperado
- O sistema deve processar apenas **UMA** requisição.
- O botão deve ficar desabilitado (disabled) logo após o primeiro clique válido.
- Não devem ser criados 20 pedidos duplicados no banco de dados.

# [TC-052] - Validar alinhamento de ícones no menu (Nojinho)

## 1. Estrutura e formatação
- **Emoção:** 💚 Nojinho
- **Prioridade:** Low
- **Severidade:** Trivial
- **Pré-condições:**
* Menu lateral expandido.

## 2. Step by step
1. Observar o alinhamento vertical dos ícones em relação ao texto.
2. Verificar a consistência dos ícones (todos com mesmo estilo/espessura).

## 3. Resultado Esperado
- Todos os ícones devem estar perfeitamente centralizados com o texto.
- Não deve haver mistura de ícones preenchidos com ícones de linha (outline).