## O que é um DataFrame
Um DataFrame é uma tabela de dados, como uma planilha do Excel ou uma tabela de banco de dados, ele tem linhas e colunas

# O que é um DataFrame no PySpark
Pensa que um DataFrame é como uma planilha do Excel, só que o PySpark consegue trabalhar com planilhas enormes, com milhões de linhas, que não caberiam na memória do seu computador.

- Agora, o que muda no PySpark?

No PySpark:
Essa “planilha” (o DataFrame) é dividida em pedacinhos.
Cada pedacinho é processado por um computador diferente (ou por vários núcleos do seu PC).
Depois, o Spark junta tudo de novo e te mostra o resultado.

O PySpark quebra o trabalho grande em partes pequenas e faz tudo ao mesmo tempo, em vez de linha por linha.

# Como é trabalhar com DataFrames no PySpark
Trabalhar com DataFrames no PySpark é muito parecido com o pandas, mas com a vantagem de lidar com dados gigantes.
Exemplo simples:

    from pyspark.sql import SparkSession

    # Cria a sessão do Spark
    spark = SparkSession.builder.appName("Exemplo").getOrCreate()

    # Cria um DataFrame
    dados = [("Ana", 25, "SP"), ("João", 30, "RJ")]
    colunas = ["nome", "idade", "cidade"]

    df = spark.createDataFrame(dados, colunas)

    # Mostra o conteúdo
    df.show()

# O que dá pra fazer com DataFrames no PySpark

Filtrar dados (df.filter(df.idade > 25))
Selecionar colunas (df.select("nome", "idade"))
Agrupar e resumir (df.groupBy("cidade").count())
Ler e salvar arquivos (csv, parquet, json, etc.)