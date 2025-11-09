### **Referencje do funkcji**
*Definicja funkcji* 
	int f() { return 0; }
*Wywołanie funkcji*
	int i = f();
*Deklaracja typu referencji*
	delegate int Div();
*Deklaracja referencji do funkcji ... i przypisanie referencji do f*
	Div rf = f;
*Wywołanie funkcji*
	int i = rf(); ... i = f();
### **Referencje funkcji przeciążonych**
*Definicja funkcji bez parametru*
	public void f() { ... }; f();
*Definicja funkcji z parametrem*
	public void f(int i) { ... }; f(0);
### **Funkcje anonimowe**
*Deklaracja typu referencji*
	delegate void Dvv();
*Deklaracja referencji do funkcji ... przypisanie funkcji anonimowej*
	Dvv? rf = delegate() { ... }
*Wywołanie funkcji anonimowej*
	rf();
	rf = null; <- nigdy się już do niej nie dostaniemy
### **Wyrażenia lambda**
*Deklaracja typu referencji*
	delegate void Dvv();
*Deklaracja referencji do funkcji*
	Dvv rf;
*Przypisanie funkcji anonimowej*
	rf = delegate() { ... }

### **delegate int Dii(int i );**
```cs
// Kod do CS ( nie jestem tego pewny na 100% )
delegate int Dii(int i);
Dii dii = null; // int i - dii(0);
	dii = delegate(int i) { return i; };
	dii = (int i) => { return i; };
	dii = i => { return 0; };
	dii = (int i) => i;
	dii = (i) => 0;
	dii = i => 0;
```

### **delegate int Div();**
```c#
Div div = null; // int i = div();
	div = delegate() { return 0; };
	div = () => { return 0; };
	div = () => 0;
```

### **delegate void Dvv();**
```cs
Dvv dvv = null;
	dvv = delegate() { ...; return; };
	dvv = () => { ...; return; };
	dvv = () = { ... };
```

### **Krotki** jako parametr
```cs
delegate int Diii( int i1, int i2 );
diii(0, 0); //wywołanie z dwoma parametrami
delegate int Dik(( int i1, int i2 ) k);
dik((0,0)); //wywołanie z parametrem krotki

diii = (i1, i2) => i1 + i2;
dik = (i1, i2) => i1 + i2;
```
