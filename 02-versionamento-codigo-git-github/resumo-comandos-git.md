# Comandos Git Essenciais

## 🎯 O que aprendi

Os comandos Git mais importantes que você usará no dia a dia. Salve esses comandos!

---

## 🎬 Antes de Começar: Configuração Inicial

### Identificar Você Mesmo no Git

Quando você faz um commit, Git precisa saber quem é você:

```bash
git config --global user.name "Seu Nome Completo"
git config --global user.email "seu.email@gmail.com"
```

**Exemplo:**
```bash
git config --global user.name "Maria Silva"
git config --global user.email "maria.silva@example.com"
```

### Verificar sua Configuração

```bash
git config --list
# Mostra todas as configurações do Git
```

---

## 📋 Os 4 Comandos Principais (90% do Uso)

Estes são os comandos que você vai usar quase todo dia:

### **1. git clone - Baixar um Projeto**

```bash
git clone URL_do_repositorio
# Baixa o projeto completo do GitHub para sua máquina
```

**Exemplos:**
```bash
# Clonar repositório com nome padrão
git clone https://github.com/usuario/projeto.git
# Cria pasta chamada "projeto"

# Clonar com outro nome
git clone https://github.com/usuario/projeto.git meu-nome
# Cria pasta chamada "meu-nome"
```

**O que acontece:**
- Baixa TODO o código
- Baixa TODO o histórico de versões
- Você tem uma cópia completa na sua máquina

---

### **2. git status - Ver o que Mudou**

```bash
git status
# Mostra quais arquivos foram modificados
# Mostra o que está pronto para commit
```

**Exemplo de saída:**
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to stage the file)
        modified:   README.md
        modified:   script.py

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        novo_arquivo.md
```

**O que significa:**
- `modified` = arquivo que você editou
- `Untracked files` = arquivos novos que Git não conhece ainda

---

### **3. git add - Preparar Arquivos para Salvar**

```bash
# Preparar UM arquivo
git add README.md

# Preparar TODOS os arquivos modificados
git add .

# O ponto (.) significa "tudo"
```

**Por que dois passos?**

Imagine que você modificou 5 arquivos, mas quer salvar apenas 3:

```bash
git add arquivo1.py   # Prepara este
git add arquivo2.py   # Prepara este
git add arquivo3.py   # Prepara este
# Os outros 2 ficam de fora

git commit -m "Corrige bugs"
# Salva apenas os 3 que preparou
```

---

### **4. git commit - Salvar as Mudanças**

```bash
git commit -m "Descrição clara do que você fez"
```

**Exemplos bons:**
```bash
git commit -m "Adiciona funcionalidade de login"
git commit -m "Corrige bug na validação de email"
git commit -m "Atualiza documentação do projeto"
```

**Exemplos ruins (evite!):**
```bash
git commit -m "ajustes"          # Muito vago
git commit -m "conserta tudo"    # Sem detalhe
git commit -m "."                # Inútil!
```

**Dica:** A mensagem é para você e seus colegas entenderem o que foi feito!

---

## 🌐 Sincronizando com GitHub

### **git push - Enviar suas Mudanças**

```bash
git push
# Envia seus commits para o GitHub
```

**Fluxo completo:**
```bash
git add .                                    # 1. Preparar
git commit -m "Adiciona calculadora"        # 2. Confirmar
git push                                    # 3. Enviar
```

### **git pull - Receber Atualizações**

```bash
git pull
# Baixa as mudanças que outras pessoas fizeram
# E mescla com seu código
```

**Importante:** Sempre faça `git pull` antes de começar a trabalhar em equipe!

```bash
# Fluxo seguro em equipe:
git pull                 # 1. Pega atualizações dos colegas
# 2. Você trabalha e faz mudanças
git add .                # 3. Prepara seus arquivos
git commit -m "..."      # 4. Confirma as mudanças
git push                 # 5. Envia para o GitHub
```

---

## 📁 Comandos para Criar Repositórios

### **git init - Inicializar um Repositório**

```bash
# Criar uma pasta
mkdir meu-projeto
cd meu-projeto

# Transformá-la em repositório Git
git init
# A partir daqui, Git rastreia mudanças nessa pasta
```

**O que o Git cria:**
- Uma pasta `.git` (oculta) com toda a configuração
- Esta pasta armazena o histórico de versões

---

## 🔗 Conectar Repositório Local com GitHub

### **git remote add - Vincular com GitHub**

```bash
# Conectar seu repositório local com o GitHub
git remote add origin https://github.com/usuario/repositorio.git
# "origin" é o nome padrão para o servidor remoto
```

### **git remote -v - Ver Repositórios Conectados**

```bash
git remote -v
# Mostra quais servidores seu repositório está conectado
```

**Exemplo de saída:**
```
origin  https://github.com/maria/projeto.git (fetch)
origin  https://github.com/maria/projeto.git (push)
```

---

## 🌳 Comandos Essenciais de Branch (Ramos)

### **git branch - Criar um Ramo**

```bash
# Ver todas as branches
git branch

# Criar uma nova branch
git branch nome-da-branch

# Exemplo: criar branch para nova feature
git branch adiciona-login
```

### **git checkout - Mudar de Branch**

```bash
# Mudar para uma branch existente
git checkout nome-da-branch

# Exemplo: voltar para main
git checkout main
```

### **Criar e Mudar em Um Comando**

```bash
# Criar nova branch E mudar para ela
git checkout -b nome-da-branch

# Exemplo
git checkout -b corrige-bug
# Você já está na branch "corrige-bug" pronto para trabalhar
```

### **git merge - Mesclar Branches**

```bash
# Estar na branch PRINCIPAL
git checkout main

# Mesclar outra branch com a principal
git merge nome-da-branch-que-quer-mesclar

# Exemplo: você terminou a feature e quer adicionar ao main
git merge adiciona-login
```

---

## 🔄 Ver o Histórico

### **git log - Ver Commits Anteriores**

```bash
git log
# Mostra todos os commits já feitos
# Com autor, data e mensagem
```

**Saída típica:**
```
commit a3c7e9f2b1d5e4c8a2f0b1c3d4e5f6a7b8c9d0e
Author: Maria Silva <maria@example.com>
Date:   Mon Nov 24 14:30:00 2025 +0100
    Adiciona calculadora

commit 5f6a7b8c9d0e1a2b3c4d5e6f7a8b9c0d1e2f3a4
Author: João Santos <joao@example.com>
Date:   Sun Nov 23 10:15:00 2025 +0100
    Corrige bug na validação
```

### **git reflog - Ver Tudo Que Você Fez**

```bash
git reflog
# Mostra TODAS as operações (mais detalhado que log)
# Útil para recuperar commits deletados
```

---

## 🚫 Desfazendo Alterações

### **git restore - Desfazer Mudanças em Um Arquivo**

```bash
# Restaurar um arquivo para o estado anterior
git restore nome_do_arquivo

# Exemplo: você editou e quer voltar como era
git restore script.py
```

**⚠️ CUIDADO:** Isso deleta suas mudanças! Use com cuidado.

### **git reset - Desfazer Commits**

```bash
# Ver o hash dos commits
git log

# Voltar para um commit anterior (3 opções)
git reset --soft a3c7e9   # Guarda mudanças para refazer
git reset --mixed a3c7e9  # Remove prep. mas guarda no disco
git reset --hard a3c7e9   # Remove TUDO (cuidado!)
```

**Diferenças:**
- `--soft` = mantém os arquivos prontos em staging
- `--mixed` = mantém os arquivos, mas não preparados
- `--hard` = apaga TUDO

### **git commit --amend - Corrigir Último Commit**

```bash
# Mudou de ideia sobre a mensagem do último commit?
git commit --amend -m "Nova mensagem"

# Esqueceu de adicionar um arquivo no último commit?
git add arquivo_esquecido.py
git commit --amend
```

---

## 🔐 .gitignore - Ignorar Arquivos

Alguns arquivos NÃO devem ir para GitHub (senhas, arquivos grandes, etc):

```bash
# Criar arquivo .gitignore
echo arquivo_secreto.txt > .gitignore
echo dados_pessoais.csv >> .gitignore

# Agora esses arquivos são ignorados pelo Git
```

**Exemplo de .gitignore profissional:**
```
# Arquivos de configuração pessoal
config.local.js
.env

# Dependências (normalmente ignoradas)
node_modules/
__pycache__/

# Arquivos do sistema
.DS_Store
Thumbs.db

# IDEs
.vscode/
.idea/
```

---

## 💾 Salvar Mudanças Temporariamente

### **git stash - Guardar Trabalho Temporariamente**

```bash
# Você está em uma branch mas não quer commitar ainda
# Quer mudar de branch? Use stash!

git stash
# Suas mudanças são salvas temporariamente

# Muda para outra branch
git checkout outra-branch

# Depois, volta e recupera seu trabalho
git checkout primeira-branch
git stash pop
# Suas mudanças voltam!
```

---

## 📋 Tabela de Referência Rápida

| Comando | O que faz |
|---------|-----------|
| `git clone URL` | Baixa projeto do GitHub |
| `git status` | Mostra o que mudou |
| `git add .` | Prepara todos os arquivos |
| `git commit -m "msg"` | Salva as mudanças |
| `git push` | Envia para o GitHub |
| `git pull` | Baixa atualizações |
| `git branch nome` | Cria nova branch |
| `git checkout nome` | Muda para branch |
| `git merge nome` | Mescla branches |
| `git log` | Ver histórico |
| `git restore arquivo` | Desfaz mudanças |
| `git reset --hard hash` | Volta para versão anterior |

---

## 🎯 Fluxo Típico do Dia a Dia

```bash
# Chegar e atualizar (sempre!)
git pull

# Trabalhar...
# (edita arquivos)

# Verificar o que mudou
git status

# Preparar tudo
git add .

# Salvar com mensagem clara
git commit -m "Adiciona botão de logout"

# Enviar para GitHub
git push

# FIM!
```

---

## ⚠️ Erros Comuns

```bash
# ❌ ERRO: Esqueceu de fazer git pull antes
# Resultado: Conflitos ao fazer git push
# ✅ SOLUÇÃO: Sempre git pull primeiro

# ❌ ERRO: Mensagem de commit confusa
# ✅ SOLUÇÃO: Mensagens claras e descritivas

# ❌ ERRO: Enviar arquivos com senhas
# ✅ SOLUÇÃO: Use .gitignore

# ❌ ERRO: git reset --hard acidentalmente
# ✅ SOLUÇÃO: Recupere com git reflog
```

---

## 🔗 Recursos Recomendados

- [Documentação Oficial do Git](https://git-scm.com/docs)
- [Pro Git Book - Português](https://git-scm.com/book/pt-br/v2)
- [Git Cheat Sheet](https://git-scm.com/docs)

---

[⬅️ Voltar ao Índice do Módulo](README.md)