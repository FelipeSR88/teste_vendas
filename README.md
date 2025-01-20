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

Determina o valor médio gasto por cliente no período de 2023-01-01 a 2023-05-26.

Comparação de vendas entre lojas ou regiões:

Compara as vendas totais por loja e por estado.

Scripts SQL:

Os scripts SQL utilizados para responder às perguntas de negócio estão organizados no arquivo queries.sql. Eles incluem:

Agregações por períodos de tempo (mês e trimestre).

Rankings de produtos mais vendidos.

Cálculo de ticket médio.

Comparações regionais.

4. Conexão com Power BI

Após restaurar o banco de dados, foi estabelecida a conexão com o Power BI para modelagem e visualização de dados. A conexão foi realizada utilizando o driver do PostgreSQL. Seguiram-se os seguintes passos:

Configuração da conexão:

No Power BI, foi selecionada a opção "Obter Dados" > "ODBC".

Inserido o endereço do servidor (localhost) e o nome do banco de dados (teste_vendas).

Credenciais de autenticação configuradas corretamente.

Configuração no Power Query:

Tabelas foram carregadas para o modelo de dados.

Relacionamentos entre as tabelas foram definidos com base nas chaves primárias e estrangeiras.

Criação de medidas DAX:

Fórmulas foram desenvolvidas para cálculos específicos, como:

Total de vendas

Lucro bruto

Retorno percentual

Variação mês a mês

Criação da tabela calendario 

5. Visualização de Dados no Power BI

Foi criado um dashboard no Power BI chamado Performance Vendas, contendo as seguintes visualizações e análises:

Indicadores principais (Cards):

Custo Total: R$44.630,00

Faturamento: R$75.832

Lucro Bruto: R$31.201,86

Retorno %: 70%

Gráficos:

Faturamento x Variação por mês:

![image](https://github.com/user-attachments/assets/c8b7da11-c63b-4b70-931e-563574097299)


Destaque para os valores e variações negativas em relação aos meses anteriores.

Faturamento por estado:

![image](https://github.com/user-attachments/assets/4aff961a-0c56-4ad9-88eb-076df9067dea)

Exemplo de destaque: faturamento em Belo Horizonte e São Paulo.

Faturamento por segmento:

Gráfico de barras que mostra a receita por diferentes segmentos de mercado (Segmento 1, Segmento 2, etc.).

![image](https://github.com/user-attachments/assets/daa21806-da1b-4150-9b39-ef965f28f52e)

Top 10 produtos:

Lista os produtos com maior faturamento em um gráfico de barras horizontal.

![image](https://github.com/user-attachments/assets/d5fdad39-0788-4e85-b86e-b075f18a5d13)

Produto 4 lidera com R$27.672, seguido pelo Produto 2 com R$21.795,64.

Tabela de detalhes:

Colunas incluem:

Nome do produto

Custo Total

Faturamento

Lucro Bruto

Retorno %

Potencial do produto de acordo com retorno (%) (classificações como Ouro, Prata, etc.)

Destaque para o Produto 17, com retorno de 479%.

![image](https://github.com/user-attachments/assets/fcd06e62-a88c-40b8-b5ad-37798e03230f)

6. Executando o Projeto

Abra o pgAdmin e conecte-se ao banco teste_vendas.

Copie e cole os scripts SQL no Query Tool.

Execute as consultas para obter os resultados desejados.

No Power BI, atualize os dados e visualize os resultados no dashboard.

7. Contato

Caso precise de suporte ou tenha dúvidas, entre em contato com o e-mail feliperocha159fgg@gmail.com
