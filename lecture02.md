

## 1. Metody Bezgradientowe (Black-box)
Stosowane, gdy nie mamy dostępu do pochodnych funkcji (np. przy doborze hiperparametrów).
* **Random Search**: Losowanie punktów z rozkładu (np. jednostajnego). Często skuteczniejszy niż Grid Search w wysokich wymiarach, bo lepiej przeszukuje istotne parametry.
* **Grid Search**: Systematyczne sprawdzanie punktów na zdefiniowanej siatce. Podatny na "klątwę wymiarowości".
* **Optymalizacja Bayesowska**: Buduje model probabilistyczny funkcji celu. Równoważy **eksplorację** (szukanie w nowych miejscach) i **eksploatację** (sprawdzanie okolic znanych minimów).

## 2. Spadek Gradientu (Gradient Descent) w 1D
Dla funkcji $f(x) = ax^2$ ($a>0$):
* **Gradient**: $f'(x) = 2ax$.
* **Reguła aktualizacji**: $x_{k+1} = x_k - h \cdot f'(x_k) = (1 - 2ah)x_k$.
* **Zbieżność**:
    * $h < \frac{1}{a}$: Metoda jest zbieżna.
    * $h < \frac{1}{2a}$: Zbieżność monotoniczna (najszybsza dla $h = \frac{1}{2a}$ – minimum w jednym kroku).
    * $\frac{1}{2a} < h < \frac{1}{a}$: Zbieżność z oscylacjami.
    * $h = \frac{1}{a}$: Stałe oscylacje (brak zbieżności).
    * $h > \frac{1}{a}$: Rozbieżność.



## 3. Optymalizacja Wielowymiarowa
Dla $f(x) = x^T Ax$:
* **Współczynnik uwarunkowania $\kappa(A)$**: Stosunek największej do najmniejszej wartości własnej ($\lambda_{max} / \lambda_{min}$).
* **Problem "Wąskiej Doliny"**: Jeśli $\kappa(A)$ jest duży, poziomicami są wydłużone elipsoidy. Gradient Descent oscyluje między ścianami, bardzo wolno posuwając się wzdłuż dna doliny.

## 4. Zaawansowane Optymalizatory
Aby przyspieszyć zbieżność, stosuje się modyfikacje:
* **Momentum (Pęd)**: Dodaje "bezwładność" do ruchu. Akumuluje poprzednie gradienty, co pozwala wygładzić oscylacje i szybciej przechodzić przez płaskie obszary.
* **RMSProp**: Adaptacyjnie skaluje krok uczenia dla każdego parametru z osobna, dzieląc gradient przez pierwiastek ze średniej kwadratów gradientów. Świetne dla funkcji o różnych skalach nachylenia.
* **Adam**: Łączy Momentum i RMSProp. Najpopularniejszy obecnie algorytm. Zawiera **korekcję błędu (bias correction)**, aby zniwelować wpływ początkowej inicjalizacji zerami.



## 5. Metodologia Uczenia Maszynowego
Dobór hiperparametrów (learning rate, rozmiar batcha) wymaga podziału danych:
1.  **Zbiór Treningowy**: Uczenie wag modelu (parametrów).
2.  **Zbiór Walidacyjny**: Wybór najlepszej konfiguracji hiperparametrów (zapobiega overfittingowi).
3.  **Zbiór Testowy**: Ostateczna ocena modelu – nigdy nie używany w procesie optymalizacji!
