# Manipulando Strings em Python

## 🎯 O que eu aprendi

Métodos essenciais da classe string, interpolação de variáveis, fatiamento de strings e formatação profissional de texto para trabalho com dados em Data Science.

---

## 🔤 O que é uma String?

Uma **string** é uma sequência de caracteres (texto) envolvida em aspas.

```python
nome = "Python"
email = "usuario@example.com"
mensagem = "Olá, Mundo!"
```

Em Python, strings têm vários métodos integrados que facilitam sua manipulação.

---

## 📊 Métodos de Transformação

### **Maiúsculas, Minúsculas e Título**

```python
curso = "python"

print(curso.upper())       # PYTHON (tudo maiúsculo)
print(curso.lower())       # python (tudo minúsculo)
print(curso.title())       # Python (primeira letra maiúscula)
print(curso.capitalize())  # Python (só a primeira letra, resto minúsculo)
```

**Uso em Data Science:**
```python
# Normalizar dados de entrada
email_usuario = "USUARIO@EXAMPLE.COM"
email_normalizado = email_usuario.lower()
print(email_normalizado)  # usuario@example.com
```

---

## 🧹 Eliminando Espaços em Branco

### **strip() - Remove das Duas Extremidades**

```python
texto = "   Python   "

print("|" + texto.strip() + "|")   # |Python| (sem espaços)
print("|" + texto.lstrip() + "|")  # |Python   | (esquerda)
print("|" + texto.rstrip() + "|")  # |   Python| (direita)
```

**Uso em Data Science:**
```python
# Limpar dados importados
dados_sujo = "  produto A  \n"
dados_limpo = dados_sujo.strip()
print(dados_limpo)  # "produto A"
```

---

## 🔗 Junção e Centralização

### **center() - Centralizar**

```python
curso = "Python"

print(curso.center(15, "#"))     # ####Python####
print(curso.center(15, "-"))     # ----Python----
print(curso.center(15))          # "    Python    " (com espaços)
```

### **join() - Juntar Lista em String**

```python
# Juntar lista com separador
linguagens = ["Python", "JavaScript", "SQL"]
resultado = ", ".join(linguagens)
print(resultado)  # Python, JavaScript, SQL

# Juntar caracteres
palavra = "Python"
resultado = "-".join(palavra)
print(resultado)  # P-y-t-h-o-n
```

**Uso em Data Science:**
```python
# Formatar lista de colunas para exibição
colunas = ["idade", "salario", "departamento"]
print("Selecionando colunas: " + ", ".join(colunas))
# Selecionando colunas: idade, salario, departamento
```

---

## 🎯 Buscando em Strings

### **find() e index()**

```python
texto = "Python é incrível"

print(texto.find("é"))          # 7 (posição do caractere)
print(texto.find("xyz"))        # -1 (não encontrado)
print(texto.index("é"))         # 7 (igual a find)

# index() gera erro se não encontrar
# print(texto.index("xyz"))     # ValueError!
```

### **count() - Contar Ocorrências**

```python
texto = "banana"
print(texto.count("a"))         # 3
print(texto.count("an"))        # 2
```

---

## 🔄 Substituição

### **replace()**

```python
texto = "Python é fácil. Python é poderoso."

# Substituir todos
novo = texto.replace("Python", "JavaScript")
print(novo)  # JavaScript é fácil. JavaScript é poderoso.

# Substituir apenas N primeiros
novo = texto.replace("Python", "JavaScript", 1)
print(novo)  # JavaScript é fácil. Python é poderoso.
```

**Uso em Data Science:**
```python
# Limpar dados
dado = "R$ 1.234,50"
valor_limpo = dado.replace("R$", "").replace(".", "").replace(",", ".")
print(valor_limpo)  # 1234.5
```

---

## ✅ Verificação

### **Métodos is**

