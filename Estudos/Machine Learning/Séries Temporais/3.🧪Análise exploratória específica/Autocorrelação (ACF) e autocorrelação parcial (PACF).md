## 🧩 Conceito: **Autocorrelação (ACF) e Autocorrelação Parcial (PACF)**

---

### 1. **O que é?**

- **ACF (Autocorrelation Function)**: mede **a correlação de uma série com seus próprios lags**. Por exemplo, quanto o valor de hoje se parece com o de ontem, anteontem, etc.
    
- **PACF (Partial Autocorrelation Function)**: mede a **correlação entre a série e seus lags**, **removendo o efeito dos lags intermediários**. Ajuda a identificar relações diretas.
    

---

### 2. **Para que serve? (Função/Objetivo)**

- Identificar **lags significativos** que influenciam o valor atual
    
- Ajudar a escolher os **parâmetros p e q** de modelos ARIMA
    
- Diagnosticar **estacionariedade** e **estrutura de dependência**
    
- Visualizar **memória da série** (por quanto tempo o passado influencia o presente)
    

---

### 3. **Como funciona? (Principais mecanismos ou estrutura)**

### 🔹 Gerar os gráficos:

python
`from statsmodels.graphics.tsaplots import plot_acf, plot_pacf  plot_acf(df['valor'], lags=25)`
`plot_pacf(df['valor'], lags=25)`

![[Pasted image 20250803195257.png]]

### 🔹 Interpretação:

| Lag | ACF | PACF | Significado                        |
| --- | --- | ---- | ---------------------------------- |
| 1   | 0.8 | 0.8  | Forte influência do valor anterior |
| 2   | 0.6 | 0.1  | Influência indireta via lag 1      |
| 3   | 0.4 | 0.0  | Influência indireta via lag 1 e 2  |
| 4+  | ≈ 0 | ≈ 0  | Sem influência relevante           |

As linhas pontilhadas no gráfico são **limites de significância** (confiança de 95%). Se a barra ultrapassa, o lag é relevante.

---

### 4. **Exemplos práticos**

|Situação|ACF|PACF|Modelo sugerido|
|---|---|---|---|
|Decaimento lento no ACF|Alto|0 após 1|AR(1)|
|Spike no ACF em lag 1|Spike|0|MA(1)|
|Spikes em ACF e PACF|Spike|Spike|ARMA|
|Padrões sazonais|Picos a cada 12 lags (mensal)|Mesma coisa|SARIMA|

---

### 5. **Importância e impactos**

- **Base para definição de modelos ARIMA/SARIMA**
    
- Ajuda a **evitar overfitting** escolhendo os lags corretos
    
- Dá suporte **visual e estatístico** na análise exploratória
    
- Permite **avaliar a estacionariedade** (ACF decai lentamente em séries não estacionárias)
    

---

### 6. **Conexões com outros conceitos**

- **Lags**: ACF e PACF ajudam a decidir quais criar
    
- **Modelos ARIMA**: p (ordem autoregressiva) ↔ PACF, q (ordem da média móvel) ↔ ACF
    
- **Estacionariedade**: séries não estacionárias têm ACF que decai lentamente
    
- **Sazonalidade**: aparece como picos periódicos nos gráficos de ACF/PACF
    

---

### 7. **Resumo pessoal (reflexão final)**

> “ACF e PACF são como lanternas no escuro: mostram quais pontos do passado ainda influenciam o presente — e quais são só sombras.”

---

### 🧠 Bônus:

#### 🧩 Dica prática: como escolher `p` e `q` pro ARIMA

|Passo|O que observar|Ação|
|---|---|---|
|1|ACF decai devagar|Diferencie a série|
|2|PACF tem spike em lag 1, depois zera|AR(1) → p = 1|
|3|ACF tem spike em lag 1, depois zera|MA(1) → q = 1|

---

#### 💡 Dica de ouro:

Se os gráficos estiverem confusos, **faça primeiro a diferenciação** (`diff()`) e **depois reavalie ACF e PACF**. Isso ajuda a remover tendência e facilita a visualização de lags reais.

---

#### ❌ Erros comuns:

⚠️ Usar série não estacionária sem diferenciar  
⚠️ Interpretar PACF como se fosse ACF (ou vice-versa)  
⚠️ Escolher muitos lags desnecessários e overfit  
⚠️ Ignorar efeitos sazonais em séries com ciclos longos