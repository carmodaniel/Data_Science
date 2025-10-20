# Documentação do Projeto de Análise e Classificação de Risco de Crédito

Este documento detalha o projeto de análise e classificação de risco de crédito utilizando dados do Sistema de Informações de Crédito (SCR) do Banco Central do Brasil.

## 1. Introdução e Contexto dos Dados
A fonte dos dados utilizada neste projeto é o **Sistema de Informações de Crédito (SCR)** do Banco Central do Brasil.
Os dados são públicos e podem ser acessados através da URL: [https://dadosabertos.bcb.gov.br/dataset/scr_data](https://dadosabertos.bcb.gov.br/dataset/scr_data).
Este projeto utiliza dados mensais referentes ao ano de **2025**.

O SCR é um banco de dados gerenciado pelo Banco Central do Brasil que contém informações detalhadas sobre as operações de crédito contratadas por pessoas físicas e jurídicas no país. Ele é uma ferramenta essencial para a supervisão do sistema financeiro, permitindo a análise do risco de crédito e o acompanhamento do endividamento.

## 2. Motivação e Problema
O propósito deste projeto é realizar uma análise aprofundada dos dados de crédito do SCR para identificar padrões de risco e inadimplência.

O problema central abordado é a necessidade de compreender melhor o perfil da carteira de crédito, identificar segmentos de clientes ou modalidades de crédito com maior propensão à inadimplência e prever o risco de crédito de novas operações. Em um cenário econômico dinâmico, a gestão eficaz do risco de crédito é fundamental para a saúde financeira das instituições e para a estabilidade do sistema financeiro.

Este projeto é útil para:
- **Instituições Financeiras:** Para melhorar a tomada de decisão na concessão de crédito, otimizar a gestão de carteiras e reduzir perdas com inadimplência.
- **Analistas de Risco:** Para aprofundar a análise de portfólio, desenvolver e validar modelos de risco e monitorar a qualidade da carteira.
- **Reguladores:** Para entender a dinâmica do mercado de crédito, identificar riscos sistêmicos e aprimorar as políticas de supervisão.

## 3. Objetivo do Projeto
O principal objetivo deste projeto é construir um modelo de classificação capaz de identificar operações de crédito com alto potencial de se tornarem problemáticas, utilizando dados históricos do SCR. Além disso, o projeto visa fornecer insights valiosos sobre a composição da carteira de crédito e os fatores que mais contribuem para o risco de inadimplência.

As principais perguntas de negócio e analíticas que este projeto busca responder são:

- Quais são os estados brasileiros com maior volume de carteira de crédito ativa e inadimplida?
- Quais modalidades de crédito representam a maior parte da carteira e qual o seu respectivo nível de inadimplência?
- Como a carteira de crédito se distribui em termos de prazos de vencimento?
- Quais portes de cliente apresentam maior percentual de inadimplência?
- É possível construir um modelo preditivo que classifique as operações de crédito entre baixo e alto risco com boa acurácia?
- Quais variáveis financeiras são mais importantes para determinar o risco de uma operação de crédito?

## 4. Valor Entregue pela Solução
A solução proposta por este projeto entrega valor significativo ao permitir uma gestão de risco de crédito mais proativa e informada. Ao identificar operações com alto risco de inadimplência, as instituições podem tomar decisões antecipadas, como:

- **Ajuste de políticas de crédito:** Refinar critérios de aprovação para segmentos ou modalidades de maior risco.
- **Otimização da cobrança:** Direcionar esforços de cobrança de forma mais eficiente para os clientes com maior probabilidade de se tornarem inadimplentes.
- **Precificação de risco:** Adequar as taxas de juros e condições de crédito ao risco real de cada operação.
- **Alocação de capital:** Gerenciar o capital de forma mais eficiente, considerando a exposição ao risco.
- **Melhora na qualidade da carteira:** Reduzir o volume de ativos problemáticos e, consequentemente, as perdas financeiras.

O impacto prático dos resultados inclui:

- **Redução de perdas com inadimplência:** Ao prever e mitigar o risco, as perdas financeiras são minimizadas.
- **Aumento da rentabilidade:** A gestão de risco aprimorada contribui para a saúde financeira e o aumento dos lucros.
- **Melhora na tomada de decisão:** Insights baseados em dados permitem decisões mais estratégicas e eficazes.
- **Cumprimento regulatório:** A análise detalhada e a capacidade preditiva auxiliam na conformidade com as exigências do Banco Central.

## 5. Tecnologias e Bibliotecas Utilizadas
Este projeto utiliza as seguintes bibliotecas Python:

- **pandas:** Essencial para manipulação e análise de dados. Foi utilizada para ler os arquivos CSV, concatenar os dados em um único DataFrame, realizar operações de limpeza (tratamento de valores nulos e conversão de tipos), agrupar dados para análise exploratória e preparar os dados para o modelo de machine learning.
- **numpy:** Usada para operações numéricas eficientes, especialmente com arrays. Foi utilizada em conjunto com o pandas para manipulações de dados e na criação da variável alvo (`np.where`).
- **matplotlib.pyplot:** Biblioteca fundamental para a criação de visualizações estáticas em Python. Foi utilizada para gerar os gráficos de barras que ilustram a distribuição da carteira por UF, modalidades de crédito, comparativo de ativos problemáticos, inadimplência por porte e distribuição por prazo.
- **seaborn:** Baseada no matplotlib, fornece uma interface de alto nível para desenhar gráficos estatísticos atraentes e informativos. Foi utilizada para aprimorar a estética dos gráficos e simplificar a criação de alguns tipos de visualização, como os barplots.
- **sklearn (scikit-learn):** Biblioteca abrangente para machine learning em Python. Foi utilizada para dividir os dados em conjuntos de treino e teste (`train_test_split`), construir e treinar o modelo de Árvore de Decisão (`DecisionTreeClassifier`), e avaliar o desempenho do modelo usando métricas como acurácia, relatório de classificação (`classification_report`) e matriz de confusão (`confusion_matrix`). A função `plot_tree` também foi usada para visualizar a árvore de decisão treinada.

## 6. Análise Exploratória de Dados (EDA)
A Análise Exploratória de Dados (EDA) foi realizada para entender a estrutura, qualidade e principais características do conjunto de dados de crédito. O foco foi identificar padrões, distribuições e relações entre as variáveis antes de construir o modelo preditivo.

Os principais resultados e interpretações da EDA são:

- **GRÁFICO 1 – Distribuição da carteira por UF (Estados):** Este gráfico mostra a concentração do volume de crédito ativo por estado. Permite identificar as regiões geográficas com maior exposição financeira e potencial para atuação, como São Paulo (SP), que apresenta o maior volume.
- **GRÁFICO 2 – Modalidades de crédito mais utilizadas:** Identifica os tipos de produtos de crédito com maior representatividade na carteira, como Crédito Habitacional e Capital de Giro. Isso indica o perfil dos clientes e os tipos de operação mais relevantes para a instituição.
- **GRÁFICO 3 – Comparação entre Carteira Ativa e Ativos Problemáticos:** Apresenta a relação entre o total de crédito ativo e o volume de ativos considerados problemáticos (inadimplentes). Um volume significativo em 'Ativos Problemáticos' sinaliza um risco elevado na carteira geral.
- **GRÁFICO 4 – Inadimplência por porte do cliente:** Calcula e visualiza o percentual de inadimplência para cada porte de cliente (Micro, Pequeno, Médio, Grande e Pessoas Físicas por faixa de renda). Ajuda a identificar quais segmentos de clientes possuem maior risco de crédito e podem necessitar de políticas mais rigorosas. PFs sem rendimento e PJs Pequenas apresentaram os maiores percentuais de inadimplência.
- **GRÁFICO 5 – Distribuição dos valores por tempo de vencimento:** Mostra como o valor total da carteira está distribuído entre diferentes faixas de prazo (até 90 dias, 91 a 360 dias, etc.). Essencial para a gestão de liquidez e para entender a composição da carteira em termos de curto, médio e longo prazo. A maior parte do crédito está concentrada em prazos mais longos (361 a 1080 dias e 91 a 360 dias).
- **GRÁFICO 6 – Carteira Ativa x Inadimplida por UF:** Compara o volume de carteira ativa e inadimplida para os 10 principais estados. Permite visualizar o volume de risco em cada região e identificar estados com alto volume de inadimplência em relação à carteira ativa.

## 7. Modelo de Classificação
Foi desenvolvido um modelo de classificação para prever se uma operação de crédito possui alto ou baixo risco. A variável alvo (`risco_alto`) foi criada com base na coluna `ativo_problematico`, onde 1 indica alto risco (ativo_problematico > 0) e 0 indica baixo risco (ativo_problematico == 0).

- **Modelo Utilizado:** Árvore de Decisão (`DecisionTreeClassifier`) da biblioteca scikit-learn. Este modelo foi escolhido por sua interpretabilidade, permitindo visualizar as regras de decisão aprendidas.
- **Características (Features):** As variáveis numéricas relacionadas aos valores a vencer em diferentes prazos, valores vencidos, carteira ativa e carteira inadimplida foram utilizadas como features para treinar o modelo.
- **Divisão dos Dados:** Os dados foram divididos em conjuntos de treino (70%) e teste (30%) usando `train_test_split`, com estratificação pela variável alvo para garantir que a proporção de classes seja similar em ambos os conjuntos.
- **Resultados de Avaliação:**
    - **Acurácia:** O modelo alcançou aproximadamente 89.5% de acurácia nos conjuntos de treino e teste, indicando uma boa capacidade geral de classificação.
    - **Relatório de Classificação:** Fornece métricas detalhadas por classe (Baixo Risco e Alto Risco). A precisão e recall para a classe de alto risco (1) são de aproximadamente 92% e 84%, respectivamente. Isso significa que, quando o modelo prevê alto risco, está correto 92% das vezes (precisão), e ele identifica 84% de todos os casos reais de alto risco (recall).
    - **Matriz de Confusão:** Mostra a quantidade de verdadeiros positivos, verdadeiros negativos, falsos positivos e falsos negativos. Confirma que o modelo tem um desempenho razoável na identificação de ambas as classes, embora haja uma quantidade notável de falsos negativos (operações de alto risco classificadas como baixo risco).
- **Visualização da Árvore:** A árvore de decisão treinada, limitada a uma profundidade de 4, mostra as regras aprendidas pelo modelo para classificar o risco. Variáveis como `vencido_acima_de_15_dias` e `carteira_inadimplida_arrastada` aparecem como critérios importantes para a divisão dos nós, reforçando sua relevância na identificação de risco.

**Interpretação do Modelo:**

O modelo de Árvore de Decisão demonstra a capacidade de identificar padrões nas variáveis financeiras que distinguem operações de baixo e alto risco. As regras visíveis na árvore fornecem insights acionáveis sobre quais combinações de características financeiras estão mais associadas a um maior risco de inadimplência. Embora a acurácia seja boa, a análise do relatório de classificação e da matriz de confusão é crucial para entender o desempenho específico na identificação da classe de interesse (alto risco), onde a precisão e o recall devem ser cuidadosamente avaliados para o contexto de negócio.
