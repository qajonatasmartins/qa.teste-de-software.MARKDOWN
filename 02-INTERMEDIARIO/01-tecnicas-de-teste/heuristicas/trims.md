# Heurística TRIMS

**Criador:** Richard Bradshaw

## O que é a Heurística TRIMS?

A heurística **TRIMS** é um modelo criado por Richard Bradshaw e sua equipe para ajudar a **avaliar, criar e reestruturar checks automatizados** de forma mais eficaz. O nome vem da ideia de **"aparar" (trimming)** testes desnecessários para focar no que realmente agrega valor.

### Significado do Acrônimo TRIMS

- **T**argeted (Direcionado)
- **R**eliable (Confiável) 
- **I**nformative (Informativo)
- **M**aintainable (Manutenível)
- **S**peedy (Rápido)

## Como Aplicar a Heurística TRIMS

### T - Targeted (Direcionado)

**Objetivo:** Direcionar testes para riscos específicos na camada mais baixa possível.

**Como aplicar:**
- Identifique o risco específico que você quer mitigar
- Escolha a camada mais baixa onde é possível testar esse risco
- Evite testar na UI quando o risco está na API ou no nível unitário

**Exemplo prático:**
```
❌ Testar validação de email na UI
✅ Testar validação de email no nível unitário
```

### R - Reliable (Confiável)

**Objetivo:** Criar testes determinísticos que executam consistentemente.

**Como aplicar:**
- Elimine dependências externas instáveis
- Use dados de teste controlados
- Implemente esperas explícitas ao invés de timeouts fixos
- Monitore e corrija testes "flaky"

**Exemplo prático:**
```javascript
// ❌ Teste não confiável
await page.waitForTimeout(3000);

// ✅ Teste confiável
await page.waitForSelector('#result', { state: 'visible' });
```

### I - Informative (Informativo)

**Objetivo:** Fornecer informações úteis tanto em falhas quanto em sucessos.

**Como aplicar:**
- Inclua capturas de tela em falhas
- Grave vídeos de execução
- Adicione logs detalhados
- Implemente relatórios claros

**Exemplo prático:**
```javascript
// ✅ Teste informativo
test('login should work', async ({ page }) => {
  await page.screenshot({ path: 'before-login.png' });
  
  try {
    await page.fill('#email', 'user@test.com');
    await page.fill('#password', 'password123');
    await page.click('#login-btn');
    
    await expect(page.locator('#dashboard')).toBeVisible();
  } catch (error) {
    await page.screenshot({ path: 'login-failure.png' });
    throw error;
  }
});
```

### M - Maintainable (Manutenível)

**Objetivo:** Facilitar a manutenção e atualização dos testes.

**Como aplicar:**
- Use Page Object Model ou padrões similares
- Evite duplicação de código
- Mantenha testes simples e legíveis
- Documente casos complexos

**Exemplo prático:**
```javascript
// ✅ Código manutenível
class LoginPage {
  constructor(page) {
    this.page = page;
    this.emailInput = '#email';
    this.passwordInput = '#password';
    this.loginButton = '#login-btn';
  }
  
  async login(email, password) {
    await this.page.fill(this.emailInput, email);
    await this.page.fill(this.passwordInput, password);
    await this.page.click(this.loginButton);
  }
}
```

### S - Speedy (Rápido)

**Objetivo:** Otimizar tanto a execução quanto a manutenção dos testes.

**Como aplicar:**
- Execute testes em paralelo quando possível
- Use dados de teste pré-criados
- Implemente feedback rápido em pipelines
- Otimize seletores e esperas

**Exemplo prático:**
```javascript
// ✅ Execução rápida
test.describe.configure({ mode: 'parallel' });

test('fast API test', async ({ request }) => {
  const response = await request.get('/api/users');
  expect(response.status()).toBe(200);
});
```

## Processo de Aplicação da Heurística

### 1. Auditoria Atual
- Revise todos os testes existentes
- Avalie cada teste contra os critérios TRIMS
- Identifique testes que não atendem aos critérios

### 2. Processo de "Trimming"
- **Delete:** Remova testes desnecessários ou duplicados
- **Refactor:** Melhore testes que podem ser salvos
- **Relocate:** Mova testes para camadas mais apropriadas

### 3. Resultado Esperado
Richard Bradshaw reduziu seus testes de **2.500 checks** para:
- **400 checks na UI**
- **500 checks na API**

## Benefícios da Heurística TRIMS

1. **Redução de testes desnecessários**
2. **Feedback mais rápido e confiável**
3. **Menor custo de manutenção**
4. **Maior confiança na automação**
5. **Melhor direcionamento de esforços**

## Pergunta-Chave

> **"Este teste está direcionado ao risco certo, é confiável, informativo, manutenível e rápido?"**

Se a resposta for "não" para qualquer critério, considere refatorar ou remover o teste.

## Referências

- [TRIMS - A Mnemonic For Valuable Automation in Testing | Automation in Testing](https://automationintesting.com/2019/08/trims-automation-in-testing-strategy.html)
- [It's Time For A TRIM(S): Richard Bradshaw | LambdaTest](https://www.lambdatest.com/blog/its-time-for-a-trim/)
- [Vídeo Original: It's Time For A TRIM(S)](https://www.youtube.com/watch?v=uIDvGzQdoxc&t=1163s)