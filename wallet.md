# Wallet

Nesse documento você ira encontrar informações relevantes do banco wallet 
alem de quais tabelas estão cada informação.

**Topicos:**
- Localizador de Informações
- Tabelas
- Relações entre Tabelas
- Mapeamento

## Localizador de informações:

- Caso você queira encontrar informações sobre os clientes, como ID do cliente, saldo, status da conta, documento (CPF ou CNPJ), entre outras informações relacionadas à conta, você pode encontrar esses dados na tabela ✅Account✅.
- Se você está procurando dados sobre reembolsos automáticos, como a data programada, o status do reembolso, o valor e informações sobre quem recebeu o reembolso (nome, documento), você pode encontrá-los na tabela ✅AutomaticRefund✅.
- As informações sobre os tipos de saldo da plataforma, como o nome da plataforma, qual plataforma está sendo usada e o CNPJ da plataforma, podem ser encontradas na tabela ✅BalanceTypes✅.
- Caso você queira obter detalhes sobre transações de saque para bancos, como ID da transação de débito, IDs de transferência bancária, data programada, informações da conta bancária (nome, número de CPF), bem como referências a outras transações, você pode encontrar esses dados na tabela ✅BankCashOut✅.
- Se você está buscando informações sobre o cancelamento de transações de saque para bancos, incluindo referências à transação original de saque e IDs de transação de crédito associados, você pode encontrar esses dados na tabela ✅CancellationBankCashOut✅.
- Para informações sobre o cancelamento de transações de saque no PIX, incluindo referências à transação original no PIX e a razão do cancelamento, você pode consultar a tabela ✅CancellationPixCashOut✅.
- Caso você queira obter detalhes sobre transações de pagamento recebidas, incluindo IDs de transação de crédito, IDs de pagamento, informações de TED Cashin (nome, conta bancária, tipo e número do documento) e informações de PIX (nome, conta, número de CPF do pagador e do recebedor), você pode encontrar esses dados na tabela ✅PaymentCashIn✅.
- Se você precisa de informações sobre transações de saque no PIX, como ID da conta, IDs de transação de débito, informações do pagador e do recebedor (nome, conta, tipo e número do documento), você pode encontrá-los na tabela ✅PixCashOut✅.
- Caso você queira encontrar informações sobre transações em geral, incluindo valor, descrição, tipo de transação (crédito ou débito) e referências à conta, você pode procurar esses dados na tabela ✅Transaction✅.


## Tabelas:

**Account:**
- ID: ID da tabela
- Customer ID: ID do cliente
- Merchant ID: ID do mercado
- Balance: Valor
- Created At: Quando o dado foi criado
- Updated At: Quando o dado foi atualizado
- Balance Type ID: Faz referência à tabela "balanceTypes"
- Status: Ativo ou inativo
- Document: Número de CPF ou CNPJ

**AutomaticRefund:**
- ID: ID da tabela
- Schedule Date: Data programada
- Status: Se foi pago ou cancelado
- Amount: Valores
- Drawee Name: Nome da pessoa ou empresa
- Drawee Document Type: Tipo do documento como CPF ou CNPJ
- Drawee Document Number: Número de CPF ou CNPJ
- Created At: Quando dado foi criado
- Updated At: Quando dado foi atualizado

**BalanceTypes:**
- ID: ID da tabela
- Name: Nome da plataforma
- Platform: Qual plataforma está sendo usada
- Created At: Quando o dado foi criado
- Updated At: Quando o dado foi atualizado
- CNPJ: CNPJ da plataforma

**BankCashOut:**
- ID: ID da tabela
- Debit Transaction ID: ID da transação de débito
- Fee Debit Transaction ID: Outro ID da transação de débito
- Fee Credit Transaction ID: ID da transação de crédito
- Schedule Date: Data programada
- Bank Transfer ID: ID de transferência do banco
- Created At: Quando o dado foi criado
- Updated At: Quando o dado foi atualizado
- Bank Account: Nome da conta do banco com número de CPF
- Ref Transaction ID: Faz referência à tabela "transaction"

