# Failure

**Criador:** Ben Simo

## O que é a Heurística Failure?

Se baseia em usabilidade no que tange a parte Funcional, Apropriada, Impacto, Log, UI, Recuperação, Emoções.

Ben Simo dizia que uma das suas irritações sobre o software era as mensagens de erros incorretas. 

Na opinião de Ben Simo, uma mensagem de erro incorreta é aquela que não informa ao usuário como o erro os afeta e o que eles precisam fazer em resposta ao erro. Muitas mensagens falham em comunicar essas informações em termos que o usuário do software entenderá. Muitas dessas mensagens são escritas para desenvolvedores, não para usuários.

Há um local para registro de erros em termos que ajudam desenvolvedores e testadores a solucionar problemas e corrigir problemas. Essas informações geralmente são melhor escritas para registrar arquivos, não exibidas na interface do usuário.

Pradeep acompanhou Ben Simo através de um exercício que demonstrava um caso em um aplicativo popular de escritório no qual Ben Simo, o usuário, não estava suficientemente informado de que um erro estava ocorrendo. Era óbvio que as ações que eu estava tentando executar não estavam funcionando, mas o software não me deu a Ben uma indicação clara de por que não funcionou como eu esperava.

Bons testadores reconhecem a necessidade de incluir "testes negativos" em sua busca por bugs significativos. Testar erros é uma parte comum dos testes funcionais. Vamos além do teste funcional de erros. Vamos testar erros de usabilidade.

Aqui está um erro testando o mnemônico que criei após a nossa conversa.

- Funcional
- Apropriado
- Impacto
- Log
- User interface
- Recuperação
- Emoções

### **Funcional**

- A detecção e o relatório de erros funcionam conforme necessário?
- Não são detectados erros que devem ser detectados? Os erros são relatados?
- As caixas de diálogo de erro funcionam como esperado? Os botões funcionam?

### **Apropriado ( ou A propósito*)**

- Os erros são detectados e relatados de maneira precisa e oportuna para o público-alvo?
- Os erros são relatados assim que uma condição de erro é atendida?
- As mensagens de aviso são exibidas enquanto há recursos suficientes para solucionar o problema?
- Um usuário pode perder tempo e esforço apenas para saber que seu trabalho não pode ser aplicado?
- O texto de uma mensagem é preciso?
- O texto transmite a situação ao público-alvo?
- O erro é descrito em termos que serão entendidos pelo público-alvo?

### **Impacto**

- O impacto do erro é suficientemente comunicado ao usuário?
- A mensagem contém pouca informação para o usuário entender o que ocorreu e como afeta o que estava tentando fazer?
- A mensagem contém informações extras que distraem a comunicação do impacto?

### **Log**

- As informações técnicas precisam ser registradas para suporte, administradores de sistema, desenvolvedores ou testadores?
- Essas informações de log estarão disponíveis se o usuário esperar para entrar em contato com o suporte?
- As mensagens de log são padronizadas para permitir a mineração automatizada de informações?
- Os registros são detalhados o suficiente para facilitar a solução de problemas? Os erros são registrados que não agregam valor? Existe muito log?
- O registro excessivo afeta negativamente o desempenho e o espaço em disco?
- O registro excessivo complica a investigação de erros?

### **UI**

- Os usuários recebem alguma indicação de que o que tentaram fazer falhou?
- As mensagens da interface do usuário são formuladas para o público-alvo?
- As mensagens de erro da interface do usuário são consistentes com a aparência do software?
- As mensagens de erro são consistentes com outras atividades que causam o mesmo erro em outras partes do aplicativo?
- Os erros são comunicados de maneira eficiente?
- Um usuário precisa clicar em caixas de diálogo excessivas?
- Esse erro é melhor comunicado como uma caixa de diálogo de erro?
- Esse erro é melhor comunicado à medida que o texto é adicionado à janela?
- Esse erro é melhor comunicado com audibilidade?

### **Recuperação**

- A mensagem de erro informa ao usuário como se recuperar da condição de erro?
- O software facilita a recuperação?
- Se necessário, as informações de contato são fornecidas?
- O usuário é solicitado a recuperar ou deixado para descobrir por conta própria?

### **Emoções**

- Que emoções provavelmente serão levantadas pela mensagem de erro?
- As informações na mensagem aumentam a frustração de um usuário ou ajudam a acalmá-la?
- Se um usuário for informado de que precisa pagar mais para usar um recurso, a mensagem os incentiva a atualizar ou os incentiva a encontrar o produto de um concorrente?
- A mensagem de erro causa mais confusão?

Aqui está uma mensagem de erro que Pradeep me deu para ajudar a testar o mnemônico. Que falhas você pode encontrar na mensagem de erro usando o mnemônico?

> **Mensagem**
> 
> Você tentou abrir a janela intitulada "Adicionando contato" e não pode abrir porque esse recurso está disponível apenas para membros premium. Para se tornar um membro premium, acesse www.questionsoftware.com. Além disso, os seguintes recursos que você não poderá usar:
> - Grupos
> - Cabide Legal
> - Contatos Especiais

Na próxima vez que você vir uma mensagem de erro ou não a vir, não pare em funcionalidade. Identifique o o porque da FALHA e retorne para o usuário.

- [Referência - Failure usability](https://www.questioningsoftware.com/2007/08/failure-usability.html)