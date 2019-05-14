# Segment Tree
É uma arvóre binária que realiza consultas em um determinado intervalo em O(logN). É construída em  O(N) e realiza atualizações em O(logN).<br>


## Imagens 

![](https://he-s3.s3.amazonaws.com/media/uploads/eec15d3.jpg)<br>
Segment Tree de soma.

## Links
https://en.wikipedia.org/wiki/Segment_tree<br>
https://www.hackerearth.com/pt-br/practice/data-structures/advanced-data-structures/segment-trees/tutorial/ <br>
https://www.geeksforgeeks.org/segment-tree-set-1-sum-of-given-range/<br>
http://www.codcad.com/lesson/53

## Problemas

## Código Exemplo
```c
int st[4*10000];// Vetor que armazena a segment tree
int v[100000];

void buildstmin(int low,int high, int pos) { //(0,n-1,0), sendo pos a raíz da arvore, ou seja, 0

	if(low == high) // Caso basse, folha.
	{
		st[pos] = v[low];
		return;
	}
	int mid = (int)(low + high)/2;
  //Chama seu filho esquerdo e direito
	buildstmin(low,mid,(pos*2)+1);

	buildstmin(mid+1,high,(pos*2)+2);

	st[pos] = min(st[(pos*2)+1],st[(pos*2)+2]); //Vê qual de seus filhos é menor


}

int querymin(int pos, int low, int high, int ql, int qh)
{
	if(ql <= low && qh >= high) // O low e high são abrangidos completamente
		return st[pos];
	if(ql > high || qh < low)// O low e high estão completamente fora do intervalo
		return INT_MAX;
  // O low e high são abrangidos parcialmente
	int mid = (low+high)/2; 
	return min(querymin((pos*2)+1,ql,qh,low,mid),
			   querymin((pos*2)+2,ql,qh,mid+1,high));

}

void updatemin(int pos, int low, int high, int nv, int v)
{
	if(low == high){ // Chega-se a folha
		st[pos] = nv;
		return;
	}
	int mid = (low + high)/2;
	if(v <= mid) // Vê se a folha está no filho esquerdo ou direito
		updatemin((pos*2)+1,nv,v,low,mid);
	else
		updatemin((pos*2)+2,nv,v,mid+1,high);
	st[pos] = min(st[pos],nv); // Atualiza os nós pais
}
```
