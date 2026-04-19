

### I. Podstawy Optymalizacji i Funkcji Kwadratowych

**1. Warunek istnienia minimum funkcji $f(w) = aw^2 + bw + c$**
* Współczynnik $a > 0$ (parabola skierowana ramionami do góry).

**2. Wzór na punkt ekstremalny funkcji jednowymiarowej**
* $w^* = -\frac{b}{2a}$

**3. Ogólna postać wielowymiarowej formy kwadratowej**
* $f(w) = w^T Aw + b^T w + c$

**4. Warunek konieczny i wystarczający na minimum wielowymiarowe**
* Macierz $A$ musi być symetryczna i słabo dodatnio określona ($A \succeq 0$).

**5. Definicja macierzy dodatnio określonej ($A > 0$)**
* Dla każdego wektora $x \neq 0$ zachodzi $x^T Ax > 0$. Wszystkie wartości własne są dodatnie.

**6. Definicja punktu krytycznego (stacjonarnego)**
* Punkt, w którym gradient funkcji wynosi zero: $\nabla f(w) = 0$.

**7. Gradient vs Pochodna (Jacobian) – wymiary**
* Gradient $\nabla f(w)$ to wektor kolumnowy ($n \times 1$), pochodna $Df(w)$ to macierz wierszowa ($1 \times n$).

**8. Hesjan (Macierz druga pochodna)**
* Macierz $H_{ij} = \frac{\partial^2 f}{\partial w_i \partial w_j}$. Określa zakrzywienie (krzywiznę) funkcji w danym punkcie.

**9. Interpretacja dodatnio określonego Hesjanu ($H > 0$)**
* Funkcja w tym punkcie ma minimum lokalne (kształt „miski”).

**10. Interpretacja ujemnie określonego Hesjanu ($H < 0$)**
* Funkcja w tym punkcie ma maksimum lokalne (kształt „kopuły”).

**11. Czym jest punkt siodłowy?**
* Punkt, w którym Hesjan ma wartości własne różnych znaków (w jednych kierunkach funkcja rośnie, w innych maleje).



**12. Twierdzenie Sylwestra (sprawdzanie określoności)**
* Macierz jest dodatnio określona, gdy wszystkie jej główne minory wiodące (wyznaczniki podmacierzy od lewego górnego rogu) są dodatnie.

---

### II. Metoda Najmniejszych Kwadratów (MNK)

**13. Funkcja celu w MNK (Suma Kwadratów Reszt)**
* $J(w) = \|Aw - b\|^2 = (Aw - b)^T (Aw - b)$

**14. Równania normalne (Normal Equations)**
* $A^T Aw = A^T b$

**15. Rozwiązanie MNK przy pełnym rzędzie kolumnowym**
* $w^* = (A^T A)^{-1} A^T b$

**16. Czym jest macierz Grama w kontekście MNK?**
* To macierz $G = A^T A$. Jest zawsze symetryczna i przynajmniej słabo dodatnio określona.

**17. Interpretacja geometryczna $Aw^*$**
* Jest to rzut ortogonalny (prostopadły) wektora $b$ na podprzestrzeń rozpiętą przez kolumny macierzy $A$.

**18. Właściwość wektora reszt $r = b - Aw^*$**
* Wektor reszt jest prostopadły do każdej kolumny macierzy $A$.

**19. Co jeśli macierz $A^T A$ nie jest odwracalna?**
* Oznacza to, że kolumny $A$ są liniowo zależne. Należy użyć pseudoodwrotności Moore’a-Penrose’a lub regularyzacji.

**20. Bias (wyraz wolny) w modelu liniowym**
* Model: $y = w^T x + w_0$. W macierzy $A$ realizuje się to poprzez dodanie kolumny samych jedynek.

---

### III. Rozszerzanie Cech i Modele Nieliniowe

**21. Dlaczego stosujemy rozszerzanie cech (Feature Expansion)?**
* Aby model liniowy (względem wag) mógł modelować nieliniowe zależności (względem danych wejściowych).

**22. Rozszerzenie wielomianowe (Polynomial Features)**
* Przekształcenie wektora $[x_1, x_2]$ w $[1, x_1, x_2, x_1^2, x_1 x_2, x_2^2]$.

**23. Czym jest funkcja bazowa (Basis Function) $\phi(x)$?**
* Funkcja transformująca dane wejściowe do nowej (zazwyczaj wyżej wymiarowej) przestrzeni.

**24. Rozszerzenie typu ReLU (Rectified Linear Unit)**
* Użycie funkcji $\max(0, x - c)$. Pozwala na tworzenie modeli kawałkami liniowych (splajnów).

**25. Problem "Przekleństwa wymiarowości" przy rozszerzaniu cech**
* Liczba cech wielomianowych rośnie wykładniczo wraz ze stopniem wielomianu, co prowadzi do overfittingu.

---

### IV. Overfitting, Underfitting i Generalizacja

