# Modelo para Apresentação do Projeto 2-Final - Modelo Conceitual e Lógico


## Modelo Conceitual
<img src='images/ModeloConceitual.png' width="600px" height="auto">

## Modelo Lógico

~~~
Nutrient(_ID_, Public_id, Nutrient_name)

Food(_ID_, Public_id, Food_name, description, food_group, food_subgroup)

Nutrient_On_Food(_ID_, nutrient_ID, food_ID, Orig_Content, unit, quantity_Ref)
  nutrient_ID: chave estrangeira para Nutrient
  food_ID: chave estrangeira para Food

Recipes(_Recipe_ID_, Title, Region)

Units(_Unit_Name_, grams)

Ingredients(_Recipe_ID_, _Food_ID_, quantity, food_name, unit)
  Recipe_ID: chave estrangeira para Recipes
  Food_ID: chave estrangeira para Food
  Unit: chave estrangeira para Units

~~~
