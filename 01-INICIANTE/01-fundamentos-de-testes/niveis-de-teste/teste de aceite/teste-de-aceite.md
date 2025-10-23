# Teste de Aceite

## O que é Teste de Aceite?

O **Teste de Aceite** é a fase final de testes antes da liberação do software para os usuários finais. Seu objetivo principal é verificar se o sistema atende aos requisitos de negócio e às expectativas dos usuários. É como uma "aprovação final" que confirma se o produto está pronto para ser usado no mundo real.

**Características principais:**
- Foca na validação dos requisitos de negócio
- Geralmente produz resultados binários (passa/falha)
- Preferencialmente realizado pelos próprios usuários finais
- É o último nível de teste antes da implantação

## Tipos de Teste de Aceite

A escolha do tipo de teste de aceite a ser realizado depende do contexto do projeto, da natureza do software e dos critérios que definem o seu sucesso.   

A variedade de tipos de testes de aceite demonstra que a "aceitação" de um software é um conceito multidimensional, que vai muito além da simples funcionalidade da interface do usuário. Um software pode ser perfeitamente funcional para o usuário (passando no UAT), mas ser impossível de manter pela equipe de TI (falhando no OAT). Pode ser amado pelos usuários e fácil de manter, mas violar uma nova lei de proteção de dados (falhando no RAT). Ou pode passar em todos esses testes, mas não entregar uma funcionalidade específica que estava no contrato de desenvolvimento (falhando no CAT).

Isso revela que a decisão de lançar um software ("Go-Live") não depende apenas da satisfação do usuário, mas de um conjunto holístico de critérios de aceitação. Uma falha em qualquer um desses eixos de validação representa um risco significativo para o negócio, podendo atrasar ou até mesmo cancelar um lançamento. Portanto, um planejamento de projeto robusto deve considerar todos esses aspectos desde o início.

A seguir, são detalhados os principais tipos de Teste de Aceite.

### Teste de Aceitação do Usuário (UAT - User Acceptance Testing)

Este é o tipo mais conhecido e comum. Seu foco principal é verificar se o sistema é adequado para o uso por parte dos usuários de negócio em seus fluxos de trabalho do dia a dia. O UAT valida se o software permite que os usuários realizem suas tarefas de maneira eficiente e eficaz em cenários do mundo real.   

### Teste de Aceitação Operacional (OAT - Operational Acceptance Testing)

Este teste concentra-se na prontidão operacional do sistema. É um tipo de teste não funcional que avalia a capacidade do sistema de ser operado e mantido no ambiente de produção. Os aspectos avaliados incluem procedimentos de backup e restauração, recuperação de desastres, gerenciamento de usuários, tarefas de manutenção, verificações de segurança e desempenho sob carga.   

### Teste de Aceitação de Contrato (CAT - Contract Acceptance Testing)

Essencial para projetos de software desenvolvidos sob encomenda, o CAT verifica se os critérios de aceite definidos em um contrato entre o cliente e o fornecedor foram atendidos. O sucesso neste teste é frequentemente um pré-requisito para o pagamento final e a aceitação formal do projeto.   

### Teste de Aceitação de Regulamentação (RAT - Regulation Acceptance Testing)

Este teste garante que o software está em conformidade com todas as leis e regulamentos governamentais ou setoriais aplicáveis. Exemplos incluem regulamentos de segurança, leis de privacidade de dados como a LGPD ou GDPR, ou normas específicas de setores como o financeiro e o de saúde.   

### Teste Alfa

É uma forma de teste de aceite realizada em um ambiente controlado, geralmente no local de desenvolvimento, por um grupo interno (funcionários, equipe de QA) ou por um grupo seleto de clientes. O objetivo é obter um feedback inicial sobre a funcionalidade e usabilidade, identificar bugs críticos antes de uma exposição mais ampla e refinar o produto.   

### Teste Beta (ou Teste de Campo)

Diferente do Teste Alfa, o Teste Beta é realizado por usuários finais reais em seus próprios ambientes, fora de um ambiente controlado. O software é disponibilizado para um público mais vasto, mas limitado, com o objetivo de obter feedback sobre o desempenho, a usabilidade e a confiabilidade do produto em uma ampla variedade de cenários do mundo real antes do seu lançamento comercial.


### Analogias do Cotidiano

