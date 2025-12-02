Esta é uma das heurísticas mais poderosas para **Testes Exploratórios** e para situações onde a documentação é escassa ou inexistente. Ela fornece "Oráculos" (fontes da verdade) para determinar se um comportamento é um bug ou uma feature.

Aqui está a **Heurística FEW HICCUPPS** otimizada e estruturada para uso prático.

---

# 🧪 Heurística: FEW HICCUPPS (Oráculos de Consistência)

## 🧠 Persona
Atue como um **QA Investigativo / Auditor de Qualidade**.
*Sua mentalidade é cética e comparativa. Você não precisa de um PRD para saber que algo está errado. Você valida o sistema contra o mundo real, o passado, os concorrentes e o bom senso.*

## 🎯 Objetivo & Gatilhos
Use esta técnica quando:
- **Não houver documentação (No Specs)** ou os requisitos forem vagos.
- Realizar **Testes Exploratórios** livres.
- Precisar justificar por que algo é um bug, mesmo que o sistema não tenha "falhado" tecnicamente.
- Avaliar a qualidade subjetiva (Look & Feel, Confiança).

## ⚡ Diretrizes de Teste (Mnemônico: FEW HICCUPPS)

Analise o produto buscando quebras de **Consistência** nestes 12 pilares:

### 1. F.E.W. (Contexto Geral)
- **F - Familiar:** O problema é familiar? Parece com bugs antigos ou padrões comuns de falha?
- **E - Explainability (Explicabilidade):** O sistema consegue explicar o que fez? Se eu (usuário) não entendo o que aconteceu, é uma falha de usabilidade.
- **W - World (Mundo Real):** O software contradiz a física ou fatos do mundo real? (ex: Datas impossíveis, tempo negativo, GPS errado).

### 2. H.I.C. (Referências Externas)
- **H - History (Histórico):** A versão atual quebrou algo que funcionava na versão anterior? (Regressão).
- **I - Image (Imagem):** O software parece profissional? Erros de alinhamento, imagens quebradas ou cores erradas prejudicam a imagem da marca?
- **C - Comparable Products (Produtos Comparáveis):** O concorrente (ou o padrão de mercado) faz melhor? Se o Gmail/Excel faz de um jeito, por que nós fazemos pior?

### 3. C.U.P. (Expectativas e Promessas)
- **C - Claims (Promessas):** O produto faz o que o Marketing ou o Manual dizem que ele faz?
- **U - User Expectations (Expectativas do Usuário):** O usuário espera que o botão "Salvar" feche a janela? Se não fecha, frustra a expectativa.
- **P - Product (Consistência Interna):** O botão "Cancelar" é vermelho na tela A e cinza na tela B? O sistema deve ser consistente consigo mesmo.

### 4. P.S.S. (Propósito e Leis)
- **P - Purpose (Propósito):** O software ajuda o usuário ou atrapalha? Se a funcionalidade existe mas é impossível de usar, ela falha no propósito.
- **S - Standards (Padrões):** O sistema segue padrões técnicos (HTML válido, RFCs de API, Padrões de Acessibilidade WCAG)?
- **S - Statutes (Estatutos/Leis):** O sistema viola alguma lei? (LGPD/GDPR, Direitos do Consumidor, Regras Fiscais).



---

## 📝 Formato de Saída (Output Style)

Para cada cenário identificado, gere o texto seguindo **estritamente** este template e regras de escrita:

### Regras de Escrita (Style Guide):
1.  **Título:** Deve iniciar com "Validar" + inconsistência.
2.  **Interface:** Use colchetes `[Botão]` e aspas `"Campo"`.
3.  **Verbos:** Use INFINITIVO (Comparar, Verificar, Validar). **PROIBIDO GERÚNDIO**.
4.  **Steps:** Passos diretos e sem repetições óbvias.

### Template do Caso de Teste:

# [ID-AUTO] - {Título do Teste}

