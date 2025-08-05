## 🧩 Conceito: **Criação de Features Temporais (Temporal Feature Engineering)**

---

### 1. **O que é?**

É o processo de **extrair informações relevantes a partir da variável de tempo (data/hora)** e transformá-las em **novas colunas/atributos** que ajudam os modelos a aprender padrões temporais.  
Exemplos: dia da semana, mês, hora do dia, feriado, distância até o fim do mês, etc.

---

### 2. **Para que serve? (Função/Objetivo)**

Serve para:

- **Representar o tempo como algo interpretável** para modelos supervisionados
    
- **Capturar sazonalidades, ciclos e efeitos de calendário**
    
- **Aumentar o poder preditivo dos modelos**, fornecendo contexto temporal
    
- Funciona como um tipo de "atenção manual" ao tempo
    

---

### 3. **Como funciona? (Principais mecanismos ou estrutura)**

### 🛠️ Exemplos em Python:

`python`
```
df['data'] = pd.to_datetime(df['data'])

# Extração básica
df['ano'] = df['data'].dt.year
df['mes'] = df['data'].dt.month
df['dia'] = df['data'].dt.day
df['dia_da_semana'] = df['data'].dt.weekday      # 0 = segunda
df['nome_dia'] = df['data'].dt.day_name()

# Sazonalidade cíclica (seno e cosseno)
df['mes_sin'] = np.sin(2 * np.pi * df['mes'] / 12)
df['mes_cos'] = np.cos(2 * np.pi * df['mes'] / 12)

# Flags

```

---

### 4. **Exemplos práticos**

| Feature criada  | O que captura?                | Exemplo de uso                        |
| --------------- | ----------------------------- | ------------------------------------- |
| `dia_da_semana` | Efeito do dia na demanda      | Vendas mais altas no sábado           |
| `mês`           | Sazonalidade anual            | Previsão de energia por estação       |
| `feriado`       | Efeito de datas especiais     | Picos de tráfego no e-commerce        |
| `hora`          | Ciclos diários                | Picos de acesso em horários de almoço |
| `sin_cos`       | Sazonalidade cíclica contínua | Input para redes neurais              |

---

### 5. **Importância e impactos**

- É **fundamental** para que modelos de ML entendam o tempo
    
- Permite **capturar padrões complexos e não lineares** com algoritmos que não têm memória temporal
    
- Pode reduzir o erro de previsão drasticamente com poucas colunas a mais
    
- Em modelos como XGBoost, **o tempo por si só (como datetime)** não é interpretável — você precisa quebrar ele em partes úteis
    

---

### 6. **Conexões com outros conceitos**

- **Parseamento de datas**: pré-requisito para extrair features temporais
    
- **Sazonalidade**: é representada por essas features
    
- **Resampling e rolling**: podem ser combinados para gerar novas colunas
    
- **One-hot encoding**: usado para transformar variáveis temporais categóricas (ex: dia da semana)
    

---

### 7. **Resumo pessoal (reflexão final)**

> “Criar features temporais é como dar um calendário e um relógio pro modelo. Só assim ele entende que segunda-feira de manhã não é igual a domingo à noite.”

---

### 🧠 Bônus:

**Features úteis por granularidade:**

| Granularidade | Features Recomendadas                               |
| ------------- | --------------------------------------------------- |
| Horária       | Hora do dia, Turno, Período do expediente           |
| Diária        | Dia da semana, Feriado, Fim de semana, Sazonalidade |
| Semanal       | Semana do ano, Indicador de início/fim de mês       |
| Mensal        | Mês, Trimestre, Sazonalidade anual                  |

**Erros comuns:**  
⚠️ Usar `datetime` diretamente no modelo (ele não entende)  
⚠️ Não representar a ciclicidade com `sin/cos` (ex: 23h e 1h não são opostos)  
⚠️ Esquecer de ajustar as features ao **resampling** feito anteriormente

**Curiosidade:**  
Modelos de deep learning como **LSTM** e **Transformer** podem detectar padrões temporais sem features manuais, mas mesmo assim, **incluir features temporais explícitas costuma melhorar o desempenho**.