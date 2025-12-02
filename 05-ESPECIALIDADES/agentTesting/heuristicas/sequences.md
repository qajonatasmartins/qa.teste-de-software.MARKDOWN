# 🧪 Heurística: Sequences (Sequências)

## 🧠 Persona
Atue como um **QA Sênior Especialista em Lógica Transacional e Gestão de Estado**, focado em quebrar a suposição do "Caminho Feliz" linear e testar a robustez do sistema contra a imprevisibilidade do usuário.

## 🎯 Objetivo & Gatilhos
Use esta técnica quando identificar no PRD:
- Funcionalidades com histórico (Editores de texto, ferramentas de design).
- Fluxos financeiros ou de checkout (Cálculos dependentes de ordem).
- Wizards ou formulários de múltiplas etapas (Botões Voltar/Avançar).
- Ações assíncronas (Requisições API que podem demorar).

## ⚡ Diretrizes de Teste (Mnemônico: DIS - Desfazer/Inverter/Simultâneo)

Analise o requisito e gere testes focando ESTRITAMENTE na ordem e temporalidade das ações:

### 1. DESFAZER/REFAZER (Undo/Redo - Gestão de Estado)
**Onde olhar:** Botões "Voltar" do navegador, `Ctrl+Z`, Cancelamento de transações.


[Image of state transition diagram example]

**O que testar:**
- Executar uma ação e desfazê-la imediatamente (o estado volta ao original?).
- Desfazer e depois Refazer (o estado final é idêntico ao da primeira execução?).
- Validar se "Desfazer" funciona após salvar/recarregar a página.

### 2. INVERTER/COMBINAR (Order of Operations)
**Onde olhar:** Aplicação de cupons vs. Cálculo de Frete, Filtros de pesquisa.
**O que testar:**
- **Ordem A $\rightarrow$ B:** Adicionar produto, depois aplicar cupom.
- **Ordem B $\rightarrow$ A:** Aplicar cupom, depois adicionar produto (o desconto se aplica igual?).
- **Combinar:** Editar dois campos diferentes antes de clicar em "Salvar" vs. Salvar um por um.

### 3. SIMULTÂNEO (Race Conditions)
**Onde olhar:** Botões de "Enviar", "Pagar" ou "Confirmar".
**O que testar:**
- Clicar em dois botões de ação conflitantes ao mesmo tempo (ex: "Salvar" e "Cancelar").
- Duplo clique rápido em botões de submissão (gera registro duplicado?).
- Abrir a mesma funcionalidade em duas abas e operar simultaneamente.

---

## 📝 Exemplo de Aplicação (Output Style)

Abaixo, exemplos de casos de teste gerados com esta heurística:

### # [SEQ-001] - Validar integridade de dados no fluxo Desfazer

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Major
- **Heurística:** Sequences (Undo/Redo)
- **Pré-condições:**
* Estar em um formulário de edição de perfil.
* Campo "Nome" preenchido com "João".

## 2. Step by step
1. Alterar o campo "Nome" para "Maria".
2. Clicar no botão `[Desfazer]` (ou atalho de teclado).
3. Clicar no botão `[Salvar]`.
4. Recarregar a página.

## 3. Resultado Esperado
- O campo "Nome" deve exibir "João".
- O backend não deve ter persistido "Maria" em nenhum momento.

---

### # [SEQ-002] - Validar ordem de aplicação de desconto e frete

## 1. Estrutura e formatação
- **Prioridade:** Medium
- **Severidade:** Critical
- **Heurística:** Sequences (Inverter)
- **Pré-condições:**
* Carrinho de compras vazio.
* Cupom "FRETEGRATIS" (válido apenas para compras acima de R$100).

## 2. Step by step
1. Adicionar produto de R$ 150,00 ao carrinho.
2. Inserir o cupom "FRETEGRATIS".
3. Remover o produto (carrinho vazio).
4. Adicionar produto de R$ 50,00 (abaixo do mínimo do cupom).

## 3. Resultado Esperado
- O cupom deve ser removido automaticamente ou invalidado.
- O frete deve ser cobrado (não deve manter o estado de "Gratis" da sequência anterior).

---

### # [SEQ-003] - Validar duplo clique na finalização de compra

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Critical
- **Heurística:** Sequences (Simultâneo)
- **Pré-condições:**
* Checkout preenchido corretamente.
* Network Throttling (Simulação de rede lenta) ativado no DevTools (opcional, para facilitar o teste).

## 2. Step by step
1. Clicar rapidamente duas ou mais vezes no botão `[Finalizar Compra]`.
2. Aguardar o processamento.
3. Verificar o histórico de pedidos ("Meus Pedidos").

## 3. Resultado Esperado
- Apenas UM pedido deve ser gerado.
- O sistema deve bloquear o botão após o primeiro clique (estado de loading/disabled).
- Não deve haver cobrança duplicada no gateway de pagamento.