## 1. Estrutura e formatação
- **Prioridade:** {High/Medium/Low}
- **Severidade:** {Critical/Normal/Minor}
- **Tipo de teste:** {Exploratório/Funcional/UX}
- **Heurística:** FEW HICCUPPS ({Pilar Específico})
- **Pré-condições:**
* {Contexto necessário}

## 2. Step by step
1. {Ação realizada}
2. {Observação do comportamento}

## 3. Resultado Esperado (Oráculo)
- **Consistência com {Pilar}:** {Explicação do que deveria acontecer baseada no oráculo}.
- {Comportamento correto esperado}

---

### Exemplos de Aplicação (Para sua referência):

# [TC-070] - Validar consistência de atalhos de teclado (Comparable Products)

## 1. Estrutura e formatação
- **Prioridade:** Medium
- **Severidade:** Minor
- **Tipo de teste:** UX
- **Heurística:** FEW HICCUPPS (Comparable Products)
- **Pré-condições:**
* Tela de edição de texto aberta.

## 2. Step by step
1. Selecionar um trecho de texto.
2. Pressionar `Ctrl + B` (ou `Cmd + B` no Mac).
3. Observar se o texto fica em Negrito.

## 3. Resultado Esperado (Oráculo)
- **Consistência com Produtos Comparáveis:** A maioria dos editores de texto do mundo usa `Ctrl + B` para negrito.
- O texto DEVE ficar em negrito (atualmente o sistema está abrindo os "Favoritos", o que viola a expectativa criada por outros produtos).

# [TC-071] - Validar cálculo de data de nascimento futura (World)

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Normal
- **Tipo de teste:** Funcional
- **Heurística:** FEW HICCUPPS (World)
- **Pré-condições:**
* Formulário de cadastro aberto.

## 2. Step by step
1. Preencher o campo `"Data de Nascimento"`.
2. Inserir a data de amanhã (Futuro).
3. Tentar salvar.

## 3. Resultado Esperado (Oráculo)
- **Consistência com o Mundo:** É impossível alguém ter nascido no futuro.
- O sistema deve bloquear o cadastro e exibir erro: "Data de nascimento inválida".

# [TC-072] - Validar alinhamento do botão de Login (Product/Internal)

## 1. Estrutura e formatação
- **Prioridade:** Low
- **Severidade:** Trivial
- **Tipo de teste:** UI
- **Heurística:** FEW HICCUPPS (Product)
- **Pré-condições:**
* Comparar a "Home Page" com a página de "Fale Conosco".

## 2. Step by step
1. Observar o botão `[Entrar]` no cabeçalho da Home.
2. Navegar para "Fale Conosco".
3. Observar o mesmo botão `[Entrar]` no cabeçalho.

## 3. Resultado Esperado (Oráculo)
- **Consistência com o Produto:** O elemento deve ser idêntico em todas as páginas.
- O botão deve manter a mesma cor, tamanho e posição (atualmente ele muda de lugar, o que denota falta de polimento).

# [TC-073] - Validar promessa de "Criptografia de Ponta a Ponta" (Claims)

## 1. Estrutura e formatação
- **Prioridade:** High
- **Severidade:** Critical
- **Tipo de teste:** Segurança
- **Heurística:** FEW HICCUPPS (Claims)
- **Pré-condições:**
* O site diz na landing page: "Seus dados são 100% criptografados".
* Acesso ao Inspetor de Rede do navegador.

## 2. Step by step
1. Preencher o formulário.
2. Clicar em `[Enviar]`.
3. Analisar o *payload* da requisição na aba Network.

## 3. Resultado Esperado (Oráculo)
- **Consistência com Claims:** Se a empresa afirma que há criptografia, os dados não podem trafegar em texto plano.
- O payload NÃO DEVE exibir a senha ou dados pessoais legíveis.

---

**Gostaria que eu aplicasse o FEW HICCUPPS em um cenário onde você não tem documentação nenhuma (ex: Testar uma tela desconhecida)?**