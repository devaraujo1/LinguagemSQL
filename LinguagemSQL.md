# Aula 1: Introdução e Fundamentos de Bancos de Dados

## 1. Introdução à Linguagem SQL

### O que é SQL?
* **SQL** significa Linguagem de Consulta Estruturada (frequentemente pronunciado como *SeQuel*).
* É a linguagem padrão utilizada para interagir com dados armazenados em bancos de dados, permitindo que os usuários realizem desde consultas simples até cálculos complexos em grandes conjuntos de dados (ex: encontrar o "Gasto Total").

### Por que aprender SQL?
* **Falar com Dados**: Permite a comunicação direta com os sistemas de dados.
* **Alta Demanda**: É uma habilidade muito requisitada no mercado de trabalho em diversas funções técnicas.
* **Caminhos de Carreira**: Conhecimento essencial para Desenvolvedores de Software, Analistas de Dados, Cientistas de Dados e Engenheiros de Dados.
* **Padrão da Indústria**: Funciona em conjunto com as principais ferramentas do mercado, como Power BI, Tableau, Kafka, Spark e Synapse.

---

## 2. Sistemas de Gerenciamento de Banco de Dados (DBMS)

Um DBMS atua como a interface entre o usuário e o banco de dados.
* **Hospedagem**: Normalmente, os bancos de dados são hospedados em servidores físicos ou na nuvem.
* **Disponibilidade**: Funcionam 24/7 para garantir o acesso ininterrupto aos dados.
* **Interação**: Aplicativos (APPs), ferramentas de BI (como Power BI) e usuários enviam consultas SQL ao DBMS para recuperar e gerenciar os dados.

### Tipos de Bancos de Dados


* **Relacional**
  * Microsoft SQL Server, MySQL, PostgreSQL, Amazon Redshift 
* **Documento**
  *  MongoDB 
* **Grafo**
  *  Neo4j 
* **Chave-Valor**
  *  Redis, Amazon DynamoDB 
* **Base de Coluna**
  *  Apache Cassandra 

--------------------------------------------------------------------------------

# Estrutura Relacional

## 3. Estrutura de um Banco de Dados Relacional

Os bancos de dados relacionais seguem uma organização hierárquica rigorosa:
1. **Servidor**: O host principal que contém um ou mais bancos de dados.
2. **Banco de Dados**: O contêiner de alto nível para os dados (ex: "Vendas" ou "RH").
3. **Esquema (Schema)**: Agrupamentos lógicos dentro de um banco de dados (ex: "Pedidos" ou "Clientes").
4. **Tabela**: Onde os dados são fisicamente armazenados em linhas e colunas.

### Componentes de uma Tabela
* **Colunas**: Categorias verticais que definem os tipos de dados.
* **Linhas**: Registros horizontais individuais.
* **Célula**: Unidade única de dado na interseção exata de uma linha com uma coluna.
* **Chave Primária**: O identificador único para cada registro dentro da tabela.
* **Armazenamento**: As tabelas são armazenadas no disco físico como arquivos de banco de dados.

### Principais Tipos de Dados
O SQL utiliza tipos de dados específicos para delimitar o formato da informação que pode ser armazenada:
* **Numéricos**: 
  * `INT` – Números inteiros.
  * `DECIMAL` – Valores numéricos com frações.
* **Texto/String**:
  * `CHAR` – Strings de comprimento fixo.
  * `VARCHAR` – Strings de comprimento variável.
* **Data & Hora**:
  * `DATE` – Formato `YYYY-MM-DD`.
  * `TIME` – Formato `HH:MM:SS`.


--------------------------------------------------------------------------------

# Aula 2.1: Tipos de Comandos SQL

## 2. Tipos de Comandos SQL

A linguagem SQL é dividida em subconjuntos com base na finalidade dos comandos:

* **DDL (Linguagem de Definição de Dados)**: Define ou modifica a estrutura do banco. 
  * CREATE – Criar novos bancos de dados ou tabelas.
  * ALTER – Modificar a estrutura existente.
  * DROP – Deletar um banco ou tabela. 
  
* **DQL (Linguagem de Consulta de Dados)**: Recupera os dados armazenados.
  * SELECT – O comando principal para buscar dados. 
 
* **DML (Linguagem de Manipulação de Dados)**: Gerencia os dados nas tabelas.
  * INSERT – Adicionar novos registros.
  * UPDATE – Modificar registros existentes.
  * DELETE – Remover registros. 
 
