## Diferente dos vídeos anteriores sobre o display: inline, block e inline-block nós iremos pegar o código e sair chutando a propriedade float. Depois de chutar, a gente vai parar um pouco analisar o que aconteceu e entender o comportamento dessa propriedade.

### Primeiro chute

Vamos aplicar na primeira div um `float:left`. 
De alguma forma sumiu o vermelho. E isso é normal. Uma vez que a gente usa float:left, a gente tinha um elemento um de baixo do outro. Quando damos um float: left, é criado um novo contexto. Quando ele estava no contexto do browser o elemento de vermelho vai para cima, eles ficam vagos, como se tivesse um espaço lá. Então eles ficam atrás do elemento roxo. Mas não temos como ver o elemento vermelho. É claro. Eles tem o mesmo tamanho, por isso eles ficam exatamente igual.
Colocamos um opacity: 0 no elemento roxo e o vermelho vai aparecer indicando que ele está atrás o tempo todo.
Onde foi parar o conteúdo que estava dentro do vermelho?
Esse é mais um comportamento padrão do float. Ele nunca esconde um conteúdo mesmo escondendo o elemento. Colocamos um color: red no elemento vermelho.

*Prestar atenção e fazer as devidas anotações sobre o conteúdo que nunca vai sumir mesmo usando float.*


