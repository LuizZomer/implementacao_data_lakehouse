# Implementação do Apache Iceberg com Spark

## Equipe 
- Luiz Felipe Silveira Zomer
- Willian Minatto
- Luiz Felipe Linhares

## Tecnologias usadas:
- UV (Gerenciador de pacotes python)
- Min.io
- Apache iceberg
- Apache spark
- Pyspark
- Jupiter notebook
- Docker

## Passos para rodar o projeto

### Passo 1 - Rodar o docker compose

Para iniciar as aplicações necessarias para uso você terá que rodar este comando na raiz do projeto:
```
docker compose up
```
Este compose foi retirado diretamente da [documentação ofical]([https://iceberg.apache.org/)](https://iceberg.apache.org/spark-quickstart/#docker-compose), apenas sendo modificado esta parte no serviço do spark-iceberg:

```
  ports:
        - 7077:7077 <-- adicionado esta exposição de portas
        - 8888:8888
        - 8080:8080
        - 10000:10000
        - 10001:10001
```

### Passo 2 - Entrar no jupiter notebook

Por meio da URL você irá acessar o jupiter notebook de forma interna no container com a url:
```
http://localhost:8888/tree?
```

### Passo 3 - Rodar o codigo

Já dentro do jupiter notebook você criará um novo notebook no botão da parte de cima da tela, apartir dele poderá copiar esta conexão do pyspark:
```py
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("Iceberg") \
    .master("spark://spark-iceberg:7077") \
    .config("spark.sql.catalog.iceberg", "org.apache.iceberg.spark.SparkCatalog") \
    .config("spark.sql.catalog.iceberg.type", "hadoop") \
    .config("spark.sql.catalog.iceberg.warehouse", "s3a://warehouse/") \
    .config("spark.sql.extensions", "org.apache.iceberg.spark.extensions.IcebergSparkSessionExtensions") \
    .config("spark.hadoop.fs.s3a.access.key", "admin") \
    .config("spark.hadoop.fs.s3a.secret.key", "password") \
    .config("spark.hadoop.fs.s3a.endpoint", "http://localhost:9001") \
    .config("spark.hadoop.fs.s3a.path.style.access", "true") \
    .config("spark.hadoop.fs.s3a.impl", "org.apache.hadoop.fs.s3a.S3AFileSystem") \
    .getOrCreate()

print("PySpark started")
```
