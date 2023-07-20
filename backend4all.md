# Backend4all

Nesse documento você ira encontrar informações relevantes do banco backend4all 
alem de quais tabelas estão cada informação.

**Topicos:**
- Localizador de Informações
- Tabelas
- Relações entre Tabelas
- Mapeamento

## Localizador de informações:

- Informações sobre endereços, como ruas, avenidas, bairros, cidades, países, etc., esses dados se encontram na tabela 🔓Address🔓.
- Dados bancários, como códigos e nomes de bancos, podem ser encontrados na tabela 🔓Bank🔓.
- Detalhes sobre contas bancárias, como status, números de contas, titulares e informações dos documentos, estão na tabela 🔓BankAccount🔓.
- Endereços de e-mails presentes na lista negra podem ser encontrados na tabela 🔓BlackList🔓.
- Informações sobre cartões de crédito, como data de expiração, últimos dígitos, titulares e atualização de saldo, estão na tabela 🔓Card🔓.
- Detalhes dos clientes, como números de telefone, e-mails, CPF, nome completo, data de aniversário, gênero, time que torce, empregador e cargo, podem ser encontrados na tabela 🔓Customer🔓.
- Solicitações de e-mails, incluindo tipos, endereços de e-mail, assuntos e datas de criação, estão na tabela 🔓EmailRequest🔓.
- Detalhes dos comerciantes, como nomes, informações da empresa, endereços, documentos e datas de criação, estão na tabela 🔓Merchant🔓.
- Transações de pagamento, como ID do mercado, ID do cliente, ID do cartão, valores e datas de pagamento e reembolso, podem ser encontradas na tabela 🔓Payment🔓.
- Informações sobre plataformas, como nomes, endereços e datas de criação, estão na tabela 🔓Platform🔓.
- Dados de sessões de clientes, como tipo de dispositivo, modelo e versão do sistema operacional do celular, além de datas de criação e atualização, estão na tabela 🔓Session🔓.


## Tabelas:

**Address:**
- Street: Ruas e avenidas
- Number: Número da casa
- Complement: Complemento da casa
- Neighborhood: Bairros
- City: Cidade
- Zip: CEP
- Province: Estado
- Country: País
- Customer ID: ID do cliente
- Merchant ID: ID de mercado
- Created At: Data que foi criado o dado
- Updated At: Última atualização do dado

**Bank:**
- ID: ID da tabela
- Code: Código do banco
- Name: Nome do banco
- Created At: Quando o dado foi criado
- Updated At: Última atualização do dado

**BankAccount:**
- ID: ID da tabela
- Status: Status da conta
- Customer ID: ID do cliente
- Bank ID: ID do banco
- Account: Conta do banco
- Account Digit: Dígito do banco
- Created At: Data que foi criado o dado
- Updated At: Última atualização do dado
- Document Type: Tipo do documento
- Document Number: Números do documento
- Name: Nome da pessoa que possui essa conta de banco

**BlackList:**
- ID: ID da tabela
- Email Address: Endereço de e-mail na lista negra
- Created At: Quando o dado foi criado
- Updated At: Última atualização do dado

**Card:**
- ID: ID da tabela
- Customer ID: ID do cliente
- Expiration Date: Mês e data de expiração
- Last Digits: Últimos dígitos do cartão
- Cardholder Name: Nome no cartão
- Created At: Quando o dado foi criado
- Updated At: Última atualização do dado
- Balance Update At: Última alteração no balanço
- Original Card ID: ID original de cada cartão

**Customer:**
- ID: ID da tabela
- Phone Number: Número de contato
- Email Address: Endereço de e-mail de contato
- CPF: CPF da pessoa
- Mother Name: Nome da mãe
- Full Name: Nome completo da pessoa
- First Name: Primeiro nome
- Middle Name: Nome do meio
- Last Name: Último nome
- Birthdate: Data de aniversário
- Gender: Se é masculino ou feminino
- Team: Time que torce
- Employer: Qual empresa trabalha
- Job Position: Qual cargo ocupa na empresa
- Default Card ID: ID que faz referência à tabela "Card"
- Default Address ID: ID que faz referência à tabela "Address"
- Created At: Quando o dado foi criado
- Updated At: Última atualização do dado
- Block Reason: Motivo do bloqueio
- Platform ID: Faz referência à tabela "Platform"

**EmailRequest:**
- ID: ID da tabela
- Type: Tipo do e-mail
- Email Address: Endereço de e-mail de contato
- Subject: Mensagem recebida
- Created At: Quando o dado foi criado
- Updated At: Última atualização do dado

**Merchant:**
- ID: ID da tabela
- Merchant Manager ID: ID do gerente do mercado
- Name: Nome da pessoa
- Company Name: Nome da companhia
- Email Address: Endereço de e-mail da empresa
- Street Address: Endereço
- Address Complement: Endereço complementar
- Street Number: Número da rua
- Neighborhood: Bairro
- Zip Code: Código postal
- City: Cidade
- State: Estado
- Document Type: Tipo do documento
- Document: Documento como CPF e CNPJ
- Created At: Quando o dado foi criado
- Next Payable Date: Próxima data de pagamento
- Updated At: Última atualização do dado

**Payment:**
- ID: ID da tabela
- Merchant ID: ID do mercado
- Customer ID: ID do cliente
- Card ID: ID do cartão
- Amount: Valor
- Paid At: Data de pagamento
- Returned At: Data de retorno
- Created At: Data que foi criado o dado
- Refund Amount: Valor dado para o reembolso
- Refunded Amount: Valor de reembolso sensibilizado
- Updated At: Data da última atualização do dado

**Platform:**
- ID: ID da tabela
- Name: Nome da plataforma
- Address: Endereços
- Created At: Quando o dado foi criado
- Updated At: Última atualização do dado

**Session:**
- ID: ID da tabela
- Customer ID: ID do cliente
- Device Type: Tipo do celular
- Device Model: Modelo do celular
- Device OS Version: Versão do OS do celular
- Created At: Quando o dado foi criado
- Updated At: Última atualização do dado



## Relações entre tabelas:

1. **Address e Customer:**
   - Você pode cruzar essas tabelas usando a coluna Customer ID para encontrar todos os endereços de um determinado cliente.

2. **Bank e BankAccount:**
   - Você pode cruzar essas tabelas usando a coluna Bank ID para encontrar todas as contas bancárias de um determinado banco.

3. **BlackList e EmailAddress:**
   - Você pode cruzar essas tabelas usando a coluna Email Address para encontrar todos os endereços de e-mail na lista negra.

4. **Card e Customer:**
   - Você pode cruzar essas tabelas usando a coluna Customer ID para encontrar todos os cartões de um determinado cliente.

5. **Customer e EmailRequest:**
   - Você pode cruzar essas tabelas usando a coluna Customer ID para encontrar todas as solicitações de e-mail de um determinado cliente.

6. **Merchant e Address:**
   - Você pode cruzar essas tabelas usando a coluna Merchant ID para encontrar todos os endereços de um determinado mercado.

7. **Payment e Card:**
   - Você pode cruzar essas tabelas usando a coluna Card ID para encontrar todos os pagamentos feitos com um determinado cartão.

8. **Payment e Customer:**
   - Você pode cruzar essas tabelas usando a coluna Customer ID para encontrar todos os pagamentos feitos por um determinado cliente.

9. **Platform e Customer:**
   - Você pode cruzar essas tabelas usando a coluna Customer ID para encontrar todas as plataformas usadas por um determinado cliente.

10. **Session e Customer:**
   - Você pode cruzar essas tabelas usando a coluna Customer ID para encontrar todas as sessões de um determinado cliente.

## Mapeamento:
 - O Diagrama do backend4all >  [backend4all]


   [backend4all]: <https://dbdiagram.io/d/6458e7a2dca9fb07c4b1fba9>

