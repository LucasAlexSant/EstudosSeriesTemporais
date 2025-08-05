## 🧩 Conceito: **Plots de Série Temporal (Visualização de Dados Temporais)**

---

### 1. **O que é?**

São **gráficos usados para visualizar como os dados mudam ao longo do tempo**. Eles permitem identificar tendências, ciclos, sazonalidades, [[Outliers]] e mudanças estruturais de forma intuitiva e rápida.

---

### 2. **Para que serve? (Função/Objetivo)**

- **Entender o comportamento da série**
    
- **Identificar padrões temporais** (tendência, sazonalidade, rupturas)
    
- **Detectar outliers e anomalias**
    
- **Ajudar na escolha de modelos e pré-processamentos**
    
- **Comunicar resultados de forma clara e impactante**
    

---

### 3. **Como funciona? (Principais mecanismos ou estrutura)**

### 🔹 1. **Gráfico de linha simples**

O mais comum: exibe os valores no eixo Y ao longo do tempo no eixo X.

![[Pasted image 20250803192521.png]]

---

### 🔹 2. **Gráfico com suavização**

Exibe a linha da série e uma média móvel.

![[Pasted image 20250803192740.png]]

---

### 🔹 3. **Gráfico com múltiplas séries**

Para comparar variáveis ao longo do tempo (ex: vendas x visitas)

![[Pasted image 20250803193254.png]]

---

### 🔹 4. **Gráfico de decomposição**

Mostra **tendência, sazonalidade e ruído** separados.

![[Pasted image 20250803193351.png]]

---

### 🔹 5. **Boxplot por tempo (mês, dia da semana, etc.)**

Ajuda a identificar **distribuições sazonais**.

![[Pasted image 20250803193448.png]]

---

### 🔹 6. **Heatmap temporal**

Visualiza padrões de volume ao longo do tempo.

![[Pasted image 20250803194145.png]]

---

### 4. **Exemplos práticos**

| Tipo de plot         | Quando usar                               |
| -------------------- | ----------------------------------------- |
| Linha simples        | Análise geral da série                    |
| Linha + média móvel  | Ver tendências escondidas no ruído        |
| Decomposição         | Separar tendências e sazonalidade         |
| Boxplot por mês      | Detectar sazonalidade ou efeitos mensais  |
| Heatmap por hora/dia | Identificar padrões sazonais intradiários |
| Multisséries         | Comparar métricas simultaneamente         |

---

### 5. **Importância e impactos**

- Permite **exploração de dados antes da modelagem (EDA)**
    
- Reduz a chance de erro por **modelar padrões que são na verdade outliers**
    
- Torna o resultado **comunicável para equipes e stakeholders**
    
- Ajuda a **validar se o modelo está acompanhando a tendência real**
    

---

### 6. **Conexões com outros conceitos**

- **Decomposição e componentes**: pode ser visualizado diretamente
    
- **Sazonalidade e granularidade**: guiados por visualizações como boxplots e heatmaps
    
- **Suavização e rolling**: usados para enriquecer visualizações
    
- **Outliers e rupturas**: geralmente detectados via gráfico
    

---

### 7. **Resumo pessoal (reflexão final)**

> “Se os números contam a história, os plots são as ilustrações. E em séries temporais, elas mostram capítulos que você nem sabia que existiam.”

---

### 🧠 Bônus:

**Dicas de boas práticas:**

- Sempre coloque `grid`, `labels`, `title`, `legend`
    
- Evite exagerar no número de linhas — simplifique!
    
- Prefira **resample** para suavizar séries muito densas
    
- Use `seaborn` ou `plotly` para visualizações mais interativas
    

**Erros comuns:**  
⚠️ Não ordenar por data antes de plotar  
⚠️ Usar séries com frequências diferentes sem tratamento  
⚠️ Ignorar valores ausentes que distorcem a linha