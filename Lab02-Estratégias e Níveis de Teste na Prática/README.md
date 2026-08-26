# Diagramas e suas utilizações
Cenário: Plataforma de E-commerce e Marketplace de grande porte
## 1. Teste de Unidade (Unit Testing)
### 1.1. [Teste de unidade](./diagramas/unidade.puml)
Caso: Calcular o total do carrinho
- Demonstra um teste unitário do componente Carrinho para a lógica do cálculo do valor total de um carrinho
- "Essa pequena unidade de código funciona?"

## 2. Teste de Integração (Integration Testing)
### 2.1. [Integração Não Incremental (Big Bang)](./diagramas/big-bang.puml)
Caso: Finalizar um pedido
- Neste cenário, todos os componentes envolvidos no processo de compra (Carrinho, Pedido, Pagamento, Estoque e Entrega) são considerados disponíveis e integrados simultaneamente. O teste verifica o fluxo completo após a integração de todos os componentes.
- "O sistema funciona depois de integrar tudo de uma vez?"

### 2.2. [Integração Incremental Top-Down (Descendente) com uso de Stubs](./diagramas/top-down.puml) 
Caso: Finalizar um pedido
- Neste cenário, apenas o componente Pedido (topo da hierarquia) é considerado disponível e utiliza Stubs para testar seu funcionamento (PagamentoStub, EntregaStub e EstoqueStub).
- Interfaces são utilizadas para permitir que o componente Pedido aceite diferentes implementações dos outros componentes
- "O componente superior funciona com dependências simuladas?"

### 2.3. [Integração Incremental Bottom-Up (Ascendente) com uso de Drivers](./diagramas/bottom-up.puml) 
Caso: Finalizar um pedido
- Neste cenário, os componentes Estoque, Entrega e Pagamento são considerados disponíveis, enquanto o componente pedido não. É utilizado um driver para simular o comportamento do componente Pedido, assim permitindo que os outros componentes sejam testados mesmo que Pedido ainda não tenha sido implementado
- "Os componentes inferiores funcionam antes da integração com os superiores?"

### 2.4. [Teste de Fumaça (Smoke Testing)](./diagramas/smoke.puml) 
Caso: Finalizar um pedido após receber nova versão do sistema
- Neste cenário, após receber uma nova versão do sistema, é executado o processo de finalizar um pedido de forma a verificar se os componentes estão funcionando minimamente da maneira esperada. O teste representa o fluxo normal de finalizar um pedido
- "A nova versão está minimamente funcional?"

### 2.5. [Teste de Regressão](./diagramas/regressao.puml)
Caso: A equipe altera o processo de finalização do pedido para permitir o pagamento via PIX 
- Neste cenário, após uma mudança no componente de pagamento, uma bateria de testes é feita nos componentes relacionados à criação e finalização de pedidos para garantir que a nova funcionalidade não quebrou ou interferiu nas funcionalidades já existentes
- "Uma alteração que fiz quebrou algo que já funcionava?"
    
## 3. Teste de Validação (Validation Testing)
### 3.1. [Critérios de Aceitação (User Acceptance Testing)](./diagramas/aceitacao.puml) 
Caso: Critérios de aceitação da finalização de uma compra
- Neste cenário, o objetivo é conferir que o fluxo atual do sistema para esse processo está de acordo com os critérios de aceitação que o cliente definiu previamente.
- "O sistema atende aos critérios definidos pelo cliente?"

### 3.2. [Teste Alfa (Alpha Testing)](./diagramas/alpha.puml)
Caso: Avaliação interna da nova versão do e-commerce antes do lançamento
- Neste cenário, uma versão Alpha do e-commerce é disponibilizada para um grupo controlado de usuários internos da empresa. Os usuários realizam operações comuns, como pesquisar produtos, adicionar itens ao carrinho e finalizar pedidos, enquanto registram problemas e feedbacks encontrados durante a utilização. A equipe utiliza essas informações para corrigir problemas e aprimorar o sistema antes de disponibilizá-lo ao público.
- "Usuários internos conseguem utilizar essa versão e encontrar problemas?"

### 3.3. [Teste Beta (Beta Testing)](./diagramas/beta.puml)
Caso: Avaliação do e-commerce com usuários externos 
- Neste cenário, após o sistema passar por várias etapadas de teste, ele é disponibilizado para um grupo limitado de usuários externos de forma que o sistema seja testado por diferentes tipos de perfis, assim avaliando a usabilidade do sistema em um ambiente próximo do real. Por meio de feedbacks e problemas identificados por esse grupo, a equipe pode analisar, corrigir e avaliar a preparação do sistema para o lançamento final.
- "Usuários reais conseguem utilizar o sistema em condições próximas das reais?"
    
## 4. Teste de Sistema (System Testing)
### 4.1. [Teste de Recuperação (Recovery Testing)](./diagramas/recovery.puml) 
Caso: Falha do sistema durante a finalização de um pedido
- Neste cenário, uma falha ocorre após a aprovação do pagamento e antes da conclusão do pedido. O teste verifica se o sistema consegue recuperar o estado da transação após a falha, mantendo a consistência dos dados e evitando operações duplicadas, como cobranças ou atualizações de estoque indevidas. Após a recuperação, o processamento deve ser retomado ou a transação deve ser revertida de maneira segura.
- "O sistema consegue se recuperar de uma falha?"

### 4.2. [Teste de Segurança (Security Testing)](./diagramas/security.puml) 
Caso: Usuário tenta acessar ou modificar recursos
- Neste cenário, um usuário autenticado tenta acessar os dados de um pedido. O teste verifica se os mecanismos de autenticação e autorização impedem o acesso indevido, caso o pedido não pertença aquele usuário, e garantem que o usuário consiga acessar somente os recursos para os quais possui permissão.
- "O sistema está protegido contra acessos/ações não autorizados?"

### 4.3. [Teste de Estresse (Stress Testing)](./diagramas/stress.puml) 
Caso: Pico extremo de acessos ao sistema
- Neste cenário, o sistema é submetido progressivamente a uma quantidade de usuários simultâneos superior à carga esperada para identificar seu limite de operação e seu comportamento sob sobrecarga. A carga é aumentada gradualmente até que ocorra degradação significativa ou saturação do sistema. Também é verificado se o sistema consegue se recuperar após a redução da carga.
- "O que acontece quando ultrapassamos a capacidade esperada?"

### 4.4. [Teste de Desempenho (Performance Testing)](./diagramas/performance.puml)
Caso: Avaliação do desempenho durante um pico 
- Neste cenário, o e-commerce é submetido a uma carga equivalente à demanda esperada em um período de alta utilização. São simulados usuários realizando operações de compra enquanto métricas como tempo de resposta, taxa de erros e quantidade de requisições processadas são coletadas. Os resultados são comparados aos requisitos de desempenho definidos para o sistema, permitindo identificar possíveis gargalos e verificar se o sistema atende aos níveis de desempenho esperados.
- "O sistema apresenta desempenho adequado sob condições esperadas?"