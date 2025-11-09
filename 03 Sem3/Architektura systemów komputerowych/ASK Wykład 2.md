# **Era Intel 8086**

### **Adresowanie:**
2^4 = 16 - 4 bitowy
2^8 = 256
2^16 = 65,536
2^20 = 1,048,576
2^24 = 16,777,216
2^32 = 4,294,967,296
2^64 = 18,446,744,073,709,551, 616

im dłuższy rejestr tym więcej danych można przetworzyć

**Intel 4004 (4-bitowy) z 1971r.** - pierwszy układ scalony przeznaczony na rynek masowy, krótkie rejestry

**1947r.** - pierwszy tranzystor ostrzowy

**1959r.** - pierwszy tranzystor typu MOSFET

**Intel 8008 (8-bitowy) z 1972r.** - układ który miał sterować pracą terminala, był w pewien sposób programowalny, nigdy nie został wykorzystany tak jak miał być, dopuszczony do użytku masowego, powstawały proste kalkulatory, tego typu układy programowalne

**Intel 8080 (8-bitowy)** - układ ogólnego przeznaczenia, dostępny dla wszystkich, 2MHz, 16-bitowa szyna adresowa, 64kB przestrzeń adresowa, była to jednostka uniwersalna, każdy kto umiał lutować mógł zrobić prosty komputer i z odpowiednimi częściami

**Oryginalny Z80 firmy Zilog** - 8-bitowy, 4MHz taktowanie, sporo tańszy od poprzedniego (Intela), 16-bitowa szyna adresowa,  64kB przestrzeń adresowa, CP/M, DR-DOS

Proste komputery ogólnego przeznaczenia nie miały pamięci masowej.

Pojawiły się potem różne firmy procesorowe, były nawet lepsze niż Intel, ale były całkowicie zamknięte. 

**Mikroprocesor Intel 8086 z 1978r.** - 16-bitowy system, 2MHz taktowanie, 16-bitowa szyna danych, 20 bitowa szyna adresowa, 64kB przestrzeń adresowa, 86-DOS, MS-DOS - microsoft kupiła 86-DOS i zmieniła nazwę i dzięki temu zaistniała. Był to drogi procesor.

**Mikroprocesor Intel 8088** - okrojony procesor 8086, 8 bitowa szyna danych. Firma IBM opracowała komputer ogólnego przeznaczenia. Zaryzykowali bo włożyli sporo funduszy i wypuściła komputer PC XT. 

**IBM (model 5150) z monitorem CGA z 1981r.** - pierwszy taki komputer od którego to wszystko się zaczęło.

Do dziś układ rejestrów został taki jak był na samym początku, żeby zachować kompatybilność.

Cały adres był przechowywany w dwóch rejestrach zawsze. Jeden adres był w rejestrze 16-bitowym, a drugi był w rejestrze segmentowym (20 biotwy w którym ostatnie 4 były same 0 (???)).

00FF:0001 -> 00FF1
segment : offset (not sure)

tryb rzeczywisty - nie ma ochrony pamięci

tryb chroniony - działają w tym wszystkie obecne procesory

Mapa pamięci dla trybu rzeczywistego: do wykorzystania tylko 640kB, RAM jeszcze ograniczony przez system. Na górze jest RAM monitora, można było tam wpisywać dane i od razu wyświetlało się na ekranie. Później było to zablokowane przy zmianie na tryb chroniony, co nie spodobało się programistom.

Procesor 8086/8088 można było podzielić na 3 części. Jednostka wykonawcza, jednostka sprzężenia z magistralą, kolejka rozkazów - 6 bajtów.

### **Pięć faz :**
*F* - pobranie (fetch), pracuje jednostka sprzężenia z magistralą
*D* - dekodowanie (decode)
*R* - odczyt (read)
*E* - wykonanie (execute) instrukcji
*W* - zapisanie (write) wyniku do pamięci

W przypadku zdekodowania przez układ wykonawczy efektywnego rozkazu skoku, wprowadzone po nim do kolejki rozkazy muszą zostać usunięte.

Czasami instrukcja, kod jest dłuższy więc może być F dwa razy. F i D mogą być wykonane równolegle, ale reszta musi poczekać, żeby poprzednie się zakończyło.

Procesor 386 rozwiązał problem przełączania trybów dzięki środowiskowi wirtualnemu. Zaczęła się pojawiać pamięć Cache.

