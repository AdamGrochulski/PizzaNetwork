# **Podstawy**
## 1. Co to jest algorytm?
- **Algorytm** jest pewną ściśle określoną procedurą obliczeniową, która dla właściwych *danych wejściowych* "produkuje" żądane *dane wyjściowe* zwane *wynikiem* działania algorytmu.
- **Algorytm** można traktować, jako sposób rozwiązania konkretnego *problemu obliczeniowego*. Należy sprecyzować wymagania dotyczące relacji między *danymi wejściowych* i *wejściowymi*, a algorytm opisuje właściwą procedurę obliczeniową, która zapewnia że ta relacja zostanie osiągnięta.
- **Algorytm jest poprawny**, gdy dla każdego egzemplarza problemu algorytm zatrzymuje się i daje dobry wynik. 
- **Algorytm jest niepoprawny**, kiedy nigdy się nie zatrzyma, da błędne wynik.
- **Algorytm** składa się z deklaracji tworzących zmienne i stałe oraz instrukcji (metod)

## 2. Co to jest dziedzina algorytmiczna?
**Dziedzina algorytmiczna** to zbiór poprawnych danych wejściowych dla których algorytm jest zdefiniowany i generuje oczekiwane wyniki. Jest to układ:
	*(A, f1, ...., fn, r1, ...., rm)*
gdzie:
- *A* jest niepustym zbiorem
- *f1, .... , fn* są funkcjami określonymi dla argumentów ze zbioru A i przyjmującymi wartości w zbiorze A
- *r1, ... , fm* są relacjami zachodzącymi między elementami zbioru A
**Podstawowe dziedziny algorytmiczne to:**
- dziedzina liczb całkowitych
- dziedzina liczb rzeczywistych
- dziedzina wartości logicznych
- dziedzina napisów
## 3. Co to jest struktura danych?
**Struktura danych** to logiczne uporządkowanie danych w pamięci komputera określające sposób dostępu do tych danych. Struktura danych określa przynajmniej częściowo sposób implementacji. Prawidłowy dobór struktury danych do algorytmu, umożliwia efektywny dostęp i manipulacje danymi.

## 4. Co to jest abstrakcyjny typ danych?
**Abstrakcyjny typ danych** to model określający zbiór danych i operacji, jakie można na nim wykonywać, bez definiowania sposobu ich implementacji. Skupia się na tym co dana struktura robi, a nie jak to implementuje.
*Przykłady*:
- kolejka (LIFO, FIFO, priorytetowa)
- zbiór
- słownik (tablica asocjacyjna, mapa)
- napis
- lista liniowa

## 5. Co to jest:
1. **Tablica** to struktura danych, kontener, w którym przechowywane są dane tego samego typu i dostęp do nich jest dyktowany za pomocą indeksu
2. **Lista liniowa** to struktura danych, w której dane są uporządkowane liniowo.  
	1. **Jednokierunkowa** - z każdego elementu możliwe jest przejście do następnego węzła
	2. **Dwukierunkowa** - z każdego elementu możliwe jest przejście do poprzedniego i następnego węzła
	3. *Cykliczna* - następnym węzłem ostatniego elementu listy jest początkowy element listy
