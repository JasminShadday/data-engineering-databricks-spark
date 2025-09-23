# Tipos de Arquiteturas de armazenamento de dados 

## Data Warehouse (DW)
Imagine um estoque super organizado, como um mercado em que cada produto já está separado em prateleiras por tipo. No DW, os dados já vêm limpos, tratados e estruturados (em tabelas, colunas e linhas).
É ótimo para relatórios, BI e análises históricas. 📊
### Exemplo: 
você quer ver o faturamento mensal dos últimos 5 anos da empresa.

## Data Lake
Agora pense em um lago gigante, onde você pode jogar qualquer coisa: garrafas, troncos, pedras, etc.
O Data Lake armazena dados de qualquer tipo: estruturados (tabelas), semiestruturados (JSON, XML) e não estruturados (imagens, áudios, PDFs).
Ele não exige tratamento prévio, você guarda tudo “cru”. 🌊
### Exemplo:
gravar cliques de usuários no app, vídeos, planilhas e arquivos de log em um só lugar.

## Data Lakehouse
Como o nome sugere, é a mistura dos dois: Lake + Warehouse.
É como se fosse um lago com áreas organizadas como prateleiras.
Você pode armazenar dados brutos (como no Data Lake) e também organizar dados tratados para relatórios (como no DW).
O objetivo é ter o melhor dos dois mundos.
### Exemplo: 
guardar logs de usuários brutos e já ter uma camada pronta para relatórios de uso do sistema. 🏠

#### Resumo rápido:

- DW → Dados organizados para análise (limpos, estruturados).
- Data Lake → Dados crus de qualquer tipo (estruturados ou não).
- Lakehouse → Combina os dois: flexibilidade do lago + organização do warehouse9
