# Perguntas feitas para QA em entrevistas

1. **Conceitos ágil**
   1. Você sabe me falar um pouco sobre como é o processo de teste no ciclo de desenvolvimento?
   2. Como você prioriza as tarefas em um contexto ágil?
   3. Quando é a hora de parar de testar?
   4. Como é o ciclo de vida do bug em um contexto ágil?
   5. Fale um pouco sobre o conceito de Scrum, Kanban (papéis, cerimônias)?
2. **Outros tópicos**
   1. Como é a sua metodologia de trabalho?
   2. Qual foi o seu principal desafio na carreira?
   3. Um projeto que atuou e usa como referência? No que contribuiu?
   4. Um projeto que atuou e não deu certo? Qual foi o problema?
   5. O que você agregaria para a equipe de Qualidade?
   6. Na área(testes e qualidade de software) cita algo que gosta de fazer e algo que não gosta de fazer...
   7. Está estudando algo nesse momento, pode citar o que/motivo...
3. **Conceitos gerais**
   1. O que é Teste funcional?
   2. O que é Teste não funcional?
   3. Cite exemplos de testes funcionais e não funcionais?
   4. Explique sobre a técnica de partição de equivalência?
   5. Explique sobre a técnica de análise de valor limite?
   6. O que é smoke test?
   7. O que é sanity test?
   8. O que é teste unitário, como é feito e porque quem é feito?
   9. O que é testes de integração?
   10. O que é testes de interface do usuário?
   11. Me fale sobre a pirâmide de Testes (conceito, como funciona)?
   12. O que é teste de mutação?
   13. Explique como escrever um caso de teste?
   14. Casos de Teste (estrutura dos casos de teste)?
   15. O que é BDD(estrutura, ferramentas e o que é gherkin) ?
   16. Conhece TDD ou ATDD, fale sobre?
   17. Sobre mock (para que serve, como funciona, quando utilizar)?
   18. Bug report (o que deve conter na descrição de um bug)?
   19. Como priorizar os bugs (como categorizar um bug) ?
   20. Quais heurísticas de testes você conhece? Fale sobre ela?
   21. CI x CD (para que serve, como deve ser implementado)?
   22. Sobre testes de API (quais ferramentas utilizadas, para que serve, status code, verbos HTTP)?
   23. O que deve conter em um relatório de testes (o que deve conter, quando gerar)?
   24. Métricas de testes (quais métricas utilizar)?
4. Ferramentas
   1. Como priorizar o que será automatizado?
   2. Qual é a importância da automação de testes?
   3. Page Objects (o que é, para que serve, como é estruturado no código)?
   4. Quais frameworks de testes automatizados você conhece? web, mobile e api?
      1. Exemplo: Selenium, WebDriverIO, robot framework, Protactor, Watir, Appium, Espresso, XCUITest, etc
   5. Quais ferramentas de gestão de dependências você já usou? (ex.: Maven, package.json, gemfile)
   6. Ferramentas de gerenciamento? (azure, jira, trello e etc..)
   7. Localizadores de elemento (quais existem, qual é mais performático)?
   8. Qual biblioteca de assertion vc já usou/usa (qual biblioteca utiliza, exemplos de assertion que utiliza no projeto, como validar os testes)
   9. O que é o cucumber, para que serve?
   10. O que é Data driven?
   11. Quais ferramentas de controle de versão (ex.: Git, SVN, TFS, etc) você conhece?
   12. Quais ferramentas de virtualização você conhece (ex.: Docker, Podman) ? já usou ou estudou qual? Para que usou?
   13. Ferramenta de CI (ex.: Jenkins, Gitlab, CircleCI, Bitrise, etc)
   14. Ferramenta de bugtracking (ex.: JIRA, Bugzilla, Mantis, etc)
   15. Device farm/Multi Browser (ex.: Browserstack, AWS Device Farm, Saucelabs, Firebase)
   16. Ferramentas controle mobile (Firebase, Testflight, Crashlytics, Bitrise)
   17. Quais bancos de dados você conhece (ex. Oracle, SQL, Mongo, Dynamo, Postgresql e ect..)?
   18. Fale um pouco sobre testes multi browser/multi devices?
       1. Exemplos de situações:
          1. Quando um determinado elemento demora para aparecer na tela, como tratar? (Exemplo de resposta: utilizar waits ao invés de esperas fixas (Thread.sleep())
          2. Como fazer um teste que o cadastro de cliente é único por CPF? (Exemplo de respostas: pode utilizar libs de geração de dados randômicos; pode excluir o registro logo antes/após o cadastro)
          3. Como fazer o teste da exclusão de um registro para que ele seja independente dos outros? (Exemplo de resposta: ter uma query ou chamada que cadastre primeiro o registro antes de excluí-lo)
5. Conceitos testes mobile
   1. O que é importante testar em um aplicativo mobile?
   2. Como escolher os dispositivos de teste? (exemplo: verificar quais são os devices mais utilizados através firebase ou outros.)
   3. Conceito de aplicativo nativo, web e híbrido?
   4. Me diga quais ferramentas para automação mobile você conhece? Como você faz para testar ios e android (faz separado ou em um mesmo projeto? Como foi montado a arquitetura do projeto?)
