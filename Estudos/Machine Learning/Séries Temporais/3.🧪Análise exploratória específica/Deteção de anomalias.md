## 🧩 Conceito: **Detecção de Anomalias em Séries Temporais**

---

### 1. **O que é?**

É o processo de **identificar valores atípicos** (anômalos, fora do padrão esperado) dentro de uma série temporal. Esses pontos **quebram o padrão normal** e podem representar **erros, fraudes, falhas técnicas ou eventos excepcionais**.

---

### 2. **Para que serve? (Função/Objetivo)**

- **Monitorar sistemas em tempo real** (ex: servidores, sensores, mercado)
    
- **Prevenir falhas e tomar ações rápidas**
    
- **Detectar fraudes** (em finanças, segurança etc.)
    
- **Garantir qualidade de dados**
    
- Ajudar no **debug** e **manutenção preventiva**
    

---

### 3. **Como funciona? (Principais mecanismos ou estrutura)**

#### 🔹 Abordagens comuns:

|Abordagem|Descrição|Exemplo|
|---|---|---|
|Estatística simples|Marca como anomalia valores muito distantes da média|`valor > média + 3*desvio`|
|Desvios de média móvel|Detecta picos fora da média móvel + tolerância|`rolling std/mean`|
|Decomposição|Identifica outliers no componente de ruído (residual)|`seasonal_decompose()`|
|Modelos|ARIMA, LSTM, Prophet, Isolation Forest, etc.|Anomalia = previsão muito diferente do real|
|Bibliotecas específicas|Usam algoritmos prontos e thresholds dinâmicos|`pycaret`, `kats`, `sktime`, `anomalize`|

---

#### 📌 Exemplo simples:

python


`import numpy as np 
```
df['rolling_mean'] = df['valor'].rolling(30).mean() 
df['rolling_std'] = df['valor'].rolling(30).std() 
df['anomaly'] = np.where(  
	(df['valor'] > df['rolling_mean'] + 3*df['rolling_std']) |
	(df['valor'] < df['rolling_mean'] - 3*df['rolling_std']),     
	1, 0 
)`
```
---

### 4. **Exemplos práticos**

| Aplicação         | Anomalia típica                          |
| ----------------- | ---------------------------------------- |
| Sensor de máquina | Pico inesperado de temperatura           |
| Sistema bancário  | Transação fora do padrão do usuário      |
| E-commerce        | Queda ou pico repentino em vendas        |
| API ou backend    | Explosão de requisições ou falha total   |
| Rede social       | Explosão de engajamento em post suspeito |

---

### 5. **Importância e impactos**

- Previne **perdas financeiras e falhas graves**
    
- Mantém a **confiabilidade do sistema**
    
- Permite agir com **respostas rápidas e automáticas**
    
- Garante **qualidade do dado** para futuras previsões
    
- É o coração de **monitoramento inteligente** em tempo real (ex: Datadog, Prometheus)
    

---

### 6. **Conexões com outros conceitos**

- **Suavização e média móvel**: usadas como baseline para detectar desvios
    
- **Decomposição**: separa o ruído, facilitando a detecção de outliers reais
    
- **Modelos preditivos**: o erro de previsão pode ser usado para encontrar anomalias
    
- **Rolling windows e lags**: ajudam a entender comportamento "normal" do passado
    

---

### 7. **Resumo pessoal (reflexão final)**

> “Detectar anomalias é como identificar batimentos cardíacos fora do ritmo: não é sobre o que é comum, é sobre o que pode ser crítico.”

---

### 🧠 Bônus:

#### 📦 Bibliotecas úteis para detecção:

- [`scikit-learn`]: Isolation Forest, OneClassSVM
    
- [`statsmodels`]: ARIMA + resíduos
    
- [`prophet`]: já detecta outliers automaticamente
    
- [`Kats (Meta/Facebook)`]: tem `AnomalyDetectionModel()` pronto
    
- [`pycaret`]: com pipeline completo para anomalias
    

#### 📊 Visualização de anomalias:


![[Pasted image 20250803200038.png]]

![[Pasted image 20250803200013.png]]
#### ⚠️ Erros comuns:

- Ignorar **sazonalidade ou tendência** e detectar falsos positivos
    
- Usar janelas muito curtas ou longas demais
    
- Tratar anomalias sem considerar o contexto do domínio
    
- Confundir "anomalia" com "variação natural" da série