# Apache Iceberg com PySpark

## O que é o Apache Iceberg?

Apache Iceberg é uma tabela de dados open source voltada para ambientes de big data. Ele permite que você trabalhe com grandes volumes de dados de forma escalável, segura e confiável, suportando operações como `UPDATE`, `DELETE` e `MERGE`, que normalmente não são suportadas nativamente em tabelas baseadas em arquivos como Parquet.

---

## Integração com PySpark

Abaixo está a explicação das configurações necessárias para integrar o PySpark ao Iceberg:

```python
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
```

---

## Explicação das configurações

**appName:** Nome do job Spark.

**master:** Define o endpoint do cluster Spark.

**spark.sql.catalog.iceberg:** Cria um catálogo chamado iceberg usando SparkCatalog.

**type = hadoop:** Define o tipo de catálogo (pode ser hadoop, hive, entre outros).

**warehouse:** Local onde os dados serão fisicamente armazenados. Neste caso, em um bucket S3.

**extensions:** Extensões do Iceberg que habilitam comandos SQL como UPDATE, DELETE, etc.

---

## Comandos suportados

Com a integração do Iceberg, podemos executar comandos avançados diretamente via Spark SQL, como:

**INSERT INTO:** Inserção de dados

**UPDATE:** Atualização de registros

**DELETE:** Remoção de registros com base em condições

**MERGE INTO:** Mesclagem de dados (estilo upsert)

---

## Exemplos

```
spark.sql("""
    UPDATE football.premier_league
    SET homeScore = 3, awayScore = 1
    WHERE `Home Team` = 'Fulham'
      AND `Away Team` = 'Liverpool'
      AND Date = '2022-08-06'
""")
```

---

## Vantagens do Apache Iceberg

**Suporte a transações ACID**

**Operações incrementais (leitura de alterações)**

**Melhor gerenciamento de partições**

**Compatível com vários motores: Spark, Flink, Trino, Hive**

---

## Quando Usar?

Iceberg é ideal para projetos que lidam com grandes volumes de dados e precisam de:

**Governança de dados**

**Suporte a atualizações e remoções**

**Evolução de schema**

**Alta performance em consultas analíticas**
