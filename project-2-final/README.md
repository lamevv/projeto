# Modelo de Apresentação da Final

# Modelo para Apresentação da Entrega Final do Projeto

## Motivação e Contexto

> O projeto proposto tem como foco central a investigação da composição e análise das receitas culinárias de diferentes regiões do mundo, visando compreender e mapear os macronutrientes presentes em cada prato. A motivação por trás desse estudo concentra-se na crescente conscientização sobre a importância da alimentação para a saúde, bem como na compreensão da diversidade gastronômica global. Dessa maneira, este projeto visa também entender como a concentração de determinado macronutriente se relaciona com os hábitos alimentares, contexto histórico e geográfico de cada região, contribuindo para uma compreensão mais profunda da relação entre alimentação e saúde.

## Slides

### Apresentação Prévia
> Coloque aqui o link para o PDF da apresentação prévia

### Apresentação Final
> Coloque aqui o link para o PDF da apresentação final

## Modelo Conceitual

> ![ER](images/ModeloConceitual.png)

## Modelos Lógicos

- Modelo Lógico Relacional
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

- Modelo Lógico de Grafos
> ![Grafos](images/ModeloLogicoGrafos.jpg)

## Dataset Publicado
> Se ao tratar e integrar os dados originais foram produzidas novas bases relacionais ou de grafos, elencar essas bases.

> TODO --> CORRIGIR A BASE DE DADOS FINAL E COLOCAR OS ARQUIVOS NA PASTA PROCESSED COMO ESPECIFICADO

