# Expectation Maximization

Metoda EM to metoda klasteryzacji podobna do k-średnich, która zamiast modelować klastry za pomocą samych centroidów, wykorzystuje również macierze kowariancji. Pozwala zatem uchwycić klastry, które nie są idealnie sferyczne.

## Expectation

Mamy $n$ próbek, które mogą należeć do $K$ klastrów. Dla każdego klastra $k$ dobieramy losowo początkową wartość centroidów oraz macierzy kowariancji. Następnie określamy przynależność punktów do tych klastrów, ale nie zupełnie tylko z jakimś prawdopodobieństwem.

$P(A | \mathbf{x}_i)$ – prawdopodobieństwo, że $\mathbf{x}_i \in A$

Niestety nie da się tego łatwo policzyć, trzeba użyć twierdzenia Bayesa.

$$
P(A | \mathbf{x}_i) = \frac{P(\mathbf{x}_i | A) P(A)}{P(\mathbf{x}_i)}
$$

$P(\mathbf{x}_i | A)$ – prawdopodobieństwo znalezienia próbki $\mathbf{x}_i$ w klastrze $A$

$P(A)$ – prawdopodobieństwo wystąpienia klastra $A$

$P(\mathbf{x}_i)$ – prawdopodobieństwo znalezienia próbki $\mathbf{x}_i$ we wszystkich klastrach

Wykorzystujemy wzór na prawdopodobieństwo przy rozkładzie normalnym.

$$
P(\mathbf{x}_i | A) = \frac{1}{\sqrt{2\pi\det(\mathbf{C}_A)}} \exp\left(-\frac{1}{2}(\mathbf{x}_i - \boldsymbol{\mu}_A)^\top\mathbf{C}^{-1}_A(\mathbf{x}_i - \boldsymbol{\mu}_A)\right)
$$

Prawdopodobieństwo wystąpienia próbki to suma prawdopodobieństw wystąpienia próbki dla każdego z klastrów pomnożonych przez prawdopodobieństwo wystąpienia klastra.

$$
P(\mathbf{x}_i) = \sum_{k=1}^K P(\mathbf{x}_i | k)\cdot P(k)
$$

Na $P(A)$ nie ma żadnego wzoru. Tutaj przyjmujemy jakąś wartość początkową. Jeżeli przyjmiemy, że występowanie każdego z klastrów jest równie prawdopodobne.

$$
P(A) = \frac1K
$$

## Maximization

Następnie dokonujemy reestymacji parametrów. Do tego wykorzystujemy zmodyfikowane wzory na średnią arytmetyczną oraz wariancję.

$$
\boldsymbol{\mu}_A = \sum_{i=1}^{n} \xi^A_i \mathbf{x}_i
$$

$$
\mathbf{C}_A = \sum_{i=1}^n \xi^A_i (\mathbf{x}_i - \boldsymbol{\mu}_A)(\mathbf{x}_i - \boldsymbol{\mu}_A)^\top
$$

Gdzie

$$
\xi_i^A = \frac{P(A|\mathbf{x}_i)}{\sum_{j=1}^{n}P(A|\mathbf{x}_j)}
$$

Mianownik jest stały dla każdego $\xi_i^A$, więc gdyby go wyciągnąć przed sumę, to dostalibyśmy po prostu średnią i kowariancję ważoną przez prawdopodobieństwo.

$$
S = \sum_{i=1}^n P(A|\mathbf{x}_i)
$$

$$
\boldsymbol{\mu}_A = \frac1S\sum_{i=1}^{n} P(A|\mathbf{x}_i) \mathbf{x}_i
$$

$$
\mathbf{C}_A = \frac1S \sum_{i=1}^n P(A|\mathbf{x}_i) (\mathbf{x}_i - \boldsymbol{\mu}_A)(\mathbf{x}_i - \boldsymbol{\mu}_A)^\top
$$

Nowe $P(A)$ natomiast to średnia przynależności punktów do klastra $A$.

$$
P(A) = \frac1n \sum_{i=1}^n P(A|\mathbf{x}_i)
$$