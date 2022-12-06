# Baica

**Criador:** Jonatas Martins Faria

## O que é a Heurística BAICA?

A heurística BAICA foi criada por Jonatas Faria para focar nos testes básicos que devem ser aplicados dentro de uma aplicação existente durante o desenvolvimento de novos produtos.

- **Básico:** Faça o básico. Quando for testar uma demanda pense em um fluxo simples visando verificar se a aplicação está se comportando corretamente. Pode se dizer que aplicamos um teste de smoke e sanidade nesta etapa.
- **Automação:** Para que seja criada a automação de testes, precisamos a cada nova demanda verificar também se existem mapeamentos corretos para desenvolvimento dos testes automatizados. Verifique se as listas de registros cadastrados, botões, campos, dropdownList/Combobox, labels entre outros possui uma identificação única não sendo obrigatoriamente ser um ID, mas sim um atributo que consiga diferenciar o elemento na hora dos testes automatizados.
- **Interrupção:** Interrompa o processo que esteja executando e veja se o sistema consegue prosseguir adiante com o que foi solicitado.
- **Criar novos dados:** Ao começar a testar uma nova funcionalidade que possua dependência de outras funcionalidades, crie os dados dependentes desde o início dos testes até chegar na funcionalidade desejada e faça todo o processo necessário. Com essa etapa você consegue identificar possíveis problemas ocasionados de uma dependência da sua funcionalidade e evita que problemas básicos sejam encontrados pelo cliente.
- **Anônimo:** Está etapa visa validar os dados da sua aplicação sendo executados em uma guia anônima, isso é interessante pois nossos clientes utilizam guias anônimas para deixa de salvar os dados de navegação e se sua aplicação necessita de salvar alguma informação é possível que o você não encontre o erro mas o cliente sim.