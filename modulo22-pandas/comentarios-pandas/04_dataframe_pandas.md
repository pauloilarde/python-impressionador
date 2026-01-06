# DataFrames em Pandas - Resumo da Aula

## 📚 Conceito Principal

Um DataFrame é como uma tabela do pandas, onde:

- **Colunas** funcionam como "chaves de dicionário"
- **Linhas** funcionam como "listas"

## 🔧 Sintaxe e Formas de Acesso

### Acessando Colunas

```python
# Uma única coluna (retorna um DataFrame com 1 coluna)
vendas_df['ID Cliente']

# Múltiplas colunas (cria novo DataFrame filtrado)
vendas_df[['Numero da Venda', 'Data da Venda', 'ID Produto']]
```

### Acessando Linhas

```python
# ❌ NÃO FUNCIONA: vendas_df[0]
# Isso gera KeyError, pois DataFrames não funcionam como listas

# ✅ Slicing funciona:
vendas_df[:0]  # Retorna apenas o cabeçalho
vendas_df[:3]  # Retorna até a linha de índice 3 (incluindo cabeçalho)
```

### Combinando Acesso (Coluna + Linha)

```python
# Pega o item da 1ª linha da coluna 'ID Produto'
vendas_df['ID Produto'][0]  # Retorna: np.int64(981)
```

## 📊 Método .info() - Entendendo seu DataFrame

O primeiro passo em qualquer análise de dados é **entender o que existe na base**. Use o método `.info()`:

```python
vendas_df.info()
```

### Saída do .info():

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 980642 entries, 0 to 980641
Data columns (total 10 columns):
 #   Column                Non-Null Count   Dtype
---  ------                --------------   -----
 0   Numero da Venda       980642 non-null  int64
 1   Data da Venda         980642 non-null  object
 2   Data do Envio         980642 non-null  object
 3   ID Canal              980642 non-null  int64
 4   ID Loja               980642 non-null  int64
 5   ID Produto            980642 non-null  int64
 6   ID Promocao           980642 non-null  int64
 7   ID Cliente            980642 non-null  int64
 8   Quantidade Vendida    980642 non-null  int64
 9   Quantidade Devolvida  980642 non-null  int64
dtypes: int64(8), object(2)
memory usage: 74.8+ MB
```

**Informações fornecidas:**

- Número total de entradas (linhas)
- Quantidade de colunas
- Nome de cada coluna
- Quantidade de valores não-nulos
- Tipo de dado (Dtype)
- Uso de memória

## 💡 Aplicações Práticas

### Exemplo 1: Criando Lista de Clientes

```python
lista_clientes = vendas_df['ID Cliente']
# Retorna uma Series com todos os IDs de clientes
```

### Exemplo 2: DataFrame Filtrado de Produtos

```python
# Criar um DataFrame apenas com informações de produtos
produtos_quantidade = vendas_df[[
    'ID Produto',
    'Quantidade Vendida',
    'Quantidade Devolvida'
]]
```

**Resultado**: Novo DataFrame com 980.642 linhas × 3 colunas, focado apenas em dados de produtos.

## ⚠️ Armadilhas Comuns

### 1. Espaços em Nomes de Colunas

```python
# ❌ ERRO: espaços extras causam KeyError
vendas_df[['Quantidade Vendida ', 'Quantidade Devolvida ']]
# KeyError: "['Quantidade Vendida ', 'Quantidade Devolvida '] not in index"

# ✅ CORRETO: nome exato da coluna
vendas_df[['Quantidade Vendida', 'Quantidade Devolvida']]
```

### 2. Tentativa de Acesso por Índice Numérico

```python
# ❌ NÃO FUNCIONA
vendas_df[0]  # KeyError: 0

# ✅ USE SLICING
vendas_df[:1]  # Retorna a primeira linha
```

### 3. Espaços no Nome do Arquivo

```python
# ❌ Pode dar erro se o nome tiver espaços extras
pd.read_csv('Contoso - Vendas  - 2017.csv', sep=';')

# ✅ Verifique o nome exato do arquivo
pd.read_csv('Contoso - Vendas - 2017.csv', sep=';')
```

## 🎯 Visualização de DataFrames

**Para DataFrames pequenos** (poucas colunas):

- Simplesmente digite o nome do DataFrame: `vendas_df`
- Ele exibe a tabela formatada completa

**Para DataFrames grandes** (muitas colunas):

- O pandas ajusta automaticamente a visualização
- Use `.info()` para ter uma visão geral estruturada
- Use `.head()` para ver as primeiras linhas

## 📖 Recursos Adicionais

**Documentação do .info():**  
[pandas.DataFrame.info](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.info.html)

## 🔄 Conceitos-Chave para Lembrar

1. **DataFrame = Tabela** (linhas × colunas)
2. **Colunas são acessadas por nome** (como chaves de dicionário)
3. **Use .info() primeiro** para entender seus dados
4. **Filtrar colunas cria um novo DataFrame** (não modifica o original)
5. **Nomes de colunas devem ser exatos** (cuidado com espaços)

---

**Base de Dados Utilizada**: Contoso - Vendas 2017 (980.642 registros × 10 colunas)