3. **Multilista** to struktura danych, będąca tablicą lub zbiorem list liniowych (lista zawierająca inne listy). Pozwala na reprezentowanie bardziej złożonych relacji między danymi np. reprezentacja grafów
4. **Kopiec** to struktura danych oparta na drzewie, w której wartości potomków węzła są w stałej relacji z wartościami rodzica np. wartość rodzica jest większa niż wartość jego potomka.
	1. **Kopiec binarny** to tablicowa struktura danych, którą można rozpatrywać jako pełne drzewo binarne:
		1. Każdy węzeł drzewa odpowiada elementowi tablicy, w którym podana jest wartość węzła
		2. Drzewo jest pełne, na wszystkich poziomach (wyjątkiem może być najniższy, który jest wypełniany od lewej strony)
		3. Tablica *A* reprezentująca kopiec ma dwa atrybuty: *length[A]* - liczba elementów tablicy; *heapSize[A]* - liczba elementów kopca przechowywanych w tablicy
		4. Korzeniem drzewa jest A[0]
		5. *Parent(i) = i/2*
		6. *Left(i) = 2i*
		7. *Right(i) = 2i + 1*
		8. Własność kopca: dla każdego węzła *i*, który nie jest korzeniem, zachodzi:
			*A[Parent(i)]  >= A[i]*
		9. **Wysokość węzła** w drzewie to liczba krawędzi na najdłuższej prostej ścieżce prowadzącej od tego węzła do liścia, a **wysokość drzewa** to log2(n).
	2. **Procedury**
		1. *Heapify* - przywracanie własności kopca **O(logn)**
		```java
		heapify(A, i)
		l <- left(i)
		r <- right(i)
		if l <= heap_size[A] i A[l] > A[i]
			then largest <- l
			else largest <- i
		if r<= heap_size[A] i A[r] > A[largest]
			then largest <- r
		if largest != i
			then zamień A[i] <-> A[largest]
				Heapify(A, largest)
		```
		
		2. *Build_Heap* - tworzymy kopiec z nieuporządkowanej tablicy danych wejściowych **O(n)**
		```java
		buildHeap(A)
			heapSize[A] <- length[A]
			for i <- |length[A]/2 - 1| downto 0
				do heapify(A, i)
		```
				   
		3. *Heapsort* - sortuje tablice w miejscu **O(n * logn)**
		```java
		heapSort(A)
			buildHeap(A)
			for i <- length[A] - 1 downto 1
			do zamień A[0] <-> A[i]
				heapSize[A] <- heapSize[A] - 1
				heapify(A, 0)
		```
		   
		4. *Extract_Max* i *Insert* - pozwalają na użycie kopca, jako kolejki priorytetowej **O(logn)**
		```java
		Heap_Extract_Max(A)
			if heapSize[A] < 1
				then error "kopiec pusty"
			max <- A[0]
			A[0] <- A[heapSize[A] - 1]
			heapSize[A] <- heapSize[A] - 1
			heapify(A, 0)
			return max
		
		Heap_Insert(A, key)
			heapSize[A] <- heapSize[A] + 1
			i <- heapSize[A]
			while i > 0 i A[parent(i)] < key
				do A[i] <- A[parent(i)]
					i <- parent(i)
			A[i] <- key
		```

1. **Drzewo (binarne)** to *abstrakcyjna struktura danych*, która ma na celu odpowiadać drzewu przedstawionemu w teorii grafów. Składa się z wierzchołków, które mają tylko jednego rodzica, mogących posiadać wiele dzieci. Każdy węzeł jest potomkiem korzenia, węzły bez dzieci są *liśćmi*. Drzewo binarne to specjalny przypadek drzewa, w którym każdy węzeł może mieć maksymalnie dwoje dzieci.
2. **Graf** to abstrakcyjna struktura danych mająca na celu odpowiadająca matematycznej definicja grafu. Graf to zbiór wierzchołków, które mogą, ale nie muszą być ze sobą połączone krawędziami. Graf może być skierowany lub nieskierowany, ważony lub nieważony.
	1. **Ścieżka** z wierzchołka *k* do wierzchołka *u*. **Długość ścieżki** jest liczbą krawędzi ścieżki (nazywamy *ścieżką prostą*, gdy wszystkie jej wierzchołki są różne)
	2. **Cykl** jest wtedy, gdy początkowy i końcowy wierzchołek ścieżki są takie same oraz zawiera co najmniej jedną krawędź.
	3.  **Graf prosty** nie zawiera pętli
	4. **Graf acykliczny** nie zawiera cyklu
	5. **Graf jest spójny** , jeśli z jednego wierzchołka da się poprowadzić ścieżkę do wszystkich innych

