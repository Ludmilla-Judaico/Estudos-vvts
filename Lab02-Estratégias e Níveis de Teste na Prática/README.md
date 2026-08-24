# Diagramas e suas utilizações
Cenário: Plataforma de E-commerce e Marketplace de grande porte
## 1. Teste de Unidade (Unit Testing)
### 1.1. [Teste de unidade](./diagramas/unidade.puml)
Caso: Calcular o total do carrinho
- Demonstra um teste unitário do componente Carrinho para a lógica do cálculo do valor total de um carrinho

## 2. Teste de Integração (Integration Testing)
### 2.1. [Integração Não Incremental (Big Bang)](./diagramas/big-bang.puml)
Caso: Finalizar um pedido
- Neste cenário, todos os componentes envolvidos no processo de compra (Carrinho, Pedido, Pagamento, Estoque e Entrega) são considerados disponíveis e integrados simultaneamente. O teste verifica o fluxo completo após a integração de todos os componentes.

### 2.2. [Integração Incremental Top-Down (Descendente) com uso de Stubs](./diagramas/top-down.puml) 
Caso: Finalizar um pedido
- Neste cenário, apenas o componente Pedido (topo da hierarquia) é considerado disponível e utiliza Stubs para testar seu funcionamento (PagamentoStub, EntregaStub e EstoqueStub).
- Interfaces são utilizadas para permitir que o componente Pedido aceite diferentes implementações dos outros componentes

### 2.3. [Integração Incremental Bottom-Up (Ascendente) com uso de Drivers](./diagramas/bottom-up.puml) 
Caso: Finalizar um pedido
- Neste cenário, os componentes Estoque, Entrega e Pagamento são considerados disponíveis, enquanto o componente pedido não. É utilizado um drive para simular o comportamento do componente Pedido, assim permitindo que os outros componentes sejam testados mesmo que Pedido ainda não tenha sido implementado

### 2.4. [Teste de Fumaça (Smoke Testing)](./diagramas/smoke.puml) 
Caso: Finalizar um pedido após receber nova versão do sistema
- Neste cenário, após receber uma nova versão do sistema, é executado o processo de finalizar um pedido de forma a verificar se os componentes continuam funciando minimamente da maneira esperada. O teste representa o fluxo normal de finalizar um pedido

### 2.5. [Teste de Regressão](./diagramas/regressao.puml)
Caso: A equipe altera o processo de finalização do pedido para permitir o pagamento via PIX 
- Neste cenário, após uma mudança no componente de pagamento, uma bateria de testes é feita nos componentes relacionados a criação e finalização de pedidos para garantir que a nova funcionalidade não quebrou ou interferiu nas funcionalidades já existentes
    
## 3. Teste de Validação (Validation Testing)
### 3.1. [Critérios de Aceitação (User Acceptance Testing)](./diagramas/aceitacao.puml) 
### 3.2. [Teste Alfa (Alpha Testing)](./diagramas/alpha.puml)
### 3.3. [Teste Beta (Beta Testing)](./diagramas/beta.puml) 
    
## 4. Teste de Sistema (System Testing)
### 4.1. [Teste de Recuperação (Recovery Testing)](./diagramas/recovery.puml) 
### 4.2. [Teste de Segurança (Security Testing)](./diagramas/security.puml) 
### 4.3. [Teste de Estresse (Stress Testing)](./diagramas/stress.puml) 
### 4.4. [Teste de Desempenho (Performance Testing)](./diagramas/performance.puml)
