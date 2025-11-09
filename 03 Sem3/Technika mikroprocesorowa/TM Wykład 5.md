# **Przerwania**![[TM Prezentacja 5.pdf#page=1&rect=229,93,606,497|TM Prezentacja 5, p.1]]
### **Rodzaje przerwań**
![[TM Prezentacja 5.pdf#page=2&rect=44,73,737,511|TM Prezentacja 5, p.2]]
*Maski przerwań*
- Maska główna (zasłania wszystko)

### **Przejęcie/wyjście z przerwania**
![[TM Prezentacja 5.pdf#page=3&rect=25,135,830,502|TM Prezentacja 5, p.3]]
*Hierarchia przerwań* - w przypadku kolizji definiuje, które przerwanie będzie obsłużone, jako pierwsze.
*Program główny* - nasz program (to ten, który jest przerywany)

### **Wariant niezagnieżdżony**
Jeśli nastąpi przerwanie w trakcie obsługi przerwania to procesor kończy obsługę tego pierwsze przerwania, a potem dopiero przejdzie do niego po powrocie do *programu głównego*.
![[TM Prezentacja 5.pdf#page=4&rect=30,143,799,486|TM Prezentacja 5, p.4]]
### **Wariant zagnieżdżony**
Jeśli nastąpi przerwanie w trakcie obsługi przerwania to procesor zaczyna przerwanie następnego priorytetu w trakcie (nie jestem pewny tej definicji)
![[TM Prezentacja 5.pdf#page=5&rect=21,158,805,499|TM Prezentacja 5, p.5]]
### **Program przycisku, który wykorzystuje przerwania**
![[TM Prezentacja 5.pdf#page=10&rect=35,68,809,555|TM Prezentacja 5, p.10]]
![[TM Prezentacja 5.pdf#page=9&rect=40,66,822,549|TM Prezentacja 5, p.9]]