**CancellationBankCashOut:**
- ID: ID da tabela
- Bank Cashout ID: Faz referência à tabela "bankCashOut"
- Credit Transaction ID: Faz referência à coluna "feeCreditTransactionId"
- Fee Debit Transaction ID: Faz referência à mesma coluna da tabela "BankCashOut"
- Created At: Quando o dado foi criado
- Updated At: Quando o dado foi atualizado

**CancellationPixCashOut:**
- ID: ID da tabela
- Pix Cashout ID: Faz referência à tabela "pixCashOut"
- Credit Transaction ID: ID da transação de crédito
- Cancellation Reason: Mensagem informando o motivo do cancelamento
- Created At: Quando o dado foi criado
- Updated At: Quando o dado foi atualizado

**PaymentCashIn:**
- ID: ID da tabela
- Credit Transaction ID: ID da transação de crédito que faz referência a outras tabelas
- Fee Credit Transaction ID: ID da transação de crédito que faz referência a outras tabelas
- Payment ID: ID de pagamento
- TED Cashin Data: Contém nome, conta bancária, tipo de documento como exemplo CPF e CNPJ e número do documento
- Pix Data: Nome de quem está pagando, tem também conta, contém número de CPF, e também contém nome de quem recebeu, conta de quem recebeu e contém número de CPF de quem recebeu
- Created At: Quando o dado foi criado
- Updated At: Quando o dado foi atualizado

**PixCashOut:**
- ID: ID da tabela
- Account ID: ID da conta que faz referência à tabela "account"
- Debit Transaction ID: ID da transação de débito que faz referência a diversas tabelas
- Payer: Contém nome, conta, tipo de documento e número do documento
- Receiver: Contém nome, conta, tipo de documento e número do documento
- Created At: Quando o dado foi criado
- Updated At: Quando o dado foi atualizado

**Transaction:**
- ID: ID da tabela
- Amount: Valor da transação
- Description: Descrição da transação
- Created At: Quando o dado foi criado
- Updated At: Quando o dado foi atualizado
- Account ID: ID da conta que faz referência à tabela "account"
- Type: Informa se foi transferência no crédito ou débito



## Relações entre tabelas:

1. **Account e Transaction:**
   - Você pode cruzar essas tabelas usando a coluna Account ID para encontrar todas as transações de uma determinada conta.

2. **AutomaticRefund e Transaction:**
   - Você pode cruzar essas tabelas usando a coluna Transaction ID para encontrar todas as transações de uma determinada devolução automática.

3. **BalanceTypes e Account:**
   - Você pode cruzar essas tabelas usando a coluna Balance Type ID para encontrar todas as contas de um determinado tipo de saldo.

4. **BankCashOut e Transaction:**
   - Você pode cruzar essas tabelas usando a coluna Debit Transaction ID para encontrar todas as transações de débito de um determinado saque bancário.

5. **CancellationBankCashOut e BankCashOut:**
   - Você pode cruzar essas tabelas usando a coluna Bank Cashout ID para encontrar todas as cancelações de um determinado saque bancário.

6. **CancellationPixCashOut e PixCashOut:**
   - Você pode cruzar essas tabelas usando a coluna Pix Cashout ID para encontrar todas as cancelações de um determinado saque Pix.

7. **PaymentCashIn e Transaction:**
   - Você pode cruzar essas tabelas usando a coluna Credit Transaction ID para encontrar todas as transações de crédito de um determinado pagamento de entrada.

8. **PixCashOut e Transaction:**
   - Você pode cruzar essas tabelas usando a coluna Debit Transaction ID para encontrar todas as transações de débito de um determinado saque Pix.

9. **Transaction e Account:**
   - Você pode cruzar essas tabelas usando a coluna Account ID para encontrar todas as transações de uma determinada conta.



## Mapeamento:
 - O Diagrama do wallet >  [wallet]


   [wallet]: <https://dbdiagram.io/d/64554f53dca9fb07c496bf48>

