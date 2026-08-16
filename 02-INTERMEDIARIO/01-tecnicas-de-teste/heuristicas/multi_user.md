# Multi-User

**Criador:** Desconhecido

## O que é a Heurística Multi-User?

> > Crie, atualize, exclua simultaneamente de duas contas ou da mesma conta conectada duas vezes.

A Heurística Multi-User (ou heurística de múltiplos usuários/sessões concorrentes) foca em concorrência, integridade de dados e controle de estado.

Na prática, a maioria dos testes foca no caminho feliz de um único usuário interagindo isoladamente com a aplicação. A heurística Multi-User quebra essa premissa ao simular o mundo real, onde múltiplos acessos disputam e alteram os mesmos recursos ao mesmo tempo.

O que essa heurística avalia na prática:

- **Race Conditions (Condições de Corrida)**: O que acontece quando duas requisições tentam alterar o mesmo registro no exato milissegundo? O sistema trava, sobrescreve silenciosamente ou lida com elegância?
- **Controle de Concorrência (Pessimista vs. Otimista)**: O sistema avisa o segundo usuário que o dado mudou antes dele salvar, ou ocorre um Lost Update (o último que salva apaga o trabalho do primeiro)?
- **Integridade Referencial e Exclusão**: Se a Conta A exclui um item no mesmo instante em que a Conta B tenta editá-lo ou visualizá-lo, o sistema lida com erro 404/conflito ou estoura um erro 500 no backend?
- **Gestão de Sessão e Cache Local**: Ao abrir a mesma conta em duas abas/dispositivos e alterar o perfil em uma delas, a outra reflete o novo estado ou continua usando dados obsoletos de cache/token?

Cenários Clássicos para Aplicar:

- Edição Concorrente
  - Ação Concorrente: Usuário 1 e Usuário 2 abrem o mesmo formulário e salvam dados diferentes.
  - O que observar: O dado final reflete a intenção correta ou houve perda silenciosa de dados?
- Exclusão vs. Edição
  - Ação Concorrente: Usuário 1 clica em "Excluir" enquanto o Usuário 2 clica em "Salvar Alterações".
  - O que observar: O sistema bloqueia a edição com mensagem amigável ou entra em estado inconsistente?
- Consumo de Recurso Único
  - Ação Concorrente: Duas contas tentam reservar a última vaga ou comprar o último item em estoque.
  - O que observar: O sistema permite overbooking (dupla compra) ou aplica lock transacional correto?
- Dupla Sessão da Mesma Conta
  - Ação Concorrente: Fazer logout em uma aba e tentar executar uma ação crítica na outra aba aberta.
  - O que observar: O token antigo é invalidado imediatamente ou continua processando requisições?
