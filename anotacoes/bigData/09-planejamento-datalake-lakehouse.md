# A importância de planejamento prévio do Datalake/Lakehouse 

O datalake deve ser concebido para resolver problemas do negócio e suas áreas, deve ser uma fonte confiável de dados que serão criados.
O planejmaneto ajuda a garantir informações verdadeiras e confiáveis

## Boas práticas para construir um datalake bem estrturado

#### Arquitetura Medallion (camadas de dados)
Landing Zone: é como uma “caixa de entrada” dos dados crus, que chegam direto das fontes (sem tratamento).
Bronze: dados brutos armazenados, apenas organizados.
Silver: dados limpos, padronizados e prontos para análises básicas.
Gold: dados refinados, já prontos para relatórios, dashboards e consumo pelo negócio.
- Pense como cozinhar: Bronze = ingredientes crus, Silver = ingredientes lavados e cortados, Gold = prato pronto.

#### Particionamento e Compactação
Particionamento: dividir os dados em pedaços menores (ex.: por data, região, ou categoria) para facilitar e acelerar consultas.
Compactação: juntar arquivos pequenos em menos arquivos maiores, reduzindo custo e tempo de leitura.
- É como organizar documentos em pastas (particionamento) e depois colocar vários papéis em um fichário (compactação).

#### Boas práticas com PySpark
Delta Lake: formato de armazenamento que traz controle de versões, transações seguras e melhor performance.
Cache: guardar dados na memória temporariamente para acelerar consultas repetidas.
- Pense no Delta Lake como “salvar com histórico e segurança”, e no Cache como “guardar na mesa o que você usa várias vezes, sem precisar ir ao arquivo toda hora”.

#### Estrutura de Dados (DataFrames no PySpark)
Trabalhar com DataFrames é mais organizado e otimizado do que usar listas ou RDDs puros.
DataFrames já vêm com esquema (colunas e tipos), permitindo processamento paralelo eficiente.
- É como usar uma tabela do Excel bem formatada em vez de uma lista bagunçada de anotações.

## Pipeline de dados
É como uma linha de produção que leva os dados da fonte até o consumo final.
Ela define os passos automáticos que os dados percorrem para sair do estado cru até virar informação útil.

### Etapas comuns de uma pipeline no Data Lake:

#### Ingestão (Landing Zone)
Captura os dados de várias fontes (bancos, APIs, arquivos CSV, logs, etc.)
Exemplo: salvar os arquivos brutos na camada Bronze.

#### Transformação (Bronze ➝ Silver)
Limpeza: remover duplicados, corrigir erros, padronizar formatos.
Enriquecimento: juntar informações de diferentes fontes.

#### Refinamento (Silver ➝ Gold)
Agregar, calcular métricas, deixar pronto para dashboards e relatórios.

#### Entrega/Consumo
Os dados da camada Gold são consumidos por ferramentas de BI (Power BI, Tableau), Machine Learning ou APIs.

#### Exemplo:
Fábrica de suco.
Ingestão (Bronze) → pegar as frutas direto da fazenda.
Transformação (Silver) → lavar, descascar, tirar as partes ruins.
Refinamento (Gold) → espremer, filtrar e engarrafar o suco.
Consumo → levar o suco pronto para o mercado (usuários finais)
