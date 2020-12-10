# O que acontece quando usamos o float?

## Primeiro chute

Usei um float: left O que aconteceu?

A caixa vermelha sumiu e isso é normal. Porque? 
Uma vez que a gente usa float:left o que acontece é o seguinte:
Nós tinhamos um elemento roxo e um elemento vermelho, um de baixo do outro. Quando eu apliquei no elemento roxo um float: left é criado um novo contexto. O elemento roxo fica a frente, flutuando, isso faz com que o espaço que o roxo estava fica vazio, dando o lugar ao elemento vermelho. Ele "sumiu" porque eles tem o mesmo tamanho.

A questão do novo contexo é que o elemento fica a frente do elemento, modificando o contexto do padrão do browser(navegador).

Para provar que isso é real, irei colocar um opacity: 0 que vai apagar ela totalmente.
Mas aonde foi parar o conteúdo que estava no vermelho? Esse é mais um comportamento padrão do nosso float. Ele nunca esconde um conteúdo, mesmo escondendo um elemento.

Para provar que isso é certo, vamos colocar no elemento vermelho, uma color: red

Ele está logo abaixo do paragrafo, exatamente abaixo do nosso vermelho.

Nós temos um elemento flutuando e ele faz com que tudo o que está abaixo dele sobe, por causa do novo contexto, mas ele esta em cima desse elemento vermelho. Como ele esta em cima do elemento vermelho, ele esconde o elemento, mas nunca o conteúdo que esta dentro do vermelho. Ele sempre dá um jeito de deixar exibido. 

Ele não esta exatamente em baixo porque temos um line-height: 200px. Se tirar ele, ele fica grudado onde ele cabe onde exatamente no lugar que ele coube. Esse é realmente um comportamento esperado do float.


## Segundo chute

Na div vermelha, damos um float: left. As duas divs estão do lado uma da outra. Um comportamento até mais fácil de entender.
Temos a div roxa e a vermelha. Quando colocamos um float: left para a roxa, ele criou um novo contexto e flutuou para a esquerda. Mas também colocamos um float: left para a div vermelha. Mas já tinha a div roxa na esquerda. Então a vermelha ficou grudada na roxa o mais que podia. 
O float sempre cria a frente do comportamento padrão do browser.
Já o paragrafo foi parar atrás dos dois elementos.

Para provar, vamos criar um seletor para o p e colocar a cor de fundo de amarelo.

De fato ele está atrás dos elementos e está sendo mostrado o conteúdo dele por causa da nossa segunda regra do float.

Pra provar que isso é verdade, damos um opacity: 0 nas duas divs. Depois dessa, de fato o p está atrás dos elementos.

## O que acontece com o pai que envolve elementos que estão flutuando?

Irei adicionar um article dentro das divs e do p no index.html
Visualmente, não mudou nada, mas irei colocar uma cor de fundo para o article. Ele está só pegando a largura do p. Como se estivesse só p a cor de fundo. Mas está no article, o article envolve esses elementos. A cor de fundo devia ir até no final dos dois elementos, em baixo. Mas vai até o final do texto(conteúdo). Porque isso não acontece?

Porque os elementos estão flutuando. Eles saíram do contexto padrão do browser, lembra? Por tanto ele não está mais dentro do article. Como que faço para ele voltar ao article sem tirar o float? No CSS, existe algumas prorpiedades que elas forçam o recalculo do contexto, ela verifica se tem alguém flutuando dentro desse contexto. 
Dentro do article no arquivo float.css usamos um `overflow:hidden`. Agora ele sabe que existe. Mas porque?

A overflow:hidden faz com que esconde uma altura e uma largura definida para esse pai. Só que não defini largura e altura então ele precisa saber o tamanho como não tem tamanho é um tamanho automatico. Porém tem elementos flutuando aqui, então preciso mostrar eles também, se não terei que esconder eles.

Para provar isso, damos um height:100px no article. Ele escondeu. Ele considera apenas o tamanho do p e esconderia boa parte dos nosso float. Então esse novo contexto precisa ser recalculado de forma automática e dessa vez ele recalcula considerando também os elementos que estão flutuando. Vamos tirar esse height. Isso é genial quando se precisa colocar uma cor de fundo, para você precisar saber se os elementos estão participando de fato. 

## O p em baixo dos elementos

Como colocar o p em baixo? Temos um elemento do lado direito e esquerdo. Mas e o p? Como colocar em baixo?
Para isso, utilizamos uma outra propriedade, o `clear: both`.
O que ele vai fazer? Ela verifica se tem algum elemento flutuando na minha esquerda ou na minha direita. No caso eu coloquei both(ambos) então ela olhar os dois lados para verificar. Se tiver, ela limpa o contexto, ficando em baixo dos elementos que estão flutuando, ele não quer ficar do lado.

Depois de darmos um F5 temos um elemento a esquerda e a direita. Se tiver um lado flutuando o both vai procurar e vai colocar o texto para baixo. Tanto left quanto right porque temos elementos na esquerda e na direita. Então quando a gente quer começar um novo contexto fazer com que não fique entre o elemento que esta flutuando, podemos usar o clear.

Para testar, vamos colocar um float: right no elemento roxo.

Agora não esta mais limpando o contexo, porque o nosso p está com clear:left e não tem nenhum elemento flutuando a esquerda dele. Se voltar para right ou both, aí ele vai quebrar novamente para baixo.

Então o clear:both, left ou right funcionam dessa maneira. Eles verificam se tem um elemento flutuando e eles verificam se tem ao lado um elemento que identifica no clear e ele limpa o contexto ficando a baixo dos elementos que estão flutuando. 

(Tem mais anotações a fazer.)

O float é mais fácil inicialmente, porém é a mais difícil de dominar. Porque ela tem muitos paralelos, muitas coisas acontecendo.