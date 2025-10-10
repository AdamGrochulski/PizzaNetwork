# Informacje
**Prowadzący** : Maciej Dziekanowski
**Kolosy** : każdy kolos → 25 pkt
- 1 kolokwium : 7/8 wykład (*tylko 1 połowa materiału* )
- 2 kolokwium : 14/15 wykład  (*tylko 2 połowa materiału* )
- konsultacje po kolokwium
- zalicza min 55% sumy punktów
- można przynieść notatki, ale papierowe
**Zaliczenie** : na podstawie kolosów
*Jest kolokwium poprawkowe*

# Część merytoryczna
**Przelicznik** → nie zmienia swojego działania, działa według algorytmów
**Procesor** → decydujemy o jego funkcjach
**Schemat blokowy procesora**  ///Slajd 12

**ALU** → Arithemetic Logic Unit
**R0 … Rn** → rejestry, mają pamiętać co jednostka zrobiła np. 2 + 2 + 2, wynik pośredni 2+2. Dane z R są przekazywane do ALU
**Układ sterowania** → skomplikowana maszyneria działająca na podstawie programu
**Zegar systemowy** → steruje czasowo ciąg zdarzeń
**I/O** ( *strzałki* ) → gdzieś się zaczyna i gdzieś się kończy
**Słowo** ( *bitowe* ) → szerokość szyny w bitach mówi o tym "'ilo bitowy jest procesor”
**Szyna adresowa** - wysyła dane do pamięci, które wybierają jaka końcówka ma zostać wczytana przez *np. Datain*
**MUX** - multiplekser, redukując ilość potrzebnych szyn, łączy data in, data out, program bus w jeden główny databus

**Budowa mikrokontrolera** ///Slajd 16
- mikroprocesor *CPU* 
- pamięć RAM ( *Random Access Memory* )
- pamięć ROM ( stała )
- I/O ( wejście i wyjście )
- dekoder pamięci (wybiera, który hardware się włącza )
- szyna data bus ( *< - >* obukierunkowa )
- szyna address bus ( *→* wychodząca )

Jest to procesor wraz z otoczeniem, może funkcjonować *samodzielnie* !
Z reguły jest jeden kontroler, ale może być ich więcej.
