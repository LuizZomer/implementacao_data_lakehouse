# Implementação do Apache Iceberg com Spark

## Equipe 
- Luiz Felipe Silveira Zomer
- Willian Minatto
- Luiz Felipe Linhares

## Tecnologias usadas:
- UV (Gerenciador de pacotes python)
- Min.io (Data lake)
- Apache iceberg
- Apache spark
- Pyspark
- Jupiter notebook
- Docker

## Passos para rodar o projeto

## Passo 1 - Clonar projeto 

Para rodar o projeto roda este comando e siga as instruções a baixo:
```
git clone https://github.com/LuizZomer/implementacao_data_lakehouse.git
```

### Passo 2 - Rodar o docker compose

Para iniciar as aplicações necessarias para uso você terá que rodar este comando na raiz do projeto:
```
docker compose up
```
Este compose foi retirado diretamente da [documentação ofical](https://iceberg.apache.org/spark-quickstart/#docker-compose), apenas sendo modificado esta parte no serviço do spark-iceberg:

```
  ports:
        - 7077:7077 <-- adicionado esta exposição de portas
        - 8888:8888
        - 8080:8080
        - 10000:10000
        - 10001:10001
```

### Passo 3 - Entrar no jupiter notebook

Por meio da URL você irá acessar o jupiter notebook de forma interna no container com a url:
```
http://localhost:8888/tree?
```

### Passo 4 - Copiar csv para o notebook

Na raiz do projeto tem um arquivo csv, com a home do jupyter notebook aberta você só arrasta e solta o arquivo. 

### Passo 4 - Rodar o codigo

Já dentro do jupiter notebook você criará um novo notebook no botão da parte de cima da tela, apartir dele poderá rodar os codigos que estão na main.ipynb, já estão na ordem correta para funcionar e com comentários explicando seus funcionamento de forma detalhada.