```python
# Verificar tipo de conteúdo
print("123".isdigit())          # True (só dígitos)
print("abc".isalpha())          # True (só letras)
print("abc123".isalnum())       # True (letras e dígitos)
print("   ".isspace())          # True (só espaços)
print("Hello".islower())        # False
print("hello".islower())        # True
print("HELLO".isupper())        # True

# Verificar início/fim
print("Python".startswith("Py"))     # True
print("Python".endswith("on"))       # True
```

**Uso em Data Science:**
```python
# Validar entrada
def eh_numero(valor):
    try:
        float(valor)
        return True
    except ValueError:
        return False

print(eh_numero("123.45"))  # True
print(eh_numero("abc"))     # False
```

---

## 🎨 Interpolação de Variáveis

### **Método format()**

```python
nome = "Maria"
idade = 28
profissao = "Cientista de Dados"
linguagem = "Python"

# Posição sequencial
print("Olá, meu nome é {}, tenho {} anos.".format(nome, idade))
# Olá, meu nome é Maria, tenho 28 anos.

# Índices explícitos
print("Estudo {} e trabalho com {}.".format(linguagem, profissao))
print("Estudo {0} e trabalho com {1}.".format(linguagem, profissao))

# Nomes (mais legível)
print("Olá, {nome}! Você tem {idade} anos.".format(nome=nome, idade=idade))
```

### **f-strings (Recomendado - Python 3.6+)**

```python
nome = "Maria"
idade = 28
profissao = "Cientista de Dados"

# Simples e direto
print(f"Olá, {nome}! Você tem {idade} anos.")

# Com expressões
print(f"Em 5 anos, você terá {idade + 5} anos.")

# Com cálculos
salario = 5000
print(f"Seu salário anual é: R$ {salario * 12:,.2f}")
```

**Diferença:**
```python
# format() precisa passar variáveis no final
frase = "Olá, {}".format(nome)

# f-string coloca a variável direto
frase = f"Olá, {nome}"  # Mais legível!
```

---

## 🔢 Formatação de Números em Strings

### **Formatação com f-strings**

```python
pi = 3.14159
valor = 1234.5

# 2 casas decimais
print(f"PI = {pi:.2f}")           # PI = 3.14

# Com espaçamento (10 caracteres, 2 casas)
print(f"Valor: {valor:10.2f}")    # Valor:    1234.50

# Moeda (com separadores)
print(f"Salário: R$ {5000:,.2f}")  # Salário: R$ 5,000.00

# Percentual
taxa = 0.856
print(f"Taxa: {taxa:.1%}")        # Taxa: 85.6%

# Preenchimento com zeros
numero = 42
print(f"ID: {numero:05d}")        # ID: 00042
```

### **Alinhamento**

```python
texto = "Python"

# Direita (padrão para números)
print(f"|{texto:>15}|")   # |         Python|

# Esquerda
print(f"|{texto:<15}|")   # |Python         |

# Centro
print(f"|{texto:^15}|")   # |    Python     |

# Centro com caractere
print(f"|{texto:*^15}|")  # |****Python****|
```

---

## ✂️ Fatiamento de Strings (Slicing)

Acessar partes específicas de uma string usando índices.

### **Índices**

```python
nome = "Python"

# Posições:  0 1 2 3 4 5
#           P y t h o n
# Negativas: -6-5-4-3-2-1

print(nome[0])        # P (primeira letra)
print(nome[-1])       # n (última letra)
print(nome[1:4])      # yth (do 1 até 3, 4 é exclusivo)
print(nome[:3])       # Pyt (do início até 3)
print(nome[2:])       # thon (do 2 até o fim)
```

### **Passo (Step)**

```python
nome = "Python"

print(nome[::2])      # Pto (cada 2º caractere)
print(nome[1::2])     # yhn (começando em 1, cada 2º)
print(nome[::-1])     # nohtyP (invertido!)
```

