# Ambiente de Desenvolvimento e Primeiros Passos

## 🎯 O que aprendi:

Configurar um ambiente profissional de desenvolvimento Python com as melhores ferramentas e práticas.

---

## 💻 Instalação do Python 3.14

### Windows

1. Acesse: https://www.python.org/downloads/
2. Clique em **Download Python 3.14** (ou versão mais recente)
3. **Importante:** Marque a opção **"Add Python to PATH"** durante a instalação
4. Clique em **Install Now**
5. Aguarde a conclusão


### Verificar Instalação

Abra o terminal e digite:

```bash
python --version
# ou
python3 --version
```

Se aparecer a versão (ex: `Python 3.14.0`), está instalado corretamente! ✅

---

## 🛠️ Instalar o VS Code

1. Acesse: https://code.visualstudio.com/
2. Escolha sua plataforma (Windows, macOS ou Linux)
3. Execute o instalador
4. Abra o VS Code

---

## 🔧 Extensões Python Essenciais no VS Code

1. Clique no ícone **Extensões** (lado esquerdo, ícone de quadrados)
2. Instale estas extensões:

### Extensões Recomendadas:

**1. Python**
- Autor: Microsoft
- Provides: IntelliSense, debugging, code formatting

**2. Pylance**
- Autor: Microsoft
- Provides: Type checking estático mais rápido

**3. Jupyter**
- Autor: Microsoft
- Provides: Suporte a Jupyter Notebooks

**4. Code Runner**
- Autor: Jun Han
- Provides: Executar código rapidamente com atalho

**5. Python Docstring Generator**
- Autor: Nils Werner
- Provides: Gerar docstrings automaticamente

---

## 📁 Estrutura de Projeto Python

Crie uma pasta para organizar seus projetos:

```
meus-projetos-python/
├── projeto-1/
│   ├── main.py
│   ├── utils.py
│   └── requirements.txt
├── projeto-2/
│   └── ...
└── README.md
```

---

## 🚀 Seu Primeiro Programa Python

### 1. Criar Arquivo

No VS Code:
1. Clique em **File** → **New File**
2. Digite: `hello_world.py`
3. Pressione **Enter**

### 2. Escrever Código

```python
# Seu primeiro programa em Python
print("Olá, Mundo!")
print("Bem-vindo ao Python!")

# Variáveis simples
nome = "Maria"
idade = 25
print(f"Meu nome é {nome} e tenho {idade} anos")
```

### 3. Executar o Programa

**Opção 1: Atalho Rápido**
- Pressione: **Strg (Ctrl)+ Alt + N** (se tiver Code Runner instalado)

**Opção 2: Via Terminal**
1. Abra o terminal: **Strg + ~**
2. Digite: `python hello_world.py`
3. Pressione **Enter**

**Saída esperada:**
```
Olá, Mundo!
Bem-vindo ao Python!
Meu nome é Maria e tenho 25 anos
```

✅ **Primeiro programa funcionou!**

---

## 📝 Modo Interativo do Python

### Iniciar o Interpretador Interativo

No terminal, digite:

```bash
python
```

Você verá algo assim:

```
Python 3.14.0 (main, Nov 24 2025, 12:00:00)
[GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

### Testar Comandos

```python
>>> print("Testando Python!")
Testando Python!

>>> x = 5
>>> y = 10
>>> x + y
15

>>> "Python" * 3
'PythonPythonPython'
```

### Sair do Modo Interativo

```python
>>> exit()
```

Ou pressione **Strg + D** (Linux/macOS) ou **Strg + Z** (Windows)

---

## 🔍 Funções Essenciais para Exploração

### `dir()` - Lista atributos de um objeto

```python
# Ver todos os métodos de uma string
dir("texto")

# Ver variáveis definidas no escopo atual
dir()
```

### `help()` - Documentação integrada

```python
# Ajuda sobre uma função
help(print)

# Ajuda sobre um método
help(str.upper)

# Sair da ajuda: pressione 'q'
```

### `type()` - Identificar tipo

```python
type(42)          # <class 'int'>
type(3.14)        # <class 'float'>
type("texto")     # <class 'str'>
type([1, 2, 3])   # <class 'list'>
```

---

## 📚 Convenções de Nomenclatura

### Variáveis e Funções (snake_case)

```python
# ✅ Correto
idade_usuario = 25
calcular_media = lambda x, y: (x + y) / 2
nome_completo = "João Silva"

# ❌ Evite
idadeUsuario = 25      # Mistura de casos
idade-usuario = 25     # Não use hífen
IdadeUsuario = 25      # Use para classes
```

### Constantes (MAIÚSCULAS)

```python
# ✅ Correto
TAXA_CONVERSAO = 1.05
LIMITE_SAQUE = 1000
PI = 3.14159

# ❌ Evite
taxa_conversao = 1.05  # Se for constante, use maiúscula
```

### Classes (PascalCase)

```python
# ✅ Correto
class UsuarioBanco:
    pass

class ProcessadorDados:
    pass

# ❌ Evite
class usuario_banco:     # Use PascalCase para classes
    pass
```

---

## ⚠️ Erros Comuns e Soluções

### Erro: "python: command not found"

**Causa:** Python não está no PATH

**Solução:**
- Reinstale Python marcando **"Add Python to PATH"**
- Ou use `python3` em vez de `python`

### Erro: "ModuleNotFoundError"

**Causa:** Você tentou importar um módulo que não existe

**Solução:**
```bash
# Instale o módulo necessário
pip install nome-do-modulo
```

### Erro: "SyntaxError: invalid syntax"

**Causa:** Erro de digitação no código

**Solução:**
- Verifique a indentação
- Procure por parênteses não fechados
- Use o linter do VS Code

---

## 🔗 Recursos Recomendados

- [Python Official Documentation](https://docs.python.org/pt-br/3/)
- [PEP 8 - Style Guide](https://www.python.org/dev/peps/pep-0008/)
- [VS Code Python Setup](https://code.visualstudio.com/docs/languages/python)

---

[⬅️ Voltar ao Índice do Módulo](README.md)