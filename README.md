# Projeto conceitual - MER - Vehiculo

Sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica
Clientes levam veículos à oficina mecânica para serem consertados ou para passarem por revisões  periódicas
Cada veículo é designado a uma equipe de mecânicos que identifica os serviços a serem executados e preenche uma OS com data de entrega.
A partir da OS, calcula-se o valor de cada serviço, consultando-se uma tabela de referência de mão-de-obra
O valor de cada peça também irá compor a OSO cliente autoriza a execução dos serviços
A mesma equipe avalia e executa os serviços
Os mecânicos possuem código, nome, endereço e especialidade
Cada OS possui: n°, data de emissão, um valor, status e uma data para conclusão dos trabalhos.

# Entidades e Relacionamentos

## Entidade Cliente
id_cliente (Chave Primária - PK)
nome
endereço
telefone

Relacionamento: Um cliente pode ter vários veículos (1:N)

## Entidade Veiculo
id_veiculo (Chave Primária - PK)
placa
modelo
ano
id_cliente (Chave estrangeiras da entidade Cliente)

Relacionamentos:
Pertence a um CLIENTE (N:1)
Gera várias ORDEM_SERVICO (1:N)

## Entidade Mecanico
id_mecanico (Chave Primária - PK)
nome
endereço
especialidade

Relacionamento: Um mecânico pode realizar vários SERVIÇOS (1:N)

## Entidade OrdenServico
id_ordenservico (Chave Primária - PK)
data_emissão
valor_total
status
data_conclusao
id_veiculo (Chave estrangeiras da entidade Veiculo)

Relacionamentos:
Gera vários SERVIÇOS (1:N)
Referencia um VEÍCULO (N:1)

## Servico
id_servico (Chave Primária - PK)
descrição
valor_mao_obra
id_mecanico (Chave estrangeiras da entidade Mecanico)
id_ordenservico  (Chave estrangeiras da entidade Orden_Servico)

Relacionamentos:
Pertence a uma ORDEM_SERVICO (N:1)
É realizado por um MECÂNICO (N:1)


### Este modelo garante que:
✔ As chaves primárias identifiquem unicamente cada registro
✔ As chaves estrangeiras mantenham a integridade referencial
