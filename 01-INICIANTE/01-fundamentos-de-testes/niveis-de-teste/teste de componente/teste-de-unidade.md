# Teste de Unidade (Unit Testing)

## O que é Teste de Unidade?

O **teste de unidade** (ou teste unitário) é a **primeira etapa do processo de validação** do software, caracterizando-se como um teste de baixo nível. Seu objetivo primordial é **testar componentes individuais de uma aplicação** para **garantir a qualidade da unidade de software** ou de um determinado componente tecnológico.

Imagine que você está construindo uma casa. Antes de juntar todas as peças, você precisa verificar se cada tijolo, cada viga e cada componente elétrico funciona corretamente de forma isolada. O teste de unidade faz exatamente isso com o código: verifica se cada pequena parte funciona antes de integrar tudo.

## Características Principais

### Quem Realiza?

O teste de unidade é geralmente realizado pelo **próprio desenvolvedor** ou por um profissional dedicado de QA com conhecimento técnico, e exige um **profundo conhecimento da estrutura interna** do produto.

### O que é uma "Unidade"?

Uma unidade pode ser:

- Uma **função** ou método
- Uma **classe**
- Um **módulo**
- Um **componente** pequeno e independente

## Objetivos do Teste de Unidade

O objetivo dos testes de unidade é **garantir a qualidade do componente tecnológico** ao avaliar tanto sua estrutura interna quanto sua perfeita adequação aos requisitos definidos.

### 1. Foco na Estrutura Interna (Caixa Branca)

Essencialmente, os testes unitários são **orientados à estrutura interna de implementação do componente**, sendo primariamente caracterizados como testes de **caixa branca**. O foco de verificação está na **menor unidade de projeto do software**.

O objetivo é **exercitar adequadamente toda a estrutura interna** do componente, como:

- Desvios condicionais (if, else, switch)
- Laços de processamento (for, while)
- Fluxos alternativos
- Tratamento de exceções

### 2. Foco nos Requisitos (Caixa Preta)

Embora o teste de unidade seja orientado à estrutura interna, a validação de uma unidade de software somente é considerada completa se forem aplicados testes que validem seus requisitos, utilizando a estratégia de **caixa preta**.

A abordagem de caixa preta em testes unitários visa validar **todos os requisitos funcionais** relacionados ao componente específico.

## Exemplos Práticos em TypeScript

### Exemplo 1: Função Simples - Calculadora

Vamos começar com um exemplo simples de uma calculadora:

```typescript
// calculadora.ts
export class Calculadora {
  somar(a: number, b: number): number {
    return a + b;
  }

  subtrair(a: number, b: number): number {
    return a - b;
  }

  multiplicar(a: number, b: number): number {
    return a * b;
  }

  dividir(a: number, b: number): number {
    if (b === 0) {
      throw new Error('Não é possível dividir por zero');
    }
    return a / b;
  }
}
```

**Teste unitário correspondente:**

```typescript
// calculadora.test.ts
import { Calculadora } from './calculadora';

describe('Calculadora', () => {
  let calculadora: Calculadora;

  beforeEach(() => {
    calculadora = new Calculadora();
  });

  // Teste de caixa preta - validando requisito funcional
  test('deve somar dois números corretamente', () => {
    const resultado = calculadora.somar(2, 3);
    expect(resultado).toBe(5);
  });

  test('deve subtrair dois números corretamente', () => {
    const resultado = calculadora.subtrair(5, 3);
    expect(resultado).toBe(2);
  });

  test('deve multiplicar dois números corretamente', () => {
    const resultado = calculadora.multiplicar(4, 3);
    expect(resultado).toBe(12);
  });

  // Teste de caixa branca - exercitando desvio condicional
  test('deve dividir dois números corretamente', () => {
    const resultado = calculadora.dividir(10, 2);
    expect(resultado).toBe(5);
  });

  // Teste de caixa branca - exercitando tratamento de exceção
  test('deve lançar erro ao dividir por zero', () => {
    expect(() => {
      calculadora.dividir(10, 0);
    }).toThrow('Não é possível dividir por zero');
  });
});
```

