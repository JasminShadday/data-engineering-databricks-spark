# Tipo de processamento de dados

## Batch (lote)
Como funciona o processamento em lote:
Você junta um monte de dados já guardados (no SQL Server, Data Lake, arquivos, etc.).
Depois o sistema processa tudo de uma vez, geralmente em horários programados (tipo de madrugada, ou de hora em hora).
O resultado é salvo em outro lugar para ser usado em relatórios, análises ou sistemas.

- Exemplos do que pode acontecer nesse processamento:
Calcular o total de vendas do mês.
Treinar um modelo de machine learning com todos os dados do último ano.
Gerar um relatório diário de movimentações para o Bacen.

## Stream (tempo real) 
Processa os dados assim que chegam (fluxo contínuo). É muito rápido, mas pode ser menos preciso.
Imagine que os dados estão chegando sem parar, como água numa torneira aberta (transações de cartão, cliques em um site, sensores de temperatura, mensagens no WhatsApp etc.).
O sistema de streaming pega cada gota (ou pequenos grupos de gotas) na hora que cai e já faz algum cálculo em cima disso.

- Exemplos do que esse processamento pode fazer:
Somar em tempo real quantos produtos foram vendidos em um site nos últimos 5 minutos.
Detectar uma fraude de cartão assim que a compra suspeita acontece.
Atualizar um painel com a temperatura atualizada a cada segundo.

### Exemplo 
É como lavar roupa:
Você não coloca uma camiseta de cada vez na máquina (streaming).
Você junta uma pilha inteira (batch) e lava tudo de uma vez.
