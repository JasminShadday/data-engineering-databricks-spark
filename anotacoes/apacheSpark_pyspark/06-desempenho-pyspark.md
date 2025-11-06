# Desempenho pyspark
PySpark é a interface Python do Apache Spark, uma ferramenta poderosa para processar grandes volumes de dados distribuídos em vários computadores. Quando falamos de desempenho no PySpark, estamos nos referindo a como fazer com que nossos códigos rodem mais rápido e usem menos recursos do cluster.

### Conceitos Básicos
O paralelismo no PySpark funciona dividindo seus dados em pedaços menores chamados **partições** e processando esses pedaços simultaneamente em diferentes núcleos de processamento. 

Vamos entender os componentes principais:

- **Partição**: É um pedaço dos seus dados que pode ser processado independentemente. 
- **Task**: É a menor unidade de trabalho no Spark, que processa uma única partição. 
- **Stage**: Um conjunto de tasks que podem ser executadas em paralelo sem necessidade de comunicação entre elas. 
- **Job**: Um conjunto de stages que formam uma ação completa (como salvar um arquivo ou mostrar resultados).

## Como o Paralelismo Funciona na Prática

Quando você executa um código PySpark:
1. O **Driver** (programa principal) cria um plano de execução otimizado. 
2. Os dados são divididos em partições.
3. Cada partição é processada por uma task em um executor diferente.
4. Quanto mais partições bem distribuídas você tiver, mais paralelismo você consegue aproveitar. 

**Exemplo simples:**
```python
# Isso cria um DataFrame com 8 partições (se o cluster tiver 8 núcleos)
df = spark.read.csv("meus_dados.csv")
# Cada partição será processada por uma task diferente em paralelo
df.groupBy("coluna").count().show()
```

## Otimizações internas do PySpark
O Spark possui um mecanismo inteligente que otimiza automaticamente as consultas e o processamento de dados.

### Catalyst Optimizer
É o otimizador de consultas SQL do Spark.
Ele analisa e melhora o plano de execução para deixar o processamento mais eficiente.
```python
df.filter("idade > 18").select("nome")
```

### Tungsten Engine
Responsável por otimizar uso de memória e CPU, ele:
Usa código binário eficiente para processar dados em memória
Evita leituras e escritas desnecessárias no disco
Faz otimizações de cache e CPU (muito mais rápido do que o Python puro)

## Análise de desempenho

### Número de partições
Poucas partições → tarefas lentas e CPU ociosa
Muitas partições → sobrecarga de coordenação
Regra geral: 1 partição por núcleo de CPU é um bom começo
```python
df = df.repartition(8)
```

### Persistência (cache/memória)
Se você usa o mesmo DataFrame várias vezes, é melhor salvá-lo em memória:
```python
df.cache()
```
Isso evita reprocessar tudo do zero.

### Evite ações desnecessárias

Cada ação (como .collect() ou .show()) força o Spark a rodar tudo.
Use o mínimo necessário.

### Uso do Spark UI

O Spark UI (interface web) mostra:

Tempo de execução de cada etapa
Quantidade de partições
Uso de CPU e memória
Gargalos (bottlenecks)
Você pode acessá-la em:
http://localhost:4040

 É como o “painel de controle” do seu código Spark.