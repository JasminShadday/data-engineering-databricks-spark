## Boas práticas para desenvolvimento com o PySpark

# Código organizado
Separe por partes: leitura dos dados, transformações e gravação do resultado.
Use nomes claros para variáveis e funções (ex: df_clientes, limpar_dados()).
Evite colocar tudo em um só arquivo — crie funções ou módulos para cada etapa.

def ler_dados(caminho):
    return spark.read.parquet(caminho)

def transformar_dados(df):
    return df.filter(df.idade > 18)

def salvar_dados(df, caminho):
    df.write.parquet(caminho)

# Tratamento de erros:

Use try e except para evitar que o programa pare de rodar por completo:

try:
    df = spark.read.csv("dados.csv", header=True)
except Exception as e:
    print(f"Erro ao ler o arquivo: {e}")

# Otimização de consultas

Filtre o mais cedo possível, pra evitar processar dados desnecessários.
Prefira formato Parquet (é mais rápido que CSV).
Evite repetir .show() ou .collect() desnecessariamente (eles fazem o Spark recalcular tudo). 
Se um dos DataFrames for pequeno, use broadcast join:

from pyspark.sql.functions import broadcast
df_final = df_grande.join(broadcast(df_pequeno), "id")

# Documentação

Use comentários simples e diretos explicando por que algo foi feito (não apenas o que faz).
No topo do script, descreva o objetivo e o que o código faz.

Exemplo:
    """
    Script: processamento_clientes.py
    Descrição: Lê dados de clientes, remove duplicados e salva em formato otimizado.
    """

    # Remove duplicados e filtra maiores de idade
    df_clientes = df_clientes.dropDuplicates().filter(df_clientes.idade > 18)