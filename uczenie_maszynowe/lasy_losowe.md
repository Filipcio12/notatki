# Lasy losowe

Agregujemy $K$ losowych klasyfikatorów (drzew decyzyjnych). Każde drzewo ma inny zbiór danych utworzony poprzez losowanie ze zwracaniem $|S|$ elementów z oryginalnego zbioru $S$, czyli ma tyle samo elementów co w oryginalnym, ale niektóre elementy się powtarzają, a niektóre w ogóle nie występują.

Losowe drzewo podczas podziału losowo dobiera $d$ cech z $D$ wszystkich cech i wybiera cechę do podziału spośród tych $d$ cech. Często się przyjmuje, że $d = \sqrt{D}$.

Lasy losowe zwiększają skuteczność drzew decyzyjnych, kosztem ich wyjaśnialności.

## Metody agregacji wyników

### Bagging

Wybieramy klasę $j$, na którą było najwięcej głosów, ale głosy klasyfikatorów z większą skutecznością mają większą wagę.

$$
f_k(\mathbf{x}) = \sum_{i \rightarrow k} \alpha_i
$$

$$
\mathrm{arg}\max_j f_j
$$

$f_k$ – suma głosów klasyfikatorów, które głosują na klasę $k$ ważona przez ich istotność $\alpha_i$

$\alpha_i$ – istotność klasyfikatora $i$

Istotność klasyfikatora ("amount to say") można różnie zdefiniować. W przypadku baggingu można by przyjąć po prostu skuteczność klasyfikatora (accuracy) na podstawie, np. walidacji krzyżowej.

### Boosting (wzmacnianie)

Jest to pewna kaskada klasyfikatorów, które mają zmodyfikowany zbiór treningowy. Każda próbka w zbiorze treningowym będzie miała jakąś wagę $w_i$, która służy do wyznaczenia prawdopodobieństwa doboru próbki do mini-batch'a.

Dla pierwszego klasyfikatora, wszystkie próbki mają jednakową wagę.

$$
w_i = \frac{1}{n}
$$

Gdzie $n$ to liczba próbek.

Dla następnych klasyfikatorów:

$$
\forall_i \ y_i \neq t_i: \ w_i = \beta \cdot \frac{1}{n} \quad \beta > 1
$$

$$
\forall_j \ y_j = t_j: \ w_j = \gamma \cdot \frac{1}{n} \quad \gamma < 1
$$

Prawdopodobieństwo doboru próbki $i$:

$$
p_i = \frac{w_i}{\sum_j w_j}
$$

### Adaptive boosting (AdaBoost)

Zazwyczaj w przypadku lasów losowych, klasyfikatory cząstkowe są tworzone z założenia słabe (weak learners). Często są to drzewa decyzyjne jednego poziomu (stump).

W przypadku adaboostingu, istotność klasyfikatora często definiuje się w poniższy sposób.

$$
\alpha = \ln \frac{1 - \epsilon}{\epsilon} + \ln(K-1)
$$

$\epsilon$ – błąd klasyfikatora, czyli np. $(1 - \mathrm{Accuracy})$

$K$ – liczba klas

Zmiana wag próbek dla nowego klasyfikatora wykorzystuje istotność poprzedniego klasyfikatora.

$$
\forall_i \ y_i \neq t_i: \ w_i^{p+1} = w_i^p \cdot e^\alpha
$$

$$
\forall_j \ y_j = t_j: \ w_j^{p+1} = w_j^p \cdot e^{-\alpha}
$$

Dla problemów wieloklasowych często przy dobrej klasyfikacji nie modyfikuje się wagi próbki.

### Gradient boosting

Najpopularniejszą metodą z rodziny gradient boostingu jest, tzw. XGBoost (Extreme Gradient Boost). Do zobrazowania algorytmu rozwiązujemy problem regresji.

Zaczynamy od bazowej predykcji

$$
F_0 = \frac1n \sum_i t_i
$$

Wykorzystujemy gradient funkcji straty, np. MSE.

$$
L = \frac1n \sum_i (t_i - y_i)^2
$$

Funkcja kryterialna służąca do podziału drzew decyzyjnych w przypadku XGBoost

$$
\mathrm{zysk} = S(\mathrm{lewa}) + S(\mathrm{prawa}) - S(\mathrm{baza})
$$

$$
S = \frac{(\sum_i g_i)^2}{\sum_i h_i + \lambda}
$$

$S$ – funkcja kryterialna

$g_i$ – gradient funkcji straty $L$ w dla próbki $i$ podzbioru

$h_i$ – hesjan funkcji straty $L$ w dla próbki $i$ podzbioru

$\lambda$ – współczynnik regularyzacji

Reestymacja predykcji:

$$
f_m(\mathbf{x}) = -\frac{\sum_i g_i}{\sum_i h_i + \lambda}
$$

$$
y^{{m+1}}_i = y^{(m)}_i + \eta f_m(\mathbf{x}_i)
$$

Predykcja:

$$
F_M(\mathbf{x})=F_0+\eta f_1(\mathbf{x})+\eta f_2(\mathbf{x})+\ldots+\eta f_M(\mathbf{x})
$$