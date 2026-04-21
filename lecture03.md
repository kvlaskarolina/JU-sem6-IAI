

## 1. Perceptron i Podstawy Neuronu
Perceptron to matematyczny model biologicznego neuronu. Składa się z trzech głównych etapów:
* **Agregacja:** Obliczanie sumy ważonej wejść: $z = w^T x + b$.
    * $w$ – wagi (ważność cech), $x$ – wejścia, $b$ – bias (przesunięcie/próg).
* **Aktywacja:** Funkcja progowa zamienia $z$ na 0 lub 1.
* **Geometria:** Perceptron tworzy **hiperpłaszczyznę** rozdzielającą klasy. Działa poprawnie tylko dla danych **liniowo separowalnych**.



## 2. Wielowarstwowy Perceptron (MLP)
Rozszerzenie perceptronu o warstwy ukryte.
* **Nieliniowość:** Dzięki nieliniowym funkcjom aktywacji (np. ReLU, Sigmoid), MLP potrafi modelować złożone, zakrzywione granice decyzyjne.
* **Aproksymacja:** Zgodnie z twierdzeniem o uniwersalnej aproksymacji, MLP z jedną warstwą ukrytą może przybliżyć dowolną funkcję ciągłą.

## 3. Optymalizacja i Spadek Gradientu (GD)
Celem jest znalezienie wag, które minimalizują funkcję błędu.
* **Klasyczny GD:** Oblicza gradient dla **całego** zbioru danych. Bardzo dokładny, ale ekstremalnie wolny przy dużych danych.
* **Stochastic Gradient Descent (SGD):** Oblicza gradient dla **jednego** losowego przykładu. Jest szybki i wprowadza "szum", który pomaga uciec z minimów lokalnych.
* **Mini-batch GD:** Złoty środek – obliczenia na małych paczkach danych (np. 32-128 przykładów).



## 4. Zaawansowane Optymalizatory
Modyfikują standardowy GD, aby szybciej i stabilniej docierać do celu:
* **Momentum:** "Pęd" wygładza oscylacje i przyspiesza ruch w stałym kierunku.
* **RMSProp:** Adaptacyjnie skaluje krok uczenia dla każdej wagi osobno (dzielenie przez średnią kwadratów gradientów).
* **Adam:** Najpopularniejszy; łączy Momentum i RMSProp, dodając korekcję biasu na początku uczenia.

## 5. Klasyfikacja i Funkcja Softmax
Dla problemów wieloklasowych (np. rozpoznawanie cyfr 0-9):
* **Softmax:** Zamienia surowe wyniki sieci (logity) na rozkład prawdopodobieństwa (wartości dodatnie sumujące się do 1).
* **Cross-entropy:** Standardowa funkcja błędu w klasyfikacji. Karze model tym mocniej, im bardziej "pewny" jest on błędnej odpowiedzi.

## 6. Metodologia: Podział danych
Aby uniknąć przetrenowania (overfittingu) i błędnego wyboru parametrów:
* **Train:** Do nauki wag.
* **Validation:** Do wyboru **hiperparametrów** (np. learning rate, liczba neuronów).
* **Test:** Do ostatecznego, obiektywnego sprawdzenia jakości modelu (nigdy nie używany w treningu!).
