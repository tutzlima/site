# R: Estudo Geral
### por Ruan Arthur Lima Santos

---

## Um guia nada pretensioso
  
Esse Markdown está baseado em um script que elaborei chamado "**Estudo Geral**". Não há aqui a pretensão de tornar o leitor um profissional formado no R -- algo que também não sou.

Na verdade, você sairá daqui, no máximo, medíocre, saberá o suficiente para realizar tarefas básicas que uma pessoa que utiliza o R necessita.

Outra observação: Se você espera por resumos e explicações decentes sobre **estatística** nesse documento, sinto muito, mas também não tenho esse propósito — até porque não sou da área da estatística.

**Reforço: O objetivo é te introduzir na linguagem e ensiná-l\* a fazer tarefas básicas**

Um último apontamento:  

As referências não estão de enfeite, é muito interessante que acesse os materiais utilizados no decorrer do script e, claro, que busque por mais fontes. Portanto, além das referências propriamente ditas — que não estão seguindo uma formatação —, deixarei alguns sites, canais etc que julgo interessantes.
  
---

## Baixando o R e Rstudio

**Um passo-a-passo para Windows**
1. Acesse o site do [Posit](https://posit.co/download/rstudio-desktop/)

1. Clique em "Install R"

    - Assim que a página carregar, clique em "Download for Windows"
    - Clique tanto em "base" quanto em "Rtools" e instale as versões mais recentes de ambas
    - Acesse a pasta na qual realizou os downloads 
    - Execute os arquivos

1. Volte para o site da Posit e clique em "Install Rstudio"

    - Acesse a pasta na qual realizou os downloads
    - Execute o arquivo

Caso seu sistema operacional seja [Mac]() ou [Linux](), basta clicar nos links disponíveis para o tutorial de instalação.

*Lembrando que, a depender do seu sistema operacional, algumas coisas vão variar e, logo, a forma de solucioná-las também!*

---

## Entendendo o layout
  
  
Por padrão, o R inicia com quatro janelas:
  
**1. Source**
  
É aqui onde escrevemos nossos scripts (código). Ou seja, é aqui que vamos escrever quando precisamos fazer uma tarefa nova ou, também, reutilizar scripts.
  
**2. Environments**
  
Como definir isso... "Environments" significa literalmente "ambientes". Não há necessidade de aprofundar agora nas outras abas, apenas saiba que será na aba principal da janela — o "Environment" — que irão aparecer os **objetos** utilizados, ou seja, os **vetores**, **dataframes** e entre outros.
  
**3. Console**

O console é uma "tela improvisada", nenhuma linha de código que desejamos no script deve ser escrita no console. Ele serve exclusivamente para operações momentâneas, testes, visualizações rápidas e, principalmente, mostrar os **erros** do código!

**4. Output**
  
A janela "saída" merece um pouco mais de atenção:

Na primeira aba, **Files**, está o local, o diretório que **você** se encontra, permitindo que você visualize suas pastas, scripts e documentos que acabe movendo, baixando ou exportando para o diretório. 
  
Em seguida temos o **Plots**, as "parcelas" se traduzido literalmente. Aqui será impresso os gráficos que construiremos a partir do R, seja por meio de funcionalidades nativas do R ou que instalaremos. 
  
**Packages** será uma seção que não usaremos muito e você entenderá o porquê mais a frente. Ainda assim, ela é bem intuitiva então não precisa se preocupar. 
  
Por fim, e talvez a mais importante de todas, **Help**. Visto que você está começando é compreensível se assustar com ela quando a utilizarmos pela primeira vez, mas, insisto, **não desista desta seção**. Como o nome diz, será ela quem vai te ajudar a encontrar informações sobre **funções**, **bibliotecas**, **argumentos** e o diabo que você puder imaginar. 
  
**html**
!!! Para mais informações:
[Rstudio User Guide](https://docs.posit.co/ide/user/ide/guide/ui/ui-panes.html)
  
---
## Atalhos básicos & sugestões para usar o Rstudio

- Posicionar o mouse ou simplesmente utilizar as setas do teclado para chegar em uma linha e apertar `Ctrl` + `Enter` irá executá-la. O mesmo ocorre caso aperte em `Run`, no canto superior da janela Source.

- `Ctrl` + `L` limpa a tela do Console.

- `Alt` + `-` cria a seta de atribuição `<-`.

- `Ctrl` + `Shift` + `m` cria o "pipe" `%>%`.
_(não se preocupe isso agora, apenas guarde a informação)_.

- `Shift` + `<- ->` você consegue selecionar mais facilmente alguma seção e adicioná-la entre parênteses ou aspas (também funciona para cima e para baixo).

- `Ctrl` + `Shift` + `1:4` deixa as janelas em tela cheia.

- `Shift` + `\` cria o sinal `|`, que significa _ou_, _or_, enfim.

Além desses atalhos, eu recomendo fortemente para você que está começando realizar as seguintes configurações:

1) Na parte superior, em `Tools`, vá em `Global Options`

2) Na seção `Appearance` configure o `Editor font` & `Editor theme` da forma que preferir (além do tamanho das fontes e a organização das janelas na seção `Pane Layout`)

3) E, por fim, ir na seção `Code` e marcar a opção `Soft-wrap R source files`, isso fará que, sempre que seu código chegue no fim da janela, ele quebre a linha automaticamente (ao invés de escrever infinitamente para os lados)

---

## Tipos de Dados no R

- `char` --> caracter, texto

- `num` --> numérico, seja inteiro (`int`) ou decimal (`double`)

- `logical` --> a clássica "booleana", **verdadeira** ou **falsa**

- `factor` --> variáveis categóricas

Duas pequenas observações antes de vermos os exemplos:
1) **Tudo que criamos no R são chamados de objetos.**
2) Os *"Hashtags"* ou sustenidos significam um comentário, não serão executados no código!

### Exemplos

- Numéricos

```r
a <- 10 # Atribuímos o valor "10" ao objeto "a"
```

Diferente de outras linguagens de programação, não há necessidade de declararmos o **tipo** de variável no R.

Observe:

```r!
5L -> b # Atribuímos o valor "5" ao objeto "b"
```

Ambos são tipos numéricos, porém, o objeto "b" é um numérico *inteiro*, isso é o "L" logo ao lado que determina. Veja:

```r
class(a) # numeric
class(b) # integer
```

- Caracteres

```r
a <- "Arthur"
b <- "Ana"

class(a) # character
class(b) # character
```

E se tentarmos realizar uma operação com esses objetos?

```r
a + b
```

O retorno será:

```r
Error in a + b : argumento não-numérico para operador binário
```

Somar letras? Não faz sentido, cuidado com isso!

- Lógico

```r
a <- T # No R, escrever T ou F significa "TRUE" e "FALSE"

class(a) # logical
```
Não darei exemplos sobre fatores no momento, paciência.

---

## Operadores

Logo de cara é preciso dizer que há dois tipos de operadores: **Matemáticos** e **Lógicos**.

#### MATEMÁTICOS

|Símbolos|Descrição|
|:--:|:--:|
|+|Soma|
|-|Subtração|
|*|Multiplicação|
|/|Divisão|
|^|Potenciação|

*Ah, mas onde estão os logarítmicos? As raízes quadradas? As médias aritméticas...*

Relaxe, na hora elas chegarão.

#### LÓGICOS

|Símbolos|Descrição|
|:--:|:--:|
|>|Maior que|
|<|Menor que|
|>=|Maior ou igual|
|<=|Menor ou igual|
|=|Atribuição ("recebe")|
|==|Comparação|
|!=|Diferente|
|%/%|Divisão de inteiros|

Conforme você utiliza o R, você irá se habituar ao uso destes operadores e quaisquer outros que possam estar faltando.

---

### Funções

Para alguns que possam estar apenas revisando, colocar funções aqui pode parecer estranho. Pessoalmente, acho que é necessário explicá-las desde já para que os demais itens sejam, de fato, compreensíveis.

**Função** nada mais é que um conjunto de códigos que executam determinadas atividades.

*A grossíssimo modo*, é isso.

O segundo ponto importante sobre funções são os **argumentos**.
Novamente, a grosso modo, argumentos são os *parâmetros*, as informações necessárias que a função **precisa** para funcionar.

Há também argumentos que são opcionais, são parâmetros adicionais, mas isso também será visto no momento correto.

Um exemplo de função? A tal média que acabamos de falar! Veja:

```r!
a <- 4L
b <- 6L
c <- c(a, b) # Não se preocupe muito com isso, apenas entenda que o nosso objeto "c" recebe "a" e "b"!

# Ou seja, criamos nossos objetos com valores numéricos inteiros
```

O que é a média (aritmética)? Basicamente, a soma de determinados elementos e, em seguida, dividir o resultado pelo número de elementos.

```r
mean(c) # 5
```

A média (`mean`) é uma função! Veremos logo o que são funções, mas que tal outro exemplo de operação matemática? Vejamos como se calcula a raiz quadrada no R:

```r
# A nossa função se chama sqrt(), se ligue:

sqrt(64) # 8

# ou

a <- 64
sqrt(a) # 8
```

Perceba, as funções sempre são escritas da seguinte forma: `function()`, ou seja, `nome_da_função` e `()`.

Dentro da nossa `function()` estão os argumentos, ou seja, `function(args)`

Nesse caso, `sqrt()` é a nossa função e `64` ou o objeto `a` são os argumentos -- sendo os números que serão calculados.

Um outro exemplo?

```r
log(100, 10) # 2
log(125,5) # 3
```

`log()` é a nossa função logarítimica.
`100` & `125` são o primeiro argumento
`10` & `5` são o segundo argumento

Por enquanto, basta guardar esse entedimento básico de funções.

---

### Vetores & Matrizes

Até agora, aprendemos a declarar objetos "simples" como `a` & `b` nos exemplos anteriores.

Porém, também declaramos o objeto `c`, que é um tipo de objeto mais complexo.

Vamos ver alguns desses objetos:

- Vetores

Vetores são objetos que

1) Armazenam **o mesmo tipo de dados**
2) Possuem **uma** dimensão

Calma, vamos por partes.

Um vetor só pode armazenar, por exemplo, dados numéricos inteiros. Outro, apenas caracteres, etc...

A respeito do segundo item, olhe a tabela a seguir:

|1L|2L|3L|4L
|---|---|---|---|

Perceba: Há somente uma dimensão, **uma linha** com **quatro colunas** e **somente um tipo de dado**. Isso é um vetor.

O nosso exemplo anterior `c` também é um vetor! 

Um último exemplo:

|Arthur|Ana|Beatriz|Paulo|
|---|---|---|---|

Uma dimensão e um tipo de dado.

- Matriz

As matrizes são, **simplesmente**, vetores com mais de uma dimensão (pse). Exemplo:

|1|2|3|
|---|---|---|
|4|5|6|
|7|8|9|

Um simples 3x3!

*"Ah, mas pra que serve essas coias?"*

*Calma, nengue...*

---

### Dataframes

Vamos lá, chegamos num ponto crucial para aprendizagem do R.

`dataframe` é, resumidamente, uma matriz que permite armezar **diferentes tipos de dados**.

As possibilidades agora são infinitas.

Vamos passar mais pra prática a partir de agora, então abra-te o Rstudio!

```r!
# O Rstudio possui alguns dataframes disponibilizados, justamente, para estudo.

# Vamos utilizar um dos mais famosos deles, o grandioso "airquality"!

data("airquality")

# "data" significa "dados"
# "airquality" é o nosso argumento

# Relaxe, já chamamos o dataframe! 

# Ele só está esperando pra ser usado.

# Vamos dar uma olhada no dataframe:

View("airquality")
```

Sem se amedontrar! Vamos entender o que estamos vendo.

 Feche essa janela ou simplesmente volte pro script!

Observe: `153 obs.` cento e cinquenta e três **linhas** ("observações" ou "casos") de `6 variables`, seis variáveis, seis **colunas!**

Que tal vermos o tipo de dados que cada coluna armazena?

```r
dplyr::glimpse(airquality)
```

Não pense em que diabos é esse `dplyr::glimpse()`, apenas olhe pro `console`!

Perceba que estamos vendo as variáveis do dataframe e entre `<>` os tipos delas.

"$Temp", por exemplo, é do tipo `<int>`

*Ah, por que esse cifrão?*

O cifrão é **uma** forma de você chamar as **colunas** de um dataframe.

Por exemplo:

```r
airquality$Temp 

# vai te mostrar as observações da coluna

airquality[,4]

# As chaves nos servem para limitar o que queremos ver!

# Nesse caso, queremos todas as linhas e a coluna 4.
```

Só para reforçar: As `[]` são **sempre** dessa forma: **linha, coluna**. Quando não escrevemos nada em um dos dois, significa que queremos todos, não fizemos seleções específicas.

Uma função muito importante do R para lidarmos com Dataframes é `summary.data.frame()` ou simplesmente `summary()`:

```r
summary(airquality)
```

Agora, todas as colunas do seu dataframe serão "sumarizadas", ou seja, resumidas!

Vamos observar o resumo da coluna `Ozone`:

```r
    Ozone
Min.   :  1.00
1st Qu.: 18.00
Median : 31.50
Mean   : 42.13
3rd Qu.: 63.25
Max.   :168.00
NA's   :37
```

`Min. : 1.00` é o valor mínimo que `Ozone` atingiu em todo o dataframe e `Median : 31.50` é a nossa mediana!

Em breve você verá que as informações mais importantes que o `summary()` nos oferece são os [quartis](https://www.youtube.com/watch?v=bky_JLhbc7k&pp=ygUgcXVhcnRpcyBlIHBlcmNlbnRpcyBNYXJjb3Mgdml0YWw%3D) e os NA'S.

*"NA'S?" Que diabo é isso?*

Logo veremos!

Mais importante pro momento é retornar ao nosso `summary()` e observar o seguinte: Me diga, meu bem, faz sentido obtermos quartis, médias e medianas de `Month` e `Day`? Não faz nenhum sentido!

Poderíamos, portanto, limitar a nossa função!

```r
summary(airquality[,c(1:4)])
```

Feinho, né? Mas vamos entender o que é isso aí:

`summary()` é a nossa função e `airquality` segue sendo nosso argumento. A diferença está nas `[]` que, se você prestou atenção, serve para limitar as coisas.

Logo, o que está acontecendo dentro das chaves é que estamos usando o `c()` ou *combine* e `:` para apontarmos ao R que queremos que ele traga das primeira à quarta coluna. 

Se decidíssimos escrever o que fizemos, seria algo assim:

```r
# [quero todas as linhas, concatene/combine(da coluna 1 à 4)]
```

Quer um outro exemplo do `c()`?

Digamos que você queira as cinco primeiras linhas de todas as colunas:
```r
airquality[c(1,2,3,4,5),]

# ou

airquality[c(1:5),]

```

Caso deseje realizar algum desses cálculos manualmente, basta fazer:

```r
mean(airquality$Ozone, na.rm = T)
```

[`na.rm = T`](https://stackoverflow.com/questions/58443566/what-does-na-rm-true-actually-means) significa dizer ao R que desejamos *remover* os NA'S ("remove").

Caso não faça isso, o retorno do código será `NA`.

---

### Outras formas de organizar os dados

#### Tibble

Tibble, tal como os Dataframes, é um formato tabular. Ou seja, apresenta os nossos dados como uma tabela, uma "planilha".

Porém, apresenta algumas particularidades que fazem com que ele seja, muitas vezes, preferível que o dataframe:

```r!

# install.packages("tibble")
# library(tibble)

as.data.frame(iris)

# Visualizando a base de dados "iris" nativa do Rstudio no formato dataframe

tibble::as.tibble(iris)

# Antes de observamos a diferença, foco no aviso!

# "Warning message:
# `as.tibble()` was deprecated in tibble 2.0.0.
# ℹ Please use `as_tibble()` instead.
# ℹ The signature and semantics have changed, see `?as_tibble`."

# O Rstudio está nos informando que a nossa função "as.tibble()" está "depreciada"! Ou seja, ela não é mais a função correta, está desatualizada!

tibble::as_tibble(iris)

```


#### Dataset's

#### Tidy ou "Organizado"

#### Não tidy

---

> ## Instalação no macOS
> ### Instalando o R
> 1. **Baixe o R:**
>   - Visite o site do [CRAN (The Comprehensive R Archive Network)](https://cran.r-project.org).
>   - Clique em "Download R for macOS".
>2. **Instale o R:**
>   - Após o download, abra o arquivo `.pkg` baixado.
>   - Siga as instruções do instalador para concluir a instalação.
> ### Instalando o RStudio
> 1. **Baixe o RStudio:**
>   - Visite o site do [RStudio](https://posit.co/download/rstudio-desktop/).
>   - Selecione a versão para macOS e baixe o instalador.
> 2. **Instale o RStudio:**
>   - Abra o arquivo `.dmg` baixado.
>   - Arraste o ícone do RStudio para a pasta `Applications`.
> ### Verificando a instalação
> 1. **Verifique a instalação do R:**
>   - Abra o Terminal.
>   - Digite `R` e pressione Enter. Você deve ver a interface de linha de comando do R.
> 2. **Verifique a instalação do RStudio:**
>   - Abra o RStudio a partir da pasta `Applications`.
> ---
> ## Instalação no Linux
> ### Instalando o R
> Para sistemas baseados em Debian (como Ubuntu):
> 1. **Adicione o repositório CRAN:**
>    ```bash!
>    sudo apt update
>    sudo apt install --no-install-recommends software-properties-common dirmngr
>    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 51716619E084DAB9
>    sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu focal-cran40/'
> 2. **Instale o R:**
>    ```bash
>    sudo apt update
>    sudo apt install r-base
> Para sistemas baseados em **Red Hat** (como **Fedora**):
> 1. **Adicione o repositório CRAN:**
>   - Crie um arquivo `R.repo` em `/etc/yum.repos.d/` com o seguinte conteúdo:
>      ```bash!
>      name=R Project
>      baseurl=https://cran.r-project.org/bin/linux/redhat/el9/x86_64/
>      gpgcheck=1
>      gpgkey=https://cran.r-project.org/bin/linux/redhat/RPM-GPG-KEY-R-CRAN enabled=1
> 2. **Instale o R:**
>    ```bash
>    sudo dnf install R
> Instalando o RStudio
> 1. **Baixe o RStudio:**
>   - Visite o site do [RStudio](https://posit.co/download/rstudio-desktop/).
>   - Selecione a versão para Linux e baixe o instalador `.deb` ou `.rpm` conforme sua distribuição.
> 2. **Instale o RStudio:**
>   Para sistemas baseados em Debian (como Ubuntu):
>    ```bash
>    sudo dpkg -i rstudio-<version>-amd64.deb
>    sudo apt-get install -f
>    ```
>    Para sistemas baseados em Red Hat (como Fedora):
>    ```bash
>    sudo dnf install rstudio-<version>-x86_64.rpm
> 1. **Verifique a instalação do R:**
>   - Abra o Terminal.
>   - Digite `R` e pressione Enter. Você deve ver a interface de linha de comando do R.
> 4. **Verifique a instalação do RStudio:**
>   - Abra o RStudio a partir do menu de aplicativos ou digitando `rstudio` no Terminal.
>
> Dicas Adicionais
> - **Atualização do R e RStudio:** Verifique regularmente os sites do CRAN e RStudio para novas versões e siga o mesmo procedimento de instalação para atualizar.
> - **Pacotes do R:** Para instalar pacotes adicionais no R, utilize o comando `install.packages("nome_do_pacote")` dentro do R ou do RStudio.
> 
> Seguindo esses passos, você deve conseguir instalar e configurar o R e o RStudio tanto no macOS quanto no Linux sem problemas. Se encontrar alguma dificuldade específica, sinta-se à vontade para perguntar!