### **Intel 80386 zmiany :**
1. 32-bitowa szyna danych i adresowa
2. Tryb wirtualny 8086
3. Wirtualna pamięć
4. Wbudowane wspomaganie dla debuggerów
5. Nowe instrukcje
6. Szybszy cykl procesora
7. Większa częstotliwość zegara
8. System OS/2, dyskietki 3,5", architektura MCA


### *MECHANIZM POTOKU I ARCHITEKTURA SUPERSKALARNA*
### *Co to mechanizm potoku? - CZĘSTO BYŁO NA ZALICZENIU*

### **Zoptymalizowane potoki**
Potoki wykonują rozkazy na liczbach całkowitych w pięciu fazach:
1. Pobranie rozkazu (PF - prefetch)
2. IF
3. ID
4. MEM
5. EX
6. WB

W danej chwili można wykonać kilka rozkazów jednocześnie. Każdy rozkaz ma wykonywaną inną fazę tego potoku.

Podstawowym mankamentem techniki potoku sa rozkazy skoku, powodujące w najgorszym wypadku potrzebę przeczyszczenia całego potoku i wycofania rozkazów, które następowały zaraz po instrukcji skoku i ropoczęcie zapełnienia potoku od początku od adresu, do którego następował skok.

Taki rozkaz skoku może powodować ogromne opóźnienia wykonywaniu programu...


### **ARCHITEKTURA SUPERSKALARNA**
	Wiele potoków - instrukcje są wykonywane równolegle.
	Problem skoków jest w tym przypadku szczególnie dotkliwy, występują tez
	inne ograniczenia.

**Ograniczenia:**
1. zależności danych - wynik operacji musi być znany przed wykonaniem kolejnej instrukcji; konflikty związane z odczyt-po-zapisie, zapisem-po-zapisie
2. Konflikt zasobów - dwie instrukcję
3. Zależności procedur - rozgałęzienia - procesor musi

**RISC**
1. Architektura odczytaj i zapisz
2. W wysokim stopniu regularne instrukcje, które w łatwy sposób mogą przechodzić przez kanał
3. Wiele rejestrów
4. Rejestry, szyna danych i adresowa co najmniej 32 bitowe

Format instrukcji procesora Pentium

Przedrostki - jeden lub więcej bajtów poprzedzających instrukcję:
1. Zmiana segmentu
2. Rozmiar adresu (16, 32 bitowy)
3. Rozmiar operandu (16, 32 bitowy)
4. Powtórzenia - używane z instrukcjami łańcuchowymi


### **PENTIUM PR, II, III**

*Pentium Pro* - koncepcję tam zastosowane są do dzisiaj używane i stosowane. zasada działania jest taka sama jak dzisiejsze procesory. Był bardzo drogi.

Procesory Pentium II i III były już nieco tańsze.

*Intel Itani* - nowa architektura która była totalnie nie kompatybilna przez co była to porażka.

AMD opracowała rozwiązanie 64-bitowe. Potem Intel z tego skorzystał. Firmy po kilku latach mogły korzystać ze wzajemnych rozwiązań. 

*Pentium Pro* - dwie kości, jedna procesor, druga pamięć Cache. Nie miał rozszerzenia MX(?) (Pentium II już miał).

### **Technologia dynamicznego wykonywania instrukcji:**
1. Wykonywanie instrukcji bez zachowania ich kolejności w programie (okno przeszukiwania 20-30 instrukcji).
2. Przewidywanie przepływu instrukcji (skoków).
3. Wybór najbardziej optymalnej kolejności wykonywania instrukcji.

### **Układ przewidywania skoków**
1. Skoku bezwarunkowe i warunkowe
2. próba przewidywania skoku albo / lub podązaniae wieloma kanałami
3. Przewidywanie statyczne
	-  Skok zawsze zachodzi - 60%
	- Skok w tył zachodzi, w przód nie zachozi - 65%
	- Decyduje opcode instrukcji
4. Przywidywania dynamiczne
	-  1-bit statusu
	-  2-bity statusu
	-  Historia skoków - 96-97%
5. ...

Tablica BTB
Tablica (128-1024 wpisy) zawierająca adresy instrukcji wywołującej skok i adresy skokow.

dwa bity sygnatury ustawienia dynamicznie
0 0 mocne założenie braku skoku
0 1 słabe założenie brau skoku
1 0 słabe założenie skoku
1 1 mocne założenie skoku

Rodzina Pentium Pro