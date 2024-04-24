---
{"dg-publish":true,"permalink":"/taragna/tar-22b-risposte-di-sistemi-del-ii-ordine/"}
---

## Introduzione 
Innanzitutto quando parliamo di sistemi del secondo ordine quello di cui parliamo sono i sistemi la cui FdT ha due poli al denominatore. 
- $\deg{N_H}<\deg{D_H}$, per cui abbiamo che il numeratore può essere una costante oppure un polinomio di I grado.
- Nei sistemi di II ordine, dato che ci possono essere due poli, questi possono anche essere complessi coniugati, cosa che non succedeva nel caso di sistemi del I ordine.
- Inoltre, la risposta all'impulso per sistemi del II ordine la ignoreremo: si parlerà **solo di risposta al gradino**.

Qui abbiamo sempre $$u(t)=\overline{u}\epsilon(t)$$quindi anche $$U(s)=\frac{\overline{u}}{s}$$ e $$Y(s)=H(s)U(s)=H(s)\frac{\overline{u}}{s}$$(perchè si, stiamo ancora considerando il caso in cui il sistema parte a riposo, quindi abbiamo solo una risposta forzata).
### Due poli reali e distinti
Abbiamo $$H(s)=\frac{K^\star}{(s-p_1)(s-p_2)}$$
con $p_1\ne p_2$ ed entrambi $\ne0$.
Allora:
$$Y(s)=\frac{K^\star\overline{u}}{s(s-p_1)(s-p_2)}$$
Questa si può scomporre in fratti semplici e antitrasformare come:
$$y(t)=\frac{K^\star\overline{u}}{p_1p_2}\left[1+\frac{p_2}{p_1-p_2}e^{p_1t}-\frac{p_1}{p_1-p_2}e^{p_2t}\right]\epsilon(t)$$
Questo è uno di quei casi in cui col cavolo che so graficare a colpo sicuro, quindi uso il teorema del valore iniziale e del valore finale dove posso.
- il teorema del valore iniziale vale sempre, perchè sicuramente la funzione è strettamente propria, e mi esce $0$
- il teorema del valore finale è valido solo se $p_1<0$ e $p_2<0$ (sono reali quindi la loro parte reale è tutto ciò che sono, va bene scrivere così) (cioè è BIBO-stabile), e mi da $y_\infty=\frac{K^\star\overline{u}}{p_1p_2}$

Posso scrivere una **costante di tempo equivalente**, ma non posso calcolarla facilmente; **posso ottenerne un'approssimazione**, immaginando una costante di tempo associata ad ogni polo e sommandole:
$$\tau_1=\left|\frac{1}{p_1}\right|,\ \tau_2=\left|\frac{1}{p_2}\right|$$
$$\tau_{eq}\approx\tau_1+\tau_2$$
(Questa approssimazione è tanto migliore più sono distanti tra loro i poli del sistema).
Se poi uno vuole, può effettivamente graficare o comunque studiare meglio questa funzione $y(t)$ per capirne l'andamento oltre che ai punti iniziale e finale, che sono di per sè simili al caso del sistema di I ordine.
Si ottiene anche un grafico molto simile alla convergenza esponenziale della risposta al gradino di un sistema di I ordine, tuttavia c'è una sostanziale differenza: in $t=0$ il segnale **parte con una tangente orizzontale**, quindi ha un punto di flesso.
![Pasted image 20231128111846.png](/img/user/img/Pasted%20image%2020231128111846.png)
![Pasted image 20231128111836.png](/img/user/img/Pasted%20image%2020231128111836.png)

In verità dato che è così simile ad un sistema del I ordine, possiamo perfino calcolarci la **costante di tempo equivalente $\tau_{eq}$** su MATLAB *come se fosse di primo ordine*, cioè con il Rise Time da $0$ al $63\%$, per esempio.
In effetti, la risposta che questo sistema ci da è veramente tanto simile alla risposta (in particolare, sono entrambe monotone crescenti e convergenti) che ci darebbe un sistema di I ordine con la stessa costante di tempo (per provarlo basta scrivere una funzione di trasferimento in forma di Bode mettendo la $\tau_{eq}$).
![Pasted image 20231128112452.png](/img/user/img/Pasted%20image%2020231128112452.png)