3. **Hash** to wynik działania funkcji haszującej, wartość, która powinna być unikalna dla każdego argumentu (w celu uniknięcia kolizji) i zwracać tą samą wartość dla danego argumentu.
4. **Hash table (hash map)** uogólnienie zwyczajnej tablicy, struktury danych korzysta z funkcji hashującej aby efektywniej przechowywać dane - gdy adresujemy tablice bezpośrednio, przy dużym uniwersum możliwych klucz potrzebujemy dużo pamięci, żeby przechowywać tablicę, która nie musi być wypełniona w dużym stopniu - wtedy użycie hash table pozwala na efektywniejsze przechowywanie danych.
5. **Drzewo poszukiwań binarnych - BST** struktura danych bazująca na drzewie, w której zachodzi zależność LeftChild <= Parent <= RightChild. Dla każdego danego węzła wszystko na lewo od niego będzie mniejsze, a na prawo większe.
6. **Drzewo AVL** struktura danych samobalansującego (uzyskujemy przez rotacje w lewo i prawo) się drzewa. Różnica wysokości dwóch poddrzew po obu stronach każdego wierzchołków zawiera się w [-1; 1]
7. **Drzewo czerwono czarne** - struktura danych samobalansującego się drzewa, które spełnia poniższe własności
	- każdy węzeł jest czerwony, albo czarny
	- każdy liść (NIL) jest czarny
	- korzeń drzewa zawsze jest czarny
	- jeśli węzeł jest czerwony, to obaj jego synowie są czarni
	- każda prosta ścieżka z ustalonego węzła do liścia ma tyle samo czarnych węzłów

## 6. Co to jest:
1. **Kontener** (kolekcja) to abstrakcyjny typ danych, grupa elementów w którym przechowywane są w logiczny sposób. Przykładowymi kontenerami są: *tablica, lista, drzewo*
2. **Zbiór** (set) to abstrakcyjny typ danych, w którym przechowywane są unikalne wartości bez konkretnego porządku.
3. **Kolejka** to abstrakcyjny typ danych, w którym mamy zdefiniowane akcje Enqueue (wkładamy do kolejki) i Dequeue (wyjmujemy z kolejki, gdzie LIFO - Last In First Out; FIFO - First In First Out). **Kolejka priorytetowa** każdy element ma przyporządkowaną wartość, zwaną kluczem.
	-  Kolejka ma początek *head* i koniec *tail*, który wskazuje na następną wolną pozycję, na którą można wstawić do kolejki następny element.
	- Enqueue(Q, x)
	   Q[tail[Q]] <- x
	   if tail[Q] = length[Q]-1
		   then tail[Q] <- 0
		   else tail[Q] <- tail[Q]+1
	- Dequeue(Q)
		x <- Q[head[Q]]
		if head[Q] = length[Q]-1
			head[Q] <- 0
			else head[Q] <- head[Q]+1
		return x
	- Obie te operacje działają w czasie *O(1)*

4. **Stos** to abstrakcyjny typ danych, w którym mamy zdefiniowane akcje pop i push. Push dodaje element na stos. Pop wyciąga ostatni dodany element, który jeszcze nie został usunięty - **LIFO**
	1. Operacja *Push* to wstawienie nowego elementu do stosu.
	   Push(S, x)
		top[S] <- top[S]+1
		S[top[S]] <- x
	2. Operacja *Pop* w wyniku zwraca wierzchołek stosu i usuwa go z niego, ale pozostaje on w tablicy.
	   Pop(S)
		if Stack_Empty(S)
			then error "niedomiar"
			else top[S] <- top[S]-1
				return S[top[S]+1]
		
		Stack_Empty(S)
		if top[S] < 0
			then return TRUE
			else return FALSE
	3. Obie te operacje działają w czasie *O(1)*

4. **Słownik** (mapa) abstrakcyjny typ danych, składa się z par klucz, wartość. Każdy klucz w mapie jest unikalny i niezmienny, wartości mogą się powtarzać i być modyfikowane. Wartość wyszukuje się po jej unikalnym kluczu. Pozwala na szybkie wyszukiwanie, wstawianie i usuwanie danych.
## 7. Jak formalnie określamy działanie algorytmu? Co to jest warunek początkowy (alfa) i końcowy (beta)?:
**Warunek początkowy** (alfa) są to wymagania dotyczące danych wejściowych, aby zapewnić poprawne działanie algorytmu.

**Warunek końcowy** (beta) własności danych wyjściowych i ich związek z danymi wejściowymi.

Algorytm *A* jest semantycznie poprawny względem warunków *alfa* i *beta* jeżeli każde jego wykonanie dla danych spełniających warunek *alfa* prowadzi w skończonym czasie do danych spełniających warunek *beta*.