### Exemplo 2: Validação de Dados - Classe de Usuário

```typescript
// usuario.ts
export class Usuario {
  private nome: string;
  private email: string;
  private idade: number;

  constructor(nome: string, email: string, idade: number) {
    this.validarNome(nome);
    this.validarEmail(email);
    this.validarIdade(idade);
    
    this.nome = nome;
    this.email = email;
    this.idade = idade;
  }

  private validarNome(nome: string): void {
    if (!nome || nome.trim().length === 0) {
      throw new Error('Nome não pode ser vazio');
    }
    if (nome.length < 3) {
      throw new Error('Nome deve ter pelo menos 3 caracteres');
    }
  }

  private validarEmail(email: string): void {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(email)) {
      throw new Error('Email inválido');
    }
  }

  private validarIdade(idade: number): void {
    if (idade < 0 || idade > 150) {
      throw new Error('Idade inválida');
    }
  }

  getNome(): string {
    return this.nome;
  }

  getEmail(): string {
    return this.email;
  }

  getIdade(): number {
    return this.idade;
  }

  ehMaiorDeIdade(): boolean {
    return this.idade >= 18;
  }
}
```

**Teste unitário correspondente:**

```typescript
// usuario.test.ts
import { Usuario } from './usuario';

describe('Usuario', () => {
  
  describe('Criação de usuário', () => {
    // Cenário básico - caixa preta
    test('deve criar um usuário válido', () => {
      const usuario = new Usuario('João Silva', 'joao@email.com', 25);
      
      expect(usuario.getNome()).toBe('João Silva');
      expect(usuario.getEmail()).toBe('joao@email.com');
      expect(usuario.getIdade()).toBe(25);
    });
  });

  describe('Validação de nome', () => {
    // Exercitando desvios condicionais - caixa branca
    test('deve lançar erro quando nome for vazio', () => {
      expect(() => {
        new Usuario('', 'joao@email.com', 25);
      }).toThrow('Nome não pode ser vazio');
    });

    test('deve lançar erro quando nome tiver menos de 3 caracteres', () => {
      expect(() => {
        new Usuario('Jo', 'joao@email.com', 25);
      }).toThrow('Nome deve ter pelo menos 3 caracteres');
    });

    test('deve aceitar nome com exatamente 3 caracteres', () => {
      const usuario = new Usuario('Ana', 'ana@email.com', 25);
      expect(usuario.getNome()).toBe('Ana');
    });
  });

  describe('Validação de email', () => {
    // Exercitando validação de padrão - caixa branca
    test('deve lançar erro quando email for inválido', () => {
      expect(() => {
        new Usuario('João Silva', 'email-invalido', 25);
      }).toThrow('Email inválido');
    });

    test('deve aceitar email válido', () => {
      const usuario = new Usuario('João Silva', 'joao.silva@empresa.com.br', 25);
      expect(usuario.getEmail()).toBe('joao.silva@empresa.com.br');
    });
  });

  describe('Validação de idade', () => {
    // Exercitando diferentes fluxos - caixa branca
    test('deve lançar erro quando idade for negativa', () => {
      expect(() => {
        new Usuario('João Silva', 'joao@email.com', -1);
      }).toThrow('Idade inválida');
    });

    test('deve lançar erro quando idade for maior que 150', () => {
      expect(() => {
        new Usuario('João Silva', 'joao@email.com', 151);
      }).toThrow('Idade inválida');
    });

    test('deve aceitar idade no limite inferior (0)', () => {
      const usuario = new Usuario('Bebê Silva', 'bebe@email.com', 0);
      expect(usuario.getIdade()).toBe(0);
    });

    test('deve aceitar idade no limite superior (150)', () => {
      const usuario = new Usuario('Matusalém Silva', 'matusalem@email.com', 150);
      expect(usuario.getIdade()).toBe(150);
    });
  });

  describe('Verificação de maioridade', () => {
    // Testando lógica de negócio - caixa preta
    test('deve retornar false para menor de idade', () => {
      const usuario = new Usuario('João Silva', 'joao@email.com', 17);
      expect(usuario.ehMaiorDeIdade()).toBe(false);
    });

    test('deve retornar true para maior de idade', () => {
      const usuario = new Usuario('João Silva', 'joao@email.com', 18);
      expect(usuario.ehMaiorDeIdade()).toBe(true);
    });

    test('deve retornar true para idade acima de 18', () => {
      const usuario = new Usuario('João Silva', 'joao@email.com', 25);
      expect(usuario.ehMaiorDeIdade()).toBe(true);
    });
  });
});
```

