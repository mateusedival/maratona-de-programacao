# Crivo de Eratóstenes

Encontra todos os primos até certo valor limite. Iniciando um vetor como se todos fossem primos, percorre-o até a raiz de seu limite, e todas as vezes que encontra-se um número primo, todos os seus múltiplos são marcados.

## Links

https://pt.wikipedia.org/wiki/Crivo_de_Eratóstenes

## Imagens

![](https://upload.wikimedia.org/wikipedia/commons/8/8c/New_Animation_Sieve_of_Eratosthenes.gif)

## Problemas

https://www.urionlinejudge.com.br/judge/pt/problems/view/1221<br>
https://www.urionlinejudge.com.br/judge/pt/problems/view/2180

## Código Exemplo
```c
#include <stdio.h>
#include "math.h"

//Vetor que indica quais são primos
//Inicialmente todos são primos
int v[1000000000];
// Zero indica um primo e Um indica um não primo

void crivo(int n){
	int i = 0;
	int j;
  //O numero um e zero não são primos, então eles são marcados com 1
	v[0] = 1;
	v[1] = 1;
  //Calcula limite do for
	double raiz = (int)sqrt(n);
	for(i = 2; i < raiz;i++)
		if(!v[i]) //Se ele for primo, marcaremos todos os seus multiplos
			for(j = i+i; j < n; j+=i)
				v[j] = 1;
	
}

int main() {
	int n = 100000;
	crivo(n);
	int i;
	for (i = 0; i < n/4; i++)
	{
		printf("%d %d\n",i, v[i]);
	}
  
	return 0;
}
```
