## 🧠📈 DOMÍNIO PROFUNDO EM SÉRIES TEMPORAIS — ROTEIRO COMPLETO

---

### 📌 1. **Fundamentos (se consolidar aqui é essencial)**

- O que é uma série temporal
    
- Componentes:
    
    - Tendência
        
    - Sazonalidade
        
    - Ciclo
        
    - Ruído
        
- Tipos de séries: univariadas vs multivariadas
    
- Frequência e granularidade (minuto, hora, dia, mês…)
    
- Estacionariedade (por que é importante e como testar)
    
- Decomposição (additiva e multiplicativa)
    

📚 Estude:

- `pandas` para manipular datas
    
- `statsmodels.tsa.seasonal_decompose`
    

---

### ⚙️ 2. **Pré-processamento de séries temporais**

- Parseamento de datas (`pd.to_datetime`)
    
- Criação de features temporais (dia da semana, mês, feriado etc.)
    
- **Lags** e **janelas móveis (rolling windows)**
    
- Resampling (mudança de frequência: `resample()`)
    
- Suavização (ex: média móvel, exponencial)
    

📚 Ferramentas:

- `pandas`, `numpy`, `scikit-learn`, `holidays` (para features especiais)
    

---

### 🧪 3. **Análise exploratória específica**

- Plots de série temporal
    
- Autocorrelação (ACF) e autocorrelação parcial (PACF)
    
- Deteção de anomalias
    
- Histogramas por estação/ano/mês
    
- Correlação cruzada (cross-correlation)
    

📚 Ferramentas:

- `matplotlib`, `seaborn`, `statsmodels.graphics.tsaplots`
    

---

### 🧠 4. **Modelos Clássicos (estatísticos)**

- Modelos AR, MA, ARMA, ARIMA, SARIMA
    
- Modelos para séries estacionárias e não estacionárias
    
- Modelagem de sazonalidade e tendência
    
- Validação cruzada em série temporal (com `TimeSeriesSplit` do sklearn)
    

📚 Ferramentas:

- `statsmodels.tsa`, `pmdarima` (auto-arima), `scikit-learn`
    

---

### ⛏️ 5. **Modelos baseados em Machine Learning**

- Regressão (com features criadas de lags/janelas)
    
- Random Forest e XGBoost para séries temporais
    
- LightGBM + feature engineering temporal
    
- Prophet (do Facebook): fácil, poderoso e interpretável
    

📚 Ferramentas:

- `prophet`, `xgboost`, `lightgbm`, `scikit-learn`, `catboost`
    

---

### 🧠🔮 6. **Deep Learning para séries temporais**

- RNN (Recurrent Neural Networks)
    
- LSTM e GRU (para dependências longas)
    
- CNN para séries (sim, funciona!)
    
- Temporal Fusion Transformer (TFT – modelo SOTA)
    
- Attention Mechanisms em séries
    
- Encoder-decoder architectures
    

📚 Frameworks:

- `TensorFlow`, `Keras`, `PyTorch`, `Darts`, `GluonTS`, `Nixtla`
    

---

### 🧮 7. **Métricas e avaliação**

- MAE, MSE, RMSE
    
- MAPE, sMAPE, WAPE
    
- Backtesting e forecast horizon
    
- Cross-validation temporal
    

---

### 🗂️ 8. **Modelos probabilísticos e Bayesian**

- Modelos bayesianos para incerteza em previsão
    
- Kalman Filter, Hidden Markov Models
    
- Prophet com incerteza (interv. bayesianos)
    

---

### 💾 9. **Bancos e Armazenamento de Séries Temporais**

- InfluxDB, TimescaleDB, Prometheus
    
- Formatos ideais de armazenamento (parquet, feather)
    
- APIs de coleta automática (sensors, logs etc.)
    

---

### 📊 10. **Visualização e dashboards**

- Gráficos de linha interativos (Plotly, Altair)
    
- Dashboards em **Streamlit** ou **Grafana**
    
- Alertas em tempo real (via API ou webhook)
    

---

### 🧪 11. **Aplicações práticas e casos reais**

- Previsão de vendas e demanda
    
- Previsão de energia elétrica
    
- Detecção de fraudes
    
- Análise de logs e falhas em servidores
    
- Previsão de tráfego em redes sociais ou web
    

---

### 📎 12. **Desafios e boas práticas**

- Lidar com dados faltantes (interpolação, imputação)
    
- Series com múltiplas entradas (multivariate)
    
- Series de alta frequência (ex: segundos)
    
- Escalonamento correto (min-max, z-score por série, etc.)
    

---

### 🛠️ Ferramentas úteis pra montar seu ambiente:

- `JupyterLab` + `nbextensions`
    
- `MLflow` ou `Weights & Biases` para experiment tracking
    
- `DVC` (Data Version Control)
    
- Git + GitHub + README bem documentado
    
- Streamlit ou Gradio para deploy de modelos
    

---

## 🚀 Recursos para estudar:

### 📚 Cursos e materiais:

- Time Series with Python - Datacamp
    
- [Time Series Forecasting – Coursera (Prof. Rob Hyndman)](https://www.coursera.org/learn/time-series)
    
- Livro: **"Forecasting: Principles and Practice"** (Grátis do Hyndman)
    
- Livro: **“Deep Learning for Time Series Forecasting”** - Jason Brownlee
    
- Blog da Nixtla (avançado e atualizado)