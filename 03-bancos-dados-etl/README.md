```markdown
# Introdução a Banco de Dados Relacionais e ETL

Resumos, tutoriais e anotações completas sobre SQL, NoSQL, normalização de dados, consultas avançadas e processos de ETL com Python.

---

## 📚 Conteúdo do Módulo

### **Bancos de Dados Relacionais (SQL)**

- [Introdução a Bancos de Dados Relacionais (SQL)](resumo-introducao-sql.md)
  - Conceitos básicos, tipos de bancos, SGBD
  - Estrutura relacional, ACID, SQL organization (DQL/DML/DDL/DCL/DTL)
  - Modelagem (MER/DER), tabelas, colunas, registros
  - Operações CRUD (Create, Read, Update, Delete)
  - Chaves primárias e estrangeiras

- [Normalização de Dados e Consultas Avançadas (SQL)](resumo-normalizacao-consultas-avancadas.md)
  - Formas normais (1FN, 2FN, 3FN, BCNF)
  - Junções (INNER, LEFT, RIGHT, FULL JOIN)
  - Subconsultas
  - Funções agregadas (COUNT, SUM, AVG, MIN, MAX)
  - GROUP BY, HAVING, ORDER BY
  - Otimização com índices (CREATE INDEX, EXPLAIN)
  - ORM (Object-Relational Mapping)

### **Bancos de Dados NoSQL**

- [Introdução a Bancos de Dados NoSQL para Data Science](resumo-introducao-nosql.md)
  - Diferenças SQL vs NoSQL
  - Tipos de NoSQL (Key-Value, Document, Coluna, Grafo)
  - MongoDB: características, estrutura, tipos de dados
  - Modelagem (denormalização vs referências)
  - Redis: cache e operações em tempo real
  - Integração com Data Science

- [Tutorial: MongoDB Atlas](tutorial-mongodb-atlas.md)
  - Criar conta e cluster gratuito
  - Configurar segurança (usuários, network access)
  - Carregar dados de exemplo
  - Conexão com MongoDB Compass
  - Operações básicas (CRUD)
  - Conexão com Python (PyMongo)

### **ETL com Python**

- [Fundamentos de ETL (Extract, Transform, Load)](tutorial-etl-vscode.md)
  - O que é ETL e por que é importante
  - Etapas do processo ETL
  - Ferramentas para ETL (Pandas, Spark, Luigi, Airflow)
  - Introdução a Pandas (estruturas, funções essenciais)
  - Introdução a Scikit-learn (preprocessamento, modelos, avaliação)
  - Manipulação de dados com Pandas
  - Framework Luigi para orquestração de pipelines
  - Exemplo prático: Pipeline completo de e-commerce

- [Guia Prático: ETL com Python no VSCode](tutorial-etl-vscode.md)
  - Instalação e configuração do VSCode
  - Extensões essenciais para desenvolvimento
  - Criar e ativar virtual environment
  - Estrutura de projeto ETL
  - Desenvolver scripts (extract.py, transform.py, load.py)
  - Executar scripts e debugging
  - Usar Jupyter Notebooks no VSCode
  - Executar pipelines Luigi
  - Versionamento com Git
  - Dicas produtivas e atalhos

---


## 💡 Conceitos-Chave

### **SQL (Relacional)**
- **Dados estruturados** em tabelas com relacionamentos
- **ACID garantido:** Atomicidade, Consistência, Isolamento, Durabilidade
- **JOINs:** Combinam dados de múltiplas tabelas
- **Normalização:** Elimina redundância (1FN, 2FN, 3FN)
- **Índices:** Aceleram buscas em grandes tabelas
- **Escalabilidade:** Vertical (mais hardware)

### **NoSQL**
- **Dados não-estruturados** com schema flexível
- **Tipos principais:**
  - Document (MongoDB): Dados em JSON/BSON
  - Key-Value (Redis): Pares simples chave-valor
  - Coluna (Cassandra): Distribuído para Big Data
  - Grafo (Neo4j): Relacionamentos complexos
- **CAP Theorem:** Consistency, Availability, Partition tolerance (escolher 2 de 3)
- **Escalabilidade:** Horizontal (múltiplos servidores)

### **ETL**
- **Extract:** Coleta dados de múltiplas fontes
- **Transform:** Limpeza, validação, enriquecimento, normalização
- **Load:** Armazenamento em data warehouse/data lake
- **Pipeline:** Automação e orquestração de tarefas
- **Data Quality:** Validação em cada etapa
- **Repetibilidade:** Processos que rodam regularmente

---

## 💻 Configuração do Ambiente Local

```
# Clone o repositório
git clone <seu-repo>
cd banco-dados-etl

# Criar virtual environment
python -m venv venv
source venv/bin/activate  # Linux/macOS
# ou
.\venv\Scripts\Activate  # Windows

# Instalar dependências
pip install -r requirements.txt

# Iniciar projeto
python main.py
```

**requirements.txt:**
```
pandas==2.0.3
numpy==1.24.3
scikit-learn==1.3.0
luigi==3.4.0
requests==2.31.0
sqlalchemy==2.0.20
pymongo==4.4.1
psycopg2-binary==2.9.7
openpyxl==3.1.2
jupyter==1.0.0
```

---

## 🔗 Recursos Recomendados

### **SQL**
- [SQL Tutorial W3Schools](https://www.w3schools.com/sql/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Mode Analytics SQL Tutorial](https://mode.com/sql-tutorial/)

### **NoSQL**
- [MongoDB Documentation](https://docs.mongodb.com/)
- [MongoDB University (Cursos Gratuitos)](https://learn.mongodb.com/)
- [Redis Documentation](https://redis.io/documentation)
- [Neo4j Graph Academy](https://graphacademy.neo4j.com/)

### **ETL e Python**
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
- [Luigi Documentation](https://luigi.readthedocs.io/)
- [Apache Airflow Documentation](https://airflow.apache.org/docs/)

### **Ferramentas**
- [VSCode Documentation](https://code.visualstudio.com/docs/)
- [Git Documentation](https://git-scm.com/doc)
- [Python Packaging](https://packaging.python.org/)

---

[⬅️ Voltar ao Índice Principal](../README.md)