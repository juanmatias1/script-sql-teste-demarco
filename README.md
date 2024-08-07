# Projeto de Gestão de Aluguéis de Produtos

Este projeto contém scripts SQL para gerenciar uma tabela de aluguéis de produtos. Inclui a estrutura da tabela, cálculo do valor total de produtos alugados por pessoa, excluindo certos produtos, e a listagem de cores distintas dos produtos alugados após uma determinada data.

## Estrutura da Tabela

A tabela `AluguelProdutos` armazena informações sobre aluguéis de produtos, incluindo detalhes sobre a pessoa que alugou, o produto alugado, a cor do produto, a data do aluguel e o valor do aluguel.

```sql
CREATE TABLE AluguelProdutos (
    id_aluguel INT PRIMARY KEY AUTO_INCREMENT,
    id_pessoa INT NOT NULL,
    nome_pessoa VARCHAR(255) NOT NULL,
    id_produto INT NOT NULL,
    nome_produto VARCHAR(255) NOT NULL,
    cor_produto VARCHAR(50),
    data_aluguel DATE,
    valor_aluguel DECIMAL(10, 2)
);
```
## Consultas
1. **Valor Total de Produtos Alugados por Pessoa:**
```sql
SELECT 
    nome_pessoa, 
    SUM(valor_aluguel) AS valor_total
FROM 
    AluguelProdutos
WHERE 
    nome_produto NOT IN ('Carro', 'Raquete')
GROUP BY 
    nome_pessoa;
```

2. **Cores Distintas dos Produtos Alugados Após Julho/22:**
Esta consulta calcula o valor total dos produtos alugados por pessoa, excluindo os produtos "Carro" e "Raquete".
```sql
SELECT DISTINCT 
    cor_produto
FROM 
    AluguelProdutos
WHERE 
    data_aluguel > '2022-07-31';
```

## Como Usar
1. Crie a tabela AluguelProdutos no seu banco de dados utilizando a estrutura fornecida.
2. Insira os dados de aluguéis de produtos conforme necessário.
3. Utilize as consultas SQL fornecidas para obter as informações desejadas.
