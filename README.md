# SmartStock AI : Previsão Inteligente de Demanda e Gestão de Estoques
Demosntração

https://github.com/user-attachments/assets/e5cac80e-f912-4d11-8fe8-6241a5ae8612



Machine Learning  •  Ciência de Dados  •  Python  •  Streamlit  •  Varejo

O SmartStock AI é um projeto de Ciência de Dados e Inteligência Artificial desenvolvido para apoiar decisões de gestão de estoques no varejo. A solução utiliza Machine Learning para prever demanda, identificar riscos de ruptura, recomendar reposição e analisar impactos operacionais e econômicos de estratégias de abastecimento.

O projeto também investiga desperdícios de alimentos com simulações de validade e a política FEFO (First Expired, First Out), além de disponibilizar um dashboard interativo desenvolvido com Streamlit.

Objetivo

- Prever a demanda futura de produtos com Machine Learning.
- Identificar possíveis situações de falta ou excesso de estoque.
- Recomendar quantidades de reposição conforme previsões e parâmetros operacionais.
- Considerar prazos de entrega, pedidos pendentes e estoque de segurança.
- Comparar políticas convencionais e inteligentes de abastecimento.
- Simular custos de armazenagem e perdas associadas ao vencimento.
- Disponibilizar resultados e recomendações em uma interface interativa.

  Tecnologias utilizadas

| Tecnologia | Aplicação |
| --- | --- |
| Python | Desenvolvimento e processamento de dados |
| Pandas e NumPy | Tratamento de dados e cálculos numéricos |
| Scikit-learn | Treinamento e avaliação dos modelos |
| Extra Trees Regressor | Previsão de demanda |
| Joblib | Persistência e carregamento dos modelos |
| Streamlit | Interface interativa |
| Plotly | Gráficos e visualizações |
| Google Colab e Drive | Desenvolvimento e armazenamento |
| Cloudflare Tunnel | Acesso temporário ao dashboard |

Base de dados

O desenvolvimento experimental utilizou aproximadamente 76.000 registros diários, referentes a 5 lojas, 20 produtos e 100 combinações de loja e produto, com 760 dias de observações entre janeiro de 2022 e janeiro de 2024. Entre as variáveis disponíveis estão vendas, demanda, estoque, preços, descontos, promoções e unidades solicitadas.

Os dados foram explorados, tratados e organizados temporalmente para possibilitar a engenharia de atributos e o treinamento dos modelos.

Funcionalidades desenvolvidas

Previsão inteligente de demanda

O modelo Extra Trees utiliza dia da semana, mês, dia do mês, identificação da loja e produto, vendas defasadas (1, 7, 14 e 30 dias), médias móveis e desvio-padrão recente. A previsão de sete dias é recursiva, utilizando previsões anteriores nos horizontes seguintes.
Recomendações de reposição
O sistema considera demanda prevista, estoque disponível, prazo de entrega, cobertura de estoque, estoque de segurança e pedidos pendentes com datas de chegada. Sinaliza riscos de falta antes de novos recebimentos e calcula uma quantidade sugerida de compra; não efetua pedidos automaticamente.

Processamento de múltiplos produtos

Por meio de arquivos CSV, o dashboard processa diferentes lojas e produtos, valida históricos, gera previsões individuais e disponibiliza uma lista consolidada de compras, alertas e relatórios exportáveis.

Simulação de estoque

O projeto compara políticas de reposição baseadas em média móvel, Extra Trees e Extra Trees com tratamento experimental da validade, considerando entradas, saídas, demanda não atendida e saldos.

Validade e desperdício

O simulador FEFO dá prioridade a lotes próximos do vencimento e contabiliza descartes simulados. Os prazos de validade utilizados são hipóteses experimentais, não perdas reais comprovadas.

Análise econômica

Compara margem de contribuição das vendas, custos hipotéticos de aquisição e armazenagem, valores atribuídos a descartes e resultados parciais. Esses valores não correspondem a lucro contábil ou economia realizada.

Avaliação do modelo

Foi realizado um backtesting temporal recursivo, com reconstrução auditável das previsões e sem utilizar vendas futuras na construção dos atributos de previsão.

| Métrica | Extra Trees | Média móvel |
| --- | --- | --- |
| MAE | 32,67 | 33,55 |
| RMSE | 41,47 | 42,83 |
| WAPE | 37,79% | 38,81% |

O Extra Trees apresentou redução aproximada de 2,63% no MAE. A análise exploratória de incerteza, porém, não estabeleceu significância estatística conclusiva para a diferença. Os resultados são retrospectivos e não garantem o mesmo desempenho com dados atuais.

Dashboard Streamlit

| Área | Função |
| --- | --- |
| Visão geral | Demanda, atendimento e estoque |
| Previsões | Comparação Extra Trees × média móvel |
| Estoque | Movimentações e reposição |
| Validade | Simulações FEFO e descartes |
| Economia | Custos e resultados parciais |
| Auditoria | Verificações e ressalvas |
| Operação individual | Previsão e compra sugerida para um produto |
| Reposição em lote | Recomendações para vários produtos e lojas |

O dashboard permite filtrar informações, consultar gráficos e exportar resultados em CSV. A aplicação foi testada com dados históricos de demonstração e inclui confirmação explícita do estoque e identificação de pedidos pendentes por data.

Validação e auditoria

A auditoria do núcleo experimental registrou 61 verificações de consistência aprovadas, incluindo conservação de estoque e demanda, continuidade dos saldos, correspondência entre políticas e reconciliação dos resultados econômicos. Essas verificações fortalecem a rastreabilidade, mas não substituem testes prospectivos de operação real.

Como executar

1. Configure um ambiente Python e instale as bibliotecas principais:
2. pip install pandas numpy scikit-learn joblib streamlit plotly

3. Disponibilize os arquivos de dados e os modelos treinados usados pelo notebook.

Ajuste os caminhos originalmente vinculados ao Google Drive para o ambiente de execução.

Inicie o dashboard com o comando:

streamlit run streamlit_app/app.py

As páginas complementares ficam em streamlit_app/pages. A aplicação depende da presença dos modelos e artefatos de dados; ainda não está preparada como implantação independente do Google Drive.

Limitações

- A base histórica disponível termina em janeiro de 2024; modelos requerem reavaliação com dados recentes.
- Não houve validação prospectiva em operação comercial.
- Prazos de validade e parte dos parâmetros econômicos são hipotéticos.
- Não foi demonstrada redução agregada de descartes na política sensível à validade no experimento final.
- As recomendações não contemplam todas as restrições logísticas, financeiras e contratuais de fornecedores.
- O dashboard ainda não possui integração automática com ERP ou sistema transacional de estoque.
- Links por Cloudflare Tunnel são temporários e não representam hospedagem permanente.

  Próximas evoluções
  
- Integração com ERP, bancos de dados e inventários atualizados.
- Retreinamento e monitoramento periódico de qualidade preditiva.
- Controle de validade baseado em lotes reais.
- Restrições de fornecedores, capacidade e orçamento nas recomendações.
- Autenticação de usuários e hospedagem permanente.
- 
Conclusão

O SmartStock AI integra previsão de demanda, simulação de reposição, análise de desperdício, avaliação econômica e visualização interativa. Seu principal resultado é um protótipo experimental funcional de apoio à decisão, com capacidade de receber históricos de vendas e produzir recomendações de compras individuais e em lote. A aplicação comercial exige dados recentes, validação operacional e ajustes de infraestrutura.


