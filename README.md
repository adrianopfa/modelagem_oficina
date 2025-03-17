Sistema de Gerenciamento de Oficina Mecânica

Visão Geral

Este projeto define o esquema de um banco de dados para o gerenciamento de uma oficina mecânica. O sistema permite cadastrar clientes, seus veículos, ordens de serviço, serviços realizados e mecânicos envolvidos em cada OS.

Estrutura do Banco de Dados

1. Clientes

Tabela para armazenar informações dos clientes.

id_cliente (INT, PRIMARY KEY)

nome (VARCHAR 100, NOT NULL)

Relacionamento: Um cliente pode possuir vários veículos (1:N).

2. Veículos

Tabela para armazenar os veículos associados aos clientes.

id_veiculo (INT, PRIMARY KEY)

modelo (VARCHAR 100, NOT NULL)

placa (VARCHAR 10, UNIQUE, NOT NULL)

id_cliente (INT, FOREIGN KEY REFERENCING Clientes(id_cliente))

Relacionamento: Um veículo pode ter várias ordens de serviço (1:N).

3. Ordem de Serviço

Tabela que armazena os dados das ordens de serviço abertas para os veículos.

id_os (INT, PRIMARY KEY)

data_emissao (DATE, NOT NULL)

status (VARCHAR 50, NOT NULL)

id_veiculo (INT, FOREIGN KEY REFERENCING Veiculos(id_veiculo))

Relacionamento: Uma OS pode conter vários serviços e vários mecânicos (N:M).

4. Serviços

Tabela que armazena os serviços disponíveis para os veículos.

id_servico (INT, PRIMARY KEY)

descricao (VARCHAR 200, NOT NULL)

5. OS_Serviços

Tabela intermediária para mapear quais serviços foram realizados em cada OS.

id_os (INT, FOREIGN KEY REFERENCING OrdemServico(id_os))

id_servico (INT, FOREIGN KEY REFERENCING Serviços(id_servico))

Chave primária composta (id_os, id_servico)

6. Mecânicos

Tabela que armazena os dados dos mecânicos.

id_mecanico (INT, PRIMARY KEY)

nome (VARCHAR 100, NOT NULL)

7. OS_Mecanicos

Tabela intermediária para registrar quais mecânicos participaram de cada OS.

id_os (INT, FOREIGN KEY REFERENCING OrdemServico(id_os))

id_mecanico (INT, FOREIGN KEY REFERENCING Mecanicos(id_mecanico))

Chave primária composta (id_os, id_mecanico)

Relacionamentos do Banco de Dados

Clientes - Veículos (1:N) → Um cliente pode ter vários veículos.

Veículos - Ordem de Serviço (1:N) → Um veículo pode ter várias ordens de serviço.

Ordem de Serviço - Serviços (N:M) → Uma OS pode conter vários serviços e um serviço pode ser feito em várias OSs.

Ordem de Serviço - Mecânicos (N:M) → Uma OS pode ter vários mecânicos e um mecânico pode participar de várias OSs.

Como Usar

Crie as tabelas no banco de dados usando um SGDB compatível com SQL (MySQL, PostgreSQL, etc.).

Insira os dados dos clientes, veículos e serviços.

Registre as ordens de serviço e vincule-as aos mecânicos e serviços executados.

Melhorias Futuras

Implementar um sistema de cobrança e pagamentos.

Adicionar controle de estoque para as peças utilizadas nos serviços.

Criar relatórios para gestão da oficina.

Autor

Desenvolvido para gerenciamento de oficina mecânica 🚗🔧.

