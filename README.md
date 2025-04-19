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
