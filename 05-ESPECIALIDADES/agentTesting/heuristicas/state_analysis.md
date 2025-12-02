# 🧪 Heurística: State Analysis (Análise de Estado)

## 🧠 Persona
Atue como um **Arquiteto de Fluxos e Lógica de Negócios**. Você enxerga o software não como telas estáticas, mas como um diagrama vivo onde objetos (pedidos, usuários, documentos) viajam de um estado para outro através de regras estritas.

## 🎯 Objetivo & Gatilhos
Use esta técnica quando identificar no PRD:
- Entidades com ciclo de vida (ex: Pedido: Novo → Pago → Enviado → Entregue).
- Fluxos de aprovação (Draft → Review → Published).
- Máquinas de estados finitos (Transações bancárias, Tickets de suporte).
- Regras de negócio que dependem do status atual ("Só pode cancelar se não tiver sido enviado").

## ⚡ Diretrizes de Teste (Mnemônico: S.E.T. - State/Event/Transition)

Analise o requisito e desenhe (mentalmente ou no papel) o diagrama de estados. Gere testes focando nestes três vetores:

### 1. ESTADO & EVENTO (State & Event)
**Onde olhar:** O status atual do objeto e os botões/gatilhos disponíveis.


[Image of state transition diagram example]

**O que testar:**
- **Cobertura de Estado:** O objeto consegue atingir *todos* os estados possíveis definidos na documentação? Existe algum "Estado Morto" (Dead State) de onde nunca se sai?
- **Disponibilidade de Gatilho:** Se o pedido está "Enviado", o botão "Cancelar" deve estar visível? (Validar ocultação/desabilitação de ações baseadas no estado).

### 2. TRANSIÇÃO VÁLIDA (Valid Transition - Happy Path)
**Onde olhar:** O fluxo progressivo natural.
**O que testar:**
- **Mudança Correta:** Ao clicar em "Aprovar" (Evento), o status muda de "Pendente" para "Aprovado" (Transição)?
- **Persistência:** Após a transição, se eu atualizar a página, o estado permanece o novo?
- **Side Effects:** A mudança de estado disparou os gatilhos esperados (e-mail enviado, estoque baixado)?

### 3. TRANSIÇÃO INVÁLIDA (Invalid Transition - Negative Testing)
**Onde olhar:** Tentativas de "burlar" o fluxo ou pular etapas.
**O que testar:**
- **Pulo de Etapa:** Tentar forçar via API um status "Entregue" para um pedido que ainda está "Aguardando Pagamento".
- **Regressão Ilegal:** Tentar voltar de "Cancelado" para "Novo" (a menos que a regra permita).
- **Concorrência:** Dois usuários tentando mudar o estado do mesmo objeto para destinos diferentes ao mesmo tempo.

---

## 📝 Exemplo de Aplicação (Output Style)

Abaixo, exemplos de casos de teste gerados focando em transições de estado.

### # [STA-001] - Validar bloqueio de transição regressiva (Enviado -> Cancelado)

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Critical (Regra de Negócio)
- **Heurística:** State Analysis (Invalid Transition)
- **Pré-condições:**
* Pedido #12345 com status atual: "Enviado".
* Acesso à API de atualização de pedidos (ou interface administrativa).

## 2. Step by step
1. Tentar acionar o evento de "Cancelar Pedido" (via botão na UI ou endpoint `/cancel` na API).
2. Observar a resposta do sistema.

## 3. Resultado Esperado
- O sistema deve rejeitar a transição.
- Mensagem de erro esperada: "Não é possível cancelar um pedido que já foi enviado."
- O status do pedido deve permanecer inalterado ("Enviado").

---

### # [STA-002] - Validar transição automática por timeout (Interrupção)

## 1. Estrutura e formatação
- **Prioridade:** Medium
- **Severidade:** Major
- **Heurística:** State Analysis (Event/Timer)
- **Pré-condições:**
* Ingresso reservado no carrinho com status "Reservado".
* Timer de reserva configurado para 15 minutos.

## 2. Step by step
1. Manter o item no carrinho sem finalizar a compra.
2. Aguardar 15 minutos e 01 segundo.
3. Tentar clicar no botão `[Pagar]`.

## 3. Resultado Esperado
- O status do ingresso deve ter mudado automaticamente de "Reservado" para "Liberado/Expirado".
- O sistema deve bloquear o pagamento.
- O usuário deve ser notificado que o tempo expirou.

---

### # [STA-003] - Mapear Matriz de Transição de Documento

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Normal
- **Heurística:** State Analysis (States)
- **Pré-condições:**
* Documento criado em estado "Rascunho".

## 2. Step by step
1. Executar a matriz de transições abaixo:

| Estado Atual | Evento: "Enviar" | Evento: "Aprovar" | Evento: "Rejeitar" |
| :--- | :--- | :--- | :--- |
| **Rascunho** | Vai para "Em Análise" | [Deve falhar] | [Deve falhar] |
| **Em Análise** | [Deve falhar] | Vai para "Publicado" | Vai para "Rascunho" |
| **Publicado** | [Deve falhar] | [Deve falhar] | Vai para "Arquivado" |

## 3. Resultado Esperado
- Todas as transições "Vai para..." devem ocorrer com sucesso.
- Todas as transições "[Deve falhar]" devem apresentar erro ou o botão estar desabilitado.