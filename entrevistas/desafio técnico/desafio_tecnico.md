# Dicas de como enviar um bom desafio técnico

1. Para desenvolvimento de projetos de testes é necessário que o nome do projeto tenha um padrão.
   1. Ex.: [sigla_empresa.nome_da_aplicação-finalidade.Framework_ou_Linguagem_de_programação]
      1. **Resultado do nome do projeto:** EM.kanui-test.Cypress
      2. Onde EM é de NOME EMPRESA, kanui é a aplicação, test é a finalidade e Cypress o framework (poderia ser JavaScript também caso optasse)
2. Crie um arquivo só de padrões de desenvolvimento, por exemplo... Durante o desenvolvimento do projeto de teste existe esse arquivo de CR (Code Review) onde tem as boas práticas de desenvolvimento dos testes.
   1. Exemplo: 
      1. Nomenclatura de métodos de testes
         1. Para métodos que retorna o texto da tela, usar o padrão: getText + NomeDoElemento, sendo assim o resultado seria getTextNameClient()
         2. Para métodos que preencha um campo da tela, usar o padrão setText + NomeCampo, sendo assim o resultado seria setTextNameCompany()
         3. E assim usar para métodos de setar valor, obter valor, espera de campos e etc...
3. Use padrão de projeto (Page Objetcs ou app Actions) para organizar o projeto e não der duplicidade de código.
4. Padronize o idioma de todo o projeto, por exemplo se seu projeto está sendo escrito em português, logo todos os métodos, classes, arquivos e etc devem ser em português.
5. Não copie um projeto da sua empresa, pois pode existir arquivos que tenham dados sensíveis que sem querer você esqueceu de excluir na hora de mandar o projeto.
6. Faça algo a mais na entrega do desafio (para se destacar mais ainda entre os demais candidatos), por exemplo use a documentação do git hub para criar um pipeline de execução dos testes após comitar na branch da master.
   1. O "a mais" pode ser também pode ser add o sonar qube ao projeto também, mostrando que está preocupada com analise estática e das boas práticas de desenvolvimento do código (sem code smells)
7. Descreva no seu arquivo readme.md a estrutura do projeto, o que contém em cada pasta do projeto, o que cada arquivo faz e etc.. Quais libs (dependências) foram usadas no projeto e o que cada uma faz? explique o porque usou elas?