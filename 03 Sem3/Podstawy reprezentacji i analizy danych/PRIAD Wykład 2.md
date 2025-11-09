### **Rodzaje danych w analizie**
- tabelaryczne
- rastrowe
- wektorowe
- tekstowe
- czasowe
- grafowe
- multimedialne
### **Dane tabelaryczne**
- przechowywane  w tablicach, bazach danych, hurtowniach danych
- wiersze -> obiekty
- kolumny -> wartości pomiarów
### **Dane rastrowe**
- *Definicja* -> siatka pikseli (wiersz x kolumna), piksel = wartość(e) kanał(ów)
- *Parametry* -> rozdzielczość przestrzenna, głębia bitowa
### **Dane wektorowe**
- *Definicja* -> prymitywy geometryczne (punkty, linie, wielokąty) + atrybuty.
- *Grafika 2D/3D* -> niezależna od rozdzielczości, transformacje geometryczne, skalowalność
- *GIS* -> warstwy obiektów, układy współrzędnych, topologia
- *Zastosowania* -> mapy, planowanie przestrzenne, nawigacja, wektoryzacja obrazów
- *Konwersja* -> raster = wektor (generalizacja/utrata lub dolina szczegółów)
### **Dane tekstowe**
- *Źródła* -> dokumenty, posty, transkrypcje, metadane (autor, czas, język)
- *Kodowanie* -> UTF-8, Normalnaizacja (znaki diaktryczne)
- *Reprezentacje* -> bag-of-words/TF-IDF, n-gramy, sekwencje tokenów/embeddingi
- *Wstępne przetwarzanie* -> tokenizacja, lematyzacja/stemming, usuwanie stop-słów
- *Zastosowania* -> klasyfikacja tematów, sentyment, wyszukiwanie, ekstrakcja informacji
- *Dziedzina* -> przetwarzanie języka naturalnego (NLP = natural language processing)
### **Dane czasowe**
- *Typy* -> regularne (sekundy, minuty, dni) vs nieregularne, jednowymiarowe vs wielowymiarowe, punktowe vs przedziały/okna
- *Składowe* -> trend, sezonowość (np. tygodniowa/roczna), cykl, szum, stacjonarność vs niestacjonarność
- *Wizualizacja* -> wykres linii, dekompozycja (trend + sezonowość + reszty)
### **Dziedziny**
- *Statystyka* -> planowanie, dobieranie danych do analiz, potwierdzenie wiarygodności liczb, dostarcza podstaw do wszystkich nowoczesnych metod uczenia maszynowego
- *Sztuczna inteligencja* -> rozumowanie, rozpoznawanie obrazów, język, robota, uczy jak łączyć wiedzę ekspercką z automatycznym wnioskowaniem