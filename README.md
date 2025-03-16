# 📌 Consultas SQL - Análise de Vendas e Clientes

## 📖 Descrição

Este projeto contém consultas SQL que simulam a análise de um gestor para avaliar dados empresariais. As consultas exploram vendas por produto, distribuição geográfica dos clientes e insights relevantes para tomada de decisões.

## 📌 Funcionalidades

- Identificar os produtos mais vendidos por país.
- Analisar quais empresas compram mais e em quais locais estão localizadas.

## 🚀 Consultas SQL

### 1️⃣ Produtos Mais Vendidos por País

```sql
SELECT P.ProductID AS CODIGO, P.ProductName AS NOME, O.ShipCountry AS PAIS,
       MAX(OD.Quantity) AS QTD_VENDIDA
FROM Products P
INNER JOIN [Order Details] OD ON OD.ProductID = P.ProductID
INNER JOIN Orders O ON O.OrderID = OD.OrderID
GROUP BY P.ProductID, P.ProductName, O.ShipCountry
ORDER BY QTD_VENDIDA DESC;
```

📌 **Explicação:**
- Agrupa os produtos vendidos por país.
- Utiliza a função `MAX()` para encontrar a maior quantidade de vendas por produto.
- Ordena os resultados para mostrar os produtos mais vendidos primeiro.

### 2️⃣ Empresas que Mais Compram e Localização

```sql
SELECT C.CompanyName AS COMPANHIA, C.Country AS PAIS, C.City AS CIDADE,
       C.Phone AS TELEFONE, P.ProductName AS NOME_PRODUTO,
       MAX(OD.Quantity) AS QTD_VENDIDA, OD.ProductID AS CODIGO_DO_PRODUTO
FROM Customers C
INNER JOIN Orders O ON O.CustomerID = C.CustomerID
INNER JOIN [Order Details] OD ON O.OrderID = OD.OrderID
INNER JOIN Products P ON P.ProductID = OD.ProductID
GROUP BY C.CompanyName, C.Country, C.City, C.Phone, OD.ProductID
ORDER BY QTD_VENDIDA DESC;
```

📌 **Explicação:**
- Relaciona clientes (empresas) com os produtos comprados.
- Identifica a localização da empresa e a quantidade comprada.
- Ordena pela quantidade de produtos adquiridos, destacando os principais clientes.

## 🛠 Tecnologias Utilizadas

- **Banco de Dados Relacional (SQL)**
- **SQL Server** (ou compatível, como MySQL, PostgreSQL)

## 📝 Como Utilizar

1. Configure um banco de dados compatível.
2. Copie e cole as consultas em seu gerenciador SQL.
3. Execute as consultas e analise os resultados.

---

**© 2025 - Desenvolvido por Nicollas Meneses**

