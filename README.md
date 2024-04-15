# Detecção de Spam com Naive Bayes

## **Introdução:** 
No mundo digital de hoje, e-mails e mensagens de texto são essenciais para comunicação pessoal e profissional. Contudo, essa conveniência é frequentemente prejudicada pela presença de 'spam', mensagens não solicitadas que podem ser irritantes e até perigosas. Neste projeto, desenvolvemos um modelo de Machine Learning baseado no algoritmo Naive Bayes para classificar mensagens como 'spam' ou 'ham' (não spam)

## 1. **Importação de Bibliotecas e Dados:** 
Inicialmente, importei as bibliotecas necessárias para o projeto e carreguei o arquivo contendo uma coleção de mensagens SMS, cada uma rotulada como 'spam' ou 'ham' (não spam).
## 2. **Balanceamento dos Dados:** 
Após uma análise inicial, observei que a proporção entre mensagens 'ham' e 'spam' no conjunto de dados era de 86% para 'ham' e 14% para 'spam'. Contudo, pesquisas indicam que a proporção real de mensagens spam que recebemos é de cerca de 50%. Para ajustar o conjunto de dados à realidade observada, normalizei e balanceei os dados para que a proporção entre 'ham' e 'spam' fosse de 50-50.
## 3. **Divisão em Conjuntos de Treino e Teste:** 
Em seguida, dividi o conjunto de dados em duas partes: 80% para treinamento e 20% para teste. Esta divisão é essencial para validar a eficácia do modelo de machine learning no reconhecimento de mensagens novas e não vistas durante o treinamento.
## 4. **Tratamento dos Dados para o Modelo Naive Bayes:**   
O modelo escolhido para a classificação das mensagens foi o Naive Bayes, que se baseia na probabilidade das palavras utilizadas nas mensagens para realizar a classificação entre 'spam' e 'ham'. Para adequar os dados ao modelo, realizei os seguintes tratamentos:   
### 4.1 **Limpeza de Texto:** 
Primeiramente, substituí todos os caracteres não alfanuméricos presentes nas mensagens por espaços em branco e converti todas as letras para minúsculas. Esta etapa é crucial para padronizar o texto e reduzir a complexidade do modelo.   
### 4.2 **Vetorização de Texto:** 
Em seguida, criei uma representação vetorial das mensagens. Para cada palavra do vocabulário, adicionei uma coluna correspondente no conjunto de dados, onde cada entrada indica quantas vezes essa palavra aparece na mensagem. Esse processo é conhecido como "bag of words" e é essencial para transformar texto em uma forma que o modelo de machine learning possa processar eficientemente.
Estas etapas são fundamentais para preparar os dados de forma que o modelo Naive Bayes possa operar eficazmente na classificação de mensagens como 'spam' ou 'ham'.
## 5. **Cálculo da Probabilidade com Naive Bayes Utilizando Suavização de Laplace:** 
Para calcular a probabilidade de uma mensagem ser 'spam' ou 'ham' usando o modelo Naive Bayes, implementei o método de suavização de Laplace. Esta fórmula é usada para calcular a probabilidade de uma palavra $w_i$ aparecer em um email dado que este email é spam, denotado como $P(w_i|\text{Spam})$.
Vamos decompor a fórmula para entender cada parte:
$$P(w_i|\text{Spam}) = \frac{N_{w_i|\text{Spam}} + \alpha}{N_{\text{Spam}} + \alpha \cdot N_{\text{vocabulary}}}$$

- $P(w_i|\text{Spam})$: é a probabilidade de ocorrer a palavra $w_i$ em um email sabendo que esse email é spam.
- $N_{w_i|\text{Spam}}$: é o número de vezes que a palavra $w_i$ aparece em emails marcados como spam.
- $N_{\text{Spam}}$: é o número total de palavras em todos os emails marcados como spam.
- $N_{\text{vocabulary}}$: é o número total de palavras únicas em todos os emails, tanto spam quanto ham. Isso é conhecido como o tamanho do vocabulário.
- $\alpha$: é um parâmetro de suavização, usado para lidar com palavras que não aparecem nos emails de spam durante o treinamento.
Normalmente, $\alpha$ é um número pequeno e positivo, como 1.

Isso é conhecido como suavização de Laplace. 
A suavização de Laplace é crucial porque garante que cada palavra, vista ou não durante o treinamento, tenha uma contribuição mínima na determinação da probabilidade de uma mensagem ser 'spam'.

## 6. **Classificação e Avaliação de Mensagens:**   
Após o cálculo das probabilidades, o próximo passo é utilizar essas probabilidades para classificar as mensagens. Criei um classificador que usa as probabilidades calculadas para determinar se uma nova mensagem é 'spam' ou 'ham'. O classificador avalia a mensagem com base nas probabilidades associadas a cada palavra contida na mensagem e faz uma previsão final.
Então testamos a acuracia do modelo com base na sua precisão em identificar corretamente 'spam' e 'ham'.

## 7. **Conclusão:**
Durante os testes de predição, o modelo analisou um total de 299 mensagens. Deste total, o modelo classificou corretamente 285 mensagens, enquanto apenas 14 foram classificadas incorretamente. Isso resultou em uma acurácia de 95%.
