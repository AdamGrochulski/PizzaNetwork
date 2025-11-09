### **Źródło niezależne napięcia lub prądu stałego**
Źródło prądu bądź napięcia jest elementem aktywnym, generującym energię elektryczną, powstającą zwykle z zamiany innego rodzaju energii, na przykład z energii mechanicznej, słonecznej, jądrowej, chemicznej itp.

#### *Rzeczywiste źródło napięcia*![[Pasted image 20251016144314.png]]
#### *Rzeczywiste źródło prądu*![[Pasted image 20251016144229.png]]
#### *Charakterystyki prądowo-napięciowe*![[Pasted image 20251016144632.png]]

### **Informacja**
Jest pojęciem abstrakcyjnym, a jej fizycznym odwzorowaniem są *sygnały*. Sygnały są funkcją czasu, ponieważ informacja podlega nieustannej zmianie.

W technice spotyka się sygnały:
- elektryczne: napięciowy (przesyłany na niewielkie odległości) i prądowy (przesyłany na większe odległości)
- mechaniczne
- pneumatyczne
- hydrauliczne
- akustyczne
- optyczne
- radiowe i inne

### **Kanały transmisji**
Sygnały złożone mogą być przesyłane na znaczne odległości tzw. *kanałem transmisji*.

**Nadajnik** -> **Tor transmisji** -> **Odbiornik**

*Tor transmisji* może być elektryczny (napięciowy lub prądowy), optyczny lub radiowy.

### **Sygnały**
Proces zamiany sygnały analogowego na dyskretny wymaga wykonaniu trzech podstawowych operacji:
- próbkowanie sygnału
- kwantowania
- kodowania
Podstawową zaletą *próbkowania* sygnału jest możliwość *zwieloktrotniania sygnałów*. Polega on na tym, że czas pomiędzy przesyłaniem kolejnych próbek można wykorzystać do przesłania tym samym kanałem także próbek innych sygnałów.
Minimalny czas próbkowania T$_p$ potrzebny do przesłania informacji bez jej straty jest określony przez twierdzenie Kotielnikowa - Shannona, gdzie:
- f$_p$ = 1/T$_p$
- f$_m$ - maksymalna częstotliwość widma sygnału (najwyższa znacząca częstotliwość harmonicznej przebiegu próbkowanego sygnału).

	$T_p <= \frac 1 {2f_m}$ lub $f_p >= 2f_m$

![[Pasted image 20251016151146.png]]

### **Zalety sygnałów dyksretnych (cyfrowych)**
- mała wrażliwość na zakłócenia
- duża dokładność pomiarów i przekształcenia sygnałów
- łatwość zapamiętywania danych
- w wielu wypadkach dogodny odczyt wartości na wskaźnikach cyfrowych
- relatywnie małe gabaryty urządzeń i wysoka funkcjonalność
- możliwość automatyzacji procesów przetwarzania informacji

Ogniskiem pośrednim pomiędzy urządzeniami cyfrowymi i układami analogowymi są *przetworniki cyfrowo - analogowe* D/A (Digital/Analog)

### **Sygnały informacji są z definicji sygnałami stochastycznymi**
Ponieważ do analizy różnych obwodów i występujących w nich zjawisk potrzebne są zdeterminowane sygnały informacji przyjęto następujący ogólny podział:
- sygnał stały (oznaczenie *DC*– Direct Current)
- sygnał przemienny (oznaczenie *AC*– Alternating Current),
- sygnał zmienny (oznaczenie *UC*– Universal Current).

### **Rodzaje sygnałów**
*Sygnał stały* lub inaczej składowa stałą to z matematycznego punktu widzenia wartość średnia sygnału (AVG - *AV*era*G*e value) za okres zmienności funkcji X(t)
	$\int_{0}^{T} X(t) \, \mathrm{d}t$
*Sygnał przemienny* to sygnał, którego wartość średnia $X_{AVG}$ spełnia zależność:
	$X_{AVG} = 0$
Wielkością jednoznacznie opisującą skutki energetyczne działania przemiennego jest *wartość skuteczna* przebiegu (RMS - Root-Mean-Squere value)
	$X = \sqrt{\frac 1 T\int_{0}^{T} X^2(t) \, \mathrm{d}t}$

