# Boas práticas para estruturação em pyspark

## Use o Delta Lake
O Delta Lake ajuda a controlar as versões dos dados — como um “histórico de alterações”.
Isso permite voltar a versões anteriores, fazer atualizações e deleções facilmente e garantir integridade dos dados.

- Pense nele como um “controle de versão” dos seus arquivos de dados, tipo um Git dos dados.

## Adicione uma coluna de data de carregamento

Sempre que carregar novos dados, crie uma coluna com a data de inserção.
Isso ajuda a saber se o dado está atualizado e facilita auditorias.

from pyspark.sql.functions import current_date
df = df.withColumn("data_carregamento", current_date())

## Evite tabelas e partições muito grandes

Divida os dados em partições menores, mas sem exagerar.
Partições muito grandes demoram pra ler; muitas partições pequenas geram lentidão também.
O ideal é que cada partição tenha cerca de 1 GB de dados.

## Use particionamento para otimizar consultas

Particionar significa organizar seus dados em “pastas” por uma coluna, como por exemplo data ou estado.
Isso permite que o Spark leia só o que precisa em vez de tudo.

Exemplo:
    /dados/
        data=2025-10-01/
        data=2025-10-02/

## Cuidado ao escolher a coluna de particionamento

Evite colunas com muitos valores diferentes (como CPF, ID, etc.), pois isso cria milhares de partições minúsculas.
Prefira colunas com menos variação, como datas, regiões ou categorias.

## Utilize cache com moderação

Evite usar cache sem necessidade, pois ocupa memória.
Mas pode ser útil para consultas repetidas durante o mesmo processamento.

df.cache()

## Desative o shuffle quando possível

Shuffle é quando o Spark precisa reorganizar dados entre os nós (por exemplo, em groupBy ou join).
Isso consome muito recurso.
Tente evitar operações que forcem shuffle ou reduza o número de partições antes de fazer joins.

## Compacte arquivos pequenos

Ter muitos arquivos pequenos atrapalha o desempenho — cada arquivo cria uma tarefa no Spark.
Melhor juntar vários arquivos pequenos em menos arquivos maiores.
Reparticionar a tabela e usar a opção dataChange=false são boas práticas quando o dado não mudou, só foi reescrito.