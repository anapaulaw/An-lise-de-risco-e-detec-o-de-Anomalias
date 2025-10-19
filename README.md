 Detecção de Fraudes com Machine Learning

Este projeto desenvolve um modelo de detecção de fraudes em transações financeiras utilizando técnicas de aprendizado supervisionado.
 O foco é identificar transações fraudulentas em meio a uma base altamente desbalanceada, 
 garantindo alta taxa de detecção (recall) sem aumentar demasiadamente os falsos positivos.
________________________________________________________________________________________________________________________________________________________

*  Objetivos
Construir um pipeline completo e automatizado de detecção de fraudes.
Corrigir o desbalanceamento de classes e evitar data leakage.
Otimizar o cutoff de decisão para maximizar a detecção de fraudes reais.
Avaliar o desempenho com métricas robustas e a Curva ROC-AUC.

___________________________________________________________________________________________________________________________________________________

*  Pipeline de Modelagem
Pré-processamento
Utiliza ColumnTransformer para preparar os dados:
Numéricas: imputação pela mediana + padronização com StandardScaler.
Categóricas: preenchimento do valor mais frequente + OneHotEncoder.


*  Balanceamento de Classes
Aplicação do SMOTE (Synthetic Minority Oversampling Technique) para aumentar artificialmente a classe minoritária (fraudes), gerando exemplos sintéticos realistas.
Corrige o desbalanceamento e melhora a capacidade do modelo de detectar fraudes.


*  Modelo Preditivo
O modelo principal utilizado foi a Regressão Logística, com:
LogisticRegression(class_weight='balanced', solver='liblinear', max_iter=1000)
Produz probabilidades que permitem calibrar o cutoff (limiar de decisão).
Enfatiza a classe de fraude sem distorcer o aprendizado geral.

_____________________________________________________________________________________________________________________________________________________________________
* Resultados

Verdadeiros Negativos (TN): 69.343
Falsos Positivos (FP): 1.736
Falsos Negativos (FN): 14
Verdadeiros Positivos (TP): 109


O modelo detectou corretamente a maioria das fraudes (TP) com baixo número de falsos positivos.
_____________________________________________________________________________________________________________________________________________________
*  Principais Métricas

AUC (ROC)
0.9725
Precision (Fraude)
Alta
Recall (Fraude)
Elevado
F1-Score (Fraude)
Balanceado

O modelo está ajustado para maximizar a detecção de fraudes reais, mesmo em cenários de forte desbalanceamento.

