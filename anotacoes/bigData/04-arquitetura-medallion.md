## Arquitetura Medallion 

A arquitetura Medallion é uma forma de organizar os dados em camadas dentro de um lakehouse.
O nome vem da ideia de “medalhas” (bronze, prata, ouro).

🥉 Camada Bronze
Onde os dados chegam crus, sem tratamento.
Tudo é armazenado aqui: planilhas, logs, JSON, CSV, etc.
É o “espelho” do que veio da fonte.

🥈 Camada Silver
Aqui os dados já estão limpos, tratados e padronizados.
Você resolve erros, remove duplicatas, ajusta formatos.
Fica pronto para análises mais sérias e combinações entre diferentes fontes.

🥇 Camada Gold
Dados já estão refinados e prontos para consumo.
Normalmente servem para relatórios de BI, dashboards ou modelos de Machine Learning.

#### Resumo simples:
A arquitetura Medallion é um passo a passo de qualidade dos dados → do cru (bronze), para tratado (silver), até pronto para análise (gold).

### Exemplo com ovo e cuzcuz:

- Bronze = ovos + flocão + queijo crus.
- Silver = ovos batidos + cuscuz hidratado + queijo cortado.
- Gold = omelete de cuscuz servida no prato.

## Exemplo Prático de Data Lakehouse (Banco Digital)

Imagina um banco digital que usa Lakehouse:
Transações financeiras (Postgres → ingestão).
Logs de acesso ao app (Kafka → streaming).
Relatórios de clientes em CSV (Data Factory → ingestão batch).

### Fluxo:

- Dados chegam no Lakehouse (Delta Lake no S3) em Bronze.
- São limpos e deduplicados, indo para a camada Silver.
- Agregações como “gastos por cliente/mês” são calculadas e salvas no Gold. Dashboards em Power BI mostram insights para os gestores Cientistas de dados usam os dados Gold para treinar modelos de detecção de fraude em tempo real.