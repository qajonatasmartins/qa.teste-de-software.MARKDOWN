# qa.teste-de-software.MARKDOWN

Projeto com conceitos, dicas, técnicas e outros pontos de teste de software.

## Índice

- [Artigos](/artigos/artigos.md)
- [Palestras](/palestras/palestras.md)
- Fundamentos de testes
  - Erro, Defeito e Falha
- Tipos de testes
  - [Testes funcional](./tipos%20de%20testes/teste%20funcional/teste_funcional.md)
    - [Teste de caixa preta](./tipos%20de%20testes/teste%20funcional/teste%20de%20caixa%20preta/caixa_preta.md)
      - [Técnicas Analise de valor limite](./tipos%20de%20testes/teste%20funcional/teste%20de%20caixa%20preta/t%C3%A9cnicas%20de%20caixa%20preta/analise_de_valor_limite.md)
      - [Técnicas Particionamento de equivalência](./tipos%20de%20testes/teste%20funcional/teste%20de%20caixa%20preta/t%C3%A9cnicas%20de%20caixa%20preta/particionamento_de_equivalencia.md)
      - [Adivinhação de erro (Erro imaginado)](./tipos%20de%20testes/teste%20funcional/teste%20de%20caixa%20preta/t%C3%A9cnicas%20de%20caixa%20preta/advinhacao_erro.md)
    - [Teste de caixa branca](./tipos%20de%20testes/teste%20funcional/teste%20de%20caixa%20branca/teste_caixa_branca.md)
    - Teste de caixa cinza
    - Teste baseado em experiência
  - [Teste não funcional](./tipos%20de%20testes/teste%20n%C3%A3o%20funcional/teste_nao_funcional.md)
    - Performance
      - Métricas de performance
      - Tipos de testes de performance
        - Teste de capacidade
        - Teste de carga
        - Teste de concorrência
        - Teste de escalabilidade
        - Teste de extresse
        - Teste de performance
        - Teste de pico
        - Teste de resistência
    - Usabilidade
    - [Segurança](./tipos%20de%20testes/teste%20n%C3%A3o%20funcional/teste%20de%20seguran%C3%A7a/teste_de_seguranca.md)
    - Compatibilidade
    - Confiabilidade
    - Manutenção
    - Portabilidade
  - Teste relacionado a mudança
- Testes dinâmicos
- Testes estáticos
- Niveis de testes
  - Teste de aceite
  - Teste de componente
  - Teste de integração
  - Teste de sistema
- Mobile
  - Emuladores e simuladores
  - Técnicas de teste baseados na experiência
  - Tipos de testes
- Segurança
- Características de qualidade de software
- [Heurística](./heur%C3%ADsticas/01_introducao.md)
- Automação de testes
  - Web
  - Mobile
  - API
  - Visual Regression
  - Mutação
  - Unitário
  - Instrumentados
  - Desktop
- Cases de sucesso (implantação de cultura de qualidade)
  - Teste de portabilidade
  - Teste de usabilidade
  - Teste de adequação funcional
  - Teste de correção funcional
  - Teste de integridade funcional
  - Teste de interoperabilidade
- DevOps
- QaOps
- [Metodos ágeis](./métodologias%20ageis/metodologias_intro.md)
- [Refêrencias de Qualidade de Software](./refer%C3%AAncias%20de%20qualidade/referencia_de_qualidade.md)
- Cursos
- [Livros para QAs do zero ao avançado](./livros%20QA/livros.md)
- [Sites para QA](./sites%20para%20QA/sitesQA.md)
- Trilha de carreira
- [Repositórios Úteis para QA](./repositorios%20uteis/repositorios.md)
- [Canais do Youtube QA](./canais%20do%20youtube%20qa/canaisQA.md)
- [Frameworks/Ferramentas](./frameworks/introducao_frameworks.md)
- [Dicas de processos de QA](./dicas%20de%20processos%20de%20QA/QA%20(Processos).png)
- Entrevistas QA
  - [Perguntas](./entrevistas/perguntas//perguntas.md)
  - [Dicas de como enviar um bom desafio técnico](./entrevistas/desafio%20t%C3%A9cnico/desafio_tecnico.md)
- FAQ
  - [Mobile](./faq/mobile/mobilefaq.md)
  - [Web](./faq//web/webfaq.md)

## Solicitações de inclusão

### Como abrir uma solicitação de inclusão de material

Visando um reconhecimento de todas as pessoas que de alguma forma contribuem com o repositório, a solicitação de inclusão deve ser feita via pull request e assim que aprovada seu nome irá aparecer como um contribuidor do projeto, que massa né?

Segue o passo a passo

#### Passo 1: Clone do Projeto

- Neste repositório, clique no botão "Fork" no canto superior direito da página para criar uma cópia do repositório em sua própria conta GitHub.
- No seu perfil GitHub, navegue até o repositório que você acabou de fazer o fork.
- Clique no botão "Code" e copie a URL do repositório.
- Na sua maquina, clone o projeto pelo vscode ou IDE desejada

#### Passo 2: Crie uma Nova Branch

- Certifique-se de estar na branch principal do repositório (geralmente chamada de "main" ou "master").
```
git checkout main
git pull origin main
```
- Crie uma nova branch para o seu trabalho. Dê a ela um nome descritivo relacionado à tarefa que você está realizando.

```
git checkout -b nome-da-sua-branch
```

#### Passo 3: Faça e Commite Suas Alterações

- Faça as alterações desejadas nos arquivos do projeto. Use os seguintes comandos para adicionar e commitar suas alterações.

```
git add .
git commit -m 
"Descrição curta das suas alterações"
```

#### Passo 4: Push das Alterações para o Seu Repositório Fork

```
git push origin nome-da-sua-branch
```

#### Passo 5: Abra o Pull Request

- Visite o repositório original [clique aqui](https://github.com/qajonatasmartins/qa.teste-de-software.MARKDOWN).
- Você deve ver um aviso indicando que você fez um novo push na sua branch recentemente. Clique no botão "Compare & pull request".
- Preencha os detalhes do pull request:
  - Escreva um título descritivo e uma descrição detalhada das suas alterações.
  - Se necessário, mencione os problemas (issues) relacionados ao seu pull request usando "#" seguido pelo número do issue.
- Clique em "Create pull request" para abrir o seu pull request.

#### Passo 6: Discussão e Revisão

- Será avaliado a sua sujestão para analisar se faz sentido a inclusão.

#### Passo 7: Merge do Pull Request

Quando o seu pull request estiver pronto para ser mesclado, um mantenedor do repositório ou colaborador com permissões suficientes irá mesclá-lo.
Após o merge, sua branch será mesclada à branch principal do repositório e seu nome será mensionado como um contribuidor do projeto.

E pronto! Você concluiu com sucesso o processo de abertura de um pull request no GitHub.
