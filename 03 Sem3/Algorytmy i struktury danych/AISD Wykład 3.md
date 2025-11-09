### **QuickSort z InSort ( implementacja C )**
Używany do sortowania danych typu int, Double, Integer itd.
```cs
int podziel( double v[], int p, int k ){
	// a: v[p] ... v[k] double
	// b: v[p] ... v[m-1] <= v[m], v[m+1] ... v[k] > v[m]
	int i = p+1;
	int j = k;
	while( i < j ) {
		while( i < j && v[i] <= v[p] )
			i++;
		while( i < j && v[j] > v[p] )
			j--;
		if( i < j ) {
			double tmp = v[i]; v[i] = v[j]; v[j] = tmp;
		}
	}
	if( v[i] > v[p] )
		i--;
	double tmp = v[p]; v[p] = v[i]; v[i] = tmp;
	return i;
}

void insort( double v[], int p, int k ){
	// a: v[p] ... v[k] double, k > p
	// b : v[p] <= v[p+1] <= ... <= v[k]
	for( int i= p+1; i <= k; i++ ) {
		int j;
		double tmp = v[i];
		for( i = j; j > p && v[j-1] > tmp; j-- )
			v[j] = v[j-1];
		v[j] = tmp;
	}
}

#define MINLQS 20

void hqsort( double v[], int n) {
	int *s = malloc( 2*n * sizeof *s);
	int sp = 0;
	s[sp++] = 0;
	s[sp++] = n -1;
	
	while( sp > 0 ) {
		int k = s[--sp];
		int p = s[--sp];
		int m = podziel( v, p, k );
		if( m-1-p <= MINLQS )
			insort( v, p, m-1 );
		else{
			s[sp++] = p;
			s[sp++] = m-1;
		}
		if( k-(m+1) <= MINLQS )
			insort( v, m+1, k );
		else{
			s[sp++] = m+1;
			s[sp++] = k;
		}
	}
	free(s);
}
```

### **MergeSort ( implementacja w C )**
Używany do sortowania danych, które są obiektami żeby zachować stabilność
```cs
#include <string.h>
void scal( double v[], int p, int m, int k , double d[] ){
	// a: v[p] <= v[p+1] <= v[p+2] <= ... <= v[m-1], v[m] <= v[m+1] <= ... V[k-1]
	// b: v[p] ... v[m-1] <= v[m], v[m+1] ... v[k] > v[m]
	int i = p;
	int j = m;
	int l = p;
	while( i < m && j < k ) {
		if( v[i] <= v[j] )
			d[l++] = v[i++];
		else
			d[l++] = v[j++]
	}
	while( i < m )
		d[l++] = v[i++];
	while( j < k )
		d[l++] = v[j++];
}

void msort( double v[], int n) {
	double *tmp = malloc( n * sizeof *tmp);
	double *src = v;
	double *ds = tmp;
	for( int l = 1; l < n; l *= 2 ) {
		for( int i = 0; i < n; i += 2*l )
			scal( src, i, i+l > n ? n : i+l, i+2*l > n ? n : i+2*l, dst );
		tmp = src;
		src = dst;
		dst = tmp;
	}
	if( src != v ){
		memcpy( src, v, n*sizeof *v)
	}
	free(tmp);
}
int main(){
	// Fragment kodu
	double *v = malloc( n * sizeof *v)
	msort()
	
}
```