**26. Definicja Generalizacji**
* Zdolność modelu do poprawnego przewidywania wyników dla nowych danych, których nie widział w procesie trenowania.

**27. Czym objawia się Underfitting (Niedouczenie)?**
* Wysokim błędem na zbiorze treningowym. Model jest zbyt prosty, by wyłapać trend.

**28. Czym objawia się Overfitting (Przeuczenie)?**
* Bardzo niskim błędem treningowym i bardzo wysokim błędem testowym. Model "wykuł" szum na pamięć.

**29. Wpływ normy wag na overfitting**
* Modele przeuczone mają zazwyczaj bardzo duże wartości wag ($w$), co powoduje gwałtowne oscylacje funkcji.

**30. Brzytwa Ockhama w modelowaniu**
* Przy podobnej skuteczności zawsze wybieraj model prostszy (mniejsza liczba cech, mniejsze wagi).

---

### V. Regularyzacja

**31. Cel regularyzacji**
* Zapobieganie overfittingowi poprzez dodanie kary za skomplikowanie modelu (wielkość wag) do funkcji celu.

**32. Funkcja celu z regularyzacją (ogólnie)**
* $J_{reg}(w) = J_{MNK}(w) + \lambda \cdot \text{kara}(w)$

**33. Co kontroluje parametr $\lambda$?**
* Siłę regularyzacji. $\lambda=0$ to czysty MNK. Bardzo duże $\lambda$ wymusza wagi bliskie zeru.

**34. Regularyzacja Ridge (Grzbietowa / L2)**
* Kara to kwadrat normy Euklidesowej: $\lambda \|w\|_2^2 = \lambda \sum w_i^2$.

**35. Rozwiązanie analityczne Ridge Regression**
* $w^* = (A^T A + \lambda I)^{-1} A^T b$. Macierz w nawiasie jest zawsze odwracalna dla $\lambda > 0$.

**36. Regularyzacja LASSO (L1)**
* Kara to suma wartości bezwzględnych: $\lambda \|w\|_1 = \lambda \sum |w_i|$.

**37. Główna zaleta LASSO (Selekcja cech)**
* LASSO potrafi wyzerować niektóre wagi, usuwając nieistotne cechy z modelu (tworzy modele rzadkie - sparse).

**38. Geometria Ridge vs LASSO**
* Ridge to kula (ogranicza wagi równomiernie). LASSO to romb (ostre wierzchołki na osiach sprzyjają zerowaniu wag).



**39. Dlaczego LASSO jest nieliniowe?**
* Ponieważ norma L1 nie jest różniczkowalna w zerze, rozwiązanie nie ma prostej postaci macierzowej jak Ridge.

---

### VI. Walidacja i Wybór Modelu

**40. Podział danych: Train / Validation / Test**
* Train: do nauki. Validation: do wyboru hiperparametrów ($\lambda$, stopień wielomianu). Test: do ostatecznej oceny.

**41. K-krotna Cross-Walidacja (K-fold)**
* Dzielimy dane na $K$ części. Trenujemy $K$ razy, za każdym razem inna część jest zbiorem walidacyjnym. Wynik to średnia.

**42. Kiedy stosować Leave-One-Out Cross-Validation (LOO)?**
* Gdy mamy bardzo małą liczbę danych (K równa się liczbie próbek).

**43. Problem Time Leakage (Wyciek czasu)**
* W szeregach czasowych użycie losowej walidacji powoduje, że model "zna przyszłość". Należy stosować podział chronologiczny.

**44. Walidacja z podziałem na grupy (Group-wise)**
* Stosowana, gdy dane są skorelowane (np. wiele zdjęć tego samego pacjenta). Cała grupa musi być albo w treningu, albo w teście.

---

### VII. Zagadnienia Uzupełniające (Trivia & Detale)

**45. Al-Chwarizmi i Kitab al-djabr**
* IX-wieczne dzieło, które dało początek nazwie "Algebra" i systematycznemu rozwiązywaniu równań kwadratowych.

**46. Metoda uzupełniania do kwadratu**
* Technika pozwalająca znaleźć minimum funkcji kwadratowej bez liczenia pochodnych.

**47. Co to jest model "rzadki" (sparse model)?**
* Model, w którym większość wag wynosi zero (wynik działania LASSO).

**48. Czy MNK jest odporny na Outliery (wartości odstające)?**
* Nie, ponieważ podnoszenie błędów do kwadratu sprawia, że jeden duży błąd drastycznie wpływa na wynik.

**49. Związek MNK z rozkładem Normalnym**
* MNK odpowiada estymatorowi największej wiarygodności (MLE), jeśli założymy, że błędy (szum) mają rozkład Gaussa.

**50. Czym jest hiperparametr?**
* Parametr, którego model nie uczy się sam z danych (np. $\lambda$ w Ridge), lecz musi zostać dobrany przez programistę.

---
