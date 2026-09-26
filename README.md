# Em construção!!
## Resumo: Repositório para alocar projeto de análise de Fundos Imobiliários através de seus indicadores

## Introdução
Os fundos imobiliários, conhecidos com FIIs, são produtos do mercado financeiro que ganharam e vem ganhado bastante relevância. São fundos de investimento que investem no mercado imobiliário, em diversos setores, e negociam cotas na bolsa de valores brasileira. Cada cota representa uma porcentagem do fundo que dá direito ao comprador receber rendimentos das receitas que o fundo adquire com os ativos imobiliários adquiridos.

## Objetivo

O objetivo deste repositório é alocar um projeto de análise de fundos imobiliários através de alguns indicadores afim de analisar quais os melhores fundos para se investir. Não há uma pretensão de recomendação de compra e venda e sim uma análise quantitativa através dos dados para analisar e comparar quais fundos estão perfomando melhor.

## De onde vem os dados?

Os dados relacionados a valores de ativos, passivos e patrimônio líquido dos fundos imobiliários tem origem no site da CVM que disponibiliza gratuitamente o download desses dados. A base dos preços vem da coleta usando a biblioteca finbr criada por Renan Moretto e os dados de dividendos são vem da biblioteca Yahoo Finance.

biblioteca finbr: https://github.com/renanmoretto/finbr

## Armazenamento

O armazenamento é feito em um banco de dados no Supabase

## Construção do banco de dados

O banco de dados até o momento foi estruturado com 04 tabelas.
  1. Tabela Periodo com três colunas: datareferencia, ano e mes. Os dados são de janeiro de 2023 até dezembro de 2025 agrupados mensalmente.
  2. Tabela fundonome com três colunas: cnpj, ticket e segmento. Armazena dados dos fundos como CNPJ, ticket de negociação na bolsa de valores e o segmento que o fundo atua no mercado imobiliário
  3. Tabela Preco com cinco colunas: Id, datareferencia, preco, ticket e dividendo. A tabela tem dados extraídos no Python usando a  biblioteca yfinance no qual os dados extraídos são: ...
  4. Tabela fundocomplemento com sete colunas: cnpj, datareferencia, numero_cotistas, valor_ativo, patrimonio_liquido, cotas_emitidas e valor_passico. É a principal tabela porque armazena os dados oriundos da CVM.

<img width="1280" height="779" alt="Diagrama em branco" src="https://github.com/user-attachments/assets/5ebccc05-b114-4c20-87fb-dd626002c069" />


## DataViz

Como forma de visualizar os indicadores e realizar comparações escolhi a ferramenta Power BI como DataViz e monitorar os indicadores. Através da conexão com o PostgreSQL, os dados são direcionados ao PBI e por lá faço o tratamento para a visualização.

## Indicadores

1. P/VP
   Este indicador demostra a relação entre o preço real do fundo imobiliário na bolsa de valores e o preço patrimonial do fundo. O preço pratimonial é calculado pela divisão do valor do patrimônio liquído pelo total de cotas do fundo, assim chegamos ao preço patrimonial para cada cota. Após isso, realizamos a segunda divisão que é o preço negociado pelo preço patrimonial. Valores abaixo de 1,0 indicam que o fundo está sendo negociado abaixo do que vale em patrimônio, ou seja, está subvalorizado. Valores acima de 1,0 indicam que o fundo está sendo supervalorizado do que realmente vale patrimonialmente. O indicador P/VP é importante para termos uma dimensão de como o mercado está precificando os fundos, mas como todo indicador não pode ser analisado sozinho porque é necessário entender o contexto do fundo e as últimas notícias e movimentos.
2. Dividend Yield
   Este indicador demonstra a relação entre o rendimento distribuído pelo preço da cota negociada na bolsa de valores. O resultado é um valor em porcentagem que indica o quanto os rendimentos distribuídos por cota representam do preço atual. Um Dividend Yield alto significa um bom presságio. O resultado que sai é o resultado por mês, então o que foi feito foi anualizar esse dividend yield para ter uma ideia do quanto seria por ano se mantido as condições de distribuição e preço.

## Análise P/VP x DY
Por fim, com os dois indicadores calculados podemos traçar um gráfico de dispersão para saber como os fundos estão distribuídos. No eixo X, o indicador P/VP e no eixo Y o indicador DY. Então, um fundo que está para baixo e para a direita é o melhor cenário porque indica um P/VP abaixo de 1,0 e um DY alto
