Documentação - Queries e Exploração de Dados

Este projeto consiste na restauração de um banco de dados PostgreSQL e na execução de consultas para responder perguntas de negócio com base nos dados disponibilizados. O banco de dados foi carregado com tabelas dimensionais e de fatos, representando um ambiente de vendas.

1. Estrutura do Banco de Dados

As principais tabelas utilizadas no projeto são:

dim_produto: Contém informações sobre os produtos.

dim_cliente: Contém informações sobre os clientes.

dim_loja: Contém informações sobre as lojas.

fato_venda: Contém os dados transacionais de vendas, relacionando produtos, clientes e lojas.

2. Restauração do Banco de Dados

Passos Realizados:

Criado o banco de dados chamado teste_vendas no pgAdmin.

O arquivo teste_vendas.sql foi carregado utilizando a ferramenta de Query no pgAdmin:

Selecionado o banco de dados teste_vendas.

Carregado o conteúdo do arquivo no Query Tool.

Executado o script para criação e população das tabelas.

Verificado que todas as tabelas foram criadas com sucesso.

3. Consultas Realizadas

Perguntas de Negócio:

Total de vendas por mês:

Consulta para calcular o total vendido em cada mês.

Top 5 produtos em valor total vendido ou quantidade:

Identifica os produtos mais vendidos em termos de receita e quantidade.

Ticket médio por cliente no último trimestre:

Determina o valor médio gasto por cliente no período de 2023-01-01 a 2023-01-07.

Comparação de vendas entre lojas ou regiões:

Compara as vendas totais por loja e por estado.

Scripts SQL:

Os scripts SQL utilizados para responder às perguntas de negócio estão organizados no arquivo queries.sql. Eles incluem:

Agregações por períodos de tempo (mês e trimestre).

Rankings de produtos mais vendidos.

Cálculo de ticket médio.

Comparações regionais.

4. Conexão com o Power BI

Configuração da Conexão:

No Power BI, clique em Obter Dados > Banco de Dados PostgreSQL.

Insira as credenciais de conexão:

Servidor: localhost (ou o IP do servidor remoto).

Porta: 5432.

Banco de Dados: teste_vendas.

Autenticação: Informe o usuário e a senha do PostgreSQL.

Confirme a conexão e importe as tabelas desejadas (dim_produto, dim_cliente, dim_loja e fato_venda).

Resolvendo Problemas Comuns:

Caso haja erros de conexão, verifique o arquivo pg_hba.conf e as configurações de firewall para garantir que a porta 5432 esteja aberta.

5. Modelagem de Dados no Power Query

No Power Query, as tabelas foram carregadas e as relações foram definidas:

fato_venda foi conectada às tabelas dimensionais (dim_produto, dim_cliente, dim_loja) por meio das chaves primárias e estrangeiras.

Criação de colunas calculadas:

Ano-Mês: Para agregar as vendas por mês.

Receita Total: Multiplicando quantidade pelo preço unitário.

Normalização e exclusão de dados duplicados ou irrelevantes.

6. Construção de Fórmulas em DAX

Métricas Criadas:

Vendas Totais:

Vendas Totais = SUM(fato_venda[receita_total])

Ticket Médio:

Ticket Médio = [Vendas Totais] / DISTINCTCOUNT(fato_venda[id_cliente])

Top 5 Produtos:

Top 5 Produtos = TOPN(5, SUMMARIZE(dim_produto, dim_produto[nome_produto], "Receita", SUM(fato_venda[receita_total])), [Receita], DESC)

Medidas para Comparativos:

Crescimento Percentual Mensal:

Crescimento Mensal = DIVIDE([Vendas Totais] - CALCULATE([Vendas Totais], PREVIOUSMONTH(fato_venda[data_venda])), CALCULATE([Vendas Totais], PREVIOUSMONTH(fato_venda[data_venda])))

7. Apresentação do Modelo no Power BI

Páginas do Relatório:

Resumo Geral:

Gráficos de barras para vendas por mês.

Indicadores de ticket médio e receita total.

Análise de Produtos:

Tabela dinâmica mostrando o Top 5 produtos.

Gráficos de pizza para distribuição de receita.

Comparativo Regional:

Gráfico de mapas mostrando vendas por região.

Barras empilhadas comparando lojas.

Caso precise, envie as imagens dos gráficos para complementar o README!
