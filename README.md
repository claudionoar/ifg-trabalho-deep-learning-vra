# Previsão de atraso médio horário de voos com Redes Neurais Recorrentes (ANAC/VRA)

## Sobre o repositório

Trabalho prático da disciplina **Deep Learning** (Prof. Dr. Sérgio Canuto) da Pós-Graduação Lato Sensu em Inteligência Artificial Aplicada do IFG, Câmpus Goiânia. A atividade segue a **Frente 3.2: Redes Recorrentes**.

**Integrantes:**
- Cláudio Antônio de Araújo
- José Allan Kardec Gonçalves

O objetivo é prever o **atraso médio das partidas na próxima hora** a partir de séries temporais horárias multivariadas. Os dados são do **Voo Regular Ativo (VRA)** da ANAC, publicados no [Portal Brasileiro de Dados Abertos](https://dados.gov.br/dados/conjuntos-dados/dadosabertos-areas-de-atuacao-voos-e-operacoes-aereas-voo-regular-ativo-vra), e cobrem o período de setembro de 2025 a agosto de 2026 (cerca de 1 milhão de voos).

Os voos foram agregados em uma série de 8.760 horas com 7 atributos: `atraso_medio`, `n_voos`, `pct_atrasados`, `n_cancel`, `hora_sin`, `hora_cos` e `fim_semana`. A partir dessa série, o trabalho:

- compara **SimpleRNN, LSTM e GRU** sob o mesmo protocolo;
- avalia janelas de entrada de **24h, 48h e 168h**;
- faz a busca de hiperparâmetros com **Optuna**;
- compara os resultados com um baseline de persistência.

A divisão em treino, validação e teste (60/20/20) é cronológica, e a padronização é ajustada somente no treino.

## Relatório e apresentação

- [Relatório Técnico (PDF)](Relat%C3%B3rio%20T%C3%A9cnico%20Trabalho%20Pr%C3%A1tico%20de%20Deep%20Learning.pdf)
- [Slides da apresentação (PDF)](apresentacao_atrasos_rnn_atualizada-v2.pdf)

## Código

- [rnn_voos_todos_aeroportos_v3.ipynb](rnn_voos_todos_aeroportos_v3.ipynb): notebook principal, com a série de todos os aeroportos. Cobre carga e limpeza dos dados, análise exploratória, janelas deslizantes, treino de SimpleRNN, LSTM e GRU, Optuna e baseline.
- [rnn_voos_guarulhos_SBGR.ipynb](rnn_voos_guarulhos_SBGR.ipynb): primeira tentativa, restrita ao Aeroporto de Guarulhos (SBGR), descrita no Anexo I do relatório.

## Código no Google Colab

Os notebooks também podem ser abertos e executados no Google Colab:

- [Notebook principal: todos os aeroportos](https://colab.research.google.com/drive/1u-z8gK_VC2RV0e9M5NF4Jy3HnG1J9xVB)
- [Primeira tentativa: Aeroporto de Guarulhos (SBGR)](https://colab.research.google.com/drive/1B1BYDwXB1Wsrxw2zQsSkqUQ5oVHhXiy2)

No Colab, basta usar `Ambiente de execução → Executar tudo`. Se os CSVs do VRA não estiverem disponíveis, o notebook os baixa diretamente do servidor da ANAC.
