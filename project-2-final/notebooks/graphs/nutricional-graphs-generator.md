### Comandos Cypher para criar os nós do modelo lógico

#### Recipes
```
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/interim/Recipes.csv' AS line,
CREATE (:Recipes {id: line.Recipe_ID, name: line.Title, region: line.Region})
```
```
CREATE INDEX FOR (r:Recipes) ON (r.id)
```
```
MATCH (n:Recipes) RETURN n LIMIT 25
```

#### Nutrient
```
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/graphs/nutrient-graphs.csv' AS line,
CREATE (:Nutrient {id: line.id, name: line.name})
```
```
CREATE INDEX FOR (n:Nutrient) ON (n.id)
```
```
MATCH (n:Nutrient) RETURN n LIMIT 25
```


#### Food
```
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/graphs/food-graphs.csv' AS line,
CREATE (:Food {id: line.id, name: line.name})
```
```
CREATE INDEX FOR (f:Food) ON (f.id)
```
```
MATCH (n:Food) RETURN n LIMIT 25
```