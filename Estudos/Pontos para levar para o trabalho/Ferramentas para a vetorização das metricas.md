## 🔝 **Principais bibliotecas para extração de features temporais**

---

### 1. **📦 tsfresh** (A que vamos Utilizar)

> **Melhor para:** Extração automática de centenas de features estatísticas.

- - Extração massiva (média, skew, entropia, autocorrelação, etc.)
        
- - Compatível com dados multivariados
        
- - Pode usar filtros de relevância (feature selection automática)
        
- 🔻 Levemente lento em grandes datasets
    


`pip install tsfresh`

---

### 2. **📦 Kats (by Facebook/Meta)**

> **Melhor para:** Pipelines completos de séries temporais + análise rápida + modelos + features.

- - Extrai estatísticas + detecta tendências/sazonalidades
        
- - Detecta mudanças, outliers, etc.
        
- - Fácil integração com modelos de forecasting
        
- 🔻 Ainda em evolução; exige `prophet` e outras dependências
    

bash

`pip install kats`

---

### 3. **📦 tsflex**

> **Melhor para:** Grandes volumes de dados, alta performance.

- - Usa pandas + numpy para extrair features
        
- - Super flexível com sliding windows
        
- 🔻 Pouco menos “automático” que tsfresh
    

bash

`pip install tsflex`

---

### 4. **📦 catch22**

> **Melhor para:** Conjunto reduzido de 22 features estatísticas mais relevantes.

- - Rápido, eficiente e interpretável
        
- - Muito usado com classificadores e clusters
        
- 🔻 Limitado a 22 features (por design)
    

bash


`pip install catch22`

---

### 5. **📦 hctsa (via R ou MATLAB)**

> **Melhor para:** Pesquisas científicas com milhares de features

- - Milhares de medidas matemáticas e estatísticas
        
- 🔻 Não é nativo de Python (tem bindings limitados)
    
- 🔻 Muito pesado para uso prático em escala
    

---

### 6. **📦 pycatch22 (wrapper do catch22)**

> Versão python do `catch22`, fácil de usar:

bash

`pip install pycatch22`

---

### 7. **📦 sktime**

> **Melhor para:** Pipeline completo + modelos + pré-processamento + vetorização

- - Integra transformadores + classificadores
        
- - Integra catch22, tsfresh, etc.
        
- 🔻 Leva tempo para dominar
    

bash


`pip install sktime`



### Comparação rápida:

| Lib     | Nº de Features | Customizável | Performance | Facilidade |
| ------- | -------------- | ------------ | ----------- | ---------- |
| tsfresh | 100+           | Alta         | Média       | Média      |
| catch22 | 22             | Baixa        | Alta        | Alta       |
| kats    | 50+            | Média        | Alta        | Alta       |
| tsflex  | Custom         | Muito Alta   | Alta        | Média      |
| sktime  | Depende        | Alta         | Média       | Média      |
