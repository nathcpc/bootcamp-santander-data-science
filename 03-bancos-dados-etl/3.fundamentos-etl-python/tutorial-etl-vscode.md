# Guia Prático: ETL com Python no VSCode

## 🎯 O que vamos aprender

Este guia ensina como configurar seu ambiente VSCode para desenvolvimento de pipelines ETL com Python, desde a instalação de extensões até a execução de scripts Pandas, Scikit-learn e Luigi.

---

## 1. Instalação e Configuração do VSCode

### 1.1 Baixar e Instalar VSCode

1. Acesse [code.visualstudio.com](https://code.visualstudio.com/)
2. Baixe a versão para seu sistema operacional (Windows, macOS, Linux)
3. Instale seguindo as instruções padrão

### 1.2 Instalar Extensões Essenciais

No VSCode, vá em **Extensions** (Ctrl+Shift+X) e instale:

| Extensão | Desenvolvedor | Função |
|----------|---------------|--------|
| **Python** | Microsoft | Suporte completo Python |
| **Pylance** | Microsoft | Intellisense avançado |
| **Jupyter** | Microsoft | Notebooks interativos |
| **Git Graph** | mhutchie | Visualizar Git |
| **Thunder Client** | rangav | Testar APIs REST |
| **Python Docstring Generator** | Nils Werner | Gerar docstrings |

**Como instalar:**
1. Clique no ícone **Extensions** (ou Ctrl+Shift+X)
2. Digite o nome da extensão
3. Clique em **Install**

---

## 2. Configurar Ambiente Python no VSCode

### 2.1 Criar e Ativar Virtual Environment

**Windows (PowerShell):**
```
# Criar venv
python -m venv venv

# Ativar
.\venv\Scripts\Activate.ps1
```

**macOS/Linux:**
```
# Criar venv
python3 -m venv venv

# Ativar
source venv/bin/activate
```

### 2.2 Selecionar Interpretador Python no VSCode

1. Pressione **Ctrl+Shift+P** (Command Palette)
2. Digite: **Python: Select Interpreter**
3. Escolha o caminho da venv criada (ex: `./venv/bin/python`)

**Verificação:** No canto inferior direito do VSCode, deve aparecer o caminho da venv.

### 2.3 Instalar Bibliotecas Necessárias

No terminal integrado do VSCode (Ctrl+`), execute:

```
pip install pandas numpy scikit-learn luigi matplotlib seaborn requests openpyxl sqlalchemy
```

---

## 3. Criar Projeto ETL no VSCode

### 3.1 Estrutura de Pastas

```
projeto-etl/
├── venv/                      # Virtual environment
├── data/
│   ├── raw/                   # Dados brutos
│   └── processed/             # Dados processados
├── src/
│   ├── __init__.py
│   ├── extract.py
│   ├── transform.py
│   └── load.py
├── notebooks/
│   └── exploracao.ipynb       # Análise exploratória
├── logs/
│   └── pipeline.log           # Logs de execução
├── requirements.txt           # Dependências
├── config.py                  # Configurações
└── main.py                    # Script principal
```

### 3.2 Criar Arquivos no VSCode

**File > New File** ou **Ctrl+N**

**requirements.txt:**
```
pandas==2.0.3
numpy==1.24.3
scikit-learn==1.3.0
luigi==3.4.0
requests==2.31.0
sqlalchemy==2.0.20
openpyxl==3.1.2
matplotlib==3.7.2
seaborn==0.12.2
```

**config.py:**
```
# Configurações do projeto
import os

# Caminhos
BASE_DIR = os.path.dirname(os.path.abspath(__file__))
DATA_RAW = os.path.join(BASE_DIR, 'data', 'raw')
DATA_PROCESSED = os.path.join(BASE_DIR, 'data', 'processed')
LOGS_DIR = os.path.join(BASE_DIR, 'logs')

# Banco de dados
DATABASE_URL = 'postgresql://user:password@localhost/database'

# Configurações gerais
DEBUG = True
```

---

## 4. Desenvolvendo Scripts ETL no VSCode

### 4.1 Exemplo: extract.py

**File > New File** > `src/extract.py`

```
import pandas as pd
import requests
from sqlalchemy import create_engine
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def extrair_csv(caminho: str) -> pd.DataFrame:
    """Extrai dados de arquivo CSV"""
    try:
        df = pd.read_csv(caminho)
        logger.info(f"Arquivo {caminho} carregado. Shape: {df.shape}")
        return df
    except Exception as e:
        logger.error(f"Erro ao carregar CSV: {e}")
        return None

def extrair_api(url: str) -> pd.DataFrame:
    """Extrai dados de API REST"""
    try:
        response = requests.get(url)
        response.raise_for_status()
        data = response.json()
        df = pd.DataFrame(data)
        logger.info(f"API {url} carregada. Shape: {df.shape}")
        return df
    except Exception as e:
        logger.error(f"Erro ao carregar API: {e}")
        return None

def extrair_sql(query: str, engine) -> pd.DataFrame:
    """Extrai dados de banco SQL"""
    try:
        df = pd.read_sql(query, engine)
        logger.info(f"Query executada. Shape: {df.shape}")
        return df
    except Exception as e:
        logger.error(f"Erro ao executar query: {e}")
        return None
```

**Atalhos úteis no VSCode:**
- **Ctrl+Space** — Autocompletar
- **Ctrl+/** — Comentar linhas
- **Alt+Up/Down** — Mover linhas
- **Ctrl+D** — Selecionar próxima ocorrência

### 4.2 Exemplo: transform.py

**File > New File** > `src/transform.py`

```
import pandas as pd
import numpy as np
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def limpar_dados(df: pd.DataFrame) -> pd.DataFrame:
    """Limpa e valida dados"""
    
    logger.info("Iniciando limpeza de dados...")
    
    # Remover duplicatas
    df_limpo = df.drop_duplicates()
    logger.info(f"Duplicatas removidas. Shape: {df_limpo.shape}")
    
    # Remover nulos críticos
    colunas_criticas = ['id', 'valor']
    df_limpo = df_limpo.dropna(subset=colunas_criticas)
    logger.info(f"Nulos críticos removidos. Shape: {df_limpo.shape}")
    
    # Preencher nulos opcionais
    df_limpo['descricao'].fillna('Sem descrição', inplace=True)
    
    return df_limpo

def converter_tipos(df: pd.DataFrame) -> pd.DataFrame:
    """Converte tipos de dados"""
    
    logger.info("Convertendo tipos de dados...")
    
    # Datas
    colunas_data = df.select_dtypes(include=['object']).columns
    for col in colunas_data:
        if 'data' in col.lower():
            df[col] = pd.to_datetime(df[col], errors='coerce')
    
    # Números
    df['valor'] = pd.to_numeric(df['valor'], errors='coerce')
    
    logger.info("Tipos convertidos com sucesso")
    return df

def criar_features(df: pd.DataFrame) -> pd.DataFrame:
    """Cria novas features"""
    
    logger.info("Criando features...")
    
    if 'data' in df.columns:
        df['ano'] = df['data'].dt.year
        df['mes'] = df['data'].dt.month
        df['dia_semana'] = df['data'].dt.dayofweek
    
    logger.info("Features criadas")
    return df

def remover_outliers(df: pd.DataFrame, coluna: str) -> pd.DataFrame:
    """Remove outliers usando IQR"""
    
    Q1 = df[coluna].quantile(0.25)
    Q3 = df[coluna].quantile(0.75)
    IQR = Q3 - Q1
    
    df_filtrado = df[
        (df[coluna] >= Q1 - 1.5*IQR) & 
        (df[coluna] <= Q3 + 1.5*IQR)
    ]
    
    removidos = len(df) - len(df_filtrado)
    logger.info(f"Outliers removidos: {removidos}")
    
    return df_filtrado

def pipeline_transformacao(df: pd.DataFrame) -> pd.DataFrame:
    """Executa pipeline completo"""
    
    df = limpar_dados(df)
    df = converter_tipos(df)
    df = criar_features(df)
    
    logger.info("Pipeline de transformação concluído")
    return df
```

### 4.3 Exemplo: load.py

**File > New File** > `src/load.py`

```
import pandas as pd
import logging
from sqlalchemy import create_engine

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def salvar_csv(df: pd.DataFrame, caminho: str):
    """Salva dados em CSV"""
    try:
        df.to_csv(caminho, index=False)
        logger.info(f"Dados salvos em {caminho}")
    except Exception as e:
        logger.error(f"Erro ao salvar CSV: {e}")

def salvar_parquet(df: pd.DataFrame, caminho: str):
    """Salva dados em Parquet (mais eficiente)"""
    try:
        df.to_parquet(caminho)
        logger.info(f"Dados salvos em {caminho}")
    except Exception as e:
        logger.error(f"Erro ao salvar Parquet: {e}")

def salvar_sql(df: pd.DataFrame, tabela: str, engine):
    """Salva dados em banco SQL"""
    try:
        df.to_sql(tabela, engine, if_exists='append', index=False)
        logger.info(f"Dados inseridos na tabela {tabela}")
    except Exception as e:
        logger.error(f"Erro ao inserir em SQL: {e}")

def salvar_multiplos(df: pd.DataFrame, nome_base: str):
    """Salva em múltiplos formatos"""
    salvar_csv(df, f'{nome_base}.csv')
    salvar_parquet(df, f'{nome_base}.parquet')
```

---

## 5. Executar Scripts no VSCode

### 5.1 Executar Script Python Diretamente

**Opção 1: Usando o Play Button**
1. Abra o arquivo `.py`
2. Clique no ícone **▶ Run** (canto superior direito)

**Opção 2: Pelo Terminal Integrado**
1. Abra o terminal: **Ctrl+`**
2. Execute: `python src/extract.py`

**Opção 3: Debug**
1. Pressione **F5** para ativar debugger
2. Coloque breakpoints (clique na linha)
3. Use a barra de debug para step/continue

### 5.2 Executar com Argumentos

```
# main.py
import sys
import argparse

parser = argparse.ArgumentParser()
parser.add_argument('--arquivo', type=str, default='dados.csv')
parser.add_argument('--debug', action='store_true')

args = parser.parse_args()

if __name__ == '__main__':
    print(f"Processando: {args.arquivo}")
```

**No terminal:**
```
python main.py --arquivo dados.csv --debug
```

---

## 6. Usar Jupyter Notebooks no VSCode

### 6.1 Criar Notebook

1. **File > New File** > selecione **Jupyter Notebook** ou **Ctrl+Shift+P** > **Create: New Jupyter Notebook**
2. Ou clique em **+ New file** na aba Explorer e renomeie para `.ipynb`

### 6.2 Estrutura do Notebook

```
# Célula 1: Importações
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Célula 2: Carregar dados
df = pd.read_csv('dados/raw/vendas.csv')
df.head()

# Célula 3: Análise exploratória
df.describe()

# Célula 4: Visualização
plt.figure(figsize=(10, 5))
df['valor'].hist()
plt.title('Distribuição de Valores')
plt.show()
```

**Atalhos:**
- **Shift+Enter** — Executar célula
- **Ctrl+Enter** — Executar sem avançar
- **Alt+Enter** — Executar e criar célula abaixo

---

## 7. Executar Pipeline Luigi no VSCode

### 7.1 Criar pipeline_luigi.py

```
import luigi
import pandas as pd
import sys
import logging

# Configurar logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s'
)

class ExtrairDados(luigi.Task):
    def output(self):
        return luigi.LocalTarget('data/raw/dados.csv')
    
    def run(self):
        df = pd.DataFrame({
            'id': ,
            'valor':[1]
        })
        df.to_csv(self.output().path, index=False)
        print("✓ Extração concluída")

class TransformarDados(luigi.Task):
    def requires(self):
        return ExtrairDados()
    
    def output(self):
        return luigi.LocalTarget('data/processed/dados_transformados.csv')
    
    def run(self):
        df = pd.read_csv(self.input().path)
        df['valor_dobrado'] = df['valor'] * 2
        df.to_csv(self.output().path, index=False)
        print("✓ Transformação concluída")

class CarregarDados(luigi.Task):
    def requires(self):
        return TransformarDados()
    
    def output(self):
        return luigi.LocalTarget('data/processed/final.csv')
    
    def run(self):
        df = pd.read_csv(self.input().path)
        df.to_csv(self.output().path, index=False)
        print("✓ Carregamento concluído")

if __name__ == '__main__':
    luigi.build([CarregarDados()], local_scheduler=True)
```

### 7.2 Executar Pipeline

**No Terminal do VSCode:**
```
python pipeline_luigi.py
```

**Com visualização do grafo:**
```
python pipeline_luigi.py --graph-format svg > pipeline.svg
```

---

## 8. Usar Git no VSCode para Versionamento

### 8.1 Inicializar Repositório

1. Abra o terminal: **Ctrl+`**
2. Execute: `git init`
3. Crie `.gitignore`:

```
venv/
__pycache__/
*.pyc
.DS_Store
.env
data/raw/
logs/
*.csv
*.parquet
```

### 8.2 Commits e Push

1. Clique em **Source Control** (Ctrl+Shift+G)
2. Escreva mensagem de commit
3. Clique em **✓** para confirmar
4. Use **Git Graph** para visualizar histórico

---

## 9. Dicas Produtivas no VSCode

### 9.1 Atalhos Essenciais

| Atalho | Ação |
|--------|------|
| **Ctrl+Shift+P** | Command Palette |
| **Ctrl+`** | Terminal integrado |
| **Ctrl+F** | Encontrar |
| **Ctrl+H** | Substituir |
| **Ctrl+D** | Selecionar palavra |
| **Alt+Shift+F** | Formatar código |
| **F5** | Debugger |
| **Ctrl+,** | Configurações |

### 9.2 Formatação Automática

Instale **Prettier** ou **Black** e configure em `settings.json`:

```
{
    "python.linting.enabled": true,
    "python.formatting.provider": "black",
    "[python]": {
        "editor.defaultFormatter": "ms-python.python",
        "editor.formatOnSave": true
    }
}
```

### 9.3 Debugging

1. Coloque **breakpoint** (clique na linha)
2. Pressione **F5**
3. Use **Watch** para monitorar variáveis
4. Use **Debug Console** para executar código

---

## 10. Exemplo Completo: Executar ETL Completo

**main.py:**
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import sys
import os
sys.path.insert(0, os.path.dirname(__file__))

import pandas as pd
from src.extract import extrair_csv
from src.transform import pipeline_transformacao
from src.load import salvar_csv, salvar_parquet
import logging

# Configurar logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s'
)
logger = logging.getLogger(__name__)

def main():
    logger.info("=" * 50)
    logger.info("Iniciando Pipeline ETL")
    logger.info("=" * 50)
    
    # EXTRACT
    logger.info("\n[1/3] EXTRACT")
    df = extrair_csv('data/raw/vendas.csv')
    if df is None:
        logger.error("Falha na extração")
        return
    
    # TRANSFORM
    logger.info("\n[2/3] TRANSFORM")
    df = pipeline_transformacao(df)
    
    # LOAD
    logger.info("\n[3/3] LOAD")
    salvar_csv(df, 'data/processed/vendas_processadas.csv')
    salvar_parquet(df, 'data/processed/vendas_processadas.parquet')
    
    logger.info("\n" + "=" * 50)
    logger.info("Pipeline concluído com sucesso!")
    logger.info("=" * 50)

if __name__ == '__main__':
    main()
```

**Executar no VSCode:**
```
# Terminal integrado (Ctrl+`)
python main.py
```

---

## 📋 Checklist de Configuração

- ✅ VSCode instalado
- ✅ Extensão Python instalada
- ✅ Virtual environment criado e ativado
- ✅ Dependências instaladas (`pip install -r requirements.txt`)
- ✅ Interpretador Python selecionado
- ✅ Estrutura de pastas criada
- ✅ Git inicializado
- ✅ Primeiro script executado com sucesso

---

## 🔗 Recursos Recomendados

- [VSCode Python Documentation](https://code.visualstudio.com/docs/languages/python)
- [Pandas Getting Started](https://pandas.pydata.org/getting_started/index.html)
- [Luigi Tutorials](https://luigi.readthedocs.io/en/stable/index.html)
- [Git no VSCode](https://code.visualstudio.com/docs/sourcecontrol/overview)

---

[⬅️ Voltar ao Índice do Módulo](README.md)