# Informacje wstępne:

- Tu są umieszczane materiały po każdym wykładzie:
[https://cloud.ee.pw.edu.pl/nextcloud/index.php/s/kYZG64qc7rmfgge](https://cloud.ee.pw.edu.pl/nextcloud/index.php/s/kYZG64qc7rmfgge) 

- Opisy ćwiczeń na laboratorium będą w każdej grupie podawane, jako ogłoszenia lub opisy kolumn w iSOD.

- Sprawozdania (formaty SQL == text,  lub PDF) będą też umieszczane w iSOD przez studentów.

- W katalogu głównym chmury jest wersja instalacyjna MSSQL2012 (serwer i klient "Sql Server Management") uczelniany.

- Do serwera PW jest dostęp z zewnątrz przez VPN (informacje na drugim wykładzie). Każdy student ma utworzoną bazę na serwerze Politechnicznym i login w postaci:

	**Baza**: b5_NumerAlbumu

	**Login**: b5_NumerAlbumu

	**Hasło**: b5_NumerAlbumu

	**Server**:  10.42.2.99 na laby (na zewnątrz i wewnątrz PW)

- Kontakt preferowany przez **Teams** → doktor Maciej Stodolski

- Ocena to średnia z ocen wykonanych na laboratorium

- Ocena końcowa to średnia wyliczona przez ISOD

	**5** to od 4.75 do 5.0

	**4.5** od (4.25 do 4.74)

	**4** od 3.75 do 4.24

	**3.5** od 3.25 do 3.74

	**3** od 3 do 3.24

- Dla chętnych możliwe indywidualne kolokwium poprawkowe (w okolicy od 1 czerwca lub koniec maja).

- Prawidłowo wykonane ćwiczenie to 5.0

- Oddane w terminie to 5.0 max, każdy tydzień spóźnienia to -1 punkt z MAX-a (najmniejsza ocena to 2)

- Do sali wchodzimy bez zaproszenia, jeżeli jest w niej prowadzący.

- Wykład punktualnie 8:15 => 9:45

# Faktyczna treść wykładu wstępnego:

Bazy danych na serwerze są rozpoznawane przez NAZWY BAZ

Wniosek → musi być zapewniona unikalność NAZW (nie można stworzyć dwóch o tych samych nazwach)

Wszystko w bazach jest identyfikowane po nazwie!!!

Baza składa się z **TABEL** i powiązań między nimi:

W jednej bazie tabele rozpoznajemy po ich nazwach.

Nazwy tabel muszą być unikalne!!!

Tabela składa się z **KOLUMN** i **WIERSZY**:
#### **KOLUMNY**

Każda kolumna w tabeli ma:
- unikalną nazwę (do kolumn odwołujemy się przez nazwy)
- ściśle określoną dziedzinę (jeden typ danych)

#### **WIERSZE**
Wiersze rozpoznajemy przez nazwę => tak naprawdę przez ZAWARTOŚĆ DANYCH


**MONEY** : zmiennoprzecinkowa (ile po kropce ?) 4 po kropce

*4 po kropce to przekleństwo informatyka ponieważ kwoty powinny być z dokładnością do 2. Dlatego wyniki operacji powinniśmy przed wstawieniem zaokrąglać*

- 1 600 0000 == 1 USD

- 2 500 000 USD

**DECIMAL** (20,2) tzn 20 cyfr z tego 2 po kropce



**INT** → duża liczba całkowita

**CHAR(#)** - ciąg znaków o max # długości (zajmuje zawsze # znaków)
- Stała szerokość: PESEL, NIP, kod pocztowy, numer zamówienia pasuje do typu char!

**VARCHAR(#)** - ciąg znaków o max # długości (zajmuje tyle ile wpiszecie)
- Ma narzut struktury pewnie min 30 bajtów - zalecany raczej do pol min 20 znaków.


**char** i **varchar** -> jeden bajt na 1 znak => wymagają dodatkowo podania strony kodowej (1250 np. PL Windows)

**nchar** i **nvarchar** -> to samo tylko jeden znak kodowany na 2 bajtach UNICODE

**BIT** - 0 lub 1

**datetime** - zakodowana binarnie data

- convert(datetime, '20250225', 112) - 112 YYYYMMDD

#### Właściwość NULL albo NOT NULL

- zy_geniusz1 BIT NULL  => 0 / 1 / NULL => pusto nie wypełnione

- czy_geniusz1 IS NOT NULL AND czy_geniusz1 = 1

- czy_geniusz2 BIT NOT NULL => 0/1

- czy_geniusz2 = 1

#### Sekcja przykładów
**Treść**:
TABELA osoby (IMIE nvarchar(40) not null, NAZWISKO nvarchar(40) not null, ADRES nvarchar(100) NULL)

Zad.1
Poproszę wiersze gdzie IMIE='Maciej' AND NAZWISKO='Stodolski' AND (Adres IS NOT NULL AND Adres='Pod Mostem')

Maciej Stodolski

Jacek Korytkowski

Zad.2
Poproszę wszystkie Maćki lub Jacki o nazwisko Stodolski

(imie = 'Maciej' OR imie = 'Jacek') AND nazwisko = Stodolski

**Potrzebujemy KLUCZ główny w każdej tabeli. Klucz główny to zbiór kolumn NOT NULL, których zawartość w tabeli musi być unikalna.**

Osoby(imie, nazwisko, miasto, kod_pocztowy, ulica)

Osoby(id_osoby IDENTITY, imie, nazwisko, miasto, kod_pocztowy, ulica)

CONSTRAINT PK_osoby PRIAMRY KEY (id_osoby)

Faktury(numer, miesiac,...)  CONSTRAINT PK_Faktury PRIMARY KEY (numer, miesiac)

miesiac = '202502'

'1' z '2025'

**Szukając po kluczu głównym mamy pewność, ze znajdziemy 1 wiersz lub wcale**.