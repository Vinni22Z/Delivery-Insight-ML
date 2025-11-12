# Delivery-Insight-ML
#  Análise dos Fatores que Influenciam a Entrega Correta de Pedidos

Este projeto tem como objetivo **prever a entrega correta de pedidos**, utilizando técnicas de **Machine Learning** aplicadas a uma pesquisa real do restaurante fictício *Kashmir Café*.

Empresas de delivery frequentemente enfrentam reclamações de clientes por erros nos pedidos e atrasos nas entregas. O uso de modelos preditivos pode ajudar a identificar padrões de insatisfação e agir preventivamente — melhorando a experiência e reduzindo prejuízos.

---

##  Objetivos do Projeto

- Identificar os fatores que mais impactam a **satisfação do cliente**.  
- Comparar o desempenho de diferentes modelos:
  - **KNN vs Random Forest**
  - Com e sem **Feature Engineering**
  - Com e sem **Balanceamento de Dados (SMOTE, Undersampling, SMOTEENN)**
- Avaliar o impacto das técnicas de otimização (GridSearchCV).

---

##  Tecnologias Utilizadas

| Categoria | Ferramentas |
|------------|-------------|
| Linguagem | Python 3.x |
| Manipulação de Dados | Pandas, NumPy |
| Visualização | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn |
| Balanceamento | imbalanced-learn |
| Persistência | Joblib |

---

##  Etapas do Projeto

### 1️⃣ Importação e Inspeção dos Dados
- Leitura do dataset `Customer-survey-data.csv`
- Renomeação e padronização de colunas
- Remoção de valores ausentes (menos de 7%)
- Conversão da variável alvo `Precisao_ped` para formato binário (`Yes` → 1, `No` → 0)

### 2️⃣ Análise Exploratória
- **Distribuição das notas** (1–5) para Experiência, Tempo e Qualidade
- **Pairplot** para observar padrões
- **Heatmap de correlação** para detectar relações entre as variáveis
- **Identificação de desbalanceamento** entre clientes satisfeitos e insatisfeitos

>  Resultado: mais de 70% das respostas pertenciam à classe “satisfeito”, tornando o dataset **altamente desbalanceado**.

### 3️⃣ Feature Engineering
- Criação de novas features via **One-Hot Encoding** das variáveis ordinais
- Comparação entre modelos **com e sem transformação de variáveis**

---

##  Modelos Testados

###  K-Nearest Neighbors (KNN)
- Baseline com `MinMaxScaler`
- Com **Undersampling**
- Com **SMOTE**
- Com **SMOTEENN**
- Otimizado com **GridSearchCV**

###  Random Forest
- Modelo padrão com `class_weight='balanced'`
- Versão otimizada via **GridSearchCV**



##  Interpretação dos Resultados

* Undersampling removeu amostras demais da classe majoritária, reduzindo a capacidade de generalização.

* SMOTE trouxe ganhos, mas ainda insuficientes para equilibrar completamente o dataset.

* SMOTEENN, apesar de promissor, eliminou instâncias úteis da minoria, piorando o desempenho.

* Random Forest se destacou pela capacidade de lidar com ruídos e relações não lineares.

* A otimização por GridSearchCV trouxe ganhos sutis, mas o principal gargalo segue sendo a qualidade e variedade dos dados.


##  Conclusões

* O Random Forest otimizado apresentou o melhor equilíbrio entre precisão e recall.

* O conjunto de dados, embora útil, não possui variáveis suficientes para prever se o pedido estava correto ou nao , com alta acurácia.

* O principal aprendizado do projeto foi a importância da qualidade dos dados sobre a escolha do modelo.

* Modelos mais complexos não superam limitações estruturais dos dados.

