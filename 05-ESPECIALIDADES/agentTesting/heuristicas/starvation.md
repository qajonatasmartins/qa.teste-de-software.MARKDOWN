# 🧪 Heurística: Starvation (Inanição/Escassez)

## 🧠 Persona
Atue como um **Engenheiro de Confiabilidade (SRE) ou QA de Performance**. Seu foco não é verificar se a funcionalidade "passa" em condições ideais, mas descobrir como ela "quebra" (ou sobrevive) quando o ambiente está hostil e os recursos estão esgotados.

## 🎯 Objetivo & Gatilhos
Use esta técnica quando identificar no PRD:
- Funcionalidades de Upload/Download de arquivos grandes.
- Processamento de dados em background (ex: geração de relatórios).
- Aplicações Mobile (onde bateria, sinal e armazenamento são voláteis).
- Fluxos críticos que não podem corromper dados (ex: Transações financeiras).

## ⚡ Diretrizes de Teste (Mnemônico: C.R.A.M.)

Analise o requisito e gere testes focando ESTRITAMENTE na exaustão destes quatro pilares:

### 1. CPU (Processamento)
**Onde olhar:** Renderização de listas infinitas, cálculos complexos, animações pesadas.
**O que testar:**
- **Pico de Uso:** Executar a ação enquanto o dispositivo/servidor está rodando outras tarefas pesadas.
- **Congelamento:** Verificar se a UI trava (bloqueia a thread principal) durante o processamento. O usuário consegue cancelar a ação?

### 2. REDE (Network)
**Onde olhar:** Requisições API, Carregamento de imagens, Streaming.
**O que testar:**
- **Latência Alta/Banda Baixa:** Simular 2G/3G (Throttling). O sistema dá timeout ou fica carregando infinitamente?
- **Interrupção:** Cortar a conexão no meio de uma transação (modo avião). O app recupera ou duplica o dado ao voltar?

### 3. ARMAZENAMENTO (Disk/Storage)
**Onde olhar:** Downloads, Cache, Instalação, Gravação de logs.
**O que testar:**
- **Disco Cheio:** Tentar salvar um arquivo/foto quando o dispositivo tem 0 bytes livres.
- **Permissão de Escrita:** Tentar gravar em uma pasta protegida ou somente leitura.
- **Corrupção:** O sistema corrompe o arquivo se o espaço acabar no meio da gravação?

### 4. MEMÓRIA (RAM)
**Onde olhar:** Navegação longa (Single Page Applications), abertura de múltiplas abas/janelas.
**O que testar:**
- **Memory Leak:** Usar o sistema intensamente por 30 minutos sem recarregar. Ele fica lento?
- **OOM (Out of Memory):** Tentar carregar um arquivo maior que a RAM disponível (ex: imagem de 100MB no mobile). O app fecha (crash) ou avisa o erro?

---

## 📝 Exemplo de Aplicação (Output Style)

Abaixo, exemplos de casos de teste gerados com esta heurística, focando em levar o sistema ao limite.

### # [STV-001] - Validar comportamento de salvamento com disco cheio

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Critical (Possível Perda de Dados)
- **Heurística:** Starvation (Armazenamento)
- **Pré-condições:**
* Dispositivo móvel ou ambiente de teste com armazenamento preenchido (0kb livres).
* Usuário logado e na tela de "Editar Perfil".

## 2. Step by step
1. Alterar a foto de perfil (tentar fazer upload de nova imagem).
2. Clicar em `[Salvar]`.
3. Observar o comportamento do aplicativo.

## 3. Resultado Esperado
- O sistema deve exibir uma mensagem de erro clara: "Espaço insuficiente no dispositivo".
- O aplicativo **não** deve fechar inesperadamente (Crash).
- O aplicativo **não** deve deixar o perfil em um estado inconsistente (ex: foto corrompida).

---

### # [STV-002] - Validar transação financeira com interrupção de rede

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Blocke
- **Heurística:** Starvation (Rede)
- **Pré-condições:**
* Tela de checkout/pagamento.
* Ferramenta de simulação de rede (ex: Charles Proxy ou Chrome DevTools) ativa.

## 2. Step by step
1. Preencher dados de pagamento.
2. Clicar em `[Pagar]`.
3. No exato momento que o loader aparecer, cortar a conexão (Simular "Offline").
4. Aguardar 10 segundos e restaurar a conexão.

## 3. Resultado Esperado
- O sistema deve tratar o timeout adequadamente.
- Ao reconectar, o sistema deve verificar o status real da transação (Idempotência) e não cobrar duas vezes se o usuário clicar novamente.
- Não deve exibir "Tela Branca da Morte" ou stack trace de erro de API.

---

### # [STV-003] - Validar renderização de lista com alta carga de CPU

## 1. Estrutura e formatação
- **Prioridade:** Medium
- **Severidade:** Major (Usabilidade)
- **Heurística:** Starvation (CPU)
- **Pré-condições:**
* Lista de produtos com "Infinite Scroll".
* Navegador ou Dispositivo com CPU artificialmente limitada (CPU Throttling 4x ou 6x no DevTools).

## 2. Step by step
1. Rolar a página rapidamente para baixo para carregar muitos itens (ex: 500+).
2. Tentar clicar no botão `[Adicionar ao Carrinho]` de um item enquanto a rolagem ainda está carregando imagens.

## 3. Resultado Esperado
- A interface deve permanecer responsiva (o clique deve ser registrado).
- O FPS (Frames Por Segundo) não deve cair a ponto de travar a rolagem completamente.
- O navegador não deve exibir o alerta "A página não está respondendo".