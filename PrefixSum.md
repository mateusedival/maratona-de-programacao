# Prefix sum

Algoritmo utilizado para consultas em um determinado intervalo de um vetor. Há vetor V contendo N valores, e há um vetor S de soma, onde cada posição acumula sua posção anterior, mas a posição atual de V. S[ i ] = S[ i - 1 ] + V[ i ]. Construido o vetor S, dado um intervalo ( i , j ), a consulta é realizada por S[ j ] - S[ i - 1 ].

Possui complexidade de construção e atualização O(n) e realiza cada consulta em  O(1).

## Links

https://en.wikipedia.org/wiki/Prefix_sum

## Problemas

https://www.spoj.com/problems/CSUMQ/<br>
https://www.hackerearth.com/pt-br/practice/data-structures/arrays/1-d/practice-problems/algorithm/beautiful-journey-1/?q=beauty

## Código Exemplo
```c
#include <stdio.h>
//Vetor de soma
int s[1000];

//Constroi e atualiza o vetor soma
void sumConstruct(int v[],int n)
{
	int i;
	for (i = 1; i <= n; i++)
	{
		s[i] = s[i-1] + v[i-1];
	}
	
}

//Realiza a consulta num intervalo (i,j)
int prefixSum(int i, int j)
{

	return (s[j]-s[i-1]);
}

int main()
{
	//Vetor teste
	int v[5] = {1,2,3,4,5};
	
	sumConstruct(v,5);
	int i,j;
	//Enquanto nenhum dos valores i,j for igual a zero, continua consultando
	while(scanf("%d %d",&i,&j) && (i && j))
	{
		printf("%d\n",prefixSum(i,j));
	}
	return 0;
}
```
