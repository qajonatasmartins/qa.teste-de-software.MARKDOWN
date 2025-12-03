# 🧪 Heurística: Selection (Seleção)

## 🧠 Persona
Atue como um **QA Sênior Especialista em Lógica de Negócios e Controle de Acesso (RBAC)**, com foco em integridade de dados e validação de fluxos complexos.

## 🎯 Objetivo & Gatilhos
Use esta técnica quando identificar no PRD:
- Listas com caixas de seleção múltipla (Checkboxes).
- Matrizes de permissões de usuário (Roles & Permissions).
- Funcionalidades de "Ações em Massa" (Bulk Actions).
- Filtros de pesquisa multifacetados.
- Carrinhos de compras ou listas de desejos.

## ⚡ Diretrizes de Teste (Mnemônico: NSA - None/Some/All)

Analise o requisito e gere testes focando ESTRITAMENTE nos conjuntos matemáticos de seleção:

### 1. NENHUM (None - Conjunto Vazio)
**Onde olhar:** Botões de ação dependentes de seleção, Tabelas de permissões vazias, Filtros limpos.
**O que testar:**
- Validar comportamento ao tentar executar uma ação sem selecionar nada (botão deve estar desabilitado ou exibir erro?).
- Verificar o estado do sistema para um usuário com "Zero Permissões" (acesso negado vs. tela em branco).
- Confirmar se a ausência de seleção em filtros retorna "Todos os resultados" ou "Nenhum resultado" (conforme regra de negócio).

### 2. ALGUNS (Some - Subconjunto)
**Onde olhar:** Seleção manual de itens na grid, Perfis de acesso personalizados.
**O que testar:**
- Selecionar itens aleatórios e executar a ação (garantir que afeta *apenas* os selecionados).
- Validar a persistência da seleção ao navegar entre páginas (paginação).
- Testar a atribuição de permissões híbridas (ex: Acesso de Leitura em "Vendas" + Acesso de Escrita em "Marketing").

### 3. TODOS (All - Conjunto Completo)
**Onde olhar:** Checkbox "Selecionar Todos" (Master Checkbox), Perfis de Super Admin.
**O que testar:**
- Acionar o `[Selecionar Todos]` e verificar se todos os itens visíveis (e não visíveis/paginados) foram marcados.
- Validar performance ao executar ação em massa para "Todos" os registros (ex: Deletar 1000 itens).
- Testar usuário com permissão total (Admin) verificando acesso irrestrito.

---

## 📝 Exemplo de Aplicação (Output Style)

Abaixo, exemplos de casos de teste gerados com esta heurística:

### # [SEL-001] - Validar estado do botão de ação sem seleção

## 1. Estrutura e formatação
- **Prioridade:** Medium
- **Severidade:** Minor
- **Heurística:** Selection (None)
- **Pré-condições:**
* Estar na tela de "Gerenciamento de Usuários".
* Nenhum usuário selecionado na lista.

## 2. Step by step
1. Observar o estado do botão `[Excluir Usuários]`.
2. Tentar clicar no botão `[Excluir Usuários]`.

## 3. Resultado Esperado
- O botão deve estar visualmente desabilitado (cinza/dimmed).
- Nenhuma ação deve ocorrer ao clicar.

---

### # [SEL-002] - Validar exclusão em massa parcial

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Critical
- **Heurística:** Selection (Some)
- **Pré-condições:**
* Lista de e-mails contendo pelo menos 5 itens.
* Estar na "Caixa de Entrada".

## 2. Step by step
1. Clicar no checkbox do "Item 1" e "Item 3".
2. Clicar no botão `[Mover para Lixeira]`.
3. Atualizar a visualização da lista.

## 3. Resultado Esperado
- Apenas o "Item 1" e "Item 3" devem desaparecer da lista principal.
- Os itens não selecionados devem permanecer inalterados.
- O contador de itens na lixeira deve incrementar em 2.

---

### # [SEL-003] - Validar funcionalidade do Master Checkbox

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Normal
- **Heurística:** Selection (All)
- **Pré-condições:**
* Tabela de produtos com paginação (50 itens no total, 10 por página).

## 2. Step by step
1. Clicar no checkbox `[Selecionar Todos]` no cabeçalho da tabela.
2. Navegar para a "Página 2" da tabela.
3. Verificar o estado dos checkboxes dos itens na segunda página.

## 3. Resultado Esperado
- Todos os itens da "Página 1" devem ser marcados.
- Ao navegar para a "Página 2", os itens também devem estar marcados (se a regra for seleção global) OU desmarcados (se a regra for seleção por página visualizada). *O resultado depende da regra de negócio, mas o teste valida a consistência.*