### Due poli reali e distinti e uno zero reale
Se la FdT ha forma $$H(s)=\frac{K^\star(s-z)}{(s-p_1)(s-p_2)}$$
con $p_1,\ p_2,\ z$ distinti e non nulli, allora
$$Y(s)=H(s)U(s)=\frac{K^\star(s-z)\overline{u}}{s(s-p_1)(s-p_2)}$$
che antitrasformando diventa 
$$y(t)=\frac{K^\star z\overline{u}}{p_1p_2}\left[1-\frac{(p_1-z)p_2}{z(p_1-p_2)}e^{p_1t}+\frac{(p_2-z)p_1}{z(p_1-p_2)}e^{p_2t}\right]$$
**Se non ci sono sotto o sovra elongazione, vedi sotto,** ha sempre un grafico dello stesso tipo di prima, una specie di esponenziale convergente ma che schiribissa alla partenza
![Pasted image 20231128115845.png](/img/user/img/Pasted%20image%2020231128115845.png)

Variando $z$ notiamo che la risposta del sistema è sempre più "veloce" (raggiunge prima il valore $0.63y_\infty$) quanto più $z$ è vicino allo $0$.
![Pasted image 20231128115954.png](/img/user/img/Pasted%20image%2020231128115954.png)

In effetti, possiamo approssimare la costante di tempo immaginando anche una costante di tempo associata allo zero e scrivendo: $$\tau_{eq}=\left(\sum_i \left|\frac{1}{p_i}\right|\right)-\left|\frac{1}{z}\right|$$
**La costante di tempo non ha senso se ci sono elongazioni, se ho capito bene.**
Notiamo però che a seconda della posizione dello zero $z$ rispetto ai poli e a $0$ possono verificarsi i fenomeni di:
- **un cazzo di niente** se lo zero si trova a sinistra del polo a modulo minore (e puoi calcolare la costante di tempo equivalente di un sistema di primo grado molto simile) - al più, più lo zero vicino è in modulo allo $0$ più la risposta è veloce
- **sovra-elongazione** se lo zero si trova tra il polo a modulo minore e $0$; in questo caso con `ltiview` mi viene facile calcolare la sovra-elongazione (distanza rispetto al valore di regime) e il valore di picco. Un valore dello zero più vicino in modulo a $0$ mi fa avere una sovra-elongazione maggiore 
	- ![Pasted image 20231201111013.png](/img/user/img/Pasted%20image%2020231201111013.png)
- **sotto-elongazione** se lo zero si trova a destra dello $0$ (è positivo). Anche qui l'effetto è maggiore minore è la differenza tra lo zero e lo $0$. Questa non è proprio semplice da vedere con MATLAB perchè non ho il "valore di picco" ma ho un picco al contrario. Magari posso fare il picco di `abs` del vettore... boh.
	- ![Pasted image 20231201111504.png](/img/user/img/Pasted%20image%2020231201111504.png)
	- Esempio: tirando la cloche di un aereo per tirarlo su ottieni sempre un "undershoot" di questo tipo (FdT tra movimento della cloche e altezza del velivolo) - quindi occhio perchè prima affossi un pochino il muso e poi ti alzi. Se provi a fare sta cosa troppo vicino ad un ostacolo sicuro ti schianti.
