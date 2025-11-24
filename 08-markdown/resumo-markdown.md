# Mini-Curso de Markdown

## 🎯 O que eu aprendi

A sintaxe completa de Markdown para criar documentação profissional e READMEs impressionantes no GitHub.

---

## 🔍 O que é Markdown?

**Markdown** é uma linguagem de formatação simples baseada em texto. Em vez de clicar em botões (como no Word), você escreve símbolos especiais que o computador interpreta.

**Vantagens:**
- ✅ Super fácil de aprender (30 minutos!)
- ✅ Funciona em qualquer lugar (texto puro)
- ✅ GitHub renderiza automaticamente
- ✅ Versiona bem no Git (diferenças claras)
- ✅ Profissional e padronizado

**Exemplo:**
```
**Negrito** → fica em negrito
*Itálico* → fica em itálico
# Título → fica grande
```

---

## 📝 Sintaxe Básica

### **1. Títulos**

```markdown
# Título 1 (Maior)
## Título 2
### Título 3
#### Título 4
##### Título 5
###### Título 6 (Menor)
```

**Resultado:**
# Título 1 (Maior)
## Título 2
### Título 3

---

### **2. Ênfase (Negrito e Itálico)**

```markdown
**Negrito** ou __Negrito__
*Itálico* ou _Itálico_
***Negrito e Itálico***
~~Riscado~~
```

**Resultado:**
- **Negrito** ou __Negrito__
- *Itálico* ou _Itálico_
- ***Negrito e Itálico***
- ~~Riscado~~

---

### **3. Listas com Bullets**

```markdown
- Item 1
- Item 2
- Item 3
  - Subitem 3.1
  - Subitem 3.2
```

**Resultado:**
- Item 1
- Item 2
- Item 3
  - Subitem 3.1
  - Subitem 3.2

---

### **4. Listas Numeradas**

```markdown
1. Primeiro
2. Segundo
3. Terceiro
   1. Subitem 3.1
   2. Subitem 3.2
```

**Resultado:**
1. Primeiro
2. Segundo
3. Terceiro
   1. Subitem 3.1
   2. Subitem 3.2

---

### **5. Links**

```markdown
[Texto do link](https://exemplo.com)
[GitHub](https://github.com)
[Link com título](https://exemplo.com "Hover text")
```