* **DCL (Linguagem de Controle de Dados)**: Gerencia permissões e acessos dos usuários.  
  * GRANT – Concede privilégios de acesso.
  * REVOKE – Revoga privilégios. 
  
* **TCL (Linguagem de Controle de Transações)**: Gerencia transações para garantir integridade.  
  * COMMIT – Salva mudanças permanentemente.
  * ROLLBACK – Desfaz mudanças se ocorrer um erro.
  * SAVEPOINT – Define um ponto para rollback parcial. 
 

--------------------------------------------------------------------------------
# Aula 2.2: Aprofundamento em DDL (Data Definition Language)

O **DDL** é a categoria de comandos usada para definir e criar o "esqueleto" (a planta estrutural ou *blueprint*) dos objetos do banco de dados. 

## Ações Principais do DDL:

### 1. CREATE (Criando Objetos)
Usado para construir novos bancos de dados ou tabelas do zero. Ao criar uma tabela, é obrigatório definir as colunas e seus respectivos tipos de dados.
```sql
-- Criando um Banco de Dados
CREATE DATABASE Venda;

-- Criando uma Tabela
CREATE TABLE Produto (
    ProdutoID INT,
    ProdutoName VARCHAR(100),
    Preco DECIMAL
);
2. ALTER (Modificando Objetos)
Utilizado para atualizar a estrutura de um objeto já existente (ex: adicionar ou remover colunas) sem precisar excluir a tabela inteira e perder os dados.
-- Adicionando uma nova coluna
ALTER TABLE Produto
ADD Categoria VARCHAR(50);

-- Removendo uma coluna existente
ALTER TABLE Produto
DROP COLUMN Preco;
3. DROP (Excluindo Objetos)
O comando DROP tem caráter destrutivo. Ele remove permanentemente toda a estrutura do objeto e todos os registros armazenados nele.
-- Excluindo a tabela permanentemente
DROP TABLE Produto;
```
--------------------------------------------------------------------------------
### Resumo de DDL


* CREATE
  * **Ação**: Construir novo
  * **Objeto Afetado**: Afetado: Banco de Dados, Tabela, Schema

* ALTER
  * **Ação**: Modificar existente
  * **Objeto Afetado**: Colunas, Tipos de Dados

* DROP
  * **Ação**: Excluir permanentemente
  * **Objeto Afetado**: Afetado: Banco de Dados, Tabela, Schema

# Aula 3.1: DML - Linguagem de Manipulação de Dados

## DML vs DDL
Nós usamos DML (Data Manipulation Language) para alterar os dados reais armazenados dentro de nossas tabelas. Enquanto a DDL (Linguagem de Definição de Dados) define o "recipiente", a DML nos permite gerenciar o conteúdo interno.

## Operações Principais de DML
Nós contamos com três comandos primários para manipular nossos dados :
* **`INSERT`**: Nós usamos para adicionar novas linhas de dados em uma tabela .
* **`UPDATE`**: Nós usamos para modificar informações existentes dentro de uma tabela.
* **`DELETE`**: Nós usamos para remover registros específicos de uma tabela.

### 1. Adicionando Dados (INSERT)
Quando queremos popular nossas tabelas, temos dois métodos principais para inserir dados:

**Método 1: Entrada Manual (VALUES)**
Nós especificamos manualmente os valores que queremos adicionar a colunas específicas].
```sql
INSERT INTO Products (ProductID, ProductName, Price)
VALUES (1, 'Laptop', 1200.00);
```

Método 2: INSERT usando SELECT Nós também podemos inserir dados em uma tabela de destino consultando-os de uma tabela de origem
```sql
INSERT INTO TargetTable
SELECT * FROM SourceTable
WHERE condition;
```

2. Modificando Dados (UPDATE)

Quando precisamos editar registros existentes, usamos a instrução UPDATE
. Regra: Sempre use WHERE para evitar atualizações em massa não intencionais. Devemos ser muito cuidadosos ao incluir uma cláusula WHERE; caso contrário, atualizaremos todas as linhas da tabela
```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE <condition>;
```

3. Removendo Dados (DELETE)
Quando os dados não são mais necessários, usamos o comando DELETE
. De forma semelhante ao update, usamos uma cláusula WHERE para filtrar linhas específicas
```sql
DELETE FROM table_name
WHERE <condition>;
```

Tabela Resumo de DML

| Comando  | Ação que tomamos | Efeito nos Dados
| :---     |:---              | :----
| INSERT   | Adicionar        | Novas linhas são criadas
| UPDATE   | Editar           | Valores existentes são alterados
| DELETE   | Remover          | Linhas selecionadas são apagadas


