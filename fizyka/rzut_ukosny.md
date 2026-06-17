# Bez oporu powietrza

$$
\frac{dx}{dt} = v_x = v_0 \cos \alpha
$$

$$
\frac{dy}{dt} = v_y = v_0 \sin \alpha - gt
$$

Całkując obustronnie (zakładając $x_0 = 0$ i $y_0 = 0$)

$$
x(t) = (v_{0}\cos \alpha)t
$$

$$
y(t) = (v_{0}\sin \alpha)t - \frac{gt^2}{2}
$$

Zauważmy, że $v_x$ nie ulega zmianie, więc ruch po $x$ jest jednostajny. Natomiast, na ruch po $y$ jest nałożone stałe przyspieszenie grawitacyjne, więc stosujemy wzór na ruch jednostajnie przyspieszony.

$$
t = \frac{x}{v_0 \cos \alpha}
$$

Podstawiamy pod $y(t)$.

$$
y(x) = v_0 \sin \alpha \frac{x}{v_0 \cos \alpha} - \frac{g}{2}\frac{x^2}{v_0^2\cos^2\alpha}
$$

Trajektoria rzutu ukośnego

$$y(x) = x\tan\alpha - \frac{g}{2v_0^2\cos^2\alpha}x^2$$

Widać, że tor ruchu jest parabolą. Jeśli $y(d)=0$, gdzie $d$ to zasięg.

$$
d\tan\alpha - \frac{g}{2v_0^2\cos^2\alpha}d^2 = 0
$$

$$
d(\tan \alpha - \frac{g}{2v_0^2\cos^2\alpha}d) = 0
$$

$$
\frac{g}{2v_0^2\cos^2\alpha}d = \frac{\sin \alpha}{\cos \alpha}
$$

$$
d = \frac{\sin \alpha}{\cos \alpha} \frac{2v_0^2\cos^2\alpha}{g} = \frac{v_0^2 \cdot 2 \sin \alpha \cos \alpha}{g}
$$

$$d = \frac{v_0^2 \sin 2\alpha}{g}$$

Odwracając wzór, liczymy $v_0$.

$$v_0 = \sqrt{\frac{gd}{\sin 2\alpha}}$$

# Z oporem powietrza

Siła oporu jest przeciwnie skierowana do kierunku ruchu.

$$
F = -kv
$$

## Ruch po x

W kierunku $x$ siła oporu to jedyna siła działająca na ciało.

$$ma_x = -kv_x$$

$$
v'_x = -\frac{k}{m}v_x
$$

$$
\frac{dv_x}{dt} = -\gamma v_x
$$

Pochodna funkcji jest równa jej samej razy jakiś współczynnik, zapewne będzie to funkcja wykładnicza $e^x$.

$$
\frac{dv_x}{v_x} = -\gamma \, dt
$$

Całkując obustronnie

$$
\ln v_x = -\gamma t + C
$$

$$
v_x = e^{-\gamma t} \cdot C
$$

Dla $t = 0$

$$
v_0 \cos \alpha = 1 \cdot C
$$

$$
v_x = e^{-\gamma t} (v_0 \cos \alpha)
$$

Teraz jeśli scałkujemy to ponownie

$$
x(t) = \int e^{-\gamma t}(v_0 \cos \alpha) \, dt
$$

$$
-\gamma t = u
$$

$$
dt = -\frac{1}{\gamma} \, du
$$

$$
x(t) = -\frac{1}{\gamma}(v_0 \cos \alpha) \int e^u \,du
$$

$$
x(t) = -\frac{1}{\gamma}(v_0 \cos \alpha) (e^{-\gamma t}) + C
$$

Dla $t = 0$

$$
0 = -\frac{1}{\gamma}(v_0 \cos \alpha) + C
$$

$$
C = \frac{1}{\gamma}(v_0 \cos \alpha)
$$

$$
x(t) = -\frac{1}{\gamma}(v_0 \cos \alpha) (e^{-\gamma t}) + \frac{1}{\gamma}(v_0 \cos \alpha)
$$

$$
x(t) = \frac{v_0 \cos \alpha}{\gamma}(1 - e^{-\gamma t})
$$

## Ruch po y

$$
ma_y = -mg - kv_y
$$

$$
\frac{dv_y}{dt} = -g - \gamma v_y
$$

$$
\frac{dv_y}{-g - \gamma v_y} = dt
$$

Mnożymy obustronnie przez $-\gamma$

$$
\frac{-\gamma\,dv_y}{-g - \gamma v_y} = -\gamma\,dt
$$

$$
\ln|-g - \gamma v_y| = -\gamma t + C
$$

$$
g + \gamma v_y = e^{-\gamma t} \cdot C
$$

Dla $t = 0$

$$
g + \gamma v_0 \sin \alpha = C
$$

$$
v_y = \frac{1}{\gamma}(e^{-\gamma t}(g +\gamma v_0 \sin \alpha) - g)
$$

