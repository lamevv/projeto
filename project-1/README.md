# Modelo para Apresentação do Projeto 1 - Modelo Conceitual e Lógico

## Slides da Apresentação
> Coloque aqui o link para o PDF da apresentação

## Motivação e Contexto

> Descrição do tema do projeto, incluindo motivação e contexto gerador.

## Bases de Dados
> Elencar as bases de dados fonte utilizadas no projeto.

título da base | link | breve descrição
----- | ----- | -----
`FooDB` | <a href='https://foodb.ca'>`https://foodb.ca`</a> | `Descrição nutricional (macro e micronutrientes) dos ingredientes`
`CulinaryDB` | <a href='https://cosylab.iiitd.edu.in/culinarydb/'>`https://cosylab.iiitd.edu.in/culinarydb`</a> | `Receitas populares (com ingredientes e suas quantidades) de acordo com suas regiões`

## Modelo Conceitual

> Coloque aqui a imagem do modelo conceitual em ER ou UML, como o exemplo a seguir:
> ![ER Taxi](images/er-taxi.png)

## Modelos Lógicos

> Coloque aqui o modelo lógico relacional dos bancos de dados relacionados ao modelos conceitual. Sugere-se o formato a seguir.

> Exemplo de modelo lógico relacional
~~~
NUTRIENTE(_Nome_, EhMacro)
GRUPO_INGREDIENTE(_Id_, Nome)
SUBGRUPO_INGREDIENTE(_Id_, Nome, IdGrupo)
  IdGrupo: chave estrangeira para GRUPO_INGREDIENTE(Id)

INGREDIENTE(_Id_, Nome, IdSubGrupo)
  IdSubGrupo: chave estrangeira para SUBGRUPO_INGREDIENTE(Id)

COMPOSICAO_INGREDIENTE(_NomeNutriente_, _IdIngrediente_, QuantidadeNutriente, CaloriasParciais)
NomeNutriente: chave estrangeira para NUTRIENTE(Nome)
  IdIngrediente: chave estrangeira para INGREDIENTE(Id)

RECEITA(_Id_, Nome, Região)
COMPOSICAO_RECEITA(_IdReceita_, _IdIngrediente_, NomeMedida, QuantidadeMedida)
  IdReceita: chave estrangeira para RECEITA(Id)
  IdIngrediente: chave estrangeira para INGREDIENTE(Id)

CATEGORIA(_Nome_, Descricao)
TIPO_RECEITA(_IdReceita_, _NomeCategoria_)
  IdReceita: chave estrangeira para RECEITA(Id)
  NomeCategoria: chave estrangeira para CATEGORIA(Nome)

MEDIDAS(_Nome_, QuantidadePadrao)
REGIAO(_Nome_)
PERFIL_NUTRICIONAL_RECEITA(_IdReceita_, Calorias, Carboidratos, Gorduras, Proteinas)
  IdReceita: chave estrangeira para RECEITA(Id)
PERFIL_NUTRICIONAL_REGIÃO(_NomeRegião_, Calorias, Carboidratos, Gorduras, Proteinas)
  NomeRegiao: chave estrangeira para REGIAO(Nome)
~~~

## Perguntas de Pesquisa/Análise

> Liste aqui as perguntas de pesquisa/análise. Nem todas as perguntas precisam de implementação associada. É possível haver perguntas em que a solução é apenas descrita para demonstrar o potencial da base. Abaixo são ilustradas três perguntas, mas pode ser um número maior a critério da equipe.

#### Pergunta/Análise 1
> * Pergunta 1
>   
>   * Explicação sucinta da análise que será feita.

#### Pergunta/Análise 2
> * Pergunta 2
>   
>   * Explicação sucinta da análise que será feita.

#### Pergunta/Análise 3
> * Pergunta 3
>   
>   * Explicação sucinta da análise que será feita.

### Perguntas/Análise Propostas mas Não Implementadas

#### Pergunta/Análise 1
> * Pergunta 1
>   
>   * Explicação em linhas gerais de como a base pode ser usada para responder esta pergunta e a sua relevância.

#### Pergunta/Análise 2
> * Pergunta 2
>   
>   * Explicação em linhas gerais de como a base pode ser usada para responder esta pergunta e a sua relevância.

#### Pergunta/Análise 3
> * Pergunta 3
>   
>   * Explicação em linhas gerais de como a base pode ser usada para responder esta pergunta e a sua relevância.