## 8. Jakie własności algorytmu sprawdzamy przy jego dowodzeniu? W jaki sposób to robimy?
 Poprawności algorytmu dowodzimy wykazując trzy jego własności:
   * **Własność stopu** - dla każdych danych wejściowych, spełniających warunek początkowy działanie algorytmu jest skończone
   * **Własność określoności** - dla każdych danych wejściowych spełniający warunek *alfa* działanie algorytmu nie będzie przerwane czy polecenia, które nie są nieokreślone
   * **Własność częściowej poprawności** - ze względu na warunki początkowy i końcowy dla każdych danych wejściowych spełniających warunek *alfa* jeżeli obliczenie dojdzie do punktu końcowego, to dane wynikowe spełniają warunek końcowy *beta*.

## 9. Co to jest niezmiennik pętli? Jak i do czego go wykorzystujemy?
   **Niezmiennik pętli** (NP) to technika dowodzenia poprawności algorytmów zawierających pętle. Nie wiadomo kiedy pętla się zakończy, więc do udowodnienia, że przetwarzanie danych spełniających warunek *alfa* doprowadzi nas do wyników spełniających warunek *beta* stosuje się technikę podobną do indukcji matematycznej.
   NP jest **zdaniem logicznym** (warunkiem) posiadającym 3 własności:
   * NP musi być prawdziwy przed wejściem do pętli
   * Z założenia prawdziwości NP dla dowolnego *k-tego* obiegu pętli powinniśmy być w stanie udowodnić, że NP pozostanie prawdziwy w następnym *k+1* obiegu pętli.
   * Z prawdziwości NP po wyjściu z pętli powinno wprost lub pośrednio wynikać spełnienie przez wyniki warunku *beta*, nazywamy to **niezmiennikiem**.

## 10. Jak formalnie określamy złożoność obliczenia algorytmu? Notacje wielkiego O, Omega, Theta?
* **Theta ($\Theta$)** - Dokładne oszacowanie asymptotyczne (ograniczenie z góry i z dołu), pesymistyczny czas, nie implikuje czasu działania dla wszystkich danych
* **O (duże O)** - Asymptotyczna górna granica (nie gorzej niż), za pomocą tego opisujemy często czas działania algorytmu, stosuje się do czasu działania dla wszystkich danych
* **Omega ($\Omega$)** - Asymptotyczna granica dolna (nie lepiej niż), najlepszy przypadek

## 11. Co to jest najgorszy przypadek? Proszę podać przykład.
- Jest to inaczej **przypadek pesymistyczny**.
- Jest to przypadek, w którym algorytm musi wykonać maksymalną możliwą liczbę operacji.
- Przykład: W sortowaniu przez wstawianie tablica wejściowa jest posortowana, ale odwrotnie np. 10, 9, 8, 7, 6, 5. Algorytm będzie musiał każdy element po kolei wstawić na początek tablicy, czyli wykona największą możliwą ilość porównań i zamiany miejsc.

## 12. Algorytm o złożoność f(n) przetwarza dane o wielkości N w czasie T, jak długo będzie ten algorytm przetwarzał dane o długości kN? (Zadanie będzie uszczegółowione przez podanie np. f(n)=n^2, N=10000, T=1 sekunda, k=10).
	k^2 = 100 s
	N^2 = 1 s
	(kN)^2 = x
	k^2 * N^2 = x
	100 * 1 = x
	x = 100 s

# **Algorytmy**
## 13. Proszę podać algorytm **wyszukiwania sekwencyjnego**. Proszę formalnie udowodnić jego poprawność.
```java
int linearSearch(int[] A, int size, int target){
	for(int i = 0; i < size; i++){
		if(A[i] == target){
			return i;
		}
	}
	return -1;
}
```

**Złożoność:**
- w najlepszym przypadku *O(1)* - szukany element jest pierwszy
- w najgorszym wypadku *O(n)* - szukany element jest na samym końcu albo go nie ma
**Dowód poprawności:**
- *Warunek alfa*: A[0]....A[n-1] - to int, size >= 0, target - to int
- *Warunek beta* zwróci k takie że A[k] = target lub -1, jeżeli nie ma takiego k
- *Własność stopu* pętla for: 
	- zaczyna się dla i = 0
	- kończy się gdy i == n (nie wykona się dla i == n ), 
	- zwiększa i po każdym obiegu o i, czyli wykona nie więcej niż n iteracji