$$
y(t) = (\frac{g}{\gamma} + v_0 \sin \alpha) \int e^{-\gamma t}\,dt - \frac{gt}{\gamma}
$$

$$
y(t) = -(\frac{g}{\gamma^2} + \frac{v_0\sin\alpha}{\gamma}) e^{-\gamma t} - \frac{gt}{\gamma} + C
$$

Dla $t = 0$

$$
0 = -\frac{g}{\gamma^2} - \frac{v_0\sin\alpha}{\gamma} + C
$$

$$
C = \frac{g}{\gamma^2} + \frac{v_0\sin\alpha}{\gamma}
$$

$$
y(t) = (\frac{g}{\gamma^2} + \frac{v_0\sin\alpha}{\gamma}) - (\frac{g}{\gamma^2} + \frac{v_0\sin\alpha}{\gamma}) e^{-\gamma t} - \frac{gt}{\gamma}
$$

$$
y(t) = (\frac{g}{\gamma^2} + \frac{v_0\sin\alpha}{\gamma})(1 - e^{-\gamma t}) - \frac{gt}{\gamma}
$$

## Tor ruchu

$$
x(t) = \frac{v_0 \cos \alpha}{\gamma}(1 - e^{-\gamma t})
$$

$$
1 - e^{-\gamma t} = \frac{\gamma}{v_0 \cos \alpha} x
$$

$$
e^{-\gamma t} = 1 - \frac{\gamma}{v_0 \cos \alpha} x
$$

$$
t = -\frac{1}{\gamma}\ln(1 - \frac{\gamma}{v_0 \cos \alpha} x)
$$

Wstawiamy wzór na $t$ oraz $1-e^{-\gamma t}$ do $y(t)$

$$
y(x) = (\frac{g}{\gamma^2} + \frac{v_0\sin\alpha}{\gamma})(1 - e^{-\gamma t}) - \frac{gt}{\gamma}
$$

$$
y(x) = (\frac{g}{\gamma^2} + \frac{v_0\sin\alpha}{\gamma})(\frac{\gamma}{v_0 \cos \alpha} x) - \frac{g}{\gamma}(-\frac{1}{\gamma}\ln(1 - \frac{\gamma}{v_0 \cos \alpha}x))
$$

$$
y(x) = (\frac{g}{\gamma v_0 \cos\alpha} + \tan\alpha)x + \frac{g}{\gamma^2}\ln(1 - \frac{\gamma}{v_0 \cos \alpha}x)
$$

## Zasięg

Przyrównujemy $y(x)$ do $0$. Rozwiązanie będzie zawierało funkcję Lamberta W. Zamiast tego znajdujemy rozwiązanie numerycznie metodą równego podziału (bisection method).

$$
y(d) = 0
$$

Musimy znaleźć przedział, w którym znajduje się rozwiązanie i granice przedziału muszą mieć przeciwne znaki.

$$
x(t) = \frac{v_0 \cos \alpha}{\gamma}(1 - e^{-\gamma t})
$$

Dla bardzo małego $0 < a \ll 1$. Na przykład, jeśli $a = 0.0001$ oraz $\gamma = 1$.

$$
1 - e^{-0.0001} = -0.0001
$$

$$
x(a) < 0
$$

Górny przedział możemy policzyć poprzez granicę.

$$
b = \lim_{t \to \infty} x(t)
$$

$$
\lim_{t \to \infty} \frac{v_0 \cos \alpha}{\gamma}(1 - e^{-\gamma t})
$$

$$
b = \frac{v_0 \cos \alpha}{\gamma}
$$

Wiadomo, że $x(b) > 0$, ponieważ pocisk nie będzie zawracał.

## Prędkość początkowa

$$
y(v_0) = 0
$$

Tutaj możemy znaleźć wartość $a$.

$$
y(x) = (\frac{g}{\gamma v_0 \cos\alpha} + \tan\alpha)x + \frac{g}{\gamma^2}\ln(1 - \frac{\gamma}{v_0 \cos \alpha}x)
$$

Argument logarytmu musi być dodatni.

$$
1 - \frac{\gamma}{v_0 \cos \alpha}d > 0
$$

$$
1 > \frac{\gamma}{v_0 \cos \alpha}d
$$

$$
v_0 > \frac{\gamma}{\cos \alpha}d
$$

$$
a = \frac{\gamma}{\cos \alpha}d(1 + \epsilon)
$$

Gdzie $0 < \epsilon \ll 1$

$$
\lim_{\epsilon \to 0^+} \ln \epsilon = -\infty
$$

$$
y(a) < 0
$$

Na górny przedział nie mamy konkrentego warunku.

$$
y(b) > 0
$$

## Dokładne rozwiązania

$$
v_0 = \frac{\gamma d}{\cos\alpha (1 + W_0(-\exp(-1 -\frac{\gamma^2d\tan\alpha}{g})))}
$$
