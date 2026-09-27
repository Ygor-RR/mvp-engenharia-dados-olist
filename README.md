# MVP de Engenharia de Dados — E-commerce Olist

Pipeline de dados ponta a ponta desenvolvido como MVP de Engenharia de Dados, utilizando o dataset público de e-commerce da Olist e o Databricks Free Edition.

## Objetivo

Construir um pipeline capaz de transformar dados brutos de e-commerce em informações organizadas e prontas para análise, utilizando a Arquitetura Medalhão:

- Bronze: dados brutos;
- Silver: dados tratados e padronizados;
- Gold: dados modelados para análise.

O projeto busca responder perguntas relacionadas a:

1. Receita e desempenho por categoria de produto;
2. Prazo médio e taxa de atraso por estado;
3. Relação entre atraso na entrega e satisfação dos clientes;
4. Distribuição de pagamentos e parcelamento;
5. Diferenças entre entregas intraestaduais e interestaduais.

## Fonte dos dados

Foi utilizado o **Brazilian E-Commerce Public Dataset by Olist**, disponibilizado no Kaggle em https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce.

O conjunto contém dados de:

- Pedidos;
- Itens dos pedidos;
- Pagamentos;
- Avaliações;
- Produtos;
- Clientes;
- Vendedores;
- Geolocalização;
- Tradução de categorias de produtos.

Os dados foram carregados em um Volume do Unity Catalog no Databricks.

## Tecnologias utilizadas

- Databricks Free Edition;
- Apache Spark;
- PySpark;
- SQL;
- Delta Lake;
- Unity Catalog;
- GitHub;
- Arquitetura Medalhão.

## Organização do pipeline

### Bronze

Armazenamento dos dados brutos carregados a partir dos arquivos CSV, preservando a estrutura original da fonte.

### Silver

Tratamento e padronização dos dados, incluindo:

- Conversão de tipos;
- Tratamento de datas;
- Deduplicação;
- Tratamento de valores nulos;
- Padronização de categorias;
- Validação de dados inconsistentes.

### Gold

Modelagem dos dados para análise, com criação de tabelas fato e dimensão, incluindo:

- `fato_itens_pedidos`;
- `fato_pagamentos`;
- `dim_cliente`;
- `dim_vendedor`;
- `dim_produto`;
- `dim_tempo`.

## Qualidade de dados

Durante o processo foi identificada uma inconsistência na coluna `review_score`, que apresentava alguns valores incompatíveis com o tipo numérico esperado.

Para evitar falhas na pipeline, foi utilizado o tratamento defensivo com `TRY_CAST`, permitindo converter somente os valores numéricos válidos e tratar os demais como nulos.

Também foram realizadas verificações de:

- Valores nulos;
- Duplicidades;
- Tipos de dados;
- Consistência de datas;
- Valores financeiros;
- Integridade das tabelas Gold.

## Notebooks

- [`ingestao_tratamento_olist.ipynb`](ingestao_tratamento_olist.ipynb)  
  Contém a ingestão, o tratamento, a construção das camadas Bronze, Silver e Gold e as consultas analíticas.

- [`unity_catalog.ipynb`](unity_catalog.ipynb)  
  Contém a criação e a documentação das tabelas e colunas no Unity Catalog.

## Relatório completo

O relatório completo apresenta o contexto do projeto, a coleta dos dados, a modelagem, o catálogo de dados, o pipeline, as validações de qualidade, as respostas às perguntas de negócio, os screenshots de evidência e a autoavaliação.

📄 [Acessar o relatório completo em PDF](./MVP%20DE%20ENGENHARIA%20DE%20DADOS.pdf)

## Repositório

Este projeto foi desenvolvido para fins acadêmicos como um MVP de Engenharia de Dados.