### Exemplo 3: Serviço com Dependências - Usando Mocks

Quando uma unidade depende de outras unidades, usamos **mocks** (simuladores) para isolar o teste:

```typescript
// conta-bancaria.service.ts
export interface ContaBancariaRepository {
  obterSaldo(contaId: string): Promise<number>;
  atualizarSaldo(contaId: string, novoSaldo: number): Promise<void>;
}

export class ContaBancariaService {
  constructor(private repository: ContaBancariaRepository) {}

  async sacar(contaId: string, valor: number): Promise<void> {
    if (valor <= 0) {
      throw new Error('Valor de saque deve ser positivo');
    }

    const saldoAtual = await this.repository.obterSaldo(contaId);

    if (saldoAtual < valor) {
      throw new Error('Saldo insuficiente');
    }

    const novoSaldo = saldoAtual - valor;
    await this.repository.atualizarSaldo(contaId, novoSaldo);
  }

  async depositar(contaId: string, valor: number): Promise<void> {
    if (valor <= 0) {
      throw new Error('Valor de depósito deve ser positivo');
    }

    const saldoAtual = await this.repository.obterSaldo(contaId);
    const novoSaldo = saldoAtual + valor;
    await this.repository.atualizarSaldo(contaId, novoSaldo);
  }
}
```

**Teste unitário com mocks:**

```typescript
// conta-bancaria.service.test.ts
import { ContaBancariaService, ContaBancariaRepository } from './conta-bancaria.service';

describe('ContaBancariaService', () => {
  let service: ContaBancariaService;
  let mockRepository: jest.Mocked<ContaBancariaRepository>;

  beforeEach(() => {
    // Criando um mock (simulador) do repositório
    mockRepository = {
      obterSaldo: jest.fn(),
      atualizarSaldo: jest.fn(),
    };
    
    service = new ContaBancariaService(mockRepository);
  });

  describe('Sacar', () => {
    // Cenário básico - caixa preta
    test('deve realizar saque com sucesso quando há saldo suficiente', async () => {
      const contaId = '123';
      const saldoInicial = 1000;
      const valorSaque = 500;

      mockRepository.obterSaldo.mockResolvedValue(saldoInicial);
      mockRepository.atualizarSaldo.mockResolvedValue();

      await service.sacar(contaId, valorSaque);

      expect(mockRepository.obterSaldo).toHaveBeenCalledWith(contaId);
      expect(mockRepository.atualizarSaldo).toHaveBeenCalledWith(contaId, 500);
    });

    // Cenário de exceção - caixa branca
    test('deve lançar erro quando valor de saque for zero', async () => {
      await expect(service.sacar('123', 0))
        .rejects.toThrow('Valor de saque deve ser positivo');
    });

    test('deve lançar erro quando valor de saque for negativo', async () => {
      await expect(service.sacar('123', -100))
        .rejects.toThrow('Valor de saque deve ser positivo');
    });

    test('deve lançar erro quando saldo for insuficiente', async () => {
      mockRepository.obterSaldo.mockResolvedValue(100);

      await expect(service.sacar('123', 500))
        .rejects.toThrow('Saldo insuficiente');
    });

    // Verificando que não houve chamada indevida
    test('não deve atualizar saldo quando não há saldo suficiente', async () => {
      mockRepository.obterSaldo.mockResolvedValue(100);

      try {
        await service.sacar('123', 500);
      } catch (error) {
        // Esperado
      }

      expect(mockRepository.atualizarSaldo).not.toHaveBeenCalled();
    });
  });

  describe('Depositar', () => {
    test('deve realizar depósito com sucesso', async () => {
      const contaId = '123';
      const saldoInicial = 1000;
      const valorDeposito = 500;

      mockRepository.obterSaldo.mockResolvedValue(saldoInicial);
      mockRepository.atualizarSaldo.mockResolvedValue();

      await service.depositar(contaId, valorDeposito);

      expect(mockRepository.obterSaldo).toHaveBeenCalledWith(contaId);
      expect(mockRepository.atualizarSaldo).toHaveBeenCalledWith(contaId, 1500);
    });

    test('deve lançar erro quando valor de depósito for zero', async () => {
      await expect(service.depositar('123', 0))
        .rejects.toThrow('Valor de depósito deve ser positivo');
    });

    test('deve lançar erro quando valor de depósito for negativo', async () => {
      await expect(service.depositar('123', -100))
        .rejects.toThrow('Valor de depósito deve ser positivo');
    });
  });
});
```

