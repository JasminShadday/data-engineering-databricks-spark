# O que é o Apache Spark?

O Apache Spark é uma ferramenta de processamento de dados em larga escala.
Ele serve para analisar e transformar grandes volumes de dados de forma rápida, paralela e distribuída — ou seja, dividindo o trabalho entre vários computadores (ou núcleos de CPU).

Pensa no Spark como um “motor” que ajuda a processar dados gigantescos que não caberiam ou demorariam muito para rodar em um computador só.

Ele é muito usado em engenharia de dados, ciência de dados e machine learning, principalmente em ambientes como Data Lake e Big Data.

## Arquitetura de uma aplicação Spark

![Arquitetura de uma aplicação Spark](../recursos/arquitetura-spark.png)

- Driver Program
É o “cérebro” da aplicação.
É quem envia o código Spark (escrito em Python, Scala, etc.) para ser executado.
Ele cria o SparkContext, que é a conexão com o cluster.

- Cluster Manager
É quem gerencia os recursos do cluster (memória, CPUs, etc.).
Pode ser: Standalone (próprio do Spark), YARN (usado no Hadoop), Kubernetes, entre outros.

- Executors
São os “trabalhadores” que realmente executam as tarefas.
Cada executor roda em uma máquina (ou nó) e processa parte dos dados.

🧩 Em resumo:
O Driver envia o plano.
O Cluster Manager distribui o trabalho.
Os Executors fazem o processamento em paralelo.

## Principais componentes do Apache Spark

- Spark Core
O coração do Spark 
Faz o gerenciamento de tarefas, memória, leitura e gravação de dados, etc.
Trabalha com estruturas chamadas RDD (Resilient Distributed Datasets).

- Spark SQL
Permite usar SQL para consultar dados.
Usa DataFrames e Datasets, mais otimizados que RDDs.

- Spark Streaming
Permite processar dados em tempo real, como logs, sensores ou dados do Kafka.

- MLlib
Biblioteca de Machine Learning do Spark (classificação, regressão, clustering, etc.).

- GraphX
Serve para analisar grafos, tipo redes sociais ou conexões entre entidades.

## Benefícios do Apache Spark

- Velocidade: Até 100x mais rápido que o Hadoop MapReduce em memória. Usa processamento em memória (RAM) em vez de ler e escrever no disco o tempo todo.

- Escalabilidade: Funciona em um cluster com milhares de máquinas.

- Versatilidade: Suporta batch, streaming, SQL, machine learning e grafos, tudo na mesma ferramenta.

- Compatibilidade: Integra com vários sistemas: Hadoop, Hive, Cassandra, S3, Kafka, etc.

- Multilinguagem: Pode ser usado com Python (PySpark), Scala, Java, R e SQL.