## 🧩 Conceito: **Lags e Janelas Móveis (Rolling Windows)**

---

### 1. **O que é?**

- **Lag**: é o valor da série em um **tempo anterior**. Por exemplo, o valor de ontem, da semana passada, do mês anterior.
    
- **Janela móvel** (rolling window): é uma **média (ou outro cálculo) feita com base em um intervalo de tempo anterior**, que vai se movendo ao longo da série.
    

---

### 2. **Para que serve? (Função/Objetivo)**

- Permitir que **modelos preditivos usem o passado para prever o futuro**
    
- Capturar padrões de dependência temporal e **autocorrelação**
    
- Suavizar flutuações aleatórias com médias móveis
    
- Transformar a série em um **problema supervisionado**, com `X = lags` e `y = valor atual ou futuro`
    

---

### 3. **Como funciona? (Principais mecanismos ou estrutura)**

#### 🔹 Lags

python
`df['lag_1'] = df['valor'].shift(1)`
`df['lag_7'] = df['valor'].shift(7)  # uma semana atrás`

#### 🔹 Janelas móveis

`python`
`df['media_movel_3'] = df['valor'].rolling(window=3).mean()`
`df['desvio_movel_5'] = df['valor'].rolling(window=5).std()`


📌 Dica: Combine ambos!

python
`df['lag_3_media_3'] = df['valor'].shift(3).rolling(window=3).mean()`

---

### 4. **Exemplos práticos**

| Técnica                      | Exemplo                  | Interpretação                   |
| ---------------------------- | ------------------------ | ------------------------------- |
| `lag_1`                      | Vendas de ontem          | Influência direta do último dia |
| `lag_7`                      | Vendas da semana passada | Ciclo semanal                   |
| `rolling(7).mean()`          | Média móvel de 7 dias    | Suaviza ruídos diários          |
| `rolling(30).std()`          | Volatilidade do mês      | Ajuda a detectar anomalias      |
| `shift(1).rolling(3).mean()` | Média móvel do passado   | Usa histórico para prever       |

---

### 5. **Importância e impactos**

- Transforma séries temporais em **matriz de features X** para algoritmos de ML
    
- Pode melhorar **drasticamente a performance de modelos supervisionados** (XGBoost, LightGBM, etc.)
    
- Ajuda a capturar **comportamentos de repetição, sazonalidade e tendência local**
    
- É a base para **modelos autoregressivos (AR, ARIMA, etc.)**
    

---

### 6. **Conexões com outros conceitos**

- **Autocorrelação (ACF)**: ajuda a escolher os melhores lags
    
- **Estacionariedade**: lags ajudam a diferenciar e tornar estacionário
    
- **Feature engineering temporal**: lags e médias móveis viram variáveis preditoras
    
- **Validação temporal**: lags devem sempre respeitar o tempo (sem dados futuros)
    

---

### 7. **Resumo pessoal (reflexão final)**

> “Lags e janelas móveis são como olhar no retrovisor antes de dirigir: eles mostram o que já passou, e isso nos ajuda a prever o que vem pela frente.”

---

### 🧠 Bônus:

**Tipos comuns de janelas móveis:**

|Tipo|Exemplo|Uso típico|
|---|---|---|
|Média|`.rolling(3).mean()`|Suavização|
|Soma|`.rolling(7).sum()`|Volume acumulado|
|Desvio Padrão|`.rolling(5).std()`|Volatilidade|
|Mín/Máx|`.rolling(10).min()`|Deteção de picos|
|Quantis|`.rolling(30).quantile(0.75)`|Análise de dispersão|

**Erros comuns:**  
⚠️ Usar lags quando há valores nulos (shift gera NaNs)  
⚠️ Usar janelas móveis que incluem o futuro (ex: centradas)  
⚠️ Criar features de lags **sem alinhar com a previsão futura**

**Curiosidade:**  
Em competições como as do Kaggle, engenheiros de dados criam **dezenas de lags e janelas móveis combinadas** para alcançar resultados top 1%.