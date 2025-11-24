# Trabalhando com GitHub

## 🎯 O que aprendi

Como usar GitHub para colaboração, backup na nuvem e construir seu portfólio profissional.

---

## 🌐 O que é GitHub?

Se **Git** é a ferramenta que você instala no seu computador, **GitHub** é a "garagem na nuvem" onde você guarda seus projetos.

### Git vs GitHub

| Git | GitHub |
|-----|--------|
| Ferramenta local | Plataforma online |
| Rastreia mudanças | Hospeda repositórios |
| Funciona offline | Precisa internet |
| Você instala | Você acessa pela web |
| Versionamento | Colaboração + backup |

---

## 🎯 Por que Usar GitHub?

### **1. Colaboração em Equipe**
Múltiplas pessoas trabalhando no mesmo projeto sem se atrapalhar.

### **2. Backup Automático**
Seu código está seguro na nuvem. Perdeu o notebook? Não há problema!

### **3. Portfólio Profissional**
Recrutadores veem seu trabalho nos seus "quadradinhos verdes" (contribuições).

### **4. Documentação e Issues**
Rastrear bugs, tarefas e discussões do projeto.

### **5. Comunidade**
Compartilhar conhecimento, receber feedback, colaborar com open source.

---

## 📁 Criar um Repositório no GitHub

### **Passo 1: Fazer Login**
1. Acesse https://github.com
2. Clique em **Sign In**
3. Faça login com sua conta

### **Passo 2: Criar Novo Repositório**
1. Clique no ícone **+** (canto superior direito)
2. Selecione **New repository**
3. Preencha os dados:

```
Repository name: meu-projeto
Description: Descrição do projeto
Visibility: Public (visível) ou Private (privado)
Initialize: ✅ Add README file
             ✅ Add .gitignore → Python
             ✅ Choose a license → MIT
```

4. Clique **Create repository**

### **Passo 3: Clonar para sua Máquina**

```bash
git clone https://github.com/seu-usuario/meu-projeto.git
cd meu-projeto
```

**Pronto! Repositório criado e clonado.**

---

## 🔐 Autenticação com GitHub

### **Método 1: Token Pessoal (Mais Fácil para Iniciantes)**

```bash
# Na primeira vez que você faz push, Git pede autenticação
git push

# GitHub pede seu username
# Depois pede sua senha (mas você usa um TOKEN)
```

**Gerar um Token:**
1. GitHub → Settings (ícone de perfil)
2. Developer settings → Personal access tokens
3. Tokens (classic)
4. Generate new token
5. Marque as opções: `repo`, `gist`, `workflow`
6. **COPIE o token** (aparece apenas uma vez!)
7. Use como senha quando Git pedir

### **Método 2: SSH (Mais Seguro para Profissionais)**

```bash
# Gerar chave SSH
ssh-keygen -t ed25519 -C "seu.email@gmail.com"

# Quando pedir, pressione Enter (sem senha)
# Isso cria 2 arquivos:
# id_ed25519 (chave privada - guarde com seu!!)
# id_ed25519.pub (chave pública - compartilhe com GitHub)

# Adicionar ao ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Adicionar chave pública ao GitHub:
# 1. Copie o conteúdo de ~/.ssh/id_ed25519.pub
# 2. GitHub → Settings → SSH and GPG keys
# 3. New SSH key → Cole e salve
```

**Agora você não precisa mais de token ou senha!**

---

## 📤 Fluxo Completo: Do Código para GitHub

### **Cenário: Você criou um novo arquivo**

```bash
# 1. Verificar o que mudou
git status
# Mostra: arquivo_novo.py (untracked)

# 2. Preparar o arquivo
git add arquivo_novo.py

# 3. Confirmar com mensagem
git commit -m "Adiciona funcionalidade nova"

# 4. Enviar para GitHub
git push
```

**Resultado:** Seu código está no GitHub!

---

## 🔀 Usando GitHub para Colaboração

### **Você Recebe Atualizações do Colega**

```bash
# Seu colega enviou mudanças (push)
# Você precisa baixar (pull)

git pull

# Agora você tem a versão mais recente
```

**Fluxo seguro em EQUIPE:**

```bash
# Manhã - chegar e puxar tudo
git pull

# Trabalhar...

# Depois de terminar
git add .
git commit -m "Mensagem clara"
git push
```

---

## 📝 Markdown no GitHub

GitHub usa **Markdown** para formatação de texto. Útil para:
- README.md
- Documentação
- Descrição de commits

### **Básico do Markdown**

```markdown
# Título Grande (h1)
## Título Médio (h2)
### Título Pequeno (h3)

**Negrito**
*Itálico*
***Negrito e Itálico***

- Lista com bullet
- Outro item
- Mais um

1. Lista numerada
2. Segundo item

[Link para Google](https://google.com)

`código inline`

\`\`\`python
# Bloco de código
print("Hello, World!")
\`\`\`

| Coluna 1 | Coluna 2 |
|----------|----------|
| A        | B        |
```

### **Criar README.md Profissional**

No GitHub, a primeira coisa que aparece é o README.md:

```markdown
# Meu Projeto Incrível

Descrição do que o projeto faz.

## Como Usar

\`\`\`bash
git clone https://github.com/usuario/projeto.git
cd projeto
python main.py
\`\`\`

## Funcionalidades

- ✅ Funcionalidade 1
- ✅ Funcionalidade 2
- 🔜 Funcionalidade 3 (em desenvolvimento)

## Tecnologias

- Python 3.14
- Git/GitHub
- VS Code

## Autor

[Seu Nome](https://github.com/seu-usuario)
```

---

## 🌍 O GitHub Online (Web Editor)

### **Editar Código Direto no Navegador**

Você pode editar arquivos diretamente no GitHub sem clonar:

1. Abra seu repositório no GitHub
2. Navegue até o arquivo
3. Clique no ícone de **lápis** (Edit)
4. Faça as mudanças
5. Clique em **Commit changes**

**Pronto! A mudança já está no repositório!**

### **VS Code Online do GitHub**

1. Abra seu repositório
2. Pressione a **tecla . (ponto)**
3. Abre um VS Code completo **no navegador!**
4. Edite, commit e push tudo online

---

## 🔗 Conectar Repositório Local Existente

**Você tem um projeto local e quer enviar para GitHub:**

```bash
# 1. Criar repositório no GitHub (sem clonar)

# 2. Na pasta do seu projeto local:
git remote add origin https://github.com/usuario/projeto.git
git branch -M main
git push -u origin main

# Pronto! Seu projeto local está conectado ao GitHub
```

---

## 📊 Acompanhar Repositório

### **Ver o Histórico no GitHub**

1. Abra seu repositório
2. Clique em **[X] commits**
3. Veja todos os commits com:
   - Mensagem
   - Autor
   - Data
   - Mudanças feitas

### **Comparar Versões**

1. Clique em **[X] commits**
2. Clique no botão **<>** (Compare) de um commit
3. Veja exatamente o que mudou

---

## 🎨 Personalizar Seu Perfil GitHub

### **Perfil Profissional**

1. Clique na sua **foto de perfil**
2. Clique em **Your profile**
3. Clique em **Edit profile**
4. Preencha:
   - Bio (descrição)
   - URL (seu site)
   - Localização
   - Foto profissional

**Dica:** Recruadores veem seu perfil!

---

## 📌 Funcionalidades Extras

### **Pinnar Repositórios**

Destaque seus melhores projetos no seu perfil:

1. Vá até o repositório
2. Clique em **⭐ Star** (favoritar)
3. Volte ao seu perfil
4. Seus repositórios mais importantes aparecem em destaque

### **Seguir Outras Pessoas**

Veja o que desenvolvedores interessantes estão fazendo:

1. Acesse o perfil deles
2. Clique em **Follow**
3. Veja suas atividades no seu feed

---

## 🚀 Boas Práticas no GitHub

✅ **Faça:**
- Commits frequentes com mensagens claras
- README.md bem preenchido
- Use .gitignore para arquivos sensíveis
- Mantenha repositórios organizados
- Colabore respeitosamente

❌ **Evite:**
- Commits com mensagens como "ajustes" ou "."
- Enviar senhas ou dados pessoais
- Esquecer de fazer `git pull` antes de trabalhar
- Repositórios com nome genérico ("projeto123")
- Falta de documentação

---

## 💡 Fluxo Típico do Dia

```bash
# Chegar (atualizar tudo)
git pull

# Trabalhar (editar arquivos)
# ...

# Preparar mudanças
git add .

# Confirmar
git commit -m "Adiciona login com email"

# Enviar
git push

# Ver no GitHub.com ✨
```

---

## 🔗 Recursos Recomendados

- [GitHub Official Documentation](https://docs.github.com/pt)
- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Skills (Cursos Gratuitos)](https://skills.github.com/)
- [Readme.so (Template README)](https://readme.so/)

---

[⬅️ Voltar ao Índice do Módulo](README.md)