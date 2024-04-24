---
{"dg-publish":true,"permalink":"/taragna/tar-20-stima-dello-stato-e-regolatore-dinamico/"}
---

## Stimatore dinamico
Molto spesso non hai accesso allo stato del sistema. Perchè magari è troppo complesso, anche se in sè il sistema è completamente raggiungibile. Allora devi *stimarlo*. 
Lo stato di un sistema si può stimare tramite un ulteriore sistema dinamico che si chiama **stimatore dinamico**.

![Pasted image 20240206234328.png](/img/user/img/Pasted%20image%2020240206234328.png)

Questo ovviamente nello *stimare* compirà degli errori; l'errore di stima è $\hat{x}(t)-x(t)=e(t)$ ma esso potrebbe annullarsi per $t\to\infty$, caso in cui si dice che lo stimatore è *uno stimatore asintotico dello stato*. Ciò è estremamente conveniente perchè vuol dire che a regime lo stimatore sarà perfetto nel ritrovare lo stato del sistema.

Tuttavia anche l'errore di stima non possiamo saperlo, ma sappiamo tramite ***magheggi folli*** che esso è pari a:
$$e(t) = e^{[(A − LC)t]}e(0)$$
per cui *se tutti i modi di $A-LC$ convergono asintoticamente a $0$*, allora *anche l'errore di stima tenderà a $0$*. Quindi il punto è trovare $L$ (che è un vettore di dimensione $n$) tale per cui **la matrice $A-LC$ abbia autovalori asintoticamente stabili.** 
Questo succede **se il sistema è completamente osservabile**: se sì, allora è possibile trovare una $L$ tale che se uso lo stimatore in un sistema reazionato per assegnare gli autovalori che dico io esso funziona piiiicisu piiiicisu.
## Regolatore dinamico
Il regolatore dinamico è la somma di stimatore asintotico dello stato e legge di controllo.

La struttura di controllo completa è così:

![Pasted image 20240206235548.png](/img/user/img/Pasted%20image%2020240206235548.png)

Per avere entrambe le componenti funzionanti (uno stimatore asintotico che davvero stimi bene lo stato e la retroazione, cioè la legge di controllo, che davvero modifichi tutti gli autovalori) il sistema deve essere:
- **completamente osservabile** per lo stimatore asintotico (per il progetto di $L$)
- **completamente raggiungibile** per la legge di controllo (per il progetto di $K$)

Alla fine, il sistema completo avrà equazioni:

![Pasted image 20240206235957.png](/img/user/img/Pasted%20image%2020240206235957.png)

> Per il progetto di $L$ serve che siano asintoticamente stabili i modi della matrice $A-LC$ e per ottenere ciò a quanto pare servono troppe cervella. Quindi generalmente negli esercizi mi sa che ci danno direttamente quali devono essere gli autovalori del sistema interno dello stimatore dinamico dello stato; noi semplicemente eseguiamo gli ordini.
> ![Pasted image 20240207000340.png](/img/user/img/Pasted%20image%2020240207000340.png)

