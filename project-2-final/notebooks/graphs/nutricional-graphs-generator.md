### Comandos Cypher para criar os nós do modelo lógico

#### Recipes
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/interim/Recipes.csv' AS line,
CREATE (:Recipes {id: line.Recipe_ID, name: line.Title, region: line.Region})
~~~
~~~cypher
CREATE INDEX FOR (r:Recipes) ON (r.id)
~~~
~~~cypher
MATCH (n:Recipes) RETURN n LIMIT 25
~~~


#### Nutrient
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/graphs/nutrient-graphs.csv' AS line,
CREATE (:Nutrient {id: line.id, name: line.name})
~~~

~~~cypher
CREATE INDEX FOR (n:Nutrient) ON (n.id)
~~~

~~~cypher
MATCH (n:Nutrient) RETURN n LIMIT 25
~~~



#### Food
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/graphs/food-graphs.csv' AS line,
CREATE (:Food {id: line.id, name: line.name})
~~~

~~~cypher
CREATE INDEX FOR (f:Food) ON (f.id)
~~~

~~~cypher
MATCH (n:Food) RETURN n LIMIT 25
~~~