- **O Test Drive de um Carro**: Quando você decide comprar um carro, o vendedor lhe apresenta uma ficha técnica com dados sobre o motor, consumo e itens de segurança. Isso é análogo aos requisitos técnicos verificados nos testes de sistema. Mas você não compra o carro apenas com base nisso. Você faz um test drive. Durante o test drive, você não está verificando a engenharia do motor; você está validando se o carro atende às suas necessidades: o banco é confortável? A dirigibilidade é agradável? O porta-malas tem espaço suficiente para as compras da sua família? O sistema de som é fácil de usar? O test drive é o seu Teste de Aceite pessoal para o carro.   

- **A Degustação em um Restaurante**: Um chef segue uma receita detalhada para preparar um prato. A receita são os requisitos técnicos. Ele garante que usou os ingredientes certos nas quantidades corretas e seguiu todos os passos. No entanto, a prova final é quando o cliente prova o prato. O cliente não sabe a receita, mas ele valida se o sabor, a textura e a apresentação estão de acordo com sua expectativa e paladar. O "aceite" do prato é dado pela satisfação do cliente, não pela precisão técnica do chef.   

- **A Montagem de um Móvel**: Ao comprar um móvel para montar em casa, você recebe um manual de instruções e um conjunto de peças. Seguir o manual corretamente garante que o móvel seja montado conforme o projeto (verificação). O Teste de Aceite ocorre depois que a montagem termina. Você abre e fecha a gaveta para ver se ela desliza suavemente. Você empurra o móvel para garantir que ele está estável. Você verifica se ele realmente cabe no espaço que você planejou e se cumpre a função desejada no seu quarto. Você valida o móvel no contexto do seu uso real.

## Teste de Aceite vs. Teste de Sistema

Esta é a fonte de maior confusão. O Teste de Sistema é realizado pela equipe de desenvolvimento ou de qualidade para verificar o sistema completo e integrado contra os requisitos funcionais e não funcionais. Seu foco é técnico. 

O Teste de Aceite, por outro lado, é tipicamente realizado por usuários finais ou clientes para validar o sistema contra as necessidades de negócio e fluxos de trabalho do usuário. Seu foco é o valor de negócio.

## Como Fazer Teste de Aceite: Passo a Passo

### Passo 1: Entender os Requisitos
- Revisar a documentação de requisitos
- Conversar com stakeholders
- Identificar critérios de aceite claros

### Passo 2: Criar o Plano de Teste
- Definir escopo do teste
- Identificar recursos necessários
- Estabelecer cronograma
- Definir critérios de entrada e saída

### Passo 3: Desenvolver Casos de Teste
- Criar cenários baseados em requisitos
- Usar linguagem simples e clara
- Incluir dados de teste realistas

### Passo 4: Executar os Testes
- Seguir os casos de teste
- Documentar resultados
- Registrar defeitos encontrados

### Passo 5: Analisar e Reportar
- Avaliar se critérios de aceite foram atendidos
- Gerar relatório de resultados
- Tomar decisão sobre aprovação

## Exemplos Práticos

### Exemplo 1: E-commerce - Processo de Compra

**Cenário:** Usuário adiciona produto ao carrinho e finaliza compra

**Critérios de Aceite:**
- O usuário consegue adicionar produtos ao carrinho
- O usuário consegue visualizar o carrinho com produtos corretos
- O usuário consegue finalizar a compra com sucesso
- O usuário recebe confirmação por email

**Teste:**
1. Acesse a página do produto
2. Clique em "Adicionar ao Carrinho"
3. Verifique se produto aparece no carrinho
4. Prossiga para checkout
5. Preencha dados de pagamento
6. Confirme a compra
7. Verifique recebimento do email de confirmação

### Exemplo 2: Sistema Bancário - Transferência

**Cenário:** Cliente realiza transferência entre contas

**Critérios de Aceite:**
- O sistema valida saldo suficiente
- A transferência é processada corretamente
- Ambas as contas são atualizadas
- Cliente recebe comprovante

**Teste:**
1. Faça login na conta
2. Acesse função de transferência
3. Insira dados da conta destino
4. Insira valor da transferência
5. Confirme a operação
6. Verifique dedução do saldo origem
7. Verifique crédito na conta destino
8. Verifique geração do comprovante

### Exemplo 3: App Mobile - Login

**Cenário:** Usuário faz login no aplicativo

**Critérios de Aceite:**
- Sistema aceita credenciais válidas
- Sistema rejeita credenciais inválidas
- Usuário é direcionado à tela principal após login
- Sistema mantém sessão ativa

**Teste:**
1. Abra o aplicativo
2. Insira email e senha corretos
3. Toque em "Entrar"
4. Verifique redirecionamento para tela principal
5. Feche e reabra o app
6. Verifique se sessão permanece ativa

## Dicas Importantes para Iniciantes

