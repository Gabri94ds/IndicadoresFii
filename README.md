# Nome do repositório: IndicadoresFii
## Resumo: Repositório para alocar projeto de análise de Fundos Imobiliários através de seus indicadores

## Introdução
Os fundos imobiliários, conhecidos com FIIs, são produtos do mercado financeiro que ganharam e vem ganhado bastante relevância. São fundos de investimento que investem no mercado imobiliário, em diversos setores, e negociam cotas na bolsa de valores brasileira. Cada cota representa uma porcentagem do fundo que dá direito ao comprador receber rendimentos das receitas que o fundo adquire com os ativos imobiliários adquiridos.

## Objetivo

O objetivo deste repositório é alocar um projeto de análise de fundos imobiliários através de alguns indicadores afim de analisar quais os melhores fundos para se investir. Não há uma pretensão de recomendação de compra e venda e sim uma análise quantitativa através dos dados para analisar e comparar quais fundos estão perfomando melhor.

## De onde vem os dados?

Os dados vem dos dados abertos disponibilizados pela CVM, órgão que regulamenta o mercado acionário brasileiro, e mensalmente o órgão disponibiliza dados de todos os fundos de investimento como número de cotas, ativo, passivo, patrimônio líquido...

## Armazenamento

Os dados são baixados em formato CSV e são armazenados dentro de um banco de dados em PostgreSQL. Os dados são inseridos no banco via script feito em Python.

## Construção do banco de dados

O banco de dados até o momento foi estruturado com 04 tabelas.
  1. Tabela Periodo com uma coluna, datareferencia, com dados de janeiro de 2023 até maio de 2025 agrupados mensalmente no formato 01/mm/yyyy
  2. Tabela FundoNome armazena dados dos fundos como CNPJ, ticket de negociação na bolsa de valores e segmento que o fundo atua no mercado imobiliário
  3. Tabela Preco é uma tabela com dados extraídos no Python na biblioteca yfinance no qual extraí dados de preço de fechamento dos fundos no período de janeiro de 2023 até maio de 2025 agrupados mensalmente também no formato 01/mm/yyyy.
  4. Tabela fundocomplemento é a principal tabela, pois armazena os dados vindo da CVM. Somente alguns dados foram selecionados para compor esta tabela sob a periodicidade de janeiro de 2023 até maio de 2025 também sob o formato 01/mm/yyyy.

  Abaixo, uma imagem de como ficou os relacionamentos entre as tabelas. A coluna Chave presente nas tabelas Preco e fundocomplemento são colunas criadas após a inserção dos dados e são as concatenações das colunas datareferencia com ticket. Na coluna fundocomplemento não há a informação de ticket e, portanto, a informação veio via JOIN da tabela FundoNome pela coluna CNPJ.

<img width="1862" height="916" alt="drawSQL-image-export-2025-07-23" src="https://github.com/user-attachments/assets/fa347aca-ccce-4a95-9389-e96a235385cd" />

## DataViz

## Indicadores

## 
