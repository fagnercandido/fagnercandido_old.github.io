---
layout: default
---


# [](#header-1)Leitura de String - C/C++

Sempre que precisamos ler uma string via teclado é uma dificuldade. O código que disponibilizo tenta sanar este inconveniente.

Por alocação dinâmica, ele vai realocando caracter por caracter para compor a string.

```c++
/*
 Sintese
   Objetivo: Ler uma String
  
   Entrada : uma String.
 
   Saida   : A String
 
   Data : 30/01/2008
*/
#include <stdio.h>
#include <stdlib.h>
int main()
{
   char fraseInicial;
   char *fraseFinal;
   int contadorLaco=0, contadorAlocacao = 2;
   if((fraseFinal = (char *)malloc(contadorAlocacao*sizeof(char *))) == NULL)
   {
      printf("ERRO NA ALOCACAO!");
      getchar();
      exit(1);
   }
   printf("Digite o Nome: ");
   fraseInicial=getchar();
   /* Dentro do laço é feita a leitura caracter a caracter
        e à realocação, para não haver desperdício de espaço.
   */
   while(fraseInicial!='\n')
   {
      fraseFinal[contadorLaco]=fraseInicial;
      contadorLaco++;
      contadorAlocacao++;
           fraseFinal = realloc(fraseFinal, contadorAlocacao*sizeof(char));
      fraseInicial=getchar();
   }
   fraseFinal[contadorLaco]='{FONTE}';
   printf(fraseFinal);
}

```
