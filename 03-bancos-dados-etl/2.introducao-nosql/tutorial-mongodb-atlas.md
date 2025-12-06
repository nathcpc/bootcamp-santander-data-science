# Tutorial: Introdução ao MongoDB Atlas

## 🎯 O que vamos aprender

Este guia ensina como criar uma conta, configurar um cluster gratuito, conectar-se ao banco de dados e realizar operações básicas no MongoDB Atlas, a plataforma de banco de dados na nuvem do MongoDB.

---

## 1. Criar Conta e Cluster Gratuito

1. Acesse [mongodb.com/cloud/atlas/register](https://www.mongodb.com/cloud/atlas/register).
2. Crie sua conta ou faça login (Google/GitHub).
3. Na tela de boas-vindas, escolha **"M0 Sandbox" (Free Tier)**.
4. Selecione o provedor de nuvem (AWS, Google Cloud ou Azure) e a região mais próxima.
5. Dê um nome ao seu Cluster (ex: `MeuClusterDS`) e clique em **Create Cluster**.
   - *Nota: A criação pode levar de 3 a 5 minutos.*

---

## 2. Configurar Segurança (Usuário e Rede)

Antes de conectar, precisamos definir quem pode acessar.

1. No menu lateral **Security**, clique em **Database Access**.
   - Clique em **+ Add New Database User**.
   - Crie um usuário (ex: `admin`) e uma senha segura.
   - Em "Database User Privileges", selecione **Atlas Admin** ou **Read and write to any database**.
   - Clique em **Add User**.

2. No menu lateral **Security**, clique em **Network Access**.
   - Clique em **+ Add IP Address**.
   - Para fins de teste, clique em **Allow Access from Anywhere** (`0.0.0.0/0`).
   - *Nota: Em produção, adicione apenas seu IP específico por segurança.*
   - Clique em **Confirm**.

---

## 3. Carregar Dados de Exemplo (Opcional)

O Atlas oferece datasets prontos para testar.

1. No painel principal (**Database**), clique nos três pontos `...` do seu Cluster.
2. Selecione **Load Sample Dataset**.
3. Confirme e aguarde o carregamento (cerca de 350MB de dados).

---

## 4. Conectar ao Banco de Dados

Você pode conectar via aplicação, terminal (Shell) ou interface gráfica (Compass). Vamos usar o **MongoDB Compass** (interface visual recomendada).

1. No Atlas, clique em **Connect**.
2. Selecione **Compass**.
3. Se não tiver o Compass instalado, baixe e instale.
4. Copie a **Connection String** fornecida.
   - Ela se parece com: `mongodb+srv://admin:<password>@meucluster.mongodb.net/`
5. Abra o MongoDB Compass.
6. Cole a string na tela inicial.
7. **Importante:** Substitua `<password>` pela senha que você criou no passo 2.
8. Clique em **Connect**.

---

## 5. Operações Básicas no Compass

### Criar um Database e Coleção
1. No Compass, clique no botão **+** ao lado de "Databases".
2. **Database Name:** `loja`
3. **Collection Name:** `produtos`
4. Clique em **Create Database**.

### Inserir Documentos (Insert)
1. Clique na coleção `produtos`.
2. Clique em **Add Data** > **Insert Document**.
3. Cole o JSON abaixo:
```json
{
  "nome": "Notebook Gamer",
  "preco": 4500.00,
  "marca": "Dell",
  "tags": ["eletronicos", "computadores"],
  "estoque": 10
}
```
4. Clique em **Insert**.

### Consultar Dados (Find)
1. Na barra de filtro (Filter), digite: `{ "marca": "Dell" }`
2. Clique em **Find**. Apenas o notebook aparecerá.

---

## 6. Conectar com Python (PyMongo)

Para Data Science, geralmente usamos Python.

### Instalar Driver
```bash
pip install pymongo[srv]
```

### Script de Conexão
```python
from pymongo import MongoClient

# Substitua <password> pela sua senha
uri = "mongodb+srv://admin:<password>@meucluster.mongodb.net/?retryWrites=true&w=majority"

client = MongoClient(uri)

# Acessar banco e coleção
db = client['loja']
colecao = db['produtos']

# Inserir via Python
novo_produto = {
    "nome": "Mouse Sem Fio",
    "preco": 150.00,
    "marca": "Logitech"
}
colecao.insert_one(novo_produto)

# Buscar
produto = colecao.find_one({"marca": "Logitech"})
print(produto)
```

---

## 🔗 Recursos Úteis

- [Documentação Oficial MongoDB Atlas](https://www.mongodb.com/docs/atlas/)
- [Download MongoDB Compass](https://www.mongodb.com/try/download/compass)
- [Curso Gratuito MongoDB University](https://learn.mongodb.com/)

---

[⬅️ Voltar ao Índice do Módulo](README.md)