- *Własność określoności*
	- jedyną operacją potencjalnie niebezpieczną jest indeksowanie po arrayu, ale jest wykorzystywana tylko wewnątrz pętli, gdzie 0 <= i < n co na mocy **warunku alfa**  jest bezpieczna
- *Własność częściowej poprawności udowodnimy za pomocą niezmiennika pętli*
	```java
	for(int i = 0; i < size; i++){
		if(A[i] == target){ return i; }
	}
	```
	- **NP** V[0]....V[i-1] nie zawiera x
		1. Dla i == 0    V[0]...V[-1] jest zbiorem pustym **NP jest prawdziwy**
		2. Jeśli wyjdziemy z pętli to {V[0]....V[k-1] } == {V[0]....V[n-1]}, bo  i == n, więc ten warunek jest równoważony warunkowi beta
		3. Jeśli V[0]....V[k-1] nie zawiera x, to zwiększamy k(i) o jeden tylko po sprawdzeniu, że A[i] != target

## 14. Proszę podać algorytm **wyszukiwania metodą bisekcji**. Proszę formalnie udowodnić jego poprawność.

Znajdowanie elementu w **posortowanej tablicy** przez ciągłe dzielenie zakresu poszukiwań na połowy, porównując szukaną wartość ze środkowym elementem i zawężając obszar poszukiwań do lewej lub prawej połowy.

```java
int binarySearch(int[] A, int n, int x){
	int left = 0;
	int right = n - 1;
	while( left <= right ){
		int mid = left + (right-left)/2;
		if(A[m] > x)
			right = mid - 1
		else if(A[m] < x)
			left = mid + 1;
		else
			return mid
	}
	return -1;
}
```

**Dowód poprawności:**
- *Warunek alfa* : A[0] <= A[1] <= A[2] <= ... <= A[n-1],  n>= 0,   x - int
- *Warunek beta* : Zwracamy i, gdy A[i] == x lub -1, gdy x nie jest w A
- *Własność stopu :*
	1.  Pętla kończy działanie, gdy left > right
	2. W każdym kroku obliczam m, gdzie left <= m <= right, a potem:
		- albo **right = m - 1;**
		- albo **left = m + 1;**
		- albo **wychodzę z binarySearch**
	3. O ile, nigdy nie wyjdę to:
		- *left* jest ciągiem rosnącym
		- *right* jest ciągiem malejącym
	4. Reasumując *left* zaczyna od 0 i rośnie, a *right* zaczyna od n-1 i maleje, więc muszą się minąć w skończonym czasie.
- *Własność określoności :*
	1. *left* zaczyna od 0, jest ciągiem rosnącym
	2. *left i* < *right i*
	3. *right* zaczyna się od n - 1, jest ciągiem malejącym
	4. *left i < right i*
	5. Wniosek z tego, że *0 <= left  i <= right i <= n -1* ; **0 <= left i <= mid i <= right i <= n - 1**
	6. Co nam daje, że **0 <= mid i <= n - 1**
- *Własność częściowej poprawności*
	- **NP** jeżeli x jest w wektorze to znajduje się w ciągu V[left] ... V[right]

## 15. Proszę podać algorytm **sortowania przez wstawienie**. Proszę formalnie udowodnić jego poprawność.
Efektywne dla niewielkiej liczby elementów. Elementy są **sortowane w miejcu** (są przechowywane cały czas w tej samej tablicy)

```java
void insertionSort(int[] A) {
	int n = A.length;
	
	for(int i = 1; i < n; i++) {
		int key = A[i];
		int j = i - 1;
		while( j >= 0 && A[j] > key) {
			A[j + 1] = A[j]
			j = j - 1;	
		}
		A[j + 1] = key;
	}
}
```

