# Pandas e CSV - Resumo da Aula

## 📚 Conceito Principal

O pandas é a biblioteca mais prática e eficiente para ler arquivos CSV em Python, oferecendo organização e facilidade de uso superiores às alternativas.

## 🔧 Funcionamento Básico

### Sintaxe Fundamental

```python
import pandas as pd
dataframe = pd.read_csv('arquivo.csv')
```

### Exemplo Prático com Base Real

Trabalhamos com a base de dados de vendas da empresa "Contoso":

```python
vendas_df = pd.read_csv('Contoso - Vendas - 2017.csv', sep=';')
display(vendas_df)

produtos_df = pd.read_csv('Contoso - Cadastro Produtos.csv', sep=';')
display(produtos_df)
```

## ⚙️ Parâmetros Importantes

### Separador (sep)

- **Problema**: Arquivos CSV podem usar vírgula (,) ou ponto e vírgula (;) como separador
- **Solução**: Especificar o parâmetro `sep=';'` quando necessário
- **Resultado**: Dados ficam organizados em colunas adequadamente

### Sem o separador correto:

❌ Dados aparecem em uma única coluna desorganizada

### Com o separador correto:

✅ Dados estruturados em múltiplas colunas (ex: 980.642 linhas × 10 colunas)

## 📁 Gerenciamento de Caminhos

### Opção 1: Mesma Pasta

Manter o notebook Jupyter e o arquivo CSV no mesmo diretório.

### Opção 2: Caminho Completo

Quando os arquivos estão em pastas diferentes:

```python
# Sem raw string (pode dar problema com caracteres especiais)
vendas_df = pd.read_csv('C:\Users\Fulano\Documents\arquivo.csv')

# Com raw string (RECOMENDADO)
vendas_df = pd.read_csv(r'C:\Users\Fulano\Documents\arquivo.csv')
```

**Dica**: Use o prefixo `r` antes do caminho para criar uma _raw string_, evitando problemas com caracteres de escape (como `\n`, `\t`).

## 📊 Visualização dos Dados

### print() vs display()

```python
# Visualização simples
print(vendas_df)

# Visualização formatada e mais agradável
display(vendas_df)
```

**Recomendação**: Use `display()` em notebooks Jupyter para melhor apresentação visual dos DataFrames.

## 🎯 Conceitos-Chave

**DataFrame**: Objeto do pandas que representa dados em formato tabular (linhas e colunas), similar a uma planilha Excel.

O pandas automaticamente mostra informações úteis:

- Número de linhas e colunas
- Estrutura dos dados
- Primeiras e últimas entradas

## 💡 Próximos Passos

Nas próximas aulas, aprenderemos a:

- Selecionar colunas específicas
- Filtrar linhas
- Manipular e transformar dados
- Realizar análises mais avançadas

---

**Base de Dados Utilizada**: Contoso - Vendas 2017 (980.642 registros de vendas com 10 atributos cada)
