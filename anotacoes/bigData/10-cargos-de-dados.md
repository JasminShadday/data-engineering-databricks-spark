## Tipos de cargas
São os métodos de ingestão, ou seja, como os dados “chegam”.
Pense como o “quando e quanto de dado entra”.

#### Incremental 
Carrega apenas os dados novos ou alterados desde a última carga.
Muito mais eficiente, pois evita duplicação e economiza recursos.
Pode ser feita de duas formas:
Append (inserção apenas): adiciona só os novos registros.
CDC (Change Data Capture): carrega os registros novos, alterados e marca os excluídos.
Exemplo: carregar somente os clientes cadastrados ou atualizados no último dia.

#### Full
Carrega todo o conjunto de dados de uma fonte para o destino.
Normalmente usado na primeira vez que um Data Lake ou Data Warehouse recebe os dados.
Desvantagem: pode ser lento e custoso se os dados forem muito grandes.
Exemplo: todo dia copiar toda a tabela de clientes para dentro do Data Lake, mesmo que só alguns tenham mudado.

#### Carga em Lote (Batch Load)
Os dados são acumulados e carregados em intervalos de tempo (ex.: 1x ao dia, de hora em hora).
Bom quando não é necessário ter os dados em tempo real.
Exemplo: todo dia às 2h da manhã carregar os dados de vendas do dia anterior.

#### Carga Contínua / Streaming (Real Time Load)
Os dados são carregados à medida que acontecem, em tempo real ou quase tempo real.
Ideal para sistemas que precisam de atualização imediata (fraudes, IoT, monitoramento).
Exemplo: transações de cartão de crédito entrando no Data Lake em segundos após a compra.

### Resumo
Full Load → carrega tudo de novo.
Incremental → só o que mudou.
Batch → em intervalos definidos (lotes).
Streaming → em tempo real.

## Formas de escrita (estratégias de como salvar os dados no destino)

São os jeitos de gravar/armazenar quando a carga chega ao Data Lake/DW:

Overwrite → apaga tudo e grava de novo.
Append → só adiciona no final (não mexe nos existentes).
Upsert (Merge) → insere novos + atualiza existentes.
Delete (menos comum sozinho, mas usado em CDC) → remove registros no destino quando foram excluídos na origem.

👉 Essas são as formas de escrita. Pense como o “o que eu faço com os dados quando eles entram”.

## Como eles “conversam” - estratégia de ingestão e tipo de escrita

A **estratégia de ingestão** e o **tipo de escrita** precisam estar **alinhadas**.  
Porque dependendo da forma como os dados chegam, **você vai escolher a forma de escrita mais adequada**.

| Estratégia de ingestão  | Tipo de escrita ideal   | Explicação |
|-------------------------|-------------------------|-------------|
| **Full load**           | **Overwrite**           | Já que você traz tudo de novo, faz sentido apagar e reescrever. |
| **Incremental**         | **Append** ou **Upsert**| Você traz só novos dados, então adiciona (append) ou atualiza (upsert). |
| **Streaming**           | **Append**              | Os dados chegam em tempo real, então você só adiciona continuamente. |

Ou seja dependendo da **estratégia de ingestão**, você realmente pode (e deve) usar **métodos diferentes de escrita**.  
Eles **“conversam”** porque um depende do outro pra manter a consistência e a performance dos seus dados.

## Analogia simples:

Imagina que você tem uma planilha de clientes:

Tipo de carga = o jeito que os dados chegam até você:

Full → recebe a lista inteira de clientes todo dia.
Incremental → recebe só os que mudaram/novos desde ontem.
Batch → recebe todo dia às 2h da manhã.
Streaming → recebe cliente por cliente em tempo real.

Forma de escrita = como você vai atualizar sua planilha:

Overwrite → apaga a planilha e cola a lista nova.
Append → só cola os novos no final.
Upsert → cola os novos e atualiza quem já existe.
Delete → remove quem saiu da empresa, por exemplo.

- Tipos de carga = definem quando/quanto dado entra.
- Formas de escrita = definem o que fazer com os dados no destino.
- Eles se combinam conforme a necessidade.