**Resultado:**
- [Texto do link](https://exemplo.com)
- [GitHub](https://github.com)

---

### **6. Imagens**

```markdown
![Texto alternativo](url-da-imagem.jpg)
![Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
```

---

### **7. Código Inline (na linha)**

```markdown
Use `git add .` para preparar arquivos
Use `python script.py` para executar
```

**Resultado:**
Use `git add .` para preparar arquivos
Use `python script.py` para executar

---

### **8. Bloco de Código**

````markdown
```python
# Código Python
def hello():
    print("Olá, Mundo!")
```

```bash
# Comando de terminal
git add .
git commit -m "Mensagem"
```

```javascript
// Código JavaScript
console.log("Hello");
```
````

**Resultado:**
```python
# Código Python
def hello():
    print("Olá, Mundo!")
```

---

### **9. Citações (Blockquote)**

```markdown
> Esta é uma citação
> Citações são úteis para destacar informações

> **Nota:** Você pode combinar com outros estilos
```

**Resultado:**
> Esta é uma citação
> Citações são úteis para destacar informações

---

### **10. Linhas Horizontais**

```markdown
---
ou
***
ou
___
```

**Resultado:**

---

---

## 📊 Tabelas

### **Básico**

```markdown
| Coluna 1 | Coluna 2 | Coluna 3 |
|----------|----------|----------|
| A        | B        | C        |
| D        | E        | F        |
```

**Resultado:**

| Coluna 1 | Coluna 2 | Coluna 3 |
|----------|----------|----------|
| A        | B        | C        |
| D        | E        | F        |

### **Com Alinhamento**

```markdown
| Esquerda | Centro | Direita |
|:---------|:------:|--------:|
| A        | B      | C       |
| D        | E      | F       |
```

| Esquerda | Centro | Direita |
|:---------|:------:|--------:|
| A        | B      | C       |
| D        | E      | F       |

**Legendas:**
- `:---` = alinhado à esquerda
- `:---:` = centralizado
- `---:` = alinhado à direita

---

## ✨ Formatação Avançada

### **Listas de Verificação (Checkboxes)**

```markdown
- [x] Tarefa completa
- [ ] Tarefa pendente
- [x] Outra tarefa pronta
```

**Resultado:**
- [x] Tarefa completa
- [ ] Tarefa pendente
- [x] Outra tarefa pronta

---

### **Emojis**

```markdown
✅ Sucesso
❌ Erro
⚠️ Aviso
🚀 Iniciar
📚 Documentação
💡 Ideia
🔗 Link
```

**Resultado:**
✅ Sucesso
❌ Erro
⚠️ Aviso
🚀 Iniciar

[Lista completa de emojis](https://www.webfx.com/tools/emoji-cheat-sheet/)

---

### **Escape Characters**

Se você quer mostrar símbolos que Markdown usa:

```markdown
\*Isso não é itálico\*
\# Isso não é título
\[Isso não é link\]
```

---

### **HTML Puro (Funciona!)**

```markdown
<div style="background-color: yellow; padding: 10px;">
  Você pode usar HTML dentro de Markdown!
</div>

<img src="https://exemplo.com/foto.jpg" width="200">
```

---

## 📄 Criando READMEs Profissionais

### **Estrutura Recomendada**

```markdown
# Nome do Projeto

Descrição clara em 1-2 linhas do que o projeto faz.

## 📋 Índice

- [Instalação](#instalação)
- [Como Usar](#como-usar)
- [Funcionalidades](#funcionalidades)
- [Tecnologias](#tecnologias)
- [Contribuindo](#contribuindo)

## 🚀 Instalação

\`\`\`bash
git clone https://github.com/usuario/projeto.git
cd projeto
pip install -r requirements.txt
\`\`\`

## 📖 Como Usar

\`\`\`bash
python main.py --help
\`\`\`

## ✨ Funcionalidades

- ✅ Funcionalidade 1
- ✅ Funcionalidade 2
- 🔜 Funcionalidade em desenvolvimento

## 🛠️ Tecnologias

- Python 3.14
- Git/GitHub
- VS Code

## 📝 Exemplo de Uso

\`\`\`python
from projeto import fazer_algo

resultado = fazer_algo("parametro")
print(resultado)
\`\`\`

## 🤝 Contribuindo

Pull requests são bem-vindos!

## 📄 Licença

MIT License - veja LICENSE para detalhes

## ✍️ Autor

[Seu Nome](https://github.com/seu-usuario)
```

---

## 💡 Dicas Práticas

### **Dica 1: Índice com Âncoras**

```markdown
## Índice
- [Seção 1](#seção-1)
- [Seção 2](#seção-2)

## Seção 1
Conteúdo...

## Seção 2
Conteúdo...
```

O Markdown automaticamente cria âncoras (links internos) a partir dos títulos!

---

### **Dica 2: Quebra de Linha**

```markdown
Parágrafo 1

Parágrafo 2 (linha em branco entre eles)

Sem quebra de linha aparece no mesmo parágrafo
```

---

### **Dica 3: Badges e Escudos**

```markdown
![Python](https://img.shields.io/badge/Python-3.14-blue)
![Status](https://img.shields.io/badge/Status-Ativo-success)
![License](https://img.shields.io/badge/License-MIT-green)
```

Site: [shields.io](https://shields.io/)

---

### **Dica 4: Detalhes Ocultáveis (Spoilers)**

```markdown
<details>
<summary>Clique para expandir</summary>

Conteúdo oculto que aparece quando clica

```python
# Código aqui
```

</details>
```

---

### **Dica 5: Comentários (Não aparecem)**

```markdown
<!-- Isto é um comentário e não aparece no GitHub -->
<!-- Útil para deixar notas para você mesmo -->
```

---

## 🎯 Exercício Prático

Crie um README para um projeto fictício com:

1. ✅ Título e descrição
2. ✅ Índice com links internos
3. ✅ Seção de instalação com código
4. ✅ Tabela comparando recursos
5. ✅ Lista de verificação
6. ✅ Badges de status
7. ✅ Seção de autor

---

## 🔗 Recursos Recomendados

- [Markdown Official](https://daringfireball.net/projects/markdown/)
- [GitHub Markdown Guide](https://docs.github.com/pt/get-started/writing-on-github)
- [Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)
- [readme.so (Template Builder)](https://readme.so/)
- [Shields.io (Badges)](https://shields.io/)

---

## ⚠️ Erros Comuns

```markdown
❌ ERRADO: *negrito**
✅ CORRETO: **negrito**

❌ ERRADO: #Título sem espaço
✅ CORRETO: # Título com espaço

❌ ERRADO: [link]
✅ CORRETO: [texto](url)

❌ ERRADO: ```javascript python
✅ CORRETO: ```javascript
```

---

## 🎓 Resumo de Sintaxe

| Elemento | Sintaxe |
|----------|---------|
| Título | `# Texto` |
| Negrito | `**Texto**` |
| Itálico | `*Texto*` |
| Link | `[Texto](url)` |
| Imagem | `![Alt](url)` |
| Código | `` `código` `` |
| Lista | `- Item` |
| Tabela | `\| Col1 \| Col2 \|` |
| Citação | `> Texto` |
| Linha | `---` |

---

## 🚀 Próximo Passo

Agora que você sabe Markdown:
1. Crie READMEs incríveis nos seus projetos
2. Use em documentação
3. Pratique no GitHub
4. Imprima recrutadores com documentação profissional

Bom aprendizado! 📝✨

---

[⬅️ Voltar ao Índice do Módulo](README.md)