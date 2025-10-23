# Teste de Confirmação e Teste de Regressão

## Introdução

Sempre que alterações são feitas em um sistema de software - seja para adicionar novos recursos ou corrigir defeitos - é fundamental realizar dois tipos específicos de teste: **Teste de Confirmação** e **Teste de Regressão**. Estes são essenciais para garantir que as mudanças funcionem corretamente e não quebrem funcionalidades existentes.

## Teste de Confirmação (Reteste)

### O que é?

O **Teste de Confirmação**, também conhecido como **Reteste**, é o processo de verificar se um defeito específico foi corrigido com sucesso. É como uma "prova" de que o problema original não existe mais.

### Características Principais

- **Objetivo:** Confirmar que a correção de um bug específico foi bem-sucedida
- **Escopo:** Focado no defeito específico que foi corrigido
- **Execução:** Repete os mesmos passos que anteriormente causavam a falha

### Como Realizar

Dependendo do risco e recursos disponíveis, o teste de confirmação pode ser feito de diferentes formas:

1. **Executar todos os casos de teste que falharam** devido ao defeito
2. **Adicionar novos testes** para cobrir mudanças necessárias na correção
3. **Em casos de pouco tempo/recurso:** Executar apenas os passos mínimos que reproduziam a falha

### Exemplo Prático 1: Bug de Login

**Cenário:** Sistema não permitia login com email contendo caracteres especiais

**Defeito original:**
- Email: `usuario+teste@email.com`
- Resultado: "Email inválido"

**Teste de Confirmação:**
1. Tentar fazer login com `usuario+teste@email.com`
2. Verificar se o login é aceito
3. Confirmar redirecionamento para página principal
4. ✅ **Resultado esperado:** Login realizado com sucesso

### Exemplo Prático 2: Cálculo de Desconto

**Cenário:** Sistema calculava desconto incorretamente para valores acima de R$ 1000

**Defeito original:**
- Produto: R$ 1200,00 com desconto de 10%
- Resultado incorreto: R$ 1080,00 (apenas R$ 120 de desconto)
- Resultado esperado: R$ 1080,00 (R$ 120 de desconto) ✅

**Teste de Confirmação:**
1. Adicionar produto de R$ 1200,00 ao carrinho
2. Aplicar cupom de 10% de desconto
3. Verificar se o desconto aplicado é R$ 120,00
4. Confirmar valor final de R$ 1080,00

## Teste de Regressão

### O que é?

O **Teste de Regressão** verifica se as mudanças feitas no sistema não causaram efeitos colaterais indesejados em outras funcionalidades que estavam funcionando corretamente.

### Características Principais

- **Objetivo:** Garantir que funcionalidades existentes não foram "quebradas"
- **Escopo:** Mais amplo, testando áreas relacionadas e não relacionadas à mudança
- **Frequência:** Executado sempre que há mudanças no código

### Tipos de Teste de Regressão

1. **Regressão Local:** Testa componentes diretamente afetados pela mudança
2. **Regressão Regional:** Testa módulos relacionados ao que foi alterado  
3. **Regressão Completa:** Testa todo o sistema (mais raro, usado em releases importantes)

### Como Realizar

1. **Análise de Impacto:** Identificar quais áreas podem ser afetadas
2. **Seleção de Casos de Teste:** Escolher testes relevantes para executar
3. **Execução:** Rodar os testes selecionados
4. **Automação:** Preferencialmente automatizar para execução frequente

### Exemplo Prático 3: Correção no Sistema de Pagamento

**Mudança realizada:** Correção no módulo de pagamento com cartão de crédito

**Teste de Regressão necessário:**

**Áreas para testar:**
- ✅ **Pagamento com débito** (função relacionada)
- ✅ **Pagamento com PIX** (função relacionada)  
- ✅ **Histórico de compras** (área que usa dados de pagamento)
- ✅ **Relatórios financeiros** (área que consome dados de pagamento)
- ✅ **Carrinho de compras** (área que interage com pagamento)

**Casos de teste exemplo:**
```
1. Realizar compra com cartão de débito
   - Resultado esperado: Compra processada normalmente

2. Realizar pagamento via PIX
   - Resultado esperado: QR Code gerado e pagamento processado

3. Consultar histórico de compras
   - Resultado esperado: Compras anteriores exibidas corretamente

4. Gerar relatório de vendas do mês
   - Resultado esperado: Relatório gerado com dados corretos
```

### Exemplo Prático 4: Nova Funcionalidade de Wishlist

**Mudança realizada:** Adição de funcionalidade de lista de desejos

**Teste de Regressão necessário:**

**Áreas para testar:**
- ✅ **Cadastro de produtos** (não deve ser afetado)
- ✅ **Carrinho de compras** (funcionalidade similar)
- ✅ **Perfil do usuário** (onde a wishlist pode aparecer)
- ✅ **Busca de produtos** (pode ter botão de wishlist)
- ✅ **Performance da página** (nova funcionalidade pode tornar página lenta)

## Diferenças Principais

| Aspecto | Teste de Confirmação | Teste de Regressão |
|---------|---------------------|-------------------|
| **Foco** | Defeito específico corrigido | Funcionalidades que não foram alteradas |
| **Escopo** | Restrito ao problema original | Amplo, múltiplas funcionalidades |
| **Objetivo** | Confirmar que o bug foi corrigido | Garantir que nada mais quebrou |
| **Casos de Teste** | Apenas os que falhavam antes | Casos existentes que passavam antes |

## Estratégias de Automação

### Teste de Confirmação
- **Automação parcial:** Casos específicos do bug
- **Execução:** Sob demanda, após correções

### Teste de Regressão  
- **Automação alta:** Suite completa de testes críticos
- **Execução:** Contínua (CI/CD pipeline)
- **Manutenção:** Constante evolução da suite

## Quando Executar

### Teste de Confirmação
- ✅ Após correção de qualquer defeito
- ✅ Antes de fechar um bug report
- ✅ Durante validação de hotfixes

### Teste de Regressão
- ✅ Após qualquer mudança no código
- ✅ Antes de releases/deploys
- ✅ Em pipeline de CI/CD
- ✅ Após integrações entre sistemas

## Boas Práticas

### Para QAs Iniciantes

1. **Documente tudo:** Registre os passos do teste de confirmação
2. **Seja metódico:** Use checklist para teste de regressão
3. **Priorize:** Foque nas funcionalidades mais críticas primeiro
4. **Automatize gradualmente:** Comece com casos mais estáveis
5. **Comunique:** Reporte qualquer efeito colateral encontrado

### Dicas de Eficiência

- **Análise de impacto primeiro:** Não teste tudo, teste o necessário
- **Mantenha suites atualizadas:** Remove testes obsoletos
- **Use dados de teste consistentes:** Facilita comparação de resultados
- **Documente casos edge:** Casos limite são importantes em regressão

## Conclusão

Teste de Confirmação e Teste de Regressão são importantes para manter a qualidade do software durante sua evolução. Enquanto o primeiro garante que problemas específicos foram resolvidos, o segundo assegura que as mudanças não criaram novos problemas.

**Lembre-se:**
- **Confirmação:** "O bug foi corrigido?"
- **Regressão:** "Algo mais quebrou?"

Ambos devem ser executados sistematicamente em qualquer processo de desenvolvimento de qualidade.

## Referências

- ISTQB Foundation Level Syllabus 4.0 - BSTQB