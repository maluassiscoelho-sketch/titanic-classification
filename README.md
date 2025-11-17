# Classificação de Sobreviventes do Titanic com Scikit-Learn  
Projeto Integrado de Classificação Supervisionada

---

## Objetivo

| Objetivo | Descrição |
|---------|-----------|
| Propósito | Aplicar e comparar modelos de classificação supervisionada no dataset Titanic. |
| Modelos utilizados | XGBoost, SVM (RBF), Random Forest (padrão e tunada). |
| Métrica principal | ROC-AUC |
| Métricas secundárias | Acurácia, F1-score, Matriz de confusão |

---

## Dataset

| Item | Descrição |
|------|-----------|
| Fonte | seaborn.load_dataset("titanic") / Kaggle |
| Target | **Survived** (0 = não sobreviveu, 1 = sobreviveu) |
| Variáveis explicativas | Pclass, Sex, Age, Fare, SibSp, Parch, Embarked |

---

## Pré-processamento

| Etapa | Técnica |
|-------|---------|
| Tratamento de nulos | Age → mediana • Embarked → moda |
| Escalonamento | StandardScaler (Age, Fare) |
| Codificação | OneHotEncoder (Sex, Embarked, Pclass) |
| Organização | ColumnTransformer + Pipeline |

---

## Modelagem

| Modelo | Detalhes |
|--------|----------|
| XGBoost | Sem tunagem – baseline forte |
| SVM (RBF) | Avaliado com parâmetros padrão |
| Random Forest (padrão) | Baseline comparativa |
| Random Forest (tunada) | Ajustada via RandomizedSearchCV |

---

## Otimização

| Item | Configuração |
|------|--------------|
| Método | RandomizedSearchCV |
| Validação | StratifiedKFold (5 folds) |
| Modelo tunado | Random Forest |
| Melhores hiperparâmetros | n_estimators=300 • min_samples_split=10 • max_depth=None |

---

## Resultados

| Modelo                 | Acurácia | F1-score | ROC-AUC | Comentários           |
| ---------------------- | -------- | -------- | ------- | --------------------- |
| XGBoost (padrão)       | 0.827    | 0.770    | 0.838   | Excelente performance |
| SVM (padrão)           | 0.810    | 0.707    | 0.824   | Mais falsos negativos |
| Random Forest (padrão) | 0.810    | 0.707    | 0.824   | —                     |
| Random Forest (tunada) | 0.810    | 0.730    | 0.838   | Melhor balanceado     |

---

## Gráficos produzidos

| Gráfico | Status |
|---------|--------|
| Curva ROC | OK |
| Curva Precision-Recall | OK |
| Matriz de confusão | OK |
| Importância das features | OK |
| Localização | Pasta `/img` |

---

## Discussão

| Tema | Síntese |
|------|---------|
| Melhor modelo | Random Forest tunada |
| Observações | Melhor equilíbrio entre performance e interpretabilidade |
| XGBoost | Alta performance, maior custo computacional |
| SVM | Desempenho inferior devido a FN elevados |
| Pré-processamento | Essencial para estabilizar os modelos |
| Redução de dimensionalidade | Não necessária |

---

## Conclusões

| Conclusão | Detalhes |
|-----------|----------|
| Eficácia | Modelos supervisionados obtiveram boa capacidade preditiva |
| Robustez | Validação cruzada + tunagem melhoraram a performance |
| Melhor escolha | Random Forest tunada |

---

## Estrutura do Repositório

| Caminho | Conteúdo |
|---------|----------|
| notebook.ipynb | Código completo no Google Colab |
| README.md | Documentação do projeto |
| /img | Gráficos e outputs |
| /doc | Resumo expandido + pôster |

---

## Execução no Google Colab

| Passo | Comando |
|-------|---------|
| Instalar dependências | `!pip install xgboost scikit-learn seaborn matplotlib` |
| Executar notebook | Rodar células em ordem |

---

## Referências

| Fonte | Detalhes |
|-------|----------|
| Scikit-learn | Pedregosa et al. (2011) |
| XGBoost | Chen & Guestrin (2016) |
| Seaborn | Documentação oficial |
| Kaggle Titanic | Dataset original |
