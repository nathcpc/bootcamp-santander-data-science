# Conhecendo Tuplas em Python

## 🎯 O que eu aprendi

Como criar e utilizar tuplas, entendendo suas diferenças fundamentais em relação às listas e quando utilizá-las.

---

## 📋 O que é uma Tupla?

Uma **tupla** é uma sequência ordenada de elementos, muito parecida com uma lista, mas com uma diferença fundamental: é **imutável**.

**Características:**
- ✅ **Imutável:** Uma vez criada, você não pode adicionar, remover ou alterar itens
- ✅ **Ordenada:** Mantém a ordem dos elementos
- ✅ **Heterogênea:** Pode conter tipos misturados
- ✅ **Segura:** Garante que os dados não serão modificados acidentalmente

```python
# Formas de criar tuplas
frutas = ("laranja", "pera", "uva",)  # Com parênteses (recomendado)
numeros = 1, 2, 3                     # Sem parênteses (funciona, mas cuidado)
vazia = ()                            # Tupla vazia
curso = tuple("Python")               # ('P', 'y', 't', 'h', 'o', 'n')
```

### ⚠️ A Vírgula "Mágica"

Se você criar uma tupla com **um único elemento**, a vírgula final é **obrigatória**. Sem ela, Python entende como uma string ou número entre parênteses.

```python
# ERRADO (vira string)
nome = ("Python")
print(type(nome))  # <class 'str'>

# CERTO (vira tupla)
nome = ("Python",)
print(type(nome))  # <class 'tuple'>
```

---

## 🔍 Acessando Valores

Funciona exatamente como nas listas.

### **Acesso Direto**

```python
frutas = ("laranja", "pera", "uva",)

print(frutas[0])   # laranja
print(frutas[-1])  # uva (último item)
```

### **Tuplas Aninhadas (Matrizes Imutáveis)**

```python
matriz = (
    (1, "a", 10),
    (2, "b", 20),
    (3, "c", 30),
)

print(matriz[0])     # (1, "a", 10)
print(matriz[0][1])  # "a"
```

---

## ✂️ Fatiamento (Slicing)

Extrair partes da tupla (gera uma nova tupla).

```python
tupla = ("P", "y", "t", "h", "o", "n")

print(tupla[2:])      # ('t', 'h', 'o', 'n')
print(tupla[:3])      # ('P', 'y', 't')
print(tupla[::2])     # ('P', 't', 'o')
print(tupla[::-1])    # ('n', 'o', 'h', 't', 'y', 'P')
```

---

## 🔄 Iterar Tuplas

Podemos percorrer tuplas com `for`, assim como listas.

```python
carros = ("gol", "celta", "palio",)

# Iteração simples
for carro in carros:
    print(carro)

# Com índice (enumerate)
for indice, carro in enumerate(carros):
    print(f"{indice}: {carro}")
```

---

## 🛠️ Métodos da Classe `tuple`

Como tuplas são imutáveis, elas **não têm** métodos de alteração como `append`, `remove`, `sort` ou `pop`.

Ela possui apenas métodos de consulta:

| Método | O que faz | Exemplo |
|--------|-----------|---------|
| `.count(x)` | Conta quantas vezes `x` aparece | `tupla.count("a")` |
| `.index(x)` | Retorna o índice da primeira ocorrência | `tupla.index("b")` |
| `len()` | Função built-in que retorna o tamanho | `len(tupla)` |

```python
cores = ("vermelho", "azul", "verde", "azul",)

print(cores.count("azul"))  # 2
print(cores.index("verde")) # 2
print(len(cores))           # 4
```

---

## 💡 Quando usar Tupla vs Lista?

| Característica | Lista `[]` | Tupla `()` |
|----------------|------------|------------|
| **Mutabilidade** | Mutável (pode mudar) | Imutável (fixa) |
| **Velocidade** | Mais lenta | Mais rápida (levemente) |
| **Memória** | Ocupa mais espaço | Ocupa menos espaço |
| **Uso Ideal** | Coleções dinâmicas de dados | Dados constantes ou estruturados |

**Exemplos de uso para Tuplas:**
- Coordenadas GPS: `(latitude, longitude)`
- Configurações de banco de dados: `(host, port)`
- Retorno múltiplo de funções
- Chaves de dicionários (listas não podem ser chaves!)

---

## 🔄 Conversão Lista ↔ Tupla

Útil quando você precisa ordenar ou modificar uma tupla temporariamente.

```python
# Tupla para Lista (para modificar)
tupla = (1, 2, 3)
lista = list(tupla)
lista.append(4)

# Lista para Tupla (para "congelar")
nova_tupla = tuple(lista)
print(nova_tupla)  # (1, 2, 3, 4)
```

---

## 🔗 Recursos Recomendados

- [Documentação Python - Tuplas](https://docs.python.org/pt-br/3/tutorial/datastructures.html#tuples-and-sequences)

---

[⬅️ Voltar ao Índice do Módulo](README.md)