título do arquivo/base | link | breve descrição
----- | ----- | -----
`Recipes.csv` | [data/interim/Recipes.csv](https://github.com/lamevv/projeto/blob/main/project-2-final/data/interim/Recipes.csv) | `Informações das receitas, incluindo um identificador único (chave primária), a descrição da receita e a região à qual ela pertence`
`ProcessedNutrient.csv` | [data/interim/ProcessedNutrient.csv](https://github.com/lamevv/projeto/blob/main/project-2-final/data/interim/ProcessedNutrient.csv) | `Especificação e descrição dos nutrientes considerados na análise da composição dos ingredientes`
`Units-Conversion.csv` | [data/interim/Units-Conversion.csv](https://github.com/lamevv/projeto/blob/main/project-2-final/data/interim/Units-Conversion.csv) | `Unidades de medida adotadas para a análise da composição de cada ingrediente em uma receita, acompanhada de seus valores padrão expressos em gramas`
`IngredientOnFood2.csv` | [data/interim/IngredientOnFood2.csv](https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/interim/IngredientOnFood2.csv) | `Detalhamento da composição de cada receita, listando ingredientes acompanhados de suas respectivas quantidades e unidade de medida`
`ProcessedContent.csv` | [data/interim/ProcessedContent.csv](https://github.com/lamevv/projeto/blob/main/project-2-final/data/interim/ProcessedContent.csv) | `Avalia a concentração específica de nutrientes em cada ingrediente para uma quantidade de referência`

> Os arquivos finais do dataset publicado devem ser colocados na pasta `data`, em subpasta `processed`. Outros arquivos serão colocados em subpastas conforme seu papel (externo, interim, raw). A diferença entre externo e raw é que o raw é em formato não adaptado para uso. A pasta `raw` é opcional, pois pode ser substituída pelo link para a base original da seção anterior.
> Coloque arquivos que não estejam disponíveis online e sejam acessados pelo notebook. Relacionais (usualmente CSV), XML, JSON e CSV ou triplas para grafos.
> Este é o conjunto mínimo de informações que deve constar na disponibilização do Dataset, mas a equipe pode enriquecer esta seção.

## Bases de Dados

título da base | link | breve descrição
----- | ----- | -----
`FooDB` | <a href='https://foodb.ca'>`https://foodb.ca`</a> | `Descrição nutricional em macro e micronutrienes dos ingredientes`
`CulinaryDB` | <a href='https://cosylab.iiitd.edu.in/culinarydb/'>`https://cosylab.iiitd.edu.in/culinarydb`</a> | `Composição de receitas regionais, detalhando ingredientes e suas quantidades correspondentes`

## Detalhamento do Projeto
> Apresente aqui detalhes do processo de construção do dataset e análise. Nesta seção ou na seção de Perguntas podem aparecer destaques de código como indicado a seguir. Note que foi usada uma técnica de highlight de código, que envolve colocar o nome da linguagem na abertura de um trecho com `~~~`, tal como `~~~python`.
> Os destaques de código devem ser trechos pequenos de poucas linhas, que estejam diretamente ligados a alguma explicação. Não utilize trechos extensos de código. Se algum código funcionar online (tal como um Jupyter Notebook), aqui pode haver links. No caso do Jupyter, preferencialmente para o Binder abrindo diretamente o notebook em questão.

~~~python
df = pd.read_excel("/content/drive/My Drive/Colab Notebooks/dataset.xlsx");
sns.set(color_codes=True);
sns.distplot(df.Hemoglobin);
plt.show();
~~~

> Se usar Orange para alguma análise, você pode apresentar uma captura do workflow, como o exemplo a seguir e descrevê-lo:
![Workflow no Orange](images/orange-zombie-meals-prediction.png)

> Coloque um link para o arquivo do notebook, programas ou workflows que executam as operações que você apresentar.

> Aqui devem ser apresentadas as operações de construção do dataset:
* extração de dados de fontes não estruturadas como, por exemplo, páginas Web
* agregação de dados fragmentados obtidos a partir de API
* integração de dados de múltiplas fontes
* tratamento de dados
* transformação de dados para facilitar análise e pesquisa

> Se for notebook, ele estará dentro da pasta `notebook`. Se por alguma razão o código não for executável no Jupyter, coloque na pasta `src` (por exemplo, arquivos do Orange ou Cytoscape). Se as operações envolverem queries executadas atraves de uma interface de um SGBD não executável no Jupyter, como o Cypher, apresente na forma de markdown.

TODO --> Luiz e Eliel pfv expliquem o processamento dos dados que vcs fizeram nos notebooks nessa parte (filtragem de colunas, sincronia de chaves estrangeiras, etc ...)

- Tratamento dos dados da composição das receitas do `CulinaryDB`

A tabela [04_Recipe-Ingredients_Aliases](https://raw.githubusercontent.com/lamevv/projeto/main/project-2-final/data/raw/culinarydb/04_Recipe-Ingredients_Aliases.csv) do `CulinaryDB` não segue uma padronização específica para apresentar a participação de um ingrediente em uma dada receita, condensando toda essa informação por meio de um texto no atributo `Original Ingredient Name`. Alguns dos formatos apresentados são: *3/4 cup mayonnaise*, *1 tablespoon butter*, *2 (4 ounce) skinless, boneless chicken breast halves*, *1 1/2 pounds ground beef*, entre outros. 

Desse modo, no notebook [units-of-measurement-data](https://github.com/lamevv/projeto/blob/main/project-2-final/notebooks/units-of-measurement-data.ipynb) foram realizadas uma série de extrações e normalizações para identificar a **quantidade** e **unidade de medida** referentes a participação dos ingredientes nas receitas. Além disso, o notebook detalha a elaboração da tabela de unidades de medida, em que cada unidade selecionada possui uma equivalência padrão em gramas, simplificando e padronizando o processo de verificação da presença dos ingredientes nas receitas.

## Evolução do Projeto
> Relatório de evolução, descrevendo as evoluções na modelagem do projeto, dificuldades enfrentadas, mudanças de rumo, melhorias e lições aprendidas. Referências aos diagramas, modelos e recortes de mudanças são bem-vindos.
> Podem ser apresentados destaques na evolução dos modelos conceitual e lógico. O modelo inicial e intermediários (quando relevantes) e explicação de refinamentos, mudanças ou evolução do projeto que fundamentaram as decisões.
> Relatar o processo para se alcançar os resultados é tão importante quanto os resultados.

## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises

> Apresente os resultados da forma mais rica possível, com gráficos e tabelas. Mesmo que o seu código rode online em um notebook, copie para esta parte a figura estática. A referência a código e links para execução online pode ser feita aqui ou na seção de detalhamento do projeto (o que for mais pertinente).

> Liste aqui as perguntas de pesquisa/análise e respectivas análises. Nem todas as perguntas precisam de queries que as implementam. É possível haver perguntas em que a solução é apenas descrita para demonstrar o potencial da base. Abaixo são ilustradas três perguntas, mas pode ser um número maior a critério da equipe.
>
### Perguntas/Análise com Resposta Implementada

> As respostas às perguntas podem devem ser ilustradas da forma mais rica possível com tabelas resultantes, grafos ou gráficos que apresentam os resultados. Os resultados podem ser analisados e comentados. Veja um exemplo de figura ilustrando uma comunidade detectada no Cytoscape:

> ![Comunidade no Cytoscape](images/cytoscape-comunidade.png)

#### Pergunta/Análise 1
> * Quais são os alimentos mais presentes nas receitas de cada região?
>   
>   * Utilizando funções de agregamento, descobrimos o quão frequente é um ingrediente na composição dos alimentos de uma região. Dessa forma, definindo-se os parâmetros, pegamos aqueles que tinham frequências acima da média das frequências relacionadas à cada região. O resultado foi que obtivemos alimentos que são muito populares, como ovo, pão e água.

~~~SQL
DROP VIEW IF EXISTS MostFrequentIngredients;

CREATE VIEW MostFrequentIngredients AS
SELECT F.Region, I.Food_Id, I.Food_Name, COUNT(Food_Id) frequencia
    FROM (SELECT Region, AVG(frequencia) std_frequencia, STDDEV(frequencia) desvpad_frequencia
                FROM (SELECT Region, Food_Id, COUNT(Food_Id) frequencia
                      FROM Recipes R JOIN Ingredients I ON R.Recipe_Id = I.Recipe_Id
                      GROUP BY Region, Food_Id
                      ORDER BY Region, frequencia DESC) F
          GROUP BY Region) F, Recipes R, Ingredients I
    WHERE  R.Region = F.Region AND R.Recipe_Id=I.Recipe_Id
    GROUP BY F.Region, I.Food_Id, I.Food_Name
    HAVING COUNT(Food_Id) >= std_frequencia + desvpad_frequencia
    ORDER BY frequencia DESC;
~~~



#### Pergunta/Análise 2
> * Quais os alimentos e receitas que mais contribuem para a ingestão de açúcares, gorduras e proteínas para cada região?
>   
>   * Traçamos um perfil nutricional de cada receita, que contém informações dos macronutrientes (proteínas, gorduras e carboidratos) presentes. A partir disso, podemos filtrar receitas com altos teores desses macronutrientes, de acordo com a região.

~~~SQL
CREATE TABLE Recipe_Profile (
    Recipe_Id INT NOT NULL,
    weight FLOAT DEFAULT 0,
    fat FLOAT DEFAULT 0,
    carbo FLOAT DEFAULT 0,
    protein FLOAT DEFAULT 0,
    PRIMARY KEY(Recipe_Id),
    FOREIGN KEY(Recipe_Id)
        REFERENCES Recipes(Recipe_Id)
            ON UPDATE NO ACTION
            ON DELETE NO ACTION
);
~~~
~~~SQL
UPDATE Recipe_Profile RP
SET RP.fat = (SELECT COALESCE(SUM(RIF.fat), 0) FROM RecipeIngredientFat RIF WHERE RIF.Recipe_Id = RP.Recipe_Id),
    RP.protein = (SELECT COALESCE(SUM(RIP.protein), 0) FROM RecipeIngredientProtein RIP WHERE RIP.Recipe_Id = RP.Recipe_Id),
    RP.carbo = (SELECT COALESCE(SUM(RIC.carbo), 0) FROM RecipeIngredientCarbo RIC WHERE RIC.Recipe_Id = RP.Recipe_Id),
    RP.weight = (SELECT COALESCE(SUM(RI.qnt_grams), 0) FROM RecipeIngredients RI WHERE RI.Recipe_Id = RP.Recipe_Id);
~~~

#### Pergunta/Análise 3
> * Quais são as receitas mais equilibradas em termos de macronutrientes (proteínas, gorduras e carboidratos) para cada região? 
>   
>   * Através do perfil nutricional de cada receita, podemos definir se a receita é balanceada com base em parâmetros padrões de proteínas, gorduras e carboidratos. Na nossa análise, consideramos balanceado uma receita que seja composta com até 10% de gordura, 50% de carboidrato e pelo menos 10% de proteína.

#### Pergunta/Análise 4
> * Existe um diferença entre o perfil nutricional de diferentes regiões, de modo que uma seja mais balanceada do que a outra?
>   
>   * Traçando um perfil nutricional de cada região, com base nas receitas consumidas, foi possível constatar que o perfil nutricional das regiões, em geral, convergem para um perfil, dado que os valores de desvio padrão da quantidade de macronutrientes é pequeno.

~~~SQL
CREATE TABLE Region_Profile (
    Region VARCHAR(50),
    Food_Total_Weight_Kg FLOAT DEFAULT 0,
    Total_Fat FLOAT DEFAULT 0,
    Total_Protein FLOAT DEFAULT 0,
    Total_Carbo FLOAT DEFAULT 0,
    Per_Fat FLOAT DEFAULT 0,
    Per_Protein FLOAT DEFAULT 0,
    Per_Carbo FLOAT DEFAULT 0,
    PRIMARY KEY(Region)
);
~~~
~~~SQL
UPDATE Region_Profile RP
SET
    Food_Total_Weight_Kg = (SELECT COALESCE(SUM(RPC.recipe_weight/1000), 0) FROM RecipeProfileComplete RPC WHERE RPC.Region = RP.Region),
    Total_Fat = (SELECT COALESCE(SUM(RPC.total_fat/1000), 0) FROM RecipeProfileComplete RPC WHERE RPC.Region = RP.Region),
    Total_Carbo = (SELECT COALESCE(SUM(RPC.total_carbo/1000), 0) FROM RecipeProfileComplete RPC WHERE RPC.Region = RP.Region),
    Total_Protein = (SELECT COALESCE(SUM(RPC.total_protein/1000), 0) FROM RecipeProfileComplete RPC WHERE RPC.Region = RP.Region);

UPDATE Region_Profile RP
SET
    Per_Protein = Total_Protein/Food_Total_Weight_Kg,
    Per_Fat = Total_Fat/Food_Total_Weight_Kg,
    Per_Carbo = Total_Carbo/Food_Total_Weight_Kg; 
~~~

~~~SQL
SELECT STDDEV(Per_Fat) DSP_Fat, AVG(Per_Fat) AVG_Fat,
        STDDEV(Per_Protein) DSP_Protein, AVG(Per_Protein) AVG_Protein,
        STDDEV(Per_Carbo) DSP_Carbo, AVG(Per_Carbo) AVG_Carbo FROM Region_Profile;
~~~


### Perguntas/Análise Propostas mas Não Implementadas

#### Pergunta/Análise 1
> * Quais são as diferenças na distribuição de macronutrientes entre receitas de diferentes regiões do mundo?
>   
>   * Utilizando métricas estatísticas, é viável examinar a distribuição dos macronutrientes (carboidratos, açúcares e proteínas) entre as diversas regiões abordadas no estudo. A análise dos padrões alimentares globais não apenas proporciona um entendimento mais profundo da diversidade culinária, mas também suas implicações na saúde. Esse estudo pode contribuir na formulação de dietas personalizadas e específicas, ao mesmo tempo em que enriquece a compreensão dos hábitos alimentares em escala mundial.

#### Pergunta/Análise 2
> * Quais são os principais ingredientes e padrões de dietas que caracterizam regiões com baixos índices de doenças crônicas?
>   
>   * Ao analisar as distribuições de macronutrientes entre diferentes regiões e correlacionar esses dados com informações auxiliares sobre os índices de doenças crônicas em países ou regiões específicas, é possível conduzir uma análise que orienta políticas de saúde pública e diretrizes sobre novas dietas, oferecendo um ponto de partida para intervenções e estratégias de promoção da saúde.

#### Pergunta/Análise 3
> * Pergunta 3
>   
>   * Explicação em linhas gerais de como a base pode ser usada para responder esta pergunta e a sua relevância.

> Coloque um link para o arquivo do notebook que executa o conjunto de queries. Ele estará dentro da pasta `notebook`. Se por alguma razão o código não for executável no Jupyter, coloque na pasta `src`. Se as queries forem executadas atraves de uma interface de um SGBD não executável no Jupyter, como o Cypher, apresente na forma de markdown.
