## Diferente dos vídeos anteriores sobre o display: inline, block e inline-block nós iremos pegar o código e sair chutando a propriedade float. Depois de chutar, a gente vai parar um pouco analisar o que aconteceu e entender o comportamento dessa propriedade.

***Irei fazer commits por chutes. Então, 3 chutes, 3 commits.***
### Primeiro chute

Vamos aplicar na primeira div um `float:left`. 
De alguma forma sumiu o vermelho. E isso é normal. Uma vez que a gente usa float:left, a gente tinha um elemento um de baixo do outro. Quando damos um float: left, é criado um novo contexto. Quando ele estava no contexto do browser o elemento de vermelho vai para cima, eles ficam vagos, como se tivesse um espaço lá. Então eles ficam atrás do elemento roxo. Mas não temos como ver o elemento vermelho. É claro. Eles tem o mesmo tamanho, por isso eles ficam exatamente igual.
Colocamos um opacity: 0 no elemento roxo e o vermelho vai aparecer indicando que ele está atrás o tempo todo.
Onde foi parar o conteúdo que estava dentro do vermelho?
Esse é mais um comportamento padrão do float. Ele nunca esconde um conteúdo mesmo escondendo o elemento. Colocamos um color: red no elemento vermelho.

Então resumindo: Basicamente é isso! Se temos um elemento flutuando, ele faz com que tudo o que está abaixo dele, suba por causa do novo contexto, mas ele está em cima desse elemento vermelho, ele esconde o vermelho mas nunca vai esconder um conteúdo que está dentro do vermelho. Ele sempre vai dar um jeito de mostrar esse conteúdo.

Se apagarmos o line-height do float.css, podemos ver ele ir até onde ele coube. 

Esse é realmente um comportamento esperado do float.

*Prestar atenção e fazer as devidas anotações sobre o conteúdo que nunca vai sumir mesmo usando float.*

### Segundo chute

Vamos adicionar na div vermelha um float: left, tirar o opacity, também o color: red para limpar o código.

Aqui está um comportamento mais fácil de entender. Aqui tínhamos a div roxa e a div vermelha. A gente falou assim: Div roxa, flutua a esquerda! 
Ela foi lá e flutuou. Fizemos a mesma coisa com a div vermelha. Porém as duas entraram no novo contexto, sendo como a div roxa já estava na esquerda ela simplesmente foi na extrema esquerda, indo até o limite da esquerda. É como dois quadrados que não podem ocupar o mesmo espaço.

*Prestar atenção quando ele explica os elementos com o parágrafo. Se não lembra volte a ver o vídeo*

### O que acontece com o pai que envolve elementos que estão flutuando? A partir do tempo 7:50

*Estudar as propriedades que calculam o recalculo do novo contexto*

overflow: hidden, clear:both.

*Estudar as quebras de tela. Quando que um elemento cai, quebra ou fica?(Porcentagem, width)*

## Resumo

O float é o mais fácil inicialmente, mas o mais difícil de dominar. 

Quando mandamos o float para esquerda ou direita ele flutua de boa, lembrando sempre do novo contexto.

Outra coisa: Se tiver um elemento que ele esconde, que fica sobre esse elemento ele fica de boa sobre o elemento, mas ele não fica sobre um conteúdo.

O pai que está guardando um elemento que está flutuando, ele perde a largura e altura, mas podemos recuperar usando um overflow: hidden.

Se você diminuir o tamanho do browser, a partir do momento em que ele não cabe mais na linha ele cai automaticamente para o sentido que você mandou. (Dois float: right vão cair para a direita)

Não podemos esquecer do clear, que limpa o contexto de um elemento que vem logo após de um elemento que está flutuando. Se você não quer que ele se encaixa ao lado desse elemento que está flutuando, que não fique atrás desse elemento que está flutuando, é só dar um clear falando qual lado que está esse elemento que está flutuando. Sendo assim ele sai desse novo contexto












