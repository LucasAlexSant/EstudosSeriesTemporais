
**Clusterizar múltiplas séries temporais** para encontrar grupos de séries com comportamentos semelhantes.

---

## ✅ Lista de Tarefas (passo a passo)

---

### 🔹 Etapa 1: Preparação dos Dados

- [ ]  Definir de onde virão as múltiplas séries (arquivos diferentes? várias colunas no mesmo CSV?)
- [ ] Padronizar as séries para todas seguirem o mesmo formato de tempo e frequência (ex: diário) 
- [ ] Unificar todas as séries em um único `DataFrame` no formato:

### 📁 Exemplo de estrutura inicial:

| Date       | Serie_A | Serie_B | Serie_C |
| ---------- | ------- | ------- | ------- |
| 2009-01-01 | 100.2   | 120.1   | 98.2    |
| 2009-01-02 | 103.4   | 119.8   | 100.4   |

id ,      ,time  ,      value
Serie_A  2013-01-01   123.4
Serie_A  2013-01-02   124.8
Serie_B  2013-01-01   89.7

---

### 🔹 Etapa 2: Vetorização com `tsfresh`

- [ ]  Instalar as libs necessárias (`tsfresh`, `pandas`, `scikit-learn`, etc.)  
- [ ]  Rodar `extract_features()` com `column_id='id'` e `column_sort='time'`  
- [ ] Remover colunas com `NaN` do resultado  
- [ ]  Exportar os vetores para CSV (backup ou para análises externas)

---

### 🔹 Etapa 3: Clusterização

- [ ]  Normalizar os dados (ex: com `StandardScaler` ou `MinMaxScaler`)  
- [ ] Reduzir a dimensionalidade com `PCA` ou `UMAP` para visualização e performance  
- [ ]  Aplicar `KMeans`, `DBSCAN` ou `AgglomerativeClustering`  
- [ ]  Determinar número ideal de clusters (ex: usando `elbow method`, `silhouette score`)

---

### 🔹 Etapa 4: Visualização e Interpretação

- [ ] Plotar os clusters em 2D (usando o resultado do PCA ou UMAP)  
- [ ] Identificar padrões dentro dos clusters (ex: séries com tendência de alta, picos, ruídos)  
- [ ] (Opcional) Plotar exemplos reais de séries de cada grupo para visualização direta

---

### 🔹 Etapa 5: Alternativas Futuras (Exploração Avançada)

- [ ] Testar clustering com `DTW` usando a lib `tslearn`  
- [ ] Testar modelos autoencoder (LSTM/VAE) para gerar representações vetoriais mais abstratas  
- [ ] Criar pipeline automatizado para inserir novas séries e atualizar os clusters