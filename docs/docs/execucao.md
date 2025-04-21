# 🚀 Execução do Projeto

Após subir os containers, acesse os seguintes serviços:

---

## 🔗 Acessos

- **Jupyter Lab**: [http://localhost:8888](http://localhost:8888)  
  O token será exibido no terminal ao iniciar os serviços.

- **MinIO (Painel Web)**: [http://localhost:9000](http://localhost:9000)  
  - Usuário: `minioadmin`  
  - Senha: `minioadmin`

---

## 🧪 Como testar

1. Acesse o Jupyter Lab
2. Abra o notebook `notebooks/main.ipynb`
3. Execute as células para:

   - Criar tabelas com Apache Iceberg
   - Ingerir dados no MinIO
   - Processar com Spark
   - Persistir dados com versionamento no Lakehouse

---

!!! note "Dica"
    Você pode modificar os dados de entrada ou transformar os scripts conforme sua necessidade para simulações mais avançadas.
