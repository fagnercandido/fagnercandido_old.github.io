---
layout: default
---


# [](#header-1)Loops rotulados em Java
Na minha jornada pela certificação OCJP, coisas interessantes que pude constatar que a linguagem Java proporciona. Confesso que até mesmo estranhas.

Desta vez, a surpresa fica por conta do loop rotulado. Isso meu caro, você não leu errado, é rotulado. Certo, isso remete a goto… Calma, não é goto, mas bem que parece…

Enfim, o loop rotulado tem por objetivo sair de loops que estejam em um nível de aninhamento muito grande. Cria-se um rótulo, seguido por dois pontos, e cria-se o loop. Dentro do loop, com as instruções break e continue você chama o rótulo.

O código abaixo ilustra bem este conceito. O mesmo faz uso tanto com o break, quanto com o continue, vale a pena rodar com ambos e tirar suas conclusões.

```java
   /*
	Sintese :
		Objetivo : Demonstrar o uso de Loops rotulados
		Entrada : /
		Saída : /
		Autor : fsouzacandido@gmail.com @fagner_candido
 
	*/
 
class LoopRotulado{
	public static void main(String[] args){
		/*
			Loop Externo, expressão rotulado
		*/
		loopExterno:
		for(int contador = 0; contador < 5; contador++){
			for(int auxiliar = 0; auxiliar < 5; auxiliar++){
				System.out.println("Auxiliar : "+auxiliar);
				System.out.println("Contador : "+contador);
				/*
					Aqui ocorre a mágica, as instruções break e continue
					fazem com que o loop seja reavalidado ou lido novamente
				*/
				//break loopExterno;
				continue loopExterno;
			}
		}
	}
 
}
```


