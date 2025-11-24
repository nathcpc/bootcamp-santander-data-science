# Conhecendo a Linguagem de Programação Python

## 🎯 O que aprendi:

Os fundamentos da linguagem Python: tipagem, estrutura de sintaxe e como Python funciona internamente.

---

## 🔍 O Que é Python?

**Python** é uma linguagem de programação:
- **Interpretada:** O código é executado linha por linha (não precisa compilar)
- **Dinamicamente tipada:** O tipo da variável é definido em tempo de execução
- **Fortemente tipada:** Não permite operações entre tipos incompatíveis sem conversão explícita
- **Multiplataforma:** Funciona em Windows, macOS, Linux
- **Multiparadigma:** Suporta Orientação a Objetos, Procedural, Funcional

---

## 📊 Tipagem em Python

### Tipagem Dinâmica vs Forte

```python
# DINÂMICA 
x = 5          # int
x = "texto"    # str (tipo pode mudar)
x = [1, 2, 3]  # list (sem problema)

# FORTE - Python NÃO permite misturar tipos
resultado = 5 + "10"  # ❌ TypeError: unsupported operand type(s)
resultado = 5 + 10    # ✅ 15 (int + int)
resultado = "5" + "10"  # ✅ "510" (str + str)
```

**O que isso significa:**
- Você não precisa declarar o tipo (como em Java: `int x = 5;`)
- Python descobre o tipo automaticamente
- Mas não permite misturar tipos sem conversão

---

## 🔤 Tipos de Dados Básicos

### 1. int - Números Inteiros

```python
# Inteiros (sem limite de tamanho)
idade = 30
saldo = -150
zero = 0
numero_grande = 999999999999999999999

# Operações
resultado = 10 + 5      # 15 (adição)
resultado = 10 - 5      # 5 (subtração)
resultado = 10 * 5      # 50 (multiplicação)
resultado = 10 / 5      # 2.0 (divisão com float)
resultado = 10 // 3     # 3 (divisão inteira)
resultado = 10 % 3      # 1 (módulo - resto)
resultado = 2 ** 10     # 1024 (potência)
```

### 2. float - Números com Casas Decimais

```python
# Ponto flutuante (decimal)
preco = 19.99
pi = 3.14159
temperatura = -5.5
notacao_cientifica = 1.5e-3  # 0.0015

# Operações
resultado = 10.5 + 2.3      # 12.8
resultado = 10 / 3          # 3.3333...
resultado = round(pi, 2)    # 3.14 (arredonda)
```

### 3. str - Texto (Strings)

```python
# Strings são sequências de caracteres
nome = "Maria"
frase = 'Python é incrível'
descricao = """Este é um texto
com múltiplas linhas
sem necessidade de gambiarra"""

# Operações
texto = "Python" + " " + "3.14"  # Concatenação: "Python 3.14"
repetido = "Ha" * 3              # "HaHaHa"
tamanho = len("Python")          # 6

# Acessar caracteres (índice começa em 0)
primeira = "Python"[0]    # "P"
ultima = "Python"[-1]     # "n"
intervalo = "Python"[0:3]  # "Pyt" (não inclui índice 3)
```

### 4. bool - Booleano (True/False)

```python
# Verdadeiro ou Falso (sempre com maiúscula)
ativo = True
bloqueado = False
resultado = 5 > 3      # True
resultado = 10 < 5     # False

# Em condições
if ativo:
    print("Ativo!")

# Operadores lógicos
resultado = True and False    # False
resultado = True or False     # True
resultado = not True          # False
```

### 5. NoneType - Valor Nulo

```python
# Representa "nenhum valor" ou "indefinido"
resultado = None
vencedor = None

# Usado em funções sem retorno
def funcao_sem_retorno():
    print("Fazendo algo...")
    # Sem return, retorna None implicitamente

valor = funcao_sem_retorno()
print(valor)  # None
```

### 6. complex - Números Complexos

```python
# Para matemática e engenharia avançada
numero = 2 + 3j  # Parte real + parte imaginária
resultado = numero.real      # 2.0
resultado = numero.imag      # 3.0
```

---

## 🔄 Conversão de Tipos

### Conversão Explícita

```python
# STRING para INT
idade_texto = "25"
idade = int(idade_texto)        # 25 (int)
print(type(idade))              # <class 'int'>

# STRING para FLOAT
preco_texto = "19.99"
preco = float(preco_texto)      # 19.99 (float)

# INT para STRING
numero = 42
texto = str(numero)             # "42" (str)

# INT para FLOAT
inteiro = 5
decimal = float(inteiro)        # 5.0 (float)

# STRING para BOOL
ativo = bool("texto")           # True (qualquer string não-vazia)
vazio = bool("")                # False (string vazia)

# BOOL para INT
verdade = True
valor = int(verdade)            # 1
falso = False
valor = int(falso)              # 0
```

### ⚠️ Erros Comuns

```python
# ❌ Erro: string contendo letra não pode virar int
numero = int("abc")  # ValueError: invalid literal for int()

# ❌ Erro: float inválido
valor = float("3.14.15")  # ValueError: could not convert string

# ✅ Solução: validar antes
def converter_seguro(texto):
    try:
        return int(texto)
    except ValueError:
        return None
```

---

## 📝 Variáveis e Atribuição

### Declaração e Atribuição

```python
# Python não precisa de declaração - só atribuição
nome = "Maria"       # Atribui e Python vê que é string
idade = 30           # int
ativo = True         # bool

# Atribuição múltipla
x, y, z = 1, 2, 3
a = b = c = 0        # Todos recebem o mesmo valor
```

### Nomenclatura Correta

```python
# ✅ CORRETO - variáveis (snake_case)
usuario_ativo = True
primeira_compra = False
saldo_atual = 100.50

# ✅ CORRETO - constantes (MAIÚSCULAS)
TAXA_JUROS = 0.05
LIMITE_SAQUE = 1000
VERSAO_PYTHON = "3.14"

# ❌ EVITAR
usuarioAtivo = True      # Mistura de casos
usuario-ativo = True     # Hífen (Python usa para subtração)
1usuario = True          # Começar com número
usuario ativo = True     # Espaço (inválido)
```

---

## 🔍 Examinando Tipos

### type() - Verificar tipo

```python
print(type(42))           # <class 'int'>
print(type(3.14))         # <class 'float'>
print(type("texto"))      # <class 'str'>
print(type(True))         # <class 'bool'>
print(type(None))         # <class 'NoneType'>
print(type([1, 2, 3]))    # <class 'list'>
```

### isinstance() - Verificar se é de um tipo

```python
idade = 25
print(isinstance(idade, int))         # True
print(isinstance(idade, (int, float))) # True (múltiplos tipos)
print(isinstance(idade, str))         # False
```

---


## 🔗 Recursos Recomendados

- [Documentação Python - Data Types](https://docs.python.org/pt-br/3/tutorial/introduction.html#numbers)
- [Type Hints (Python 3.5+)](https://docs.python.org/pt-br/3/library/typing.html)

---

[⬅️ Voltar ao Índice do Módulo](README.md)