# Explorando Conjuntos em Python

## 🎯 O que eu aprendi

Como usar conjuntos (sets) para eliminar duplicatas e realizar operações matemáticas de união, interseção e diferença.

---

## 📋 O que é um Conjunto (Set)?

Um **conjunto (set)** é uma coleção **não ordenada** de elementos **únicos**.

**Características principais:**
- ✅ **Não permite duplicatas:** Se você adicionar o mesmo item duas vezes, ele será ignorado.
- ✅ **Não ordenado:** Os itens não têm posição fixa (não têm índice).
- ✅ **Matemático:** Suporta operações como união e interseção.

```python
# Criando conjuntos
numeros = {1, 2, 3, 4}
frutas = {"maçã", "uva", "maçã"}  # "maçã" repetida é ignorada
vazio = set()  # Atenção: {} cria um dicionário, não um set!

print(frutas)  # {'uva', 'maçã'}
```

### 🧹 Eliminando Duplicatas de Listas

O uso mais comum de sets no dia a dia é limpar listas com itens repetidos.

```python
lista_com_repeticao = [1, 2, 2, 3, 3, 3, 4]
lista_limpa = list(set(lista_com_repeticao))

print(lista_limpa)  # [1, 2, 3, 4]
```

---

## 🔍 Acessando Dados

Como sets **não são ordenados**, você **NÃO PODE** usar índices ou fatiamento.

```python
conjunto = {1, 2, 3}

# ❌ ISSO DÁ ERRO:
# print(conjunto[0])  # TypeError: 'set' object is not subscriptable

# ✅ COMO ACESSAR:
# 1. Iterar com for
for numero in conjunto:
    print(numero)

# 2. Transformar em lista (se precisar de índice)
lista = list(conjunto)
print(lista[0])
```

---

## 🔢 Operações Matemáticas de Conjuntos

Python implementa a teoria dos conjuntos de forma visual e intuitiva.

Vamos usar dois conjuntos de exemplo:
```python
conjunto_a = {1, 2, 3}
conjunto_b = {2, 3, 4}
```

### **1. União (union)**
Junta todos os elementos (sem repetir).

```python
#   ( A ) ∪ ( B )
resultado = conjunto_a.union(conjunto_b)
print(resultado)  # {1, 2, 3, 4}
```

### **2. Interseção (intersection)**
Apenas o que tem nos DOIS ao mesmo tempo.

```python
#   ( A ∩ B )
resultado = conjunto_a.intersection(conjunto_b)
print(resultado)  # {2, 3}
```

### **3. Diferença (difference)**
O que tem no A que NÃO tem no B.

```python
#   ( A - B )
resultado = conjunto_a.difference(conjunto_b)
print(resultado)  # {1}

resultado = conjunto_b.difference(conjunto_a)
print(resultado)  # {4}
```

### **4. Diferença Simétrica (symmetric_difference)**
Tudo o que NÃO está na interseção (o que é exclusivo de cada um).

```python
#   ( A Δ B )
resultado = conjunto_a.symmetric_difference(conjunto_b)
print(resultado)  # {1, 4}
```

---

## 🕵️ Verificações de Subconjuntos

### **issubset** (É subconjunto?)
Verifica se todos os elementos de A estão dentro de B.

```python
a = {1, 2}
b = {1, 2, 3, 4}

print(a.issubset(b))  # True (A está contido em B)
print(b.issubset(a))  # False
```

### **issuperset** (É superconjunto?)
Verifica se B contém todos os elementos de A.

```python
print(b.issuperset(a))  # True (B contém A totalmente)
```

### **isdisjoint** (É disjunto?)
Verifica se NÃO há interseção (se são totalmente diferentes).

```python
c = {5, 6, 7}
print(a.isdisjoint(c))  # True (não têm nenhum número em comum)
print(a.isdisjoint(b))  # False (têm 1 e 2 em comum)
```

---

## 🛠️ Métodos de Manipulação

| Método | O que faz | Exemplo |
|--------|-----------|---------|
| `.add(x)` | Adiciona elemento (se não existir) | `s.add(5)` |
| `.discard(x)` | Remove valor (ignora se não existir) | `s.discard(1)` |
| `.remove(x)` | Remove valor (dá ERRO se não existir) | `s.remove(1)` |
| `.pop()` | Remove e retorna um valor aleatório (o "primeiro") | `valor = s.pop()` |
| `.clear()` | Limpa todo o conjunto | `s.clear()` |
| `.copy()` | Cria uma cópia superficial | `novo = s.copy()` |
| `len()` | Retorna tamanho (sem duplicatas) | `len(s)` |
| `in` | Verifica se valor existe | `1 in s` |

### Diferença entre remove e discard

```python
s = {1, 2, 3}

s.discard(4)  # Não faz nada (seguro)
# s.remove(4) # KeyError: 4 (dá erro e para o programa)
```

---

## 🔄 Iteração

Podemos usar `for` e `enumerate` normalmente.

```python
carros = {"gol", "celta", "palio"}

for indice, carro in enumerate(carros):
    print(f"{indice}: {carro}")

# Nota: A ordem pode mudar a cada execução, pois sets não têm ordem fixa!
```

---

## 🔗 Recursos Recomendados

- [Documentação Python - Sets](https://docs.python.org/pt-br/3/tutorial/datastructures.html#sets)

---

[⬅️ Voltar ao Índice do Módulo](README.md)