**Dowód poprawności:**
- *Warunek alfa* : A[0], A[1], .... A[n-1] - int;     A.length > 0
- *Warunek beta*: A[0] <= A[1] <= .... <= A[n-1]
- *Własność stopu:*
	- Pętla zewnętrzna (for) jest sterowana zmienną i, która zaczyna się od i = 1 i jest zwiększa o 1 w każdym kroku. Warunek końcowy to i < n. Ponieważ n jest skończone to i osiągnie wartość n po skończonej liczbie kroków n-1 iteracji.
	- Pętla wewnętrzna (while) jest sterowana zmienną j, która zaczyna się od j = i -1. W każdej iteracji wykonujemy j = j -1. Warunek kontynuacji wymaga j >= 0. Ponieważ startowe j jest skończone, a w każdym kroku maleje, zmienna j osiągnie wartość -1, co przerwie pętle.
	- **Wniosek:** Obie pętle są skończone, więc cały algorytm posiada własność stopu.
- *Własność określoności*
	- Jedynie potencjalnie niebezpiecznie operacje to dostęp do tablicy przez indeksy i oraz j
	- Zmienna i przyjmuje wartości z zakresu [1, n -1]. Dla n >= 2 jest to zawsze wewnątrz zakresu tablicy. Jeśli n < 2, pętla for się nie wykona.
	- Zmienna j w pętli while jest dekrementowana. Warunek pętli *j >= 0 && A[j] > key*. Pierwszy warunek, który jest sprawdzany to *j>=0*, więc jeśli j < 0 to druga część *A[j] > key* nigdy nie zostanie sprawdzone. Gwarantuje to, że nigdy nie odwołamy się do A[-1].
	- **Wniosek**: Algorytm bezpiecznie bierze dostęp do tablicy, indeksy nie wychodzą poza zakres tablicy, więc algorytm jest dobrze określony.
- *Własność częściowej poprawności* :
	- **NP** A[0] <= A[1] <= .... <= A[n-1] tablica jest już posortowana
	- 
## 16. Proszę podać algorytm **sortowania szybkiego**. Proszę formalnie udowodnić jego poprawność.
- Jest to często najlepszy wybór ( *pesymistyczny czas* działania to **O(n^2)**, a *oczekiwany czas* działania to **O(n x logn)** )
- **Zalety:** sortuje w miejscu i dobrze działa w środowiskach z pamięcią wirtualną.
- **Metoda "dziel i zwyciężaj"**
- *Dziel:* Tablica A[p,...,r] jest dzielona na dwie niepuste podtablice A[p,....,q] i A[q+1,...,r]. Indeks *q* jest obliczany przez procedurę dzielącą.
- *Zwyciężaj:* Te dwie podtablice są sortowane przez rekurencyjne wywołania tego algorytmu.
- *Połącz:* Dzięki temu, że podtablice są sortowane w miejscu to nie trzeba nic robić żeby je łączyć, tablica jest od razu posortowana.
```Java
void quickSort(int[] A, int p, int r){
	if( p < r ){
		int q = partition(A, p, r);
		quickSort(A, p, q);
		quickSort(A, q + 1, r);
	}
}
int partition(int[] A, int p, int r){
	int pivot = A[p];
	int i = p - 1;
	int j = r + 1;
	while(True){
		while(A[++i] < pivot){};
		while(A[--j] > pivot){};
		if(i < j) {
			int temp = A[i];
			A[i] = A[j];
			A[j] = temp;
		}
	}
	return j;
}
```

## 17. Proszę podać algorytm **sortowania przez scalenie**. Proszę formalnie udowodnić jego poprawność.
- *Złożoność O(n x logn)*
- *Metoda dziel i zwyciężaj* : dzielenie problemu na mniejsze podobne, rozwiązanie podproblemów, łączenie w celu rozwiązania całego problemu.
- *Dziel* Dzielimy n-elementowy ciąg na dwa podciągi po n/2 elementów.
```Java
	void mergeSort(int[] A, int start, int end)
	if( start < end ){
		int mid = start + (end - start) / 2
		mergeSort(A, start, mid)
		mergeSort(A, mid+1, end)
		merge(A, start, mid, end)
	}
```

## 18. Proszę podać algorytm **sortowania przez kopcowanie**. Proszę formalnie udowodnić jego poprawność.
```Java
heapify(A, i)
	l = left(i);
	r = right(i);
	if(l <= )
```
