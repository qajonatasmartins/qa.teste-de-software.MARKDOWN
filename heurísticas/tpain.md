# T-PAIN

**Criador:** Rafael Bandeira

## O que é a Heurística T-PAIN?

A técnica foca nos aspectos onde o sistema operacional exerce controle sobre aplicativos, como removê-los da CPU por conta de uma política de escalonamento. Ela pode ser usada em qualquer app nativo desenvolvido para API 23 (Android 6.0) ou superior, ou seja, aplicável em mais de 85% dos dispositivos Android do mundo.

Ela é composta por 5 características: Rotação, Permissões, Modo Avião, Interrupções e Conexões. Por envolver o sistema operacional, exercitá-la pode ser especialmente eficiente em aplicações que estão em estágios iniciais de desenvolvimento, revelando brechas em sua arquitetura. Abaixo, exemplifico formas de explorá-las:

### **Ro[T]ação (RoTation)**

Preencha informações na tela e rotacione o dispositivo:

As informações persistem?
Há sobreposição?
Inicie um fluxo e rotacione o dispositivo:

O que acontece ao rotacionar no meio de uma requisição a um serviço web?
A aplicação se perde ao ser rotacionada?

### **[P]ermissões (App Permissions)**

Como o aplicativo se comporta ao não ter todas as permissões?
O que acontece se ela perder as permissões durante o uso?
As permissões solicitadas fazem sentido?

### **Modo [A]vião (Airplane Mode)**

O quão dependente o aplicativo está de conexões com a rede?
Como a app se gerencia offline?

### **[I]nterrupções (Interruptions)**

**Terceiras (Third-party):**

Como o aplicativo se comporta quando o sistema escalona outras aplicações por cima da atual?
E quando recebe uma chamada?
E quando exibe uma notificação de prioridade 0?

**Sistêmicas (System-calls):**

O que acontece quando o Android mata processos em background?
Forçar parada com a aplicação em uso faz o quê com os processos?
É possível reutilizar a app após removê-la da memória?
O que acontece ao remover a cache com a aplicação em uso?

### **Co[N]exões (CoNnections)**

Como a app lida com um ping alto?
E quando é uma conexão 2G ou 3G?
Como o aplicativo reage a timeouts?

- [Referência - Explorando aplicações Android com a Heurística T-PAIN](https://medium.com/revista-tspi/t-pain-heur%C3%ADstica-de-testes-para-aplica%C3%A7%C3%B5es-android-11260f9f98c1)