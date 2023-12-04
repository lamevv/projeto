## Análise Nutricional - Banco de Dados em Grafos

#### Recipes
Criação dos nós
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/interim/Recipes.csv' AS line
CREATE (:Recipes {id: line.Recipe_ID, name: line.Title, region: line.Region})
~~~
Criação de um índice para o nó
~~~cypher
CREATE INDEX FOR (r:Recipes) ON (r.id)
~~~
Listagem dos nós
~~~cypher
MATCH (n:Recipes) RETURN n LIMIT 25
~~~

#### Nutrient
Criação dos nós
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/graphs/nutrient-graphs.csv' AS line
CREATE (:Nutrient {id: line.id, name: line.name})
~~~
Criação de um índice para o nó
~~~cypher
CREATE INDEX FOR (n:Nutrient) ON (n.id)
~~~
Listagem dos nós
~~~cypher
MATCH (n:Nutrient) RETURN n LIMIT 25
~~~



#### Food
Criação dos nós
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/graphs/food-graphs.csv' AS line
CREATE (:Food {id: line.id, name: line.name})
~~~
Criação de um índice para o nó
~~~cypher
CREATE INDEX FOR (f:Food) ON (f.id)
~~~
Listagem dos nós
~~~cypher
MATCH (n:Food) RETURN n LIMIT 25
~~~

#### Nutrient -> Food (Compose)
Criação da relação entre os nós Nutrient e Food
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/interim/ProcessedContent.csv' AS line
MATCH (f:Food {id: line.food_id})
MATCH (n:Nutrient {id: line.source_id})
CREATE (n)-[r:Compose {id: line.id}]->(f)
SET r.orig_content = line.orig_content,
    r.unit = line.unit,
    r.quantity_ref = line.quantity_ref
~~~
Listagem das relações
~~~cypher
MATCH p=()-[r:Compose]->() RETURN p LIMIT 25
~~~

#### Food -> Recipes (Produces)
Criação da relação entre os nós Food e Recipes
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/interim/IngredientOnFood2.csv' AS line
MATCH (f:Food {id: line.Food_ID})
MATCH (r:Recipes {id: line.Recipe_ID})
CREATE (f)-[p:Produces {id: line.id}]->(r)
SET p.quantity = line.quantity,
    p.unit = line.unit
~~~
Listagem das relações
~~~cypher
MATCH p=()-[r:Produces]->() RETURN p LIMIT 25
~~~