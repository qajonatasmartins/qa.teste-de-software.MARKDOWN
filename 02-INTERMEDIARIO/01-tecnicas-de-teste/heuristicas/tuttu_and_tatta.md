# Heurística TuTTu and TaTTa

**Criador:** Mark Winteringham

## O que é a Heurística TuTTu and TaTTa?

A heurística **TuTTu and TaTTa** é uma técnica que ajuda os testadores a determinar o **nível apropriado** para realizar testes de navegador e evitar o anti-padrão de verificação cross-browser desnecessária.

### Significado dos Acrônimos

- **TuTTu**: *Testing the UI* (Testando a Interface do Usuário)
- **TaTTa**: *Testing Through the UI* (Testando Através da Interface do usuário)

## Como Aplicar a Heurística

### 1. Testing the UI (TuTTu) - Quando usar Cross-Browser Testing

**Use quando:**
- Testando funcionalidades JavaScript que criam HTML dinamicamente
- Verificando renderização específica da interface
- Testando componentes visuais e interações de UI

**Exemplo prático:**
```javascript
// Teste necessário em múltiplos navegadores
function createDynamicMenu() {
    const menu = document.createElement('div');
    menu.className = 'dropdown-menu';
    // Lógica de criação de menu dinâmico
}
```

### 2. Testing Through the UI (TaTTa) - Quando NÃO usar Cross-Browser Testing

**Use quando:**
- Testando submissão de formulários
- Verificando armazenamento de dados
- Testando lógica de backend através da interface

**Exemplo prático:**
```javascript
// Teste em um único navegador é suficiente
function submitForm(data) {
    fetch('/api/users', {
        method: 'POST',
        body: JSON.stringify(data)
    });
}
```

## Pergunta-Chave para Aplicar a Heurística

> **"Estou testando um componente específico da UI ou apenas usando a UI como método de acesso?"**

- **Se testando componente específico da UI**: Use cross-browser testing (TuTTu)
- **Se testando lógica de backend**: Use teste em navegador único ou nível de API (TaTTa)

## Benefícios

1. **Otimização de recursos**: Evita testes cross-browser desnecessários
2. **Maior eficiência**: Direciona esforços para onde realmente importa
3. **Estratégia de teste mais precisa**: Testa no nível mais baixo possível que ainda valida a funcionalidade

## Recomendação Principal

**Empurre as verificações para a camada de teste mais baixa possível** que possa efetivamente validar a funcionalidade, minimizando a complexidade cross-browser desnecessária.

## Referências

- [ANTI-PADRÃO: VERIFICAÇÃO CRUZADA DO NAVEGADOR](https://www.mwtestconsultancy.co.uk/cross-browser-checking-anti-pattern/)