## Scaffolding - Estrutura de Suporte para Testes

Como um componente não é um programa independente, é necessário o uso de uma **estrutura temporária** (conhecida como *scaffolding*) para criar o framework de teste. Isso geralmente envolve:

### Driver (Controlador de Testes)

Um **pseudocontrolador** que atua como um "programa principal" para aceitar dados de caso de teste, passá-los para o componente (unidade a ser testada) e imprimir resultados relevantes. A criação de **controladores para aplicar os testes unitários** permite o processamento automatizado, proporcionando rapidez e confiabilidade na execução das validações.

### Stub/Mock (Simulador)

Substitui módulos subordinados chamados pelo componente em teste. No exemplo acima do `ContaBancariaService`, o `mockRepository` é um simulador (stub) que substitui o repositório real.

## Abordagens de Teste de Unidade

### 1. Abordagem Isolada

As unidades são testadas de forma **totalmente isolada** das demais. Isso elimina dependências e permite testes paralelos.

**Exemplo:** Para testar uma unidade de software (Unidade E) que chama as Unidades H, I e J, é necessário construir **simuladores** (Simulador H, Simulador I, Simulador J) para responder às chamadas da Unidade E.

```typescript
// Exemplo de teste isolado
describe('ServicoE', () => {
  test('deve processar dados usando serviços dependentes', () => {
    const mockServicoH = { processar: jest.fn().mockReturnValue('resultado H') };
    const mockServicoI = { processar: jest.fn().mockReturnValue('resultado I') };
    const mockServicoJ = { processar: jest.fn().mockReturnValue('resultado J') };
    
    const servicoE = new ServicoE(mockServicoH, mockServicoI, mockServicoJ);
    const resultado = servicoE.executar();
    
    expect(resultado).toBeDefined();
    expect(mockServicoH.processar).toHaveBeenCalled();
  });
});
```

### 2. Abordagem Top-down

Comum em projetos estruturados. Unidades de níveis hierárquicos superiores (que chamam a unidade testada) são usadas, mas as unidades inferiores (chamadas pela unidade testada) ainda não foram criadas, necessitando de **simuladores**.

### 3. Abordagem Bottom-up

Comum em projetos orientados a objetos. As unidades mais básicas e especializadas são codificadas antes. Os testes exigirão **controladores de testes** (drivers) para simular as chamadas às rotinas especializadas das classes. Essa abordagem não exige a utilização de simuladores, pois o processo de criação é de baixo para cima.

## Testes Unitários em Arquitetura OO

Em projetos orientados a objetos (OO), os pacotes de especialização (*packages*) podem orientar quais requisitos testar em cada unidade:

| Tipo de Pacote | Foco do Teste | Exemplo de Cenário |
|----------------|---------------|-------------------|
| **User Packages** (Interfaces) | Requisitos de Usabilidade | Testar navegações, padrões de telas, validações de entrada e campos obrigatórios |
| **Business Packages** (Transações) | Requisitos Funcionais | Testar cenários básicos, alternativos e de exceção vinculados a regras de negócios |
| **Data Packages** (Acesso a Dados) | Requisitos de Armazenamento | Testar operações de CRUD, stored procedures e transações de backup |

## Pontos de Validação em Testes de Caixa Branca

- **Exercitar todas as linhas de código** existentes no código-fonte
- **Exercitar todos os desvios condicionais** (if, else, switch)
- **Exercitar todos os laços de processamento** (for, while, do-while)
- **Exercitar todos os fluxos alternativos** de processamento
- **Exercitar o tratamento de exceções**

## Benefícios dos Testes de Unidade

1. **Detecção Precoce de Bugs**: Problemas são encontrados logo no início do desenvolvimento
2. **Documentação Viva**: Os testes servem como documentação de como o código deve funcionar
3. **Facilita Refatoração**: Você pode modificar o código com confiança, sabendo que os testes alertarão sobre quebras
4. **Design Melhor**: Escrever testes força você a pensar em design modular e desacoplado
5. **Redução de Custos**: Corrigir bugs na fase de desenvolvimento é muito mais barato que em produção

## Boas Práticas

1. **Teste uma coisa por vez**: Cada teste deve verificar apenas um comportamento específico
2. **Nomenclatura Clara**: O nome do teste deve descrever o que está sendo testado
3. **Arrange-Act-Assert (AAA)**: Organize seus testes em três seções claras
4. **Independência**: Testes não devem depender uns dos outros
5. **Rápidos**: Testes unitários devem executar rapidamente
6. **Isolamento**: Use mocks para isolar a unidade testada de suas dependências

## Ferramentas Comuns para TypeScript

- **Jest**: Framework de testes completo com suporte a mocks
- **Mocha + Chai**: Combinação popular para testes
- **Vitest**: Alternativa moderna e rápida ao Jest
- **Sinon**: Biblioteca para criação de mocks, stubs e spies

## Conclusão

O teste de unidade é fundamental para garantir a qualidade do software desde o início do desenvolvimento. Ao testar componentes individuais de forma isolada, você constrói uma base sólida e confiável para sua aplicação, reduzindo bugs, facilitando manutenção e melhorando o design do código.

Lembre-se: **código sem testes é código legado desde o momento em que é escrito**. Invista tempo em aprender e praticar testes unitários, pois isso se pagará muitas vezes ao longo do ciclo de vida do software.

---

## Referências

1. **PRESSMAN, Roger S.; MAXIM, Bruce R.** *Engenharia de Software: Uma Abordagem Profissional*. 8ª edição. McGraw-Hill, 2016.

2. **BLACK, Rex.** *Advanced Software Testing - Vol. 1: Guide to the ISTQB Advanced Certification as an Advanced Test Analyst*. Rocky Nook, 2008.

3. **BARTIE, Alexandre.** *Garantia de Qualidade de Software*. Campus, 2002.

4. **BECK, Kent.** *TDD - Desenvolvimento Guiado por Testes*. Bookman, 2010.

5. **MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom.** *The Art of Software Testing*. 3rd edition. Wiley, 2011.

6. **BSTQB - Brazilian Software Testing Qualifications Board.** *Syllabus CTFL 4.0*. Disponível em: https://bstqb.online/files/syllabus_ctfl_4.0br.pdf

7. **FOWLER, Martin.** *Refactoring: Improving the Design of Existing Code*. 2nd edition. Addison-Wesley, 2018.

8. **THOMAS, Dave; HUNT, Andrew.** *The Pragmatic Programmer: Your Journey to Mastery*. 20th Anniversary Edition. Addison-Wesley, 2019.

