---
{"dg-publish":true,"permalink":"/taragna/tar-19-osservabilita-e-rilevabilita/"}
---

Le proprietà di osservabilità e di rilevabilità descrivono la possibilità di *stimare lo stato del sistema tramite l’uscita e l’ingresso*. 
La differenza delle proprietà di raggiungibilità e controllabilità sta nel fatto che queste ultime si preoccupavano di modificare lo stato del sistema tramite particolari ingressi.
## Osservabilità
Possibilità di **stimare lo stato iniziale** dati uscita e ingresso.
- Stato **non osservabile**: uno stato $x^\star\ne0$ è non osservabile se per qualunque $t^\star$ la componente libera dell'uscita conseguente allo stato iniziale $x(t_0)=x^\star$ risulti nulla per ogni $t>t_0$ - cioè, mi sembra di capire, se un sistema è immediato nella risposta, quindi non deve settlarsi la risposta libera e poi avere la propria risposta forzata, se ha direttamente la forzata, non è possibile capire da che stato fosse partito (perchè in effetti la sua uscita non dipende mai dallo stato ma solo dall'entrata così)
	- Un sistema può avere degli stati non osservabili e averne altri osservabili (per esempio un sistema che ha risposta immediata se l'ingresso è un certo ingresso ma invece deve settlarsi la risposta libera su altri ingressi) -> in quel caso c'è un *sottospazio di non osservabilità* - corrispondente all'*insieme di non osservabilità a dimensione minima* cioè praticamente siccome come nel caso della raggiungibilità, gli insiemi dipendono dal tempo, ma qui è in negativo, devo prendere $X_{\text{NO}}(t)$ con il $t$ che porta ad avere l'insieme più piccolo di non osservabilità.
- Se il **sottospazio di osservabilità** *che è il complementare di quello di non osservabilità* coincide con tutto lo spazio dello stato $X$ allora il sistema è **completamente osservabile.
## Rilevabilità
Possibilità di **stimare lo stato finale** del sistema mediante la misura dell’uscita e dell’ingresso.
- Stato **non rilevabile**: uno stato $x^\star$ è non rilevabile se per qualunque $t^\star$ la componente libera dell'uscita che ha come stato finale $x(t^\star)=x^\star$ risulti nulla. Anche in questo caso, quindi, stiamo parlando di un'uscita libera nulla, e quindi di una risposta immediata del sistema che non mi permette di stimare lo stato, sebbene quello stato avesse le caratteristiche in regola per essere uno di quelli che volevo.
- Se il **sottospazio di rilevabilità** *che è il complementare di quello di non rilevabilità, che è l'insieme di non rilevabilità nell'istante in cui esso ha dimensione minima* coincide con tutto lo spazio dello stato $X$ allora il sistema è **completamente rivelabile**.

## Sistemi LTI
Guarda un po', anche qui, **se un sistema LTI è completamente osservabile, è anche completamente rilevabile**.

> Non ho capito st'immagine.
	![Pasted image 20240206232914.png](/img/user/img/Pasted%20image%2020240206232914.png)

Anche qui come nel caso della raggiungibilità, nel caso in cui il sistema non sia completamente osservabile, allora si hanno alcuni autovalori relativi alla parte osservabile e alcuni relativi alla parte non osservabile.
### Sistemi LTI SISO - analisi della osservabilità
La dimensione del sottospazio di osservabilità del sistema LTI SISO è uguale al rango di $M_O=[C\ CA\ \dots\ CA^{n-c}]^T$ con $c$ il rango di $C$.
## Realizzazione di una funzione di trasferimento secondo la forma canonica di osservabilità
![Pasted image 20240206233429.png](/img/user/img/Pasted%20image%2020240206233429.png)

## Principio di dualità
![Pasted image 20240206233600.png](/img/user/img/Pasted%20image%2020240206233600.png)