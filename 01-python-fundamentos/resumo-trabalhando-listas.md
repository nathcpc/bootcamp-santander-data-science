# Trabalhando com Listas em Python

## 🎯 O que eu aprendi

Como criar, manipular e realizar operações avançadas em listas, uma das estruturas de dados mais importantes para Data Science.

---

## 📋 O que é uma Lista?

Uma **lista** é uma sequência que pode armazenar **qualquer tipo de objeto** de forma ordenada.

**Características:**
- ✅ **Mutável:** Pode alterar, adicionar ou remover itens
- ✅ **Ordenada:** Os itens mantêm a ordem de inserção
- ✅ **Heterogênea:** Pode misturar tipos (int, str, bool, etc.)

```python
# Formas de criar listas
frutas = ["banana", "maçã", "goiaba"]
vazia = []
numeros = list(range(5))      # [0, 1, 2, 3, 4]
letras = list("Python")       # ['P', 'y', 't', 'h', 'o', 'n']

# Lista mista (muito comum em linhas de datasets)
carro = ["Ferrari", "F8", 2020, 2900.0, True]
```

---

## 🔍 Acessando Valores

### **Acesso Direto (Índice)**

A contagem começa em **0**.

```python
frutas = ["banana", "maçã", "goiaba"]

print(frutas[0])   # banana
print(frutas[2])   # goiaba
```

### **Índices Negativos**

Útil para pegar o último item sem saber o tamanho da lista.

```python
print(frutas[-1])  # goiaba (último)
print(frutas[-2])  # maçã (penúltimo)
```

---

## 🏗️ Listas Aninhadas (Matrizes)

Listas dentro de listas. Fundamental para entender tabelas e DataFrames.

```python
matriz = [
    [1, "a", 10],
    [2, "b", 20],
    [3, "c", 30]
]

# Acessar linha 0, coluna 1
print(matriz[0][1])  # "a"
```

---

## ✂️ Fatiamento (Slicing)

Extrair subconjuntos da lista.

**Sintaxe:** `lista[inicio:fim:passo]` (o fim é exclusivo)

```python
numeros = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(numeros[2:])      # [2, 3, ..., 9] (do 2 até o fim)
print(numeros[:5])      # [0, 1, 2, 3, 4] (do início até 4)
print(numeros[1:4])     # [1, 2, 3] (entre 1 e 3)
print(numeros[::2])     # [0, 2, 4, 6, 8] (pulando de 2 em 2)
print(numeros[::-1])    # [9, 8, ..., 0] (inverter lista)
```

---

## 🔄 Iterar Listas

### **Usando `for` (Mais Comum)**

```python
carros = ["gol", "celta", "palio"]

for carro in carros:
    print(carro)
```

### **Usando `enumerate`**

Quando você precisa do índice E do valor.

```python
for indice, carro in enumerate(carros):
    print(f"{indice}: {carro}")

# Saída:
# 0: gol
# 1: celta
# 2: palio
```

---

## ⚡ List Comprehension (Essencial para Data Science)

Uma forma concisa e poderosa de criar listas a partir de outras. Substitui loops `for` simples.

**Sintaxe:** `[expressao for elemento in iteravel]`

### **Exemplos Práticos:**

**1. Dobrar valores**
```python
numeros = [1, 2, 3, 4, 5]
dobrados = [num * 2 for num in numeros]
# [2, 4, 6, 8, 10]
```

**2. Filtrar (com `if`)**
```python
# Filtrar apenas pares
pares = [num for num in numeros if num % 2 == 0]
# [2, 4]

# Filtrar vendas altas
vendas = [150, 200, 75, 300, 50]
vendas_altas = [v for v in vendas if v > 100]
# [150, 200, 300]
```

**3. Converter Tipos (Limpeza de Dados)**
```python
dados_texto = ['10', '20', '30']
dados_numeros = [int(x) for x in dados_texto]
# [10, 20, 30]
```

**4. Manipular Strings**
```python
nomes = ['maria', 'joão']
maiusculos = [nome.upper() for nome in nomes]
# ['MARIA', 'JOÃO']
```

---

## 🛠️ Métodos Importantes da Classe `list`

| Método | O que faz | Exemplo |
|--------|-----------|---------|
| `.append(x)` | Adiciona `x` ao final | `lista.append("novo")` |
| `.clear()` | Limpa toda a lista | `lista.clear()` |
| `.copy()` | Retorna uma cópia superficial | `nova = lista.copy()` |
| `.count(x)` | Conta quantas vezes `x` aparece | `lista.count(10)` |
| `.extend(y)` | Junta lista `y` no final de `lista` | `lista.extend([1, 2])` |
| `.index(x)` | Retorna índice da 1ª ocorrência de `x` | `lista.index("banana")` |
| `.pop()` | Remove e retorna o último item (pilha) | `ultimo = lista.pop()` |
| `.pop(i)` | Remove e retorna item no índice `i` | `item = lista.pop(0)` |
| `.remove(x)` | Remove a primeira ocorrência do valor `x` | `lista.remove("maca")` |
| `.reverse()` | Inverte a ordem **in-place** (altera a lista) | `lista.reverse()` |
| `.sort()` | Ordena a lista **in-place** | `lista.sort()` |

---

## 📊 Ordenação Avançada

### **sort() vs sorted()**

- `.sort()`: Altera a própria lista (retorna `None`)
- `sorted()`: Retorna uma NOVA lista ordenada (função built-in)

### **Exemplos de Ordenação**

```python
linguagens = ["python", "c", "java", "go"]

# Ordem alfabética (crescente)
linguagens.sort()
# ['c', 'go', 'java', 'python']

# Ordem decrescente (reverse=True)
linguagens.sort(reverse=True)
# ['python', 'java', 'go', 'c']

# Ordenar por critério (key)
# Ex: ordenar pelo tamanho da palavra
linguagens.sort(key=lambda x: len(x))
# ['c', 'go', 'java', 'python'] (menor para maior)
```

---

## ⚠️ Cuidados Importantes

### **Cópia de Listas**

```python
lista_a = [1, 2, 3]
lista_b = lista_a        # ❌ Isso NÃO copia! Cria referência
lista_b[0] = 99
print(lista_a)           # [99, 2, 3] (lista_a mudou!)

# ✅ Forma correta de copiar
lista_c = lista_a.copy()
lista_d = lista_a[:]
```

---

## 🔗 Recursos Recomendados

- [Documentação Python - Listas](https://docs.python.org/pt-br/3/tutorial/datastructures.html#more-on-lists)
- [Python List Comprehension](https://docs.python.org/pt-br/3/tutorial/datastructures.html#list-comprehensions)

---

[⬅️ Voltar ao Índice do Módulo](README.md)