### ✅ Boas Práticas
- **Use linguagem simples:** Escreva testes que qualquer pessoa possa entender
- **Seja específico:** Defina critérios claros e mensuráveis
- **Use dados reais:** Teste com dados similares aos que serão usados em produção
- **Documente tudo:** Registre resultados, defeitos e observações
- **Envolva usuários:** Sempre que possível, inclua usuários finais nos testes

### ❌ Erros Comuns a Evitar
- Não confundir com testes funcionais (foco no negócio, não na função)
- Não deixar para a última hora
- Não assumir que testes técnicos são suficientes
- Não ignorar feedback dos usuários
- Não pular a documentação dos resultados

## Teste de Aceitação Ágil

O **Teste de Aceitação Ágil** é uma abordagem que integra práticas de validação de software diretamente no ciclo de desenvolvimento ágil. Diferente do teste de aceite tradicional (feito no final), o teste ágil acontece **durante todo o processo**, focando em comunicação colaborativa e especificação por exemplos.

**Características principais:**
- Baseado em **especificação por exemplos** em vez de requisitos abstratos
- Usa **workshops colaborativos** para definir critérios de aceitação
- Integrado ao ciclo de desenvolvimento (não apenas no final)
- Foco na comunicação entre negócio, desenvolvedores e testadores
- Gera uma **especificação viva** que guia o desenvolvimento

### Como Fazer Teste de Aceitação Ágil

#### 1. Workshop de Especificação (Início da Sprint)

**Participantes:**
- Product Owner/Stakeholders de negócio
- Desenvolvedores
- Testadores
- Facilitador (geralmente BA)

**Processo:**
1. **Apresentação da funcionalidade** pelo Product Owner
2. **Discussão colaborativa** usando exemplos realistas
3. **Exploração de casos limite** e cenários de erro
4. **Documentação de exemplos** em formato estruturado
5. **Definição dos critérios de aceitação** finais

**Duração:** 3-4 horas para uma sprint de 2 semanas

#### 2. Criação de Critérios com Formato Gherkin

Use o formato **Dado-Quando-Então** para estruturar os exemplos:

```
Cenário: Compra com cartão válido
Dado que o usuário tem um cartão com saldo suficiente
Quando ele finaliza uma compra de R$ 100,00
Então a compra é aprovada, debitando do cartão o valor
E o usuário recebe confirmação por email
```

#### 3. Integração com Histórias de Usuário (3 Cs)

**Cartão:** História de usuário básica
```
Como cliente
Quero finalizar compras online
Para receber produtos em casa
```

**Conversa:** Workshop de especificação (detalhamento)

**Confirmação:** Critérios de aceitação gerados no workshop

#### 4. Desenvolvimento Orientado por Exemplos

- Desenvolvedores usam os exemplos como **especificação viva**
- Testadores criam casos de teste baseados nos exemplos
- Automação de testes segue os mesmos critérios
- Validação contínua durante o desenvolvimento

#### 5. Validação e Feedback

- **Teste contínuo** durante a sprint
- **Demo** com stakeholders usando os exemplos definidos
- **Retrospectiva** para melhorar o processo
- **Refinamento** dos critérios se necessário

### Exemplo Prático: E-commerce

#### Workshop de Especificação

**Funcionalidade:** Sistema de desconto por cupom

**Exemplos discutidos:**
1. Cupom válido de 10% em compra de R$ 100 = R$ 90 final
2. Cupom expirado = mensagem de erro "Cupom expirado"
3. Cupom já usado = mensagem "Cupom já utilizado"
4. Valor mínimo não atingido = "Valor mínimo R$ 50"

**Critérios de Aceitação Resultantes:**
```
Cenário: Aplicar cupom válido
Dado que existe um cupom "DESC10" de 10% de desconto
E o cupom está válido
E não foi usado
E a compra é de R$ 100,00
Quando o usuário aplica o cupom "DESC10"
Então o desconto de R$ 10,00 é aplicado
E o valor final é R$ 90,00

Cenário: Cupom expirado
Dado que existe um cupom "DESC10" expirado
Quando o usuário tenta aplicar o cupom
Então o sistema exibe "Cupom expirado"
E nenhum desconto é aplicado
```

## Referências

- ISTQB Foundation Level Syllabus - Acceptance Testing
- Qase.io Blog: Acceptance Testing Guide. Disponível em: https://qase.io/blog/acceptance-testing/
- User Acceptance Testing: A step-by-step guide por Brian Hambling e Pauline van Goethem
- Bridging the Communication Gap: Specification by Example and Agile Acceptance Testing (English Edition)