**Uso em Data Science:**
```python
# Extrair partes de um código
codigo_produto = "PROD-2024-001"
ano = codigo_produto[5:9]
numero = codigo_produto[-3:]
print(f"Ano: {ano}, Número: {numero}")  # Ano: 2024, Número: 001

# Reverter string
dados = "12345"
print(dados[::-1])    # 54321
```

---

## 📝 Strings de Múltiplas Linhas

### **Triplas Aspas**

```python
# Preserva quebras de linha e espaçamento
mensagem = """
Olá, meu nome é Python,
Eu sou uma linguagem de programação,
Muito usada em Data Science!
"""

print(mensagem)

# Com f-string
nome = "Maria"
curriculo = f"""
Nome: {nome}
Experiência: 5 anos
Habilidades: Python, SQL, Machine Learning
"""
print(curriculo)
```

---

## 🔍 Buscando Padrões com split()

### **split() - Dividir String**

```python
# Dividir por espaço (padrão)
frase = "Python é incrível"
palavras = frase.split()
print(palavras)  # ['Python', 'é', 'incrível']

# Dividir por caractere específico
csv = "Python,JavaScript,SQL,Go"
linguagens = csv.split(",")
print(linguagens)  # ['Python', 'JavaScript', 'SQL', 'Go']

# Limitar divisões
data = "2024-11-26"
partes = data.split("-", 1)
print(partes)  # ['2024', '11-26'] (máximo 1 divisão)
```

**Uso em Data Science:**
```python
# Processar CSV manualmente
linha = "Maria,28,São Paulo,5000"
dados = linha.split(",")
nome, idade, cidade, salario = dados
print(f"{nome} tem {idade} anos e ganha R$ {salario}")
```

---

## 📋 Resumo de Métodos Importantes

| Método | O que faz | Exemplo |
|--------|-----------|---------|
| `upper()` | Maiúsculas | `"hello".upper()` → `HELLO` |
| `lower()` | Minúsculas | `"HELLO".lower()` → `hello` |
| `strip()` | Remove espaços | `"  x  ".strip()` → `x` |
| `replace()` | Substitui | `"abc".replace("a", "x")` → `xbc` |
| `split()` | Divide | `"a,b".split(",")` → `['a','b']` |
| `join()` | Junta | `",".join(['a','b'])` → `a,b` |
| `find()` | Busca posição | `"abc".find("b")` → `1` |
| `count()` | Conta ocorrências | `"aaa".count("a")` → `3` |
| `startswith()` | Começa com? | `"hello".startswith("h")` → `True` |
| `endswith()` | Termina com? | `"hello".endswith("o")` → `True` |

---

## 💡 Exemplo Prático: Processar Dados CSV

```python
# Simular dados brutos
dados_bruto = "  Python  ,  28  ,  São Paulo  "

# Limpar e processar
dados_limpo = dados_bruto.strip()
partes = dados_limpo.split(",")
partes = [p.strip() for p in partes]

linguagem, anos, cidade = partes

print(f"Linguagem: {linguagem}")
print(f"Anos: {anos}")
print(f"Cidade: {cidade}")

# Criar saída formatada
saida = f"{linguagem.upper()}: {anos} anos em {cidade.title()}"
print(saida)  # PYTHON: 28 anos em São Paulo
```

---

## ⚠️ Strings são Imutáveis

```python
texto = "Python"

# ❌ Não pode modificar um caractere
# texto[0] = "J"  # TypeError!

# ✅ Precisa criar nova string
novo_texto = "J" + texto[1:]  # Jython
```

---

## 🔗 Recursos Recomendados

- [Documentação Python - String Methods](https://docs.python.org/pt-br/3/library/stdtypes.html#string-methods)
- [Python String Formatting](https://docs.python.org/pt-br/3/tutorial/inputandoutput.html)
- [f-strings PEP 498](https://www.python.org/dev/peps/pep-0498/)

---

[⬅️ Voltar ao Índice do Módulo](README.md)