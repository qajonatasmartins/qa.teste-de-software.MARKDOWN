# Dependencies

**Criador:** Desconhecido

## O que é a Heurística Dependencies?

- Identifique os relacionamentos "tem um" (um cliente tem uma fatura; uma fatura tem vários itens de linha).
- Aplique as heurísticas [CRUD](./crud.md), [Count](./count.md), [Position](./position.md) e/ou [Selection](./selection.md) (o cliente tem 0, 1, muitas faturas; a fatura tem 0, 1, muitos itens de linha; exclua o último item de linha e leia.
- Atualize o primeiro item de linha
- Alguns, nenhum, todos os itens de linha são tributáveis
- Excluir cliente com 0, 1, muitas faturas)