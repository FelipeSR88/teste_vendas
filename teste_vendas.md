-2.3. Queries de Exploração

Scripts SQL para as perguntas de negócio e transformações adicionais

Pergunta 1: Total de vendas por mês

SELECT 
    DATE_TRUNC('month', data_venda) AS mes,
    SUM(valor_total) AS total_vendas
FROM fato_venda
GROUP BY DATE_TRUNC('month', data_venda)
ORDER BY mes;

-- Pergunta 1: Total de vendas por categoria de produto

SELECT 
    dp.categoria,
    SUM(fv.valor_total) AS total_vendas
FROM fato_venda fv
JOIN dim_produto dp ON fv.id_produto = dp.id_produto
GROUP BY dp.categoria
ORDER BY total_vendas DESC;


Pergunta 2: Top 5 produtos em valor total vendido

SELECT 
    dp.nome_produto,
    SUM(fv.valor_total) AS total_vendido
FROM fato_venda fv
JOIN dim_produto dp ON fv.id_produto = dp.id_produto
GROUP BY dp.nome_produto
ORDER BY total_vendido DESC
LIMIT 5;

-Pergunta 2: Top 5 produtos em quantidade vendida

SELECT 
    dp.nome_produto,
    SUM(fv.quantidade) AS total_quantidade
FROM fato_venda fv
JOIN dim_produto dp ON fv.id_produto = dp.id_produto
GROUP BY dp.nome_produto
ORDER BY total_quantidade DESC
LIMIT 5;

Pergunta 3: Ticket médio por cliente no último trimestre disponível

-- Identificar o trimestre mais recente
SELECT MAX(data_venda) AS ultima_data FROM fato_venda;

 Calcular ticket médio no trimestre correspondente (2023-01-01 a 2023-05-26)

SELECT 
    dc.nome_cliente,
    AVG(fv.valor_total) AS ticket_medio
FROM fato_venda fv
JOIN dim_cliente dc ON fv.id_cliente = dc.id_cliente
WHERE fv.data_venda BETWEEN '2023-01-01' AND '"2023-05-26"'
GROUP BY dc.nome_cliente
ORDER BY ticket_medio DESC;

Pergunta 4: Comparação de vendas por loja

SELECT 
    dl.nome_loja,
    SUM(fv.valor_total) AS total_vendas
FROM fato_venda fv
JOIN dim_loja dl ON fv.id_loja = dl.id_loja
GROUP BY dl.nome_loja
ORDER BY total_vendas DESC;

Pergunta 4: Comparação de vendas por região (estado)

SELECT 
    dl.estado,
    SUM(fv.valor_total) AS total_vendas
FROM fato_venda fv
JOIN dim_loja dl ON fv.id_loja = dl.id_loja
GROUP BY dl.estado
ORDER BY total_vendas DESC;
