# Baica

**Criador:** Jonatas Martins Faria

## O que é a Heurística BAICA?

A heurística BAICA foi criada por Jonatas Faria com o objetivo de focar nos testes básicos que devem ser aplicados dentro de uma aplicação existente durante o desenvolvimento de novos produtos.

- **Teste Básico:** Realize as ações mais simples. Quando estiver testando uma demanda, pense em um fluxo simples para verificar se a aplicação está se comportando corretamente. Pode-se dizer que aplicamos um teste de "smoke" e sanidade nessa etapa.
- **Automação:** Para criar a automação de testes, é necessário verificar, a cada nova demanda, se existem mapeamentos corretos para o desenvolvimento dos testes automatizados. Verifique se as listas de registros cadastrados, botões, campos, dropdowns/comboboxes, rótulos, entre outros, possuem uma identificação única, que não necessariamente precisa ser um ID, mas sim um atributo que possa diferenciar o elemento durante os testes automatizados.
- **Interrupção**: Pare o processo em execução e verifique se o sistema consegue continuar a funcionar corretamente com o que foi solicitado.
- **Criação de Novos Dados:** Ao começar a testar uma nova funcionalidade que depende de outras funcionalidades, crie os dados dependentes desde o início dos testes até alcançar a funcionalidade desejada e execute todo o processo necessário. Essa etapa permite identificar possíveis problemas causados por dependências da sua funcionalidade e evita que problemas básicos sejam encontrados pelo cliente.
- **Modo Anônimo:** Esta etapa visa validar os dados da sua aplicação sendo executados em uma guia anônima. Isso é importante, pois nossos clientes utilizam guias anônimas para não salvar os dados de navegação, e se sua aplicação precisa salvar alguma informação, é possível que você não encontre o erro, mas o cliente sim.
