# Modelo para Apresentação do Projeto 1 - Modelo Conceitual e Lógico

## Slides da Apresentação
> Coloque aqui o link para o PDF da apresentação

## Motivação e Contexto

> O projeto visa traçar o perfil nutricional médio por países e regiões com base nas suas respectivas receitas populares, buscando comparar e compreender as diferenças alimentares globais. A motivação do estudo reflete o contexto de crescente preocupação com a saúde e nutrição, dado o papel crucial da dieta no bem-estar humano.
A análise da diversidade culinária por regiões permite entender como ingredientes e técnicas culinárias influenciam as refeições. Além disso, compreender o perfil nutricional médio destes pratos populares também possibilita a compreensão mais profunda das escolhas alimentares globais e suas implicações para a saúde pública.

## Bases de Dados

título da base | link | breve descrição
----- | ----- | -----
`FooDB` | <a href='https://foodb.ca'>`https://foodb.ca`</a> | `Descrição nutricional (macro e micronutrientes) dos ingredientes`
`CulinaryDB` | <a href='https://cosylab.iiitd.edu.in/culinarydb/'>`https://cosylab.iiitd.edu.in/culinarydb`</a> | `Receitas populares (com ingredientes e suas quantidades) de acordo com suas regiões`

## Modelo Conceitual

> Coloque aqui a imagem do modelo conceitual em ER ou UML, como o exemplo a seguir:
> ![ER Taxi](images/er-taxi.png)

## Modelos Lógicos

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

#### Pergunta/Análise 1
> * Quais são os alimentos mais consumidos na população de uma dada região estudada?
>   
>   * Cruzando as informações das receitas mais populares de certo país através do CulinaryDB, podemos reconhecer os padrões de alimentação e analisar os alimentos mais consumidos por essa população.


#### Pergunta/Análise 2
> * Quais os alimentos e receitas que mais contribuem para a ingestão de açúcares, gorduras e sódio para cada país/região?
>   
>   * Reconhecendo os padrões de alimentação de cada região através das receitas e cruzando isso com as informações nutricionais dos ingredientes, podemos definir quais deles têm maior contribuição na ingestão desses componentes.


#### Pergunta/Análise 3
> * Quais são as receitas mais equilibradas em termos de macronutrientes (proteínas, gorduras e carboidratos) para cada país/região? 
>   
>   * Analisando os macronutrientes dos ingredientes de cada receita, podemos definir os macronutrientes da própria receita e assim compará-las para definir a mais equilibrada.

#### Pergunta/Análise 4
> * Qual a região com o perfil nutricional mais equilibrado?
>   
>   * Tendo como base as receitas mais consumidas em determinada região e traçando o perfil nutricional de cada uma, podemos definir o perfil da região com um todo.


### Perguntas/Análise Propostas mas Não Implementadas

### Pegunta/Análise 1

> * Quais são os ingredientes comuns em receitas de regiões com altas taxas de longevidade?
>
>   * Podemos identificar os ingredientes das receitas populares das regiões filtradas através de dados auxiliares como: Expectativa de vida e Índice de Segurança Alimentar da região analisada. Assim, é possível investigar o padrão de consumo comum destas regiões, contribuindo assim para uma melhor compreensão da relação entre alimentação e longevidade.


### Pergunta/Análise 2
> * Existe uma correlação entre a taxa de obesidade e a falta de alimentos saudáveis nas receitas populares em uma região?
>
>   * Através de informações de Taxa de obesidade, Consumo de Frutas e Vegetais, Consumo de Alimentos Processados podemos filtrar as regiões e investigar uma correlação entre esses fatores e a carência de alimentos saudáveis nas receitas populares das regiões. A relação identificada pode ser crucial para formar políticas de saúde, promover escolhas alimentares mais saudáveis e uma possível reflexão da influência dos padrões culturais de alimentação na saúde de uma dada população.

### Pergunta/Análise 3
> * Quais são as melhores receitas para pessoas com restrições alimentares para um determinado país?
>
>   * Fontes de proteínas para veganos/vegetarianos
Receitas com baixo teor de gordura
Fontes de cálcio para intolerantes à lactose
