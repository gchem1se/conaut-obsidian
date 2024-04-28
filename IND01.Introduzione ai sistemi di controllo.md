---  
share: true  
---  
Esempio di sistema di controllo: l'automobile. In questo caso, il regolatore dinamico (o meglio, *il controllore*) sono io. Attraverso il piede (che è il mio *ingresso di controllo*) implemento la legge di controllo, che tiene conto dell'attuale uscita (la forza sul pedale), dell'obiettivo voluto (andare ad 80 Km/h) e dello stato attuale (l'attuale velocità), che vedo attraverso l'occhio (lo stimatore).  
Il sistema è *osservabile* attraverso il tachimetro. Una velocità non segnata sul tachimetro non è in se osservabile (meaning that anche in un tempo infinito non potrei raggiungere la velocità di 5000 Km/h); la velocità è *controllabile* attraverso il pedale (meaning that se voglio aumentarla o diminuirla agisco sui pedali - e non tutte le velocità sono controllabili a tutte le altre, oppure sì in questo caso scemo).  
  
![Pasted image 20240207122708.png](./img/Pasted%20image%2020240207122708.png)  
  
## Elementi comuni ai sistemi di controllo  
- **Sistema**: ha come ingressi *disturbi* e una *variabile di comando* $u_C$, ha un'*uscita di interesse soggetta a controllo* $y_S$ e degli *stati interni non sempre accessibili e misurabili* $x$  
- **Azionamento / attuatore**: ha come ingresso una *variabile di controllo ad energia trascurabile* $u$, come uscita la *variabile di comando del sistema* $u_C$. Questi sono già disponibili sul mercato, quindi non è necessario progettarli da zero.  
- **Trasduttore**: ha come ingresso *la variabile di uscita del sistema* $y_S$ e come uscita *la misura $y$ della stessa $y_S$ (ad energia trascurabile)*. Idealmente è lineare, statico, a parametri concentrati, senza disturbi. Già disponibile sul mercato.  
- **Riferimento**: $r$ spesso coincide con l'*uscita desiderata* $y_{\text{des}}$. Se costante, è detto **regolazione**. Se non costante, è detto **inseguimento**.  
- **Nodo di confronto**: ha come ingressi *le variabili $y_{\text{des}}$ e $y$* e ha come uscita *un segnale di errore $e$*. Effettua una differenza. Idealmente è lineare, statico, a parametri concentrati, senza disturbi.   
- **Controllore**: ha in ingresso *il segnale di errore $e$* e in uscita *il segnale di controllo $u$* dell'attuatore. Può essere analogico o digitale.  
- **Sistemi di monitoraggio**: diagnostica, allarmi, backup dei dati.  
### Schemi a blocchi  
Per qualche motivo, piacciono tanto.  
![Pasted image 20240207124621.png](./img/Pasted%20image%2020240207124621.png)![Pasted image 20240207124630.png](./img/Pasted%20image%2020240207124630.png)![Pasted image 20240207124702.png](./img/Pasted%20image%2020240207124702.png)  
I blocchi in parallelo sommano la loro $F(s)$ e quelli in serie la moltiiplicano. Ma già lo sapevi. L'unica cosa figa è *per scrivere velocemente la retroazione*:  
  
![Pasted image 20240207124841.png](./img/Pasted%20image%2020240207124841.png)  
  
La $F(s)$ di un anello è $\frac{G(s)}{1\mp G(s)H(s)}$. Quindi al denominatore c'è un $-$ se è una retroazione positiva e c'è un $+$ se è una retroazione positiva.  
## Specifiche di progetto  
Le specifiche di progetto definiscono il modo in cui l’uscita deve inseguire il riferimento. Le principali specifiche di progetto riguardano:  
- La stabilità del sistema di controllo (è la cosa più importante)  
- La robustezza della stabilità del controllo  
- Specifiche di progetto in regime permanente  
- La precisione dell’inseguimento  
- La capacità di rispondere in maniera ottimale ai disturbi, minimizzandone gli effetti  
- La forma della risposta del sistema durante il transitorio  
- L’attività sulla variabile di controllo  
### Specifiche di progetto in regime permanente  
Se il sistema è stabile è possibile garantire un regime permanente. Si definisce **precisione** di un sistema la specifica di progetto che dice che il mio sistema deve dare in output un'uscita $y_\infty$ uguale ad un valore noto (anche nullo) scelto in precedenza o al massimo discostarsi da esso di un $e_{\max}$ anch'esso noto (avere un *errore di inseguimento* $|y_{\text{des}}-y_\infty|\le e_{\max}$).  
  
![Pasted image 20240207125437.png](./img/Pasted%20image%2020240207125437.png)  
### Specifiche sulla risposta in transitorio  
Nella maggior parte dei casi stiamo parlando di vincoli sulla risposta al gradino. Per esempio ci può essere durante il transitorio un *errore di inseguimento* come in regime permanente (però, se ho ben capito, questo solo se metto in ingresso una rampa)  
  
![Pasted image 20240207125623.png](./img/Pasted%20image%2020240207125623.png)  
  
oppure, nel caso di sistemi di ordine dal secondo in poi, di una **sovraelongazione massima** $\hat{s}=y_\max-y_\infty$   
![Pasted image 20240207125813.png](./img/Pasted%20image%2020240207125813.png)  
  
Altre specifiche sono sul tempo:  
- **tempo di salita**: $t_R = t_{90\%} − t_{10\%}$ in caso di risposta non oscillante oppure $t_S=\min({t\ |\ y(t_S)=y_\infty})$ (cioè il primo istante in cui tocca il valore di regime) nel caso di risposta oscillante  
- **tempo di assestamento** (settling time): $t_a$ necessario perchè $y(t)$ entri in una fascia che si discosti di un massimo noto da $y_\infty$.  
	  ![Pasted image 20240207130131.png](./img/Pasted%20image%2020240207130131.png)  
### Specifiche sulla risposta in frequenza  
Considerando la $F(s)$ del sistema che si sta progettando, si potrebbero avere specifiche sulla sua **banda passante**, **picco di risonanza** ecc.