# Vendinha Plena

Aplicacao de console em C#/.NET para controle de clientes, vendas e dividas penduradas de uma vendinha.

## Funcionalidades

- Cadastro, listagem, edicao e exclusao de clientes.
- Validacao de CPF diretamente no model `Cliente`, no formato `000.000.000-00`, e bloqueio de CPF duplicado.
- Idade calculada automaticamente pela data de nascimento.
- Listagem de clientes com busca por nome e ordenação por maior divida.
- Cadastro de vendas pagas na hora ou penduradas.
- Uma única divida aberta por cliente, somando várias vendas penduradas.
- Detalhe de clientes e vendas com atalho para a divida relacionada.
- Tela de dividas com detalhes, quitação e aplicação de juros quando houver atraso.
- Persistencia em SQL Lite local.

## Banco de dados

O projeto usa Entity Framework Core com SQL Lite. O arquivo `schema.sql` contém o script de criação do banco para consulta ou DBeaver.

No DBeaver, é possível criar uma conexão SQL Lite apontando para o arquivo `vendinha.db` gerado após a primeira execução.

## Regra de divida

Cada cliente pode ter várias vendas penduradas, mas apenas uma divida aberta. Quando uma nova venda é pendurada, o sistema soma o valor ao total da divida aberta do cliente. Ao quitar, a divida fica fechada e uma nova divida poderá ser criada em compras futuras.