---

### Aula 3.2: Anatomia de uma Declaração SQL

## Elementos de uma Instrução SQL
Uma instrução SQL é composta de elementos específicos que dizem ao banco como processar o pedido:
* **Comentários (`--`)**: Documentam o código .
* **Palavras-chave**: Reservadas e com significado especial.
* **Cláusulas**: Blocos que constroem a instrução.
* **Funções**: Ferramentas internas que transformam dados.
* **Identificadores**: Nomes de objetos de banco como tabelas ou colunas.
* **Operadores**: Usados para comparações.
* **Literais**: Valores constantes ou strings.

## Estrutura Básica de Consulta
```sql
SELECT column_name
FROM table_name;
```

Filtragem e Ordenação
```sql
WHERE: Filtra registros com condições específicas
.
ORDER BY: Ordena resultados em ordem ascendente ou descendente
```

Ferramentas Avançadas de Seleção
```sql
DISTINCT: Remove duplicatas

TOP / LIMIT: Especifica o número de registros retornados
```

**Aliases (AS):** 
Usados para dar nome temporário a tabelas ou colunas para tornar os resultados mais legíveis
.

Ordem Lógica de Avaliação

O SQL não processa as cláusulas na ordem escrita
. A execução lógica padrão é
```sql
1.FROM
2.WHERE
3.SELECT
4.ORDER BY
```



### Aula 4.1: Chave Estrangeira


## O que é Chave Estrangeira (Foreign Key)?
A chave estrangeira é um campo de uma tabela que aponta para a chave primária de outra tabela.

👉 Ela serve para criar relacionamento entre tabelas . Em outras palavras, é o que “liga” uma tabela à outra em um banco de dados relacional .

## Por que precisamos dela?
**Sem chave estrangeira :**
* As tabelas ficam isoladas.
* Não há garantia de que os dados combinam.
* Podem existir registros “órfãos” (sem relação real).

**Com chave estrangeira :**
* O banco garante integridade dos dados.
* Evita erros e inconsistências.
* Representa relações do mundo real (cliente → pedido, aluno → matrícula, etc.).

## Exemplo Prático

**Tabela de Clientes**
| Id (PK) | Nome |
| :--- | :--- |
| 1 | Ana Silva  |
| 2 | João Souza  |

**Tabela de Pedidos**
| Id (PK) | clienteId (FK) | Total |
| :--- | :--- | :--- |
| 1001 | 1 | 3500  |
| 1002 | 2 | 200  |
| 1003 | 1 | 1200  |

--------------------------------------------------------------------------------


# Aula 4.2: Normalização de Banco de Dados

## O que é Normalização?
Normalizar um banco de dados é organizar as informações para que cada dado exista apenas uma vez, evitando repetição, erros e bagunça nas tabelas .

