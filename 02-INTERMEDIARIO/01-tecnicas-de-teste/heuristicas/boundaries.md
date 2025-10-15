# Boundaries - Heurística de Teste de Valores Limite

**Criador:** Desconhecido

## O que é a Heurística Boundaries?

A heurística Boundaries (Limites) foca em encontrar defeitos testando valores próximos aos limites de um sistema. Esta abordagem se baseia no princípio de que a maioria dos erros ocorre nas fronteiras dos domínios de entrada, onde as condições de contorno podem não ter sido adequadamente tratadas pelos desenvolvedores.

## Conceito Central

O objetivo é testar valores que estão:
- **No limite exato** (valor limite)
- **Imediatamente antes do limite** (quase pequeno demais)
- **Imediatamente depois do limite** (quase grande demais)
- **Fora dos limites** (inválidos)

## Tipos de Limites para Testar

### 1. Limites Numéricos

#### Exemplo: Campo de Idade (18-65 anos)
```
Valores de teste:
• 17 (inválido - menor que mínimo)
• 18 (válido - limite mínimo)
• 19 (válido - após limite mínimo)
• 64 (válido - antes do limite máximo)
• 65 (válido - limite máximo)
• 66 (inválido - maior que máximo)
```

#### Exemplo: Sistema de Pontuação (0-100 pontos)
```
Valores críticos:
• -1 (inválido)
• 0 (limite mínimo)
• 1 (primeiro valor válido)
• 99 (antes do máximo)
• 100 (limite máximo)
• 101 (inválido)
```

### 2. Limites de Tamanho de String

#### Exemplo: Campo Nome (máximo 50 caracteres)
```
Cenários de teste:
• String vazia: "" (0 caracteres)
• 1 caractere: "A"
• 49 caracteres: "João Silva Santos Costa Ferreira Lima Rodrigues"
• 50 caracteres: "João Silva Santos Costa Ferreira Lima Rodrigues M"
• 51 caracteres: "João Silva Santos Costa Ferreira Lima Rodrigues Ma"
```

#### Exemplo: Campo Senha (8-20 caracteres)
```
Testes de limite:
• 7 caracteres: "abc123!" (inválido)
• 8 caracteres: "abc1234!" (mínimo válido)
• 9 caracteres: "abc12345!" (após mínimo)
• 19 caracteres: "abc123456789012345!" (antes do máximo)
• 20 caracteres: "abc1234567890123456!" (máximo válido)
• 21 caracteres: "abc12345678901234567!" (inválido)
```

### 3. Limites de Data e Tempo

#### Exemplo: Sistema de Agendamento (próximos 30 dias)
```
Data atual: 15/01/2024

Cenários:
• 14/01/2024 (ontem - inválido)
• 15/01/2024 (hoje - válido?)
• 16/01/2024 (amanhã - válido)
• 13/02/2024 (29 dias - válido)
• 14/02/2024 (30 dias - limite máximo)
• 15/02/2024 (31 dias - inválido)
```

#### Exemplo: Horário de Funcionamento (08:00-18:00)
```
Testes:
• 07:59 (inválido)
• 08:00 (limite início)
• 08:01 (após início)
• 17:59 (antes do fim)
• 18:00 (limite fim)
• 18:01 (inválido)
```

### 4. Limites de Quantidade

#### Exemplo: Carrinho de Compras (máximo 99 itens)
```
Cenários:
• 0 itens (carrinho vazio)
• 1 item (primeiro item)
• 98 itens (antes do limite)
• 99 itens (limite máximo)
• 100 itens (excede limite)
```

#### Exemplo: Upload de Arquivos (máximo 5MB)
```
Tamanhos de teste:
• 0 bytes (arquivo vazio)
• 1 byte (arquivo mínimo)
• 4.99 MB (antes do limite)
• 5.00 MB (exatamente no limite)
• 5.01 MB (excede limite)
```

### 5. Limites de Precisão Decimal

#### Exemplo: Campo Preço (2 casas decimais)
```
Valores:
• 10 (sem decimais)
• 10.1 (1 casa decimal)
• 10.99 (2 casas - limite)
• 10.999 (3 casas - excede)
• 0.01 (valor mínimo)
• 0.001 (menor que precisão)
```

## Aplicação Prática em Diferentes Contextos

### E-commerce

#### Desconto Promocional (5% a 50%)
```
Testes de boundary:
• 4% (inválido)
• 5% (mínimo válido)
• 6% (após mínimo)
• 49% (antes do máximo)
• 50% (máximo válido)
• 51% (inválido)
```

#### Código Promocional (6 dígitos)
```
Códigos de teste:
• "12345" (5 dígitos - inválido)
• "123456" (6 dígitos - válido)
• "1234567" (7 dígitos - inválido)
• "PROMO1" (letras - formato inválido)
```

### Sistema Bancário

#### Transferência PIX (R$ 1 a R$ 5.000)
```
Valores críticos:
• R$ 0,99 (inválido)
• R$ 1,00 (mínimo)
• R$ 1,01 (após mínimo)
• R$ 4.999,99 (antes do máximo)
• R$ 5.000,00 (máximo)
• R$ 5.000,01 (inválido)
```

### Sistema de Reservas

#### Reserva de Hotel (check-in: hoje a 365 dias)
```
Datas de teste:
• Ontem (inválido)
• Hoje (válido)
• Amanhã (válido)
• 364 dias (antes do limite)
• 365 dias (limite máximo)
• 366 dias (inválido)
```

## Cenários Especiais de Boundary

### 1. Valores Zero e Negativos
```typescript
// Exemplo: Quantidade de produtos
function adicionarProduto(quantidade: number) {
    // Testes boundary:
    // -1 (negativo - inválido)
    // 0 (zero - caso especial)
    // 1 (primeiro valor positivo)
}
```

### 2. Caracteres Especiais em Strings
```
Campo de busca (máximo 100 caracteres):
• "@#$%^&*()" (caracteres especiais)
• "café" (acentos)
• "João's" (apóstrofe)
• "test@email.com" (formato email)
```

### 3. Limites de Performance
```
Upload simultâneo (máximo 3 arquivos):
• 2 arquivos (antes do limite)
• 3 arquivos (no limite)
• 4 arquivos (excede limite)
```

## Estratégias de Implementação

### 1. Identificação de Limites
- **Especificações:** Revisar documentação para encontrar limites
- **Interface:** Observar campos com restrições visuais
- **Banco de dados:** Verificar constraints e tipos de dados
- **Business rules:** Entender regras de negócio

### 2. Criação de Casos de Teste
```
Para cada limite identificado, criar testes:
1. Valor no limite inferior
2. Valor imediatamente abaixo do limite inferior
3. Valor imediatamente acima do limite inferior
4. Valor no limite superior
5. Valor imediatamente abaixo do limite superior
6. Valor imediatamente acima do limite superior
```

## Benefícios da Heurística Boundaries

1. **Alta Efetividade:** Muitos bugs ocorrem nos limites
2. **Cobertura Focada:** Testa pontos críticos com poucos casos
3. **Aplicável Universalmente:** Funciona em qualquer domínio
4. **Fácil Automação:** Casos de teste bem definidos
5. **ROI Alto:** Máximo de bugs encontrados com mínimo esforço