### **Znaczące sygnały**
W elektronice pośród wielu sygnałów reprezentujących wyżej wymienione przebiegi do najbardziej znaczących należą:
- przebieg harmoniczny - $X(t) = Asin(\omega t + \phi)$
- skok jednostkowy - 1(t), funkcja Heavside'a
- impuls Diracka - $\sigma (t)$
- pojedynczy impuls prostokątny
- ciąg impulsów prostokątnych (jednobiegunowy lub inaczej unipolarny, dwubiegunowy lub inaczej bipolarny)
- przebieg trójkątny lub liniowo narastający lub liniowo opadający (uni- lub bipolarny)
- przebieg trapezoidalny (uni- lub bipolarny)
Naturalną reprezentacją sygnału zdeterminowanego jest:
- wykres przebiegu w funkcji czasu
- tabela wartości chwilowych
- funkcja matematyczna

Takie przedstawienie sygnału informuje o kształcie sygnału i jego zmienności w funkcji czasu.

### **Widmo sygnału**
Inną reprezentacją tego samego sygnału informacji jest widmo sygnału. Obrazem widma jest charakterystyka widmowa sygnału. Każdą funkcję okresową, która spełnia zależność $X(t) = X(t_0+T)$ można zastąpić w sposób dokładny lub przybliżony sumą trygonometryczną:![[Pasted image 20251016153120.png]]
Funkcję $X(t)$ można również zapisać w postaci szeregu:![[Pasted image 20251016153203.png]]

W postaci zespolonej szereg Fouriera można zapisać zależnością:![[Pasted image 20251016153317.png]]
### **Widmo amplitudowe i fazowe**
Przedstawiając na wykresach zależności $A_n = f(\omega)$ oraz ${\phi}_n = f(\omega)$ uzyskuje się tzw. *widmo amplitudowe* i *widmo fazowe* przebiegu sygnału.![[Pasted image 20251016153538.png]]
Zależność ${A_n}^2 = f(\omega)$ nazywa się *widmem mocy* sygnału. Amplitudy poszczególnych prążków tego widma szybko maleją ze wzrostem częstotliwości dlatego z dobrym przybliżeniem zakłada się, że ponad 90% energii sygnału informacji jest przenoszone przez kilka pierwszych harmonicznych.

### **Odkształcanie sygnału wyjściowego**
Wszystkie układy elektroniczne odkształcają sygnał wyjściowy, który nie jest już wierną kopią sygnału wejściowego. Zniekształcenia wprowadzane przez układ elektroniczny można podzielić na dwie zasadnicze grupy:
- zniekształcenia liniowe
- zniekształcenia nieliniowe.

*Zniekształcenia liniowe* są spowodowane innym kształtem charakterystyk amplitudowych i fazowych niż założony – np. kształt idealny.

*Zniekształcenia nieliniowe* powstają w układach z elementami nieliniowymi i polegają na wprowadzeniu do sygnałów wyjściowych dodatkowych harmonicznych, których nie ma w sygnalewejściowym (sygnał wyjściowy ma inny kształt niż sygnał wejściowy

### **Modulacja i demodulacja**![[Pasted image 20251016153738.png]]
**Z tego względu wyróżnia się dwie podstawowe grupy modulacji:**
1. Modulacje sinusoidalne
2. Modulacje impulsowe lub ogólnie niesinusoidalne.

**Do grupy modulacji sinusoidalnych zalicza się:**
- Modulację amplitudową AM (Amplitude Modulation)
- Modulację częstotliwościową FM (Frequency Modulation)
- Modulację fazową PM (Phase Modulation)

**Do grupy modulacji impulsowych należą:**
- Modulacja impulsowa amplitudowa *PAM* (Pulse Amplitude Modulation)
- Modulacja impulsowa częstotliwościowa *PFM* (Pulse Frequency Modulation)
- Modulacja położenia impulsów *PPM* (Position Phase Modulation)
- Modulacja szerokości impulsów *PWM* (Pulse Width-Modulation)
- Modulacja kodowa impulsowa *PCM* (Pulse Code Modulation)
- Modulacja kodowa impulsowa delta *DPCM* (Delta Pulse Code Modulation)

### **Modulacja szerokości impulsów PWM**![[Pasted image 20251016154030.png]]
