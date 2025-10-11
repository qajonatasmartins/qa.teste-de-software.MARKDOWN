# Error guessing ou Erro imaginado

É uma técnica de teste baseada em experiência, na qual o testador usa sua experiência para adivinhar as áreas problemáticas do aplicativo. **Essa técnica requer necessariamente testadores qualificados e experientes.**

É um tipo de técnica de teste de caixa preta e pode ser vista como uma abordagem não estruturada ao teste de software. Nesta técnica, pressupoem que o testador pode desenvolver situações de teste baseado na sua própria experiência e intuição. Lembre-se, a técnica de adivinhação de erros não segue nenhuma regra específica.

Considerando-se os nossos exemplos abaixo:

## Exemplos

### **Exemplo número 1**

```18 <= Idade <= 65```

Poderíamos supor os seguintes testes de Error guessing:

>> Idade = 0000
>> Idade = 9999
>> Idade = Branco
>> Idade = -1
>> Idade = Inserir um espaço

### **Exemplo número 2**

Dado uma tela de login com campos de e-mail, senha, botão [Logar] e botão de [Esqueci a senha?], pode ser feitos os seguintes testes baseados em erros imaginados pelo testador:

- Inserindo espaços em branco nos campos de texto (e-mail e senha)
- Pressionando o botão Logar sem inserir valores.
- Clique rapidamente nos botões de logar
- Informe muitos caracteres no campo de e-mail e senha e clique em Logar
- E-mail inválido, sem mascara e etc.

## Quando executar o Error guessing?

Geralmente deve ser realizado quando a maioria das técnicas formais de teste for aplicada.

## Os seguintes fatores podem ser usados para Error guessing

- Lições aprendidas em lançamentos anteriores
- Intuição do testador
- Aprendizagem histórica
- Defeitos anteriores
- Tickets de produção
- Lista de verificação de revisão
- interface do aplicativo
- Resultados de testes anteriores
- Relatórios de risco do aplicativo
- Variedade de dados usados para testes.
- Regras gerais de teste
- Conhecimento sobre Ambiente
- Compreensão da aplicação testada

## Vantagens da técnica de Error guessing

- Prova ser muito eficaz quando usado em combinação com outras técnicas formais de teste.
- Ele descobre os defeitos que, de outra forma, não seriam possíveis de descobrir, através de testes formais. Assim, a experiência do testador economiza muito tempo e esforço.
- O Error guessing complementa as técnicas formais de design de teste.
- Muito útil para adivinhar áreas problemáticas do aplicativo.

## Desvantagens da técnica de Error guessing

- A falha focal dessa técnica é que ela depende da pessoa e, portanto, a experiência do testador controla a qualidade dos casos de teste.
- Também não pode garantir que o software tenha atingido a referência de qualidade esperada.
- Somente testadores experientes podem realizar esse teste. Iniciantes não podem executa-la.

## Referências

- [O Que É A Técnica De Adivinhação De Erros?](https://www.softwaretestinghelp.com/error-guessing-technique/)
- [Livro Análise de riscos em projetos de teste de software](https://www.amazon.com.br/An%C3%A1lise-Riscos-Projetos-Teste-Software/dp/8576081008/ref=sr_1_1?__mk_pt_BR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=18CKU7GN3FNZU&keywords=An%C3%A1lise+de+riscos+em+projetos+de+teste+de+software&qid=1674428102&sprefix=an%C3%A1lise+de+riscos+em+projetos+de+teste+de+software%2Caps%2C192&sr=8-1)