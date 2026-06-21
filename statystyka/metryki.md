# Klasyfikacja binarna

Czułość możemy interpretować jako prawdopodobieństwo, że jeśli występuje klasa pozytywna, to czy klasyfikator to potwierdzi.

$$
\mathrm{czułość} = P(Y=1 | T=1) = \frac{\mathrm{TP}}{\mathrm{TP} + \mathrm{FN}}
$$

Natomiast precyzja to prawdopodobieństwo, że jeśli klasyfikator stwierdza występowanie klasy pozytywnej, to się nie myli.

$$
\mathrm{precyzja} = P(T=1 | Y=1) = \frac{\mathrm{TP}}{\mathrm{TP} + \mathrm{FP}}
$$

F1-score to średnia harmoniczna czułości i precyzji.

$$
H = \frac{n}{\displaystyle \sum \dfrac{1}{x_i}}
$$

$$
F_1 = \frac{2}{\mathrm{czułość}^{-1} + \mathrm{precyzja}^{-1}}
$$

Istnieje również $F_\beta$-score, gdzie $\beta$ oznacza, ile razy czułość jest ważniejsza od precyzji.

$$
F_\beta = \frac{\beta^2 + 1}{(\beta^2 \cdot \mathrm{czułość}^{-1}) + \mathrm{precyzja}^{-1}}
$$

Są też dodatkowe współczynniki, które skupiają się na klasie negatywnej. Jednym z nich jest współczynnik fałszywej akceptacji FAR (False Acceptance Rate) lub inaczej FMR (False Match Rate). Drugim natomiast jest współczynnik fałszywego odrzucenia FRR (False Rejection Rate) lub FNMR (False Non-Match Rate).

$$
\mathrm{FAR} = P(Y=1 | T=0) = \frac{\mathrm{FP}}{\mathrm{FP} + \mathrm{TN}}
$$

$$
\mathrm{FRR} = P(Y=0 | T=1) = \frac{\mathrm{FN}}{\mathrm{FN} + \mathrm{TP}}
$$

Poprawność albo jakość to jest iloraz sumy wartości po przekątnej macierzy pomyłek przez sumę wszystkich wartości.

$$
\mathrm{ACC} = \frac{\mathrm{TP} + \mathrm{TN}}{\mathrm{TP} + \mathrm{TN} + \mathrm{FP} + \mathrm{FN}}
$$

# Klasyfikacja wieloklasowa

Balanced accuracy to efektywnie średnia czułości dla wszystkich klas.

$$
\mathrm{Balanced\ accuracy} = \frac1K \sum_{i=1}^K R_i 
$$

Podobnie macro F1 to średnia F1 dla wszystkich klas.

$$
\mathrm{Macro\ F1} = \frac1K \sum_{i=1}^K F_1^i 
$$

Matthews' correlation coefficient

$$
\mathrm{MCC} = \sqrt{\mathrm{TPR}\cdot\mathrm{TNR}\cdot\mathrm{PPV}\cdot\mathrm{NPV}} - \sqrt{\mathrm{FNR}\cdot\mathrm{FPR}\cdot\mathrm{FOR}\cdot\mathrm{FDR}}
$$

Gdzie

$$
\mathrm{FNR} = 1 - \mathrm{TPR}
$$

$$
\mathrm{FPR} = 1 - \mathrm{TNR}
$$

$$
\mathrm{FOR} = 1 - \mathrm{NPV}
$$

$$
\mathrm{FDR} = 1 - \mathrm{PPV}
$$

Natomiast TPR oraz TNR to czułości dla odpowiednio pozytywnej i negatywnej klasy, a PPV i NPV to precyzje.