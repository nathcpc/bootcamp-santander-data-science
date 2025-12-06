# Introdução a Bancos de Dados NoSQL para Data Science

## 🎯 O que eu aprendi

Bancos de dados NoSQL são sistemas não relacionais projetados para armazenar grandes volumes de dados variados, distribuídos e dinâmicos. Eles oferecem alta escalabilidade horizontal, flexibilidade no esquema e são ideais para cenários onde a consistência imediata não é crítica. São amplamente utilizados em Big Data, aplicações web, análises exploratórias, e sistemas com dados semi ou não estruturados.

---

## 🗃️ O que são Bancos NoSQL?

- **Não seguem o modelo relacional** (tabelas e relacionamentos rígidos)
- **Alta flexibilidade estrutural** — suportam dados mutáveis, variáveis e heterogêneos
- **Alta escalabilidade horizontal** para lidar com grandes volumes e múltiplos servidores
- **Uso comum quando consistência forte não é prioridade imediata**

---

## ⚖️ Diferenças SQL x NoSQL

| Feature            | SQL                                     | NoSQL                                |
|--------------------|-----------------------------------------|------------------------------------ |
| Modelo             | Estruturado, fixo (tabelas)              | Flexível (documentos, chave-valor)  |
| Escalabilidade     | Vertical (mais hardware)                   | Horizontal (vários servidores)       |
| Transações ACID    | 100% garantidas                           | Parcial ou ausente, depende do SGBD |
| Linguagem          | SQL padronizado                          | Linguagens específicas de cada SGBD |

---

## 🧩 Tipos Principais de Bancos NoSQL

| Tipo          | Características                        | Exemplos              | Uso em Data Science                                  |
|---------------|--------------------------------------|-----------------------|-----------------------------------------------------|
| **Key-Value** | Par chave-valor simples               | Redis, Riak, DynamoDB | Sessões, cache, contagem, dados rápidos             |
| **Document**  | Armazena documentos JSON/BSON         | MongoDB, CouchDB      | Catálogos, registros semiestruturados                |
| **Coluna**    | Armazena dados em colunas distribuídas| Cassandra, HBase      | Grandes volumes de logs, análises em larga escala  |
| **Grafo**     | Modela vértices e relações            | Neo4j, JanusGraph     | Redes sociais, recomendação, análise de conexões     |

---

## 🚀 MongoDB: Exemplo de Banco NoSQL Orientado a Documentos

- Armazena documentos flexíveis em BSON (Binary JSON)
- Não exige esquema rígido (schemaless)
- Suporta consultas complexas e rica modelagem

### Estrutura MongoDB

- **Banco de Dados** → contém várias **coleções**
- **Coleção** → agrupamento de documentos (não requer esquema uniforme)
- **Documento** → dados em pares chave-valor, cada um com um `_id` único

### Tipos de Dados em MongoDB

- Simples: string, number, boolean, date, null, ObjectId
- Compostos: array, documento embutido (embedded), referências, GeoJSON

### Modelagem

- **Denormalização** (dados relacionados embutidos para evitar join custoso)
- **Referências** (dados separados com relação entre coleções)

### Exemplo de documento usuário

{
"_id": ObjectId("507f1f77bcf86cd799439011"),
"nome": "Maria",
"idade": 28,
"enderecos": [
{
"rua": "Av. Brasil",
"numero": 123,
"cidade": "São Paulo",
"estado": "SP"
}
]
}

text

---

## ⚙️ Operações e Comandos NoSQL

### Redis (Key-Value in-memory store)

- Alta performance pela operação em memória
- Utilizado para cache, filas de mensagens, estatísticas em tempo real

Principais comandos:

- `SET chave valor` — adiciona chave-valor  
- `GET chave` — obtém valor da chave  
- `DEL chave` — deleta chave  
- `EXISTS chave` — verifica se chave existe  
- `INCR chave` / `DECR chave` — incrementa/decrementa valor numérico

---

## 💻 Integração com Data Science

- Muitas ferramentas Python suportam conexão com NoSQL (MongoDB, Redis)
- Utilizado em pipelines ETL para dados brutos e não estruturados
- Base para uso em ML e análises que exigem dados heterogêneos

---

## 🔗 Recursos Recomendados

- [MongoDB University](https://university.mongodb.com/)  
- [MongoDB com Python](https://pandas.pydata.org/pandas-docs/stable/user_guide/io.html#mongodb)  
- [Redis Documentation](https://redis.io/documentation)  
- [Neo4j Developer Guide](https://neo4j.com/developer/)  
- [Padrões para Modelagem em MongoDB](https://www.luiztools.com.br/post/padroes-para-modelagem-de-dados-documentos-em-mongodb)  

---

[⬅️ Voltar ao Índice do Módulo](README.md)