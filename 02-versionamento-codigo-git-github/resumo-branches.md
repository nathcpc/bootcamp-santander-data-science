# Fluxo de Trabalho com Branches

## 🎯 O que aprendi

Como usar branches (ramos) para trabalhar em múltiplas funcionalidades simultaneamente sem atrapalhar o código principal.

---

## 🌳 O que é uma Branch?

Uma **branch** é um "ramo" do seu projeto. Pense assim:

```
                    PRINCIPAL (main)
                         ↑
                    ✅ Funcionando
                         ↓
        ┌─────────────┼─────────────┐
        ↓             ↓             ↓
    Feature 1    Feature 2    Bug Fix
   (em andamento) (em teste)  (correção)
```

**Analogia:**
Imagine que você está escrevendo um livro. A `main` é o livro "finalizado". Você cria uma `branch` para adicionar um novo capítulo sem mexer no livro principal. Quando o capítulo estiver pronto, você mescla (`merge`) de volta.

---

## 🚀 Por que Usar Branches?

| Benefício | Descrição |
|-----------|-----------|
| **Isolamento** | Código novo não quebra o que já funciona |
| **Colaboração** | Cada pessoa trabalha em sua branch |
| **Organização** | Fácil rastrear o que está em desenvolvimento |
| **Segurança** | `main` sempre pronto para produção |
| **Testes** | Testar antes de mesclar |

---

## 📋 Branch Padrão

Quando você cria um repositório, Git cria uma branch padrão (normalmente `main` ou `master`).

```bash
# Ver em qual branch você está
git branch

# Resultado (o * indica a branch atual):
* main      ← Você está aqui
  develop
  feature/login
```

---

## 🔄 Fluxo Básico de Branches

### **1. Criar uma Branch**

```bash
# Criar branch para uma nova funcionalidade
git branch nova-feature

# Ou criar E mudar em um comando
git checkout -b nova-feature
```

### **2. Mudar para a Branch**

```bash
git checkout nova-feature
# Agora você está trabalhando na branch "nova-feature"
```

### **3. Trabalhar Normalmente**

```bash
# Editar arquivos...
git add .
git commit -m "Adiciona nova funcionalidade"
git push

# Importante: Quando fizer push em uma branch nova:
git push -u origin nova-feature
```

### **4. Mesclar com a Principal**

```bash
# Voltar para main
git checkout main

# Puxar atualizações
git pull

# Mesclar a branch
git merge nova-feature

# Enviar para GitHub
git push
```

### **5. Deletar a Branch (Opcional)**

```bash
# Deletar localmente
git branch -d nova-feature

# Deletar no GitHub
git push origin --delete nova-feature
```

---

## 🎯 Exemplo Prático Passo a Passo

**Cenário:** Você quer adicionar um botão de login sem quebrar o site atual.

### **Passo 1: Criar Branch**
```bash
git checkout -b adiciona-login
# Você está em "adiciona-login"
```

### **Passo 2: Trabalhar**
```bash
# Edita o arquivo de login
echo "<button>Login</button>" >> login.html

# Prepara
git add login.html

# Confirma
git commit -m "Adiciona botão de login"

# Envia
git push -u origin adiciona-login
```

### **Passo 3: Testar no GitHub**
1. Acesse seu repositório no GitHub
2. Você verá um aviso: "Compare & pull request"
3. Clique para revisar mudanças

### **Passo 4: Mesclar**
```bash
# Voltar para main
git checkout main

# Puxar tudo o que pode ter mudado
git pull

# Mesclar sua feature
git merge adiciona-login

# Enviar
git push
```

**Pronto! Login está agora no site principal!**

---

## 🏗️ Estratégias de Branches Comuns

### **Git Flow**

Modelo mais estruturado para grandes projetos:

```
main           (produção)
  ↑
  └─ develop   (desenvolvimento)
      ↑
      ├─ feature/...  (novas funcionalidades)
      ├─ bugfix/...   (correções rápidas)
      └─ release/...  (preparar versão)
```

**Fluxo:**
```bash
git checkout -b feature/nova-feature develop
# Trabalhar...
git merge feature/nova-feature develop
git checkout main
git merge develop
```

### **Trunk-Based Development**

Mais simples, para times pequenos:

```
main
  ↑
  ├─ feature-a
  ├─ feature-b
  └─ bugfix-1
```

**Fluxo:**
```bash
git checkout -b feature-a
# Trabalhar (commits pequenos)
git push
# Mesclar rapidamente
```

---

## 🔍 Comparar Branches

### **Ver Diferenças Entre Branches**

```bash
# Quais mudanças tem em feature que não estão em main?
git diff main nova-feature

# Mostra quais arquivos mudaram
git diff main nova-feature --name-only
```

### **Ver Commits de Uma Branch**

```bash
# Ver último commit de cada branch
git branch -v

# Ver todos os commits da feature
git log nova-feature
```

---

## ⚠️ Conflitos de Merge

Às vezes, Git não consegue mesclar automaticamente (conflitos).

### **Cenário: Conflito Acontece**

```bash
git merge nova-feature

# Resultado:
# CONFLICT (content conflict in arquivo.py)
# Automatic merge failed; fix conflicts and then commit the result.
```

### **Como Resolver**

**Opção 1: Resolver Manualmente**

1. Abra o arquivo em conflito
2. Você verá algo assim:

```python
<<<<<<< HEAD
versao_atual = "v1.0"
=======
versao_nova = "v2.0"
>>>>>>> nova-feature
```

3. Escolha qual versão manter:

```python
# Mantém a nova (deleta as marcas)
versao_nova = "v2.0"
```

4. Salva o arquivo
5. Confirma:

```bash
git add arquivo.py
git commit -m "Resolve conflito no merge"
git push
```

**Opção 2: Abortar Merge**

```bash
# Cancela o merge e volta ao estado anterior
git merge --abort
```

---

## 🔗 Trabalhar com Branches Remotas

### **Ver Branches no GitHub**

```bash
# Ver todas as branches (local + remota)
git branch -a

# Resultado:
# main
# * develop
# remotes/origin/develop
# remotes/origin/main
# remotes/origin/feature/login
```

### **Clonar uma Branch Específica**

```bash
# Clonar só uma branch (mais rápido)
git clone URL --branch nome-branch --single-branch
```

### **Sincronizar com Branch Remota**

```bash
# Buscar mudanças sem mesclar
git fetch origin

# Comparar com remota
git diff main origin/main

# Atualizar com remota
git pull origin main
```

---

## 🎯 Convenções de Nomes de Branches

Use nomes descritivos e organizados:

```bash
# ✅ BOM
feature/adiciona-login
feature/carrinho-compras
bugfix/corrige-validacao-email
hotfix/seguranca-senha
release/v1.0

# ❌ RUIM
feature1
nova-coisa
teste
test123
fix
```

**Padrão comum:**
```
[tipo]/[descrição]

tipo: feature, bugfix, hotfix, release
descrição: clara e em lowercase com hífens
```

---

## 💡 Boas Práticas

✅ **Faça:**
- Branches curtas e focadas em uma funcionalidade
- Commits frequentes na branch
- Mensagens de commit claras
- Sincronize com `main` regularmente (`git pull`)
- Delete branches após mesclar

❌ **Evite:**
- Branches muito longas (mais de alguns dias)
- Branches com múltiplas funcionalidades
- Não fazer commit
- Esquecer de fazer `pull` antes de trabalhar

---

## 📊 Fluxo Diário em Equipe

```bash
# Chegar ao trabalho
git checkout main
git pull

# Criar branch para sua tarefa
git checkout -b feature/minha-tarefa

# Trabalhar
# ... edita arquivos ...

# Ao longo do dia
git add .
git commit -m "Progresso na funcionalidade"
git push

# Quando terminar
git add .
git commit -m "Funcionalidade completa"
git push

# Ir para GitHub
# Clique "Create Pull Request"
# Colegas revisam

# Após aprovação
git checkout main
git pull
git merge feature/minha-tarefa
git push

# Limpar
git branch -d feature/minha-tarefa
```

---

## 🚀 Comandos Rápidos

| Comando | O que faz |
|---------|-----------|
| `git branch` | Lista branches locais |
| `git branch -a` | Lista todas (local + remota) |
| `git branch nova` | Cria branch |
| `git checkout -b nova` | Cria e muda para branch |
| `git checkout nome` | Muda para branch |
| `git merge nome` | Mescla branch |
| `git branch -d nome` | Deleta branch |
| `git push origin --delete nome` | Deleta no GitHub |
| `git diff main outra` | Compara branches |
| `git log nome` | Ver commits da branch |

---

## 🎓 Próximo Passo: Pull Request

**Pull Request (PR)** é a forma profissional de mesclar branches no GitHub:

1. Você faz push em uma branch
2. GitHub avisa que tem mudanças
3. Você clica "Create Pull Request"
4. Colegas revisam seu código
5. Se estiver bom, clicam "Merge"
6. Código vai para `main`

Isso será tema de outro resumo!

---

## 🔗 Recursos Recomendados

- [Git Branching - Pro Git Book](https://git-scm.com/book/pt-br/v2/Ramifica%C3%A7%C3%A3o-em-Git)
- [GitHub Flow Guide](https://guides.github.com/introduction/flow/)
- [Git Flow Cheatsheet](https://danielkummer.github.io/git-flow-cheatsheet/)

---

[⬅️ Voltar ao Índice do Módulo](README.md)