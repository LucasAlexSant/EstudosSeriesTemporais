## 🧩 Conceito: **Resampling (Reamostragem) de Séries Temporais**

---

### 1. **O que é?**

**Resampling** é o processo de **alterar a frequência temporal dos dados**.  
Pode significar:

- **Downsampling**: reduzir a granularidade (ex: de minuto → hora)
    
- **Upsampling**: aumentar a granularidade (ex: de dia → minuto)
    

---

### 2. **Para que serve? (Função/Objetivo)**

- Adaptar a série à **granularidade de análise desejada**
    
- Suavizar séries muito densas (downsample)
    
- Preencher intervalos ausentes para previsões mais finas (upsample)
    
- Calcular **agregações temporais** (ex: média por dia, total por semana)
    
- Preparar a série para **modelos que requerem frequência regular**
    

---

### 3. **Como funciona? (Principais mecanismos ou estrutura)**

### 🔹 Downsampling (reduzir frequência)

python
`# Média diária de uma série horária`
`df.resample('D').mean()`

`# Soma mensal de uma série diária`
`df.resample('M').sum()`

### 🔹 Upsampling (aumentar frequência)

`Transformar dados diários em horários`
`df.resample('H').asfreq()  # Insere NaNs nas horas`
`df.resample('H').ffill()   # Preenche com valor anterior (forward fill)`
`

📌 Frequências comuns:

- `'T'`: Minuto
    
- `'H'`: Hora
    
- `'D'`: Dia
    
- `'W'`: Semana
    
- `'M'`: Mês
    
- `'Q'`: Trimestre
    
- `'Y'`: Ano
    

---

### 4. **Exemplos práticos**

| Tarefa                                       | Exemplo                    |
| -------------------------------------------- | -------------------------- |
| Agrupar vendas por mês                       | `df.resample('M').sum()`   |
| Calcular média semanal de temperatura        | `df.resample('W').mean()`  |
| Prever hora a hora com base em dados diários | `df.resample('H').ffill()` |
| Criar frequência regular para ARIMA          | `df = df.asfreq('D')`      |

---

### 5. **Importância e impactos**

- Garante **consistência temporal** (intervalos regulares)
    
- Impacta diretamente a **modelagem, decomposição e visualização**
    
- Impede **problemas de frequência irregular** que quebram modelos
    
- Permite o uso de técnicas como **rolling, diferenciação, lags e validação temporal**
    

---

### 6. **Conexões com outros conceitos**

- **Granularidade**: resampling permite mudar a granularidade da série
    
- **Rolling windows**: precisam de frequência regular
    
- **Parseamento de datas**: obrigatório antes de aplicar `.resample()`
    
- **Preenchimento de dados faltantes**: necessário após upsampling
    

---

### 7. **Resumo pessoal (reflexão final)**

> “Resampling é como mudar a lente da câmera: às vezes você precisa enxergar mais de longe (por mês), outras, mais de perto (por minuto). O segredo é escolher a lente certa para o que você quer enxergar.”

---

### 🧠 Bônus:

**Agregações comuns em downsampling:**

- `sum()`: total por período (vendas, contagens)
    
- `mean()`: média por período (temperatura, métricas)
    
- `max()/min()`: detectar picos
    

**Técnicas em upsampling:**

- `.ffill()` ou `.bfill()`
    
- Interpolação: `df.resample('H').interpolate()`
    

**Erros comuns:**  
⚠️ Não parsear a coluna de data como datetime  
⚠️ Usar `.resample()` em séries sem índice temporal  
⚠️ Não preencher os valores nulos gerados por upsampling  
⚠️ Fazer `mean()` em colunas categóricas sem querer