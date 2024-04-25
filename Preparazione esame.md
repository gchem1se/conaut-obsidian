---  
share: true  
tags:  
  - specificare  
---  
Loro hanno separato 7 + 5 quindi 12 tipologie (= appelli).  
Se devo fare 12 cose, più qualcosa sui laboratori più qualcosa di riepilogo e vecchi appelli, quindi consideriamo tipo 14 cose in 6 giorni,  
devo fare 14/6 = 2.33 cose al giorno.  
Quindi almeno 2 appelli di Taragna e 2 appelli di Indri al giorno.  
Ce la posso fare, su. Solo che non so un cazzo come si fa la modellistica; farò tutto il resto per ora tralasciando quella.  
Devo prendere 18 alla prima parte e 18 alla seconda, in entrambi i casi, su 32.  
Quindi nella prima tipo 6 / 10 e nella seconda fare bene il controllore (che comunque è soggettivo).  
  
- 15 febbraio  
	- giorno 1  
	- ne mancano 6 incluso oggi  
	- ne mancano 5 da domani  
	- Contenuti  
		- modellistica sistema meccanico in rotazione #specificare  
		- modellistica sistema meccanico in traslazione #specificare  
		- dato un generico SISO LTI TD e dati gli autovalori di A trovare la stabilità interna del sistema (controllare che i moduli di tutti gli autovalori siano minori strettamente di 1)   
		- dato un sistema LTI di matrici date che deriva dalla linearizzazione di un sistema non lineare nell'intorno di un punto di equilibrio, dire se tale punto di equilibrio sia stabile (criterio di Lyapunov)   
		- dato il grafico della risposta di un sistema LTI ad un gradino, scrivere la FdT (scrivi in funzione di guadagno e costante di tempo nel caso di un primo ordine; scrivi in funzione di guadagno, smorzamento e pulsazione naturale in caso di secondo ordine, ricavando lo smorzamento dal coefficiente di sovrelongazione massima e la pulsazione naturale dal tempo di picco)  
		- dato un sistema non lineare, descritto come equazioni, e un ingresso di equilibrio, trovare gli stati di equilibrio. Praticamente all'equilibrio si ha $\dot{x}=0$. Quindi poni questi e funziona.   
		- dato un sistema con FdT nota dire per quali valori di un parametro succede che il sistema sia esternamente stabile => dato che i poli della FdT sono sottoinsieme degli autovalori di A, tanto vale capire se è asintoticamente stabile => usare i criteri di stabilità di Routh o Jury visto che non abbiamo gli autovalori in bella vista  
		- data una funzione di trasferimento e un ingresso determinare l'espressione analitica dell'uscita (trasformi l'ingresso, moltiplichi per FdT e antitrasformi tutto, con Laplace) - la parte problematica è la scomposizione in fratti semplici. In TC, tieni anche $s=0$ invece in TD se è moltiplicato per $z$ prima toglila dividendola e poi metti il ritardo dopo in quello che ti esce. Ricordati le formule della scomposizione e le tavole di Laplace e Zeta da stampare...  
		- data FdT , trova $y_\infty$ cioè risposta in regime permanente => questa intanto esiste solo se la FdT è internamente asintoticamente stabile => dopo verificato questo le formule per la risposta permanente sono:  
			- se l'ingresso è costante $u(t)=\overline{u}\epsilon(t)$  
				- $y_\infty=H(0)\overline{u}\epsilon(t)$  
			- se l'ingresso è sinusoidale $A\sin(\omega_0t+\theta)$  
				- $y_\infty=A·H(j\omega_0)·\sin(\omega_0t+\angle(H(j\omega_0)))·\epsilon(t)$  
			- altrimenti in teoria dovresti poter usare il teorema del valore finale  
				- $\lim_{t\to\infty}y(t)=\lim_{s\to0}sY(s)$  
		- trova il $K$ della retroazione degli stati per pilotare gli autovalori di un sistema a matrici $A,B$ date in valori dati anch'essi (la legge di controllo) - si fa, ma con tanti tanti calcoli.  
			- in pratica prima controlli che sia completamente raggiungibile (che sia in forma canonica di raggiungibilità oppure che il rango di $M_r$ sia uguale alla dimensione del sistema $n$) - poi devi fare il polinomio caratteristico di $A-BK$ ed eguagliarlo al polinomio caratteristico desiderato (cioè quello che ha come radici gli autovalori che ti da). Senza calcolatrice sei morto, basically, ma anche con non scherza mica. Il rango non lo calcoli davvero ti basta sapere che se la matrice è quadrata allora il suo rango è uguale a $n$ solo se non è singolare (det!=0)  
		- trovare $L$ del ricostruttore asintotico per un sistema con matrici $A,C$ date  
			- prima verifichi sia completamente osservabile, poi imponi gli autovalori di $A-LC$ come facevi con la legge di controllo.  
		- modellistica di sistema termico #specificare   
- 16 febbraio   
	- giorno 2  
	- ne mancano 5 incluso oggi  
	- ne mancano 4 da domani  
	- Contenuti  
		- Classificazione di un sistema dalle sue equazioni  
			- ![Pasted image 20240216185742.png](./img/Pasted%20image%2020240216185742.png)  
		- Dato un sistema TD dalle sue equazioni ricavare $G(z)$ (facile perchè trasformata Zeta sfrutta bene le equazioni alle differenze)  
		- Linearizzazione di un sistema dato per equazioni attorno ad un punto di equilibrio, chiede le matrici.  
			- sembra che sia solamente questione di fare le Jacobiane.  
		- Studiare la stabilità interna di un sistema LTI date le matrici da cui è facile trovare gli autovalori => fai praticamente analisi modale. Se c'è uno che diverge, è instabile.  
		- ![Pasted image 20240216200517.png](./img/Pasted%20image%2020240216200517.png)  
			- essendo di grado 2 usa le disequazioni non serve Jury, e poi cartesio per l'ultima, così eviti jury anche qui  
		- Assolutamente non ho capito perchè, ma un esercizio di questo tipo ![Pasted image 20240216201820.png](./img/Pasted%20image%2020240216201820.png) ha quella soluzione perchè essendo sia controllabile che osservabile deve avere poli fino al quinto ordine, ed essendo $D\ne0$ anche il numeratore ha grado 5, altrimenti aveva grado 4.  
		- ![Pasted image 20240216204937.png](./img/Pasted%20image%2020240216204937.png)  
			- Va calcolata G(s), posto che sia esternamente stabile per sapere qualcosa in più su $K$ se vuoi, e poi usi teorema del valore finale per trovare $y_\infty$ in funzione di $K$, e li provi tutti.  
				- A me sembra strano che serva imporre la stabilità esterna, ma magari tra le opzioni c'era pure "il sistema non ha risposta permanente" o qualcosa di simile, booh.  
- 17 febbraio  
	- giorno 3  
	- ne mancano 4 incluso oggi  
	- ne mancano 3 da domani  
	- Contenuti  
		- Oggi faccio solo e soltanto MATLAB e solo la parte dei temi d'esame di Indri (perchè diciamocelo chiaro, a che cazzo mi serve fare RESIDUE se devo progettare un controllore? Penso proprio a nulla.)  
		-   
- 18 febbraio  
	- giorno 4  
	- ne mancano 3 incluso oggi  
	- ne mancano 2 da domani  
- 19 febbraio  
	- giorno 5  
	- ne mancano 2 incluso oggi  
	- ne mancano 1 da domani  
- 20 febbraio  
	- giorno 6  
	- ne mancano 1 incluso oggi  
	- l'esame è domani alle 08:30  
- 21 febbraio  
	- esame alle 08:30  
  
## Prima parte  
### Esercizi del sito  
![Pasted image 20240215193133.png](./img/Pasted%20image%2020240215193133.png)  
### Tipologie come le hanno separate loro  
#### 1  
#### 2  
#### 3  
#### 4  
#### 5  
#### 6  
#### 7  
### Vecchi appelli presi da TG  
## Seconda parte  
### Esercizi del sito  
![Pasted image 20240215193148.png](./img/Pasted%20image%2020240215193148.png)  
### Tipologie come le hanno separate loro  
#### 1  
  
#### 2  
#### 3  
#### 4  
#### 5  
### Vecchi appelli presi da TG