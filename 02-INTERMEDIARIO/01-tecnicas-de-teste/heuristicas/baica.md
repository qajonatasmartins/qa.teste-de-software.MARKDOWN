# BAICA - Heurística para Testes Básicos

**Criador:** Jonatas Martins Faria

## O que é a Heurística BAICA?

A heurística BAICA é uma abordagem estruturada criada por Jonatas Faria para garantir que os testes fundamentais sejam aplicados consistentemente durante o desenvolvimento de novas funcionalidades em aplicações existentes. Esta heurística foca nos aspectos essenciais que frequentemente são negligenciados mas que podem causar problemas significativos em produção.

## Componentes da Heurística BAICA

### **B - Básico**
Realize as ações mais simples e fundamentais da funcionalidade.

**Objetivo:** Verificar se os fluxos principais funcionam corretamente antes de partir para cenários complexos.

**Como aplicar:**
- Execute o caminho feliz (happy path) da funcionalidade
- Teste as operações CRUD básicas (Create, Read, Update, Delete)
- Verifique se as validações essenciais estão funcionando
- Confirme que as mensagens de sucesso/erro aparecem adequadamente

**Exemplo prático:** 
Ao testar um formulário de cadastro, primeiro verifique se é possível cadastrar um usuário com dados válidos, visualizar na listagem, editar as informações e excluir o registro.

**Benefícios:** Funciona como um teste de smoke/sanidade, identificando problemas básicos rapidamente.

### **A - Automação**
Verifique a testabilidade da funcionalidade para futura automação.

**Objetivo:** Garantir que os elementos da interface possam ser identificados de forma única e consistente para testes automatizados.

**Como aplicar:**
- Verifique se botões, campos, dropdowns possuem identificadores únicos
- Confirme que listas e tabelas têm elementos identificáveis
- Valide se rótulos e mensagens podem ser localizados programaticamente
- Teste se os estados da aplicação são verificáveis

**Exemplo prático:**
Em um formulário, verifique se cada campo tem um ID, name ou data-testid único. Botões devem ter identificadores que não mudem entre deploys.

**Benefícios:** Facilita a criação de testes automatizados futuros e reduz retrabalho.

### **I - Interrupção**
Teste o comportamento da aplicação quando processos são interrompidos.

**Objetivo:** Verificar a robustez da aplicação quando operações são canceladas ou falham.

**Como aplicar:**
- Interrompa uploads de arquivos no meio do processo
- Cancele operações de salvamento
- Feche o navegador durante transações
- Simule timeouts de rede
- Teste navegação durante carregamentos

**Exemplo prático:**
Durante o upload de um arquivo grande, feche a aba do navegador e reabra. Verifique se o sistema mantém consistência e não deixa dados corrompidos.

**Benefícios:** Identifica problemas de integridade de dados e melhora a experiência do usuário em cenários reais.

### **C - Criação de Novos Dados**
Execute o fluxo completo criando todos os dados necessários do zero.

**Objetivo:** Testar dependências entre funcionalidades e validar o fluxo end-to-end.

**Como aplicar:**
- Comece com um ambiente limpo (sem dados pré-cadastrados)
- Crie todos os dados de dependência necessários
- Execute o fluxo completo até a funcionalidade alvo
- Verifique se todas as etapas funcionam em sequência

**Exemplo prático:**
Para testar a geração de um relatório de vendas, crie: usuário → produto → cliente → pedido → venda → relatório. Execute todo o fluxo sem usar dados pré-existentes.

**Benefícios:** Expõe problemas de dependência e garante que o fluxo completo funciona para novos usuários.

### **A - Anônimo (Modo Anônimo)**
Valide o comportamento da aplicação em navegação privada/anônima.

**Objetivo:** Garantir que a aplicação funcione corretamente quando cookies, cache e storage local não estão disponíveis.

**Como aplicar:**
- Execute todos os testes principais em modo anônimo/privado
- Verifique se funcionalidades dependentes de cookies funcionam
- Teste login/logout em modo privado
- Valide se dados sensíveis não ficam expostos
- Confirme que a aplicação não quebra sem cache

**Exemplo prático:**
Abra a aplicação em uma aba anônima e execute o fluxo de login, navegação e logout. Verifique se todas as funcionalidades permanecem funcionais.

**Benefícios:** Simula o comportamento de usuários conscientes de privacidade e identifica dependências não documentadas de armazenamento local.

## Quando Aplicar BAICA

- **Desenvolvimento de novas funcionalidades**
- **Integração de funcionalidades existentes**
- **Testes de regressão após mudanças**
- **Validação antes de releases**
- **Onboarding de novos testadores**

## Benefícios da Heurística BAICA

1. **Cobertura Essencial:** Garante que aspectos fundamentais não sejam esquecidos
2. **Detecção Precoce:** Identifica problemas básicos antes que cheguem ao cliente
3. **Preparação para Automação:** Facilita futuras iniciativas de automação
4. **Robustez:** Testa cenários reais de uso e interrupção
5. **Experiência do Usuário:** Simula comportamentos reais de usuários

## Exemplo de Aplicação Completa

**Cenário:** Testando uma nova funcionalidade de upload de documentos

**B - Básico:**
- Upload de um arquivo válido
- Visualização do arquivo na lista
- Download do arquivo
- Exclusão do arquivo

**A - Automação:**
- Verificar IDs únicos em botões de upload, lista e ações
- Confirmar que mensagens de status são identificáveis
- Validar que progress bars têm atributos testáveis

**I - Interrupção:**
- Cancelar upload no meio do processo
- Fechar navegador durante upload
- Simular perda de conexão

**C - Criação de Novos Dados:**
- Começar com usuário novo
- Criar pasta de documentos
- Fazer upload do primeiro documento
- Testar todo o fluxo sem dados pré-existentes

**A - Anônimo:**
- Executar todo o fluxo em modo privado
- Verificar se funciona sem cookies persistentes
- Confirmar que não há vazamento de dados entre sessões

## Conclusão

A heurística BAICA fornece uma abordagem sistemática para garantir qualidade básica mas essencial em funcionalidades. Ao seguir estes cinco pilares, testadores podem ter confiança de que cobriram os aspectos fundamentais que impactam diretamente a experiência do usuário final.