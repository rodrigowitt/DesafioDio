Desafio de Modelagem de Banco de Dados - E-commerce

Descrição do Projeto

Este projeto tem como objetivo a criação de um esquema conceitual para um sistema de e-commerce, abordando aspectos fundamentais como clientes, pagamentos e entrega. O modelo foi refinado para garantir uma estrutura bem definida e organizada.

Estrutura do Modelo

Cliente (PJ e PF)

Um cliente pode ser uma pessoa física (PF) ou uma pessoa jurídica (PJ). Para garantir essa distinção, a modelagem prevê que uma conta não possa ter os dois tipos de informação simultaneamente. Dessa forma, a entidade Cliente foi projetada para conter os seguintes atributos:

id_cliente (PK)

tipo (ENUM: 'PJ' ou 'PF')

nome (se PF) ou razao_social (se PJ)

cpf (se PF) ou cnpj (se PJ)

email

telefone

Pagamento

Cada cliente pode cadastrar mais de uma forma de pagamento para facilitar a finalização dos pedidos. As formas de pagamento estão relacionadas à entidade Cliente e podem incluir cartão de crédito, boleto, PIX, entre outras.

id_pagamento (PK)

id_cliente (FK)

tipo_pagamento (ENUM: 'Cartão', 'Boleto', 'PIX', etc.)

detalhes_pagamento (dados específicos do meio escolhido, como número do cartão parcialmente mascarado)

Pedido

Os pedidos realizados pelos clientes estão vinculados a uma forma de pagamento e contêm informações essenciais para o processamento da compra.

id_pedido (PK)

id_cliente (FK)

id_pagamento (FK)

data_pedido

valor_total

status_pedido (ENUM: 'Em processamento', 'Enviado', 'Entregue', 'Cancelado')

Entrega

Para o controle das entregas, o modelo inclui informações sobre o status e o código de rastreio do pedido. Isso permite um acompanhamento mais preciso pelo cliente e pela equipe responsável.

id_entrega (PK)

id_pedido (FK)

status (ENUM: 'Aguardando envio', 'Em transporte', 'Entregue')

codigo_rastreio

data_envio

data_prevista_entrega

Considerações Finais

O esquema foi desenvolvido para garantir a integridade dos dados e melhorar a eficiência do gerenciamento de informações no e-commerce. Com essa estrutura, buscamos assegurar um sistema flexível, escalável e bem organizado.

