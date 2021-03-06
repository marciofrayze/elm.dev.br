# Aula 6 - Nossa primeira animação.

Esta aula será um pouco mais teórica pois vamos aprender os
fundamentos para que seja possível criarmos animações.

## O que vamos aprender?

1. Nossa primeira animação.  
2. Conhecendo a função *animation*.  
3. Rotacionando uma figura de acordo com o tempo.  
4. Conhecendo a função *spin*.  
4.1 Entendendo melhor o controle do tempo.  

## 1- Nossa primeira animação.

Até agora desenhamos apenas imagens estáticas, mas o
*Elm Playground* permite também apresentar animações.

Então hoje vamos aprender a colocar movimentos nas
nossas figuras! Isso será nosso próximo grande passo
em direção a fazer nossos próprios jogos.

Nesta aula vamos aprender a desenhar um triângulo
girando na tela e este é o código que vamos analisar:

```
import Playground exposing (..)

main =
  animation view

view time =
    [ triangle red 100
          |> rotate (spin 8 time)
    ]
```

## 2. Conhecendo a função *animation*.

*animation* (animação em inglês) é o nome da função que
precisamos acionar para permitir que o nosso programa
entenda que queremos criar uma imagem animada.

A função *animation* recebe um parâmetro
diferente do que aprendemos nas aulas anteriores: ela
espera que passemos como argumento uma função. Ou seja,
é uma função que recebe como parâmetro uma outra função!

Isso é algo que costuma gerar dúvidas mas
na verdade é bastante simples.

Em *Elm* (e também *JavaScript* e muitas outras linguagens
de programação) isso é bastante comum: às vezes nossas
funções vão receber valores como números ou textos
e em outros casos receberá uma função como argumento.

No nosso exemplo a função *animation* está recebendo como
argumento a função *view* (que significa **vista** ou **ver**
em inglês).   
Em *Elm* este costuma ser o nome padrão dado para a função
onde iremos definir o que será exibido na tela.

Perceba que a função *view* recebe um parâmetro chamado *time* 
(que significa **tempo** ou **hora** em inglês).  
Poderíamos dar qualquer outro nome mas, por convenção,
este é o nome que costumamos usar neste parâmetro.  

Através de uma animação podemos alterar o nosso desenho
ao longo do tempo. Por isso, precisamos deste parâmetro
para sabermos qual o valor atual do tempo e, assim,
especificarmos como o desenho deve ser apresentado.

Pense assim: imagine que você chutou uma bola de futebol
em linha reta. Conhecendo a direção que ela está indo
e a intensidade do seu chute, como poderíamos saber qual
a posição atual da bola? A resposta é: depende! Depende do
*tempo*. Zero segundos após você chutar, ela ainda estará
encostada em seu pé. Um segundo depois estará um pouco
mais longe. Ou seja, para descobrirmos onde deveríamos 
desenhar esta bola precisaríamos saber o tempo decorrido
desde o momento do seu chute.

Voltando para nosso código, a nossa função *view* será
executada (automaticamente pelo computador) diversas vezes,
e em cada execução o valor da variável *time* será diferente (contendo
a hora atual no momento daquela execução).  
É isso que permite que na primeira vez que esta função
seja acionada nosso triângulo seja desenhado de uma forma
e nas demais, conforme o valor da hora (*time*) muda, a
forma como nosso triângulo é desenhado também.

Todas as animações deste curso serão feitas seguindo esta
lógica: nossas funções vão precisamos do tempo (*time*) 
decorrido para saber qual o momento atual da animação.

## 4. Conhecendo a função *spin*.

Já havíamos utilizado a função *rotate* antes, para
rotacionarmos as imagens. Como você deve lembrar, ela
recebe um parâmetro com o ângulo que queremos rotacionar
(um número entre -360 e 360). No nosso exemplo o valor
passado como parâmetro é este:

```
rotate (spin 8 time)
```

A primeira obervação importante que preciamos fazer aqui
é o uso dos parânteses. Se os retirarmos, nosso programa
não vai funcionar.  
Eles são importantes pois indicam para o computador
que ele deve dar prioridade em resolver tudo que está dentro
do parânteses para só em seguida pegar o resultado destas
operações e usar o valor deste resultado como argumento da função
rotate.  
Você pode fazer uma associação com a matemática:  

```
x = 2 * 1 + 1  
y = 2 * (1 + 1)  
```

No exemplo acima, *x* é igual a 3 e *y* é igual a 4.  
Assim como na matemática, os parânteses são
muito importantes na programação.

Voltando pro nosso exemplo, primeiro será avaliado o 
valor de *spin 8 time* para em seguida usar este valor
como argumento para a função rotate.

*Spin* em inglês significa girar.  
Você consegue imaginar o que ela faz? Pare e reflita um pouco
antes de continuar lendo.

Mais uma vez, como quase tudo em *Elm*, *spin* é uma função.
E como você deve ter observado, ela recebe dois parâmetros.
O primeiro é o período, indicando quantos segundos deve
demorar cada rotação da imagem. Quanto menor o valor, mais rápida
será a velocidade de rotação. No nosso exemplo, este valor é
8. Isso significa que nosso triângulo irá rodar por completo 1
vez a cada 8 segundos.  
O segundo parâmetro é o tempo decorrido. Em geral vamos apenas
repassar o valor que já recebemos como argumento da nossa função.
Quem controla o tempo é o computador e ele repassa esta informação
pra gente.

## 4.1 Entendendo melhor o controle do tempo.

Nosso programa começa na função *main*. Mas quem aciona esta função?
O computador! Ou mais tecnicamente falando, a *runtime* do *Elm*.

Neste nosso exemplo, a função *main* foi definida da seguinte forma:

```
main =
  animation view
```

A função *animation* em algum momento irá acionar a função *view* 
e, como já víamos antes, a função *view* recebe um parâmetro
indicando o tempo (no nosso exemplo, o parâmetro *time*):

```
view time =
```

Você não precisa se preocupar com o controle desta variável, o computador vai
fazer este trabalho pra você. Precisa apenas saber que irá receber este
valor e o que ele representa.

Se toda esta explicação ficou muito confusa, não se preocupe!
Tudo vai ficar mais claro conforme você treina.

## E agora?

Agora chegou a hora de você colocar as mãos na massa
e praticar um pouco!

Siga para os [desafios da Aula 6](/aula_6_desafios.html) e bons estudos.
