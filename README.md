# Dashboard Executivo de Vendas & Performance — Seu Poroca

Este repositório contém a solução completa de Engenharia e Análise de Dados desenvolvida para o estabelecimento **Seu Poroca**. O objetivo do projeto foi centralizar, consolidar e tratar dados pulverizados de vendas, transformando relatórios fragmentados e sem conexões diretas em painéis executivos dinâmicos para suporte à tomada de decisão.

---

## Desafio de Negócio

O cliente possuía diversos relatórios operacionais extraídos de seu sistema de vendas (formatos `.xls`/`.xltx`), porém com os seguintes entraves:

1. **Bases Desfragmentadas:** Informações soltas divididas por períodos ou tipos de dados (ex: quantidades vendidas de produtos, faturamento diário, quebra por formas de pagamento).
2. **Ausência de Chaves de Ligação:** Faltava um modelo relacional unificado que conectasse o faturamento por forma de pagamento, a movimentação de itens do cardápio e a evolução do ticket médio.
3. **Limpeza e Padronização:** Presença de dados despadronizados e impossibilidade de consolidação direta via ferramenta tradicional sem pré-processamento prévio.

---

## Arquitetura da Solução & Ferramentas

* **Ingestão & Concatenação (ETL):** `Python` / `Pandas`
  * Leitura de múltiplos arquivos `.xls.xltx`, empilhamento/concatenação e exportação para base unificada.
* **Modelagem & BI Principal:** `Power BI`
  * Limpeza final, criação de colunas calculadas/DAX e construção do painel em formato `.pbix` / `.pdf`.
* **Dashboard Web Interativo:** `Gemini AI` + `HTML5/CSS3/Chart.js`
  * Geração de protótipo de dashboard executivo web customizado para navegadores e dispositivos móveis.

---

## Fluxo de Trabalho (Pipeline de Dados)

### 1. Concatenação e Tratamento Inicial com Python (`Pandas`)
Devido ao volume desfragmentado de arquivos gerados pelo sistema, utilizou-se o script Python em ambiente Jupyter/Colab para unir os dados com precisão:
* Leitura de tabelas separadas por bloco de tempo (`vendas_por_forma_pagamento.xls.xltx`, etc.).
* Concatenação via `pd.concat()` garantindo a integridade dos atributos (`Quantidade`, `Valor Pago`, `Taxa`, `Faturado`).
* Exportação da base estruturada para alimentação nos painéis visuais.

### 2. Modelagem e Construção no Power BI
Com a base unificada, o Power BI foi utilizado para estruturar os visualizadores executivos e aplicar métricas operacionais:
* **KPIs Principais:** Faturamento Total, Faturamento por Couvert Artístico/Pessoal e Ticket Médio por atendimento.
* **Análise Temporal:** Evolução mensal das vendas no período.
* **Desempenho de Cardápio:** Rankings Top 5 de cervejas mais vendidas e pratos/comidas mais consumidos.
* **Análise Financeira:** Distribuição de formas de pagamento (Crédito, Débito, PIX, Dinheiro) e respectivas taxas aplicadas.

### 3. Protótipo Web Interativo (Gemini + Chart.js)
Aproveitando os dados tratados, foi utilizado o **Gemini** para codificar uma versão **web standalone em HTML5/CSS3** orientada à identidade visual e UI/UX do estabelecimento:
* Inclusão de filtros dinâmicos por intervalo de datas (mês inicial/final) e filtro por produto.
* Renderização de gráficos usando **Chart.js** (Linha de Tendência com duplo eixo Y para Ticket Médio vs Faturamento, Rosca para Formas de Pagamento e Barras para Cervejas).
* Tabela interativa com badges por categoria de produto (Cervejas, Caldinhos, Beliscar, etc.).

---

## Indicadores Mapeados (KPIs)

* **Faturamento Bruto Total**
* **Faturamento Total de Couvert Pessoal** 
* **Ticket Médio**
* **Ranking Top 5 Cervejas** 
* **Ranking Top 5 Comidas** 
* **Participação por Forma de Pagamento** 

---

## Estrutura de Arquivos do Repositório

```text
├── data/
│   ├── base_vendas_seuporoca.xlsx      # Jupyter Notebook com o script Python de concatenação em Pandas
├── dashbaords/
│   ├── dashboard_seu_poroca.pdf        # Relatório final exportado em Power BI
│   ├── dashboard_seuporoca_gemini.html # Dashboard web interativo gerado via Gemini (Chart.js)
├── docs/
│   ├── kpi´s.txt                       # Escopo de KPIs solicitados pelo cliente
│   ├── prompt.txt                      # Prompt de orientações de UI/UX e parâmetros enviados ao Gemini
└── README.md                           # Documentação oficial do projeto



