# Modelagem de Dados no Data Warehouse
É o processo de estruturar as tabelas e relacionamentos dentro de um Data Warehouse para facilitar a análise e melhorar o desempenho das consultas.

## Star Schema (Esquema em Estrela) ⭐

O que é: modelo simples com uma tabela fato no centro e tabelas dimensão ao redor.
Uso: quando queremos simplicidade e rápida visualização dos dados.
Vantagem: consultas mais rápidas, ideal para BI.
Desvantagem: pode haver repetição de informações.
Exemplo: tabela fato de vendas + dimensões de tempo, cliente, produto e loja.

## Snowflake Schema (Esquema em Floco de Neve) ❄️

O que é: modelo mais detalhado, com dimensões divididas em subdimensões.
Uso: quando precisamos de organização e reduzir redundância.
Vantagem: dados mais consistentes e organizados.
Desvantagem: consultas mais complexas e lentas.
Exemplo: dimensão de produto dividida em produto → categoria → departamento.

## Relação com Engenharia de Dados

O engenheiro de dados define o modelo de schema durante o processo de ETL (Extract, Transform, Load).
O modelo escolhido influencia como os dados serão consultados, a performance das análises e a estrutura do Data Warehouse.