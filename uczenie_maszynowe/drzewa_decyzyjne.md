# Drzewa decyzyjne

Jest to metoda klasyfikacji, która nie dorównuje jakością metodzie SVM, ale jej zaletą jest, tzw. "wyjaśnialność" wyników klasyfikacji (XAI – Explainable AI).

Celem budowy drzewa decyzyjnego jest dobór cech oraz progów, które zwiększają jednorodność (homogeniczność) nowo utworzonych podzbiorów.

$$
z = \max_i \ (H^i_{k+1} - H_k)
$$

Próbujemy znaleźć podział $i$, dla którego mamy największy zysk homogeniczności.

$$
H^i_{k+1} = \frac{n_{+}}{n}H^i_{+} + \frac{n_{-}}{n}H^i_{-}
$$

Homogeniczność podziału, to średnia homogeniczności podzbiorów ważona przez ich liczebność.

Kryteria zakończenia podziałów:

- niedodatni zysk,
- minimalna liczebność podzbioru przed podziałem (min_samples_split),
- minimalna liczebność podzbioru po podziale (min_samples_leaf),
- maksymalna głębokość drzewa.

## Miary homogeniczności

### Entropia Shannona

$$
H = -\sum_{k=1}^K p_k \log p_k
$$

$p_k$ – prawdopodobieństwo znalezienia klasy $k$

$K$ – liczba klas w podzbiorze

### Współczynnik Gini'ego

$$
G = P(t_i \neq t_j) = 1 - P(t_i = t_j)
$$

$$
G= 1 - \sum_{k=1}^K p_k^2
$$

$t_i$ – etykieta próbki $i$ podzbioru