### Due poli complessi coniugati
Una FdT con due poli complessi coniugati si può scrivere in [[Taragna/TAR06.Analisi nel dominio del tempo e della trasformata di Laplace di sistemi LTI TC#Forma zeri e poli generalizzata a polinomi aventi radici complesse\|forma zeri e poli generalizzata a polinomi aventi radici complesse]], quindi in forma
$$K\frac{\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$$
con
- $K$ guadagno,
- $\omega_n$ pulsazione naturale (della coppia di complessi coniugati),
- $0<\zeta<1$ smorzamento (della coppia di complessi coniugati)
![Pasted image 20230426154439.png](/img/user/img/Pasted%20image%2020230426154439.png)

Definiamo allora una **costante di tempo** come $\tau=1/\zeta\omega_n$.

La risposta la calcoliamo dall'antitrasformata di $Y(s)=H(s)U(s)$ come prima, e a sto giro faccio copia e incolla prima di uccidermi:
![Pasted image 20231201112717.png](/img/user/img/Pasted%20image%2020231201112717.png)

Cioè abbiamo $$\text{costante}\cdot(1-\text{inviluppo esponenziale decrescente (poli a parte reale strettamente negativa)}\cdot\text{termine oscillante)}$$
![Pasted image 20231201113240.png](/img/user/img/Pasted%20image%2020231201113240.png)

Presenta **sia sovra-elongazione sia sottoelongazione**, inoltre dopo questi due picchi continua ad oscillare, fermandosi dopo poco dato l'inviluppo esponenziale. La risposta quindi non è assolutamente monotona.

I parametri tipici sono:
- valore di regime $y_\infty$, calcolabile con il teorema del valore finale (sì, vale se poli a parte reale strettamente negativa) - il valore finale è $K\overline{u}$
- valore di picco $y_\max$ che otteniamo da `ltiview`, sempre plottando, ed è ovviamente $>y_\infty$
- sovraelongazione massima $\hat{s}=(y_\max-y_\infty)/y_\infty$ tra $0$ e $1$, si può anche considerare in termini percentuali $\hat{s}_\%=\hat{s}\cdot100\%$
- tempo di picco $\hat{t}$, tempo tale per cui $y(\hat{t})=y_\max$
- tempo di salita $t_s$, primo istante temporale in cui la risposta raggiunge il valore di regime $y(t_s)=y_\infty$, anche se dopo la risposta cresce per arrivare al picco (questo si può definire sempre)
	- ![Pasted image 20231201114338.png](/img/user/img/Pasted%20image%2020231201114338.png)
- rise time $t_r$ dal $10\%$ al $90\%$ (solo per sistemi del secondo ordine con risposta oscillante, quindi con poli complessi coniugati si può fare - non si può per quelli del secondo ordine non oscillanti)
	- ![Pasted image 20231201114713.png](/img/user/img/Pasted%20image%2020231201114713.png)
- tempo di assestamento al $5\%$ - tempo perchè la risposta differisca dal valore finale di non più del $5\%$. (sarebbe il rise time da $0\%$ al $95\%$).
Ci sono anche formule che ti permettono di calcolare alcuni di questi parametri senza plottare, per cui la sovraelongazione massima dipende unicamente dallo smorzamento, mentre tempo di picco sia da smorzamento che da pulsazione naturale (valgono solo nel caso di questi valori complessi coniugati, non nel caso di secondo ordine quelli di prima coi poli reali):
![Pasted image 20231201114114.png](/img/user/img/Pasted%20image%2020231201114114.png)
![Pasted image 20231201114627.png](/img/user/img/Pasted%20image%2020231201114627.png)
![Pasted image 20231201114829.png](/img/user/img/Pasted%20image%2020231201114829.png)
![Pasted image 20231201114917.png](/img/user/img/Pasted%20image%2020231201114917.png)

Vediamo che al variare del solo smorzamento abbiamo questo tipo di effetto sulla risposta (più oscillazioni):
![Pasted image 20231201115054.png](/img/user/img/Pasted%20image%2020231201115054.png)

Al variare della sola pulsazione naturale, invece, le elongazioni restano uguali ma si velocizza la risposta:
![Pasted image 20231201115133.png](/img/user/img/Pasted%20image%2020231201115133.png)

#### Caso $\zeta=1$
![Pasted image 20231201115307.png](/img/user/img/Pasted%20image%2020231201115307.png)
![Pasted image 20231201115316.png](/img/user/img/Pasted%20image%2020231201115316.png)
![Pasted image 20231201115338.png](/img/user/img/Pasted%20image%2020231201115338.png)