### Forma Não Normalizada (UNF)
Todos os dados estão misturados em uma única tabela, com grupos repetidos . Dados do cliente ficam repetidos, o que torna difícil consultar e manter .
*(Exemplo: Uma tabela única contendo 

OrderI| CustomerName | CustomerPhone | Products | Total 
| :--- | :--- | :--- | :--- | :--- 
1001| Ana Silva | 9999-1111 | Notebook, Mouse | 3500 
1002| João Souza | 9888-2222 | Teclado | 200
1003| Ana Silva | 9999-1111 | Monitor, Cabo HDMI, Mouse | 1200
 

### Primeira Forma Normal (1FN)
* **Regra:** Os campos devem ser atômicos (um único valor por célula).
* **Problema restante:** Os dados do cliente continuam duplicados para cada produto do pedido, o total pertence apenas ao pedido, e ainda existem dependências (responsabilidades) na mesma tabela.

| OrderID | CustomerName | CustomerPhone | Product | Total |
| :--- | :--- | :--- | :--- | :--- |
| 1001 | Ana Silva | 9999-1111 | Notebook | 3500 |
| 1001 | Ana Silva | 9999-1111 | Mouse | 3500 |
| 1002 | João Souza | 9888-2222 | Teclado | 200 |
| 1003 | Ana Silva | 9999-1111 | Monitor | 1200 |
| 1003 | Ana Silva | 9999-1111 | Cabo HDMI | 1200 |
| 1003 | Ana Silva | 9999-1111 | Mouse | 1200 |

### Segunda Forma Normal (2FN)
* **Regras:** Deve estar na 1FN e removemos dependências parciais. Cada entidade passa a ter sua própria tabela e sua própria chave primária.
* **Problema restante:** O Produto é um texto livre, está "solto" na tabela.

| CustomerID | Nome | Telefone |
| :--- | :--- | :--- |
| 1 | Ana Silva | 9999-1111 |
| 2 | João Souza | 9888-2222 |

| OrderID | CustomerID | Total |
| :--- | :--- | :--- |
| 1001 | 1 | 3500 |
| 1002 | 2 | 200 |
| 1003 | 1 | 1200 |

| OrderID | Produto |
| :--- | :--- |
| 1001 | Notebook |
| 1001 | Mouse |
| 1002 | Teclado |
| 1003 | Monitor |
| 1003 | Cabo HDMI |
| 1003 | Mouse |

### Terceira Forma Normal (3FN)
* **Regras:** Deve estar na 2FN e remover dependências transitivas . Campos não-chave DEVEM depender apenas da chave .
* **Solução:** O Produto ganha sua própria tabela com um `ProductID`, e a tabela de vínculos do pedido usa apenas o `OrderID` e o `ProductID`.

| CustomerID | Nome | Telefone |
| :--- | :--- | :--- |
| 1 | Ana Silva | 9999-1111 |
| 2 | João Souza | 9888-2222 |

| ProductID | NomeProduto |
| :--- | :--- |
| 10 | Notebook |
| 11 | Mouse |
| 12 | Teclado |
| 13 | Monitor |
| 14 | Cabo HDMI |

| OrderID | CustomerID | Total |
| :--- | :--- | :--- |
| 1001 | 1 | 3500 |
| 1002 | 2 | 200 |
| 1003 | 1 | 1200 |

| OrderID | ProductID |
| :--- | :--- |
| 1001 | 10 |
| 1001 | 11 |
| 1002 | 12 |
| 1003 | 13 |
| 1003 | 14 |
| 1003 | 11 |


## Resultado da Normalização
O banco de dados agora possui :
* Ausência de redundância.
* Relacionamentos claros (Chaves Estrangeiras).
* Estrutura relacional correta.
* Melhor desempenho e manutenção facilitada.

Isso torna os bancos de dados :
* Mais eficientes e confiáveis.
* Mais fáceis de escalar e entender.

--------------------------------------------------------------------------------
# Aula 5: Métodos de Combinação na Linguagem SQL


## JOINS (Adição de Colunas - Horizontal)
Conectamos tabelas lateralmente através de uma coluna comum (Chave).
* **Inner Join:** Apenas o que existe em ambas as tabelas .
* **Left Join:** Mantemos tudo da tabela à esquerda e trazemos o que houver da direita .
* **Right Join:** Mantemos tudo da direita e trazemos o que houver da esquerda.
* **Full Join:** Trazemos tudo de ambos os lados, independentemente de haver correspondência .

**Como Usamos Joins:**
Ao escrevermos um JOIN, devemos especificar a relação :
```sql
SELECT
    TabelaA.Nome,
    TabelaB.Pais
FROM
    TabelaA INNER JOIN TabelaB ON TabelaA.id = TabelaB.id;
```


**Operadores SET (Adição de Linhas - Vertical)**

 - Empilhamos resultados de consultas diferentes, desde que tenham a mesma estrutura de colunas.

 - UNION: Combina os resultados e remove duplicados.

 - UNION ALL: Combina tudo, incluindo duplicados (é mais rápido).

 - EXCEPT / MINUS: Mostra o que existe no primeiro conjunto mas não no segundo.

INTERSECT: Mostra apenas o que é comum a ambos os conjuntos.
```sql
Como Usamos Operadores SET:
SELECT Nome FROM Clientes
UNION
SELECT Nome FROM Funcionarios;
```


# Aula 6: Linguagem SQL - Funções de Linha Única no SQL


## O que são Funções SQL?
* **Definição:** Conjuntos de instruções que recebem um ou mais valores de entrada e retornam um valor de saída.
* **Processo:** Entrada (Valor) -> FUNÇÃO -> Saída (Novo Valor) .

### Utilidade:
* **Limpeza:** Remover espaços extras ou caracteres indesejados .
* **Transformação:** Alterar formatos de data ou converter textos .
* **Análise:** Realizar cálculos rápidos por linha .

## Funções de Texto (String Functions)

### Manipulação
| Função | Descrição |
| :--- | :--- |
| **CONCAT** | Une duas ou mais strings (ex: Nome + Sobrenome) . |
| **UPPER / LOWER** | Converte o texto para MAIÚSCULO ou minúsculo . |
| **TRIM** | Remove espaços em branco no início e no fim . |
| **REPLACE** | Substitui um caractere ou trecho de texto por outro . |

### Extração e Medida
| Função | Descrição |
| :--- | :--- |
| **LEN** | Retorna a quantidade de caracteres . |
| **LEFT / RIGHT** | Extrai caracteres a partir da esquerda ou direita . |
| **SUBSTRING** | Extrai uma parte específica do texto de qualquer posição . |

## Funções de Data e Hora (Date & Time)

### Cálculos
| Função | Descrição |
| :--- | :--- |
| **DATEADD** | Adiciona um intervalo (dias, meses, anos) a uma data . |
| **DATEDIFF** | Calcula a diferença entre duas datas . |

### Extração de Partes e Conversão
| Função | Descrição |
| :--- | :--- |
| **YEAR, MONTH, DAY** | Extraem o ano, mês ou dia numérico . |
| **DATENAME** | Retorna o nome da parte da data (ex: "Janeiro", "Segunda-feira") . |
| **CAST / CONVERT** | Alteram o tipo de dado (ex: de Texto para Data) . |
| **FORMAT** | Define como a data será exibida (ex: 'dd/MM/yyyy') . |

## Tratamento de Valores Nulos (NULL Functions)
**Por que tratar nulos?** Evitar erros em cálculos e garantir relatórios precisos .

| Principais Funções | Descrição |
| :--- | :--- |
| **ISNULL(valor, substituto)** | Se o valor for nulo, substitui por outro . |
| **COALESCE(v1, v2, ...)** | Retorna o primeiro valor não nulo de uma lista . |
| **NULLIF(v1, v2)** | Retorna nulo se os dois valores forem iguais . |
| **IS NULL** | Operador para filtrar registros sem dados . |

## Lógica Condicional (CASE Statement)
* **O que é:** Funciona como um "SE... ENTÃO" (IF... THEN) dentro do SQL .
* **Aplicações:**
  * Categorização: Se Venda > 1000 então 'Premium' .
  * Padronização: Converter 'Alemanha' para 'DE', 'Brasil' para 'BR' .

**Sintaxe Básica**:
```sql
CASE
  WHEN Condição THEN Resultado
  ELSE Resultado_Padrão
END
```

## Funções Aninhadas (Nested Functions)
* **Conceito:** Usar uma função como entrada para outra função .

**Exemplo Prático:**
* `LEN(LOWER(LEFT('Maria', 2)))` 
* `LEFT('Maria', 2)` -> 'Ma' 
* `LOWER('Ma')` -> 'ma' 
* `LEN('ma')` -> Resultado Final: 2 

## Conclusão
Funções de linha única retornam um resultado para cada linha . Podem ser usadas no SELECT (para exibir), no WHERE (para filtrar) e no ORDER BY (para ordenar) .

---

# Aula 7: Linguagem SQL - Funções de Agregação


## O que são Funções de Agregação?
As funções de agregação processam um conjunto de valores para retornar um único valor resumido . Elas são essenciais para transformar dados brutos em informações estratégicas .

### Tabela de Funções de Agregação

| Função | Finalidade | Tipos de Dados Compatíveis |
| :--- | :--- | :--- |
| **COUNT** | Conta o número de registros (linhas) . | Qualquer tipo . |
| **SUM** | Soma os valores de uma coluna . | Apenas Numéricos . |
| **AVG** | Calcula a média aritmética dos valores . | Apenas Numéricos . |
| **MAX** | Identifica o valor máximo (maior) . | Numéricos, Datas e Texto . |
| **MIN** | Identifica o valor mínimo (menor) . | Numéricos, Datas e Texto . |

## Cláusula GROUP BY (Agrupamento)
A cláusula `GROUP BY` é utilizada para organizar linhas que possuem valores idênticos em grupos . Ela é quase sempre utilizada em conjunto com as funções de agregação mencionadas acima .

* **Condensação de Registros:** A principal função do `GROUP BY` é reduzir (achatar) múltiplos registros em uma única linha de resumo por grupo .
* **Cálculos em Nível de Grupo:** Ao contrário de uma conta simples no banco de dados inteiro, o agrupamento permite realizar Cálculos de Nível de Grupo (ex: calcular o faturamento total por categoria de produto em vez do faturamento total da loja) .

### Exemplo Prático
Se você tem uma tabela de vendas e usa `GROUP BY regiao`, o SQL pegará todas as vendas de "Sul", "Norte" e "Leste" e entregará apenas uma linha para cada região com os totais somados .
