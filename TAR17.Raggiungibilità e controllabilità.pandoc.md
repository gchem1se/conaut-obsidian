---  
dg-publish: true  
share: true  
---  
Proprietà strutturali {#proprietà-strutturali heading="Proprietà strutturali"}  
---------------------  
  
Stabilità, raggiungibilità e controllabilità sono **proprietà  
strutturali**, il che significa che un sistema *simile* ad un sistema in  
esame avente una di queste proprietà la ha anch\'esso.  
  
Dire che due sistemi sono *simili* vuol dire che posso trasformare la  
matrice di stato []{.math .math-inline .is-loaded} del primo sistema in  
quella del secondo una trasformazione di similarità (un cambio di base).  
  
In pratica, questo significa che le proprietà strutturali sono proprietà  
del sistema che dipendono unicamente *dagli autovalori* della matrice  
[]{.math .math-inline .is-loaded}.  
  
Raggiungibilità {#raggiungibilità heading="Raggiungibilità"}  
---------------  
  
Uno stato []{.math .math-inline .is-loaded} è detto *raggiungibile dallo  
stato []{.math .math-inline .is-loaded} al tempo []{.math .math-inline  
.is-loaded}* se con un particolare ingresso []{.math .math-inline  
.is-loaded} riesco ad ottenere []{.math .math-inline .is-loaded}.  
  
![Pasted image  
20240206190616.png](/home/gchemise/cache_uni/obs_conaut_publish/Pasted%20image%2020240206190616.png){.internal-embed}  
  
Esiste quindi un *insieme di raggiungibilità []{.math .math-inline  
.is-loaded}* che mi racchiude tutti gli stati raggiungibili partendo  
dallo stato []{.math .math-inline .is-loaded} in un tempo finito (in  
particolare, []{.math .math-inline .is-loaded}).\  
Il *sottospazio di raggiungibilità* in particolare è l\'insieme di  
raggiungibilità di cardinalità più grande (quindi c\'è un tempo  
particolare al quale si manifesta l\'insieme di dimensione massima).\  
Se il sottospazio di raggiungibilità è diverso dall\'intero spazio dello  
stato (l\'insieme dei possibili valori di []{.math .math-inline  
.is-loaded}) ci sarà anche un insieme di non raggiungibilità: tali stati  
non sono raggiungibili in tempo finito dal sistema, per nessun ingresso.  
  
Controllabilità {#controllabilità heading="Controllabilità"}  
---------------  
  
Uno stato []{.math .math-inline .is-loaded} si dice *controllabile allo  
stato []{.math .math-inline .is-loaded} al tempo []{.math .math-inline  
.is-loaded}* se con un particolare ingresso []{.math .math-inline  
.is-loaded} riesco ad ottenere []{.math .math-inline .is-loaded}.  
  
![Pasted image  
20240206191203.png](/home/gchemise/cache_uni/obs_conaut_publish/Pasted%20image%2020240206191203.png){.internal-embed}  
  
Sistemi LTI {#sistemi-lti heading="Sistemi LTI"}  
-----------  
  
Per sistemi LTI, []{.math .math-inline .is-loaded}, perlomeno a tempo  
continuo.\  
In sistemi a tempo discreto []{.math .math-inline .is-loaded} potrebbe  
essere un po\' più piccolo: se []{.math .math-inline .is-loaded} non è  
singolare, però, si ricade nel caso precedente.  
  
**Un sistema LTI completamente raggiungibile allora è anche  
completamente controllabile**. Noi faremo riferimento alle proprietà di  
raggiungibilità.  
  
Gli autovalori della matrice di stato []{.math .math-inline .is-loaded}  
determinano completamente l\'andamento della risposta (libera) del  
sistema. È per questo che facciamo l\'analisi modale: già analizzando  
gli autovalori di []{.math .math-inline .is-loaded} si possono ottenere  
tante informazioni sul sistema, in particolare, informazioni sulla sua  
stabilità.  
  
Gli autovalori di []{.math .math-inline .is-loaded} sono da  
classificarsi in base alla raggiungibilità del sistema.\  
In un sistema LTI **non completamente raggiungibile** succede che  
*alcuni autovalori della matrice []{.math .math-inline .is-loaded} sono  
\"da associare\" al sottospazio di raggiungibilità e alcuni al  
sottospazio di non raggiungibilità*. Per ora non è troppo chiaro, ma lo  
sarà vedendo la legge di controllo per la retroazione statica dello  
stato. TAR18.Retroazione statica dello stato \> Assegnazione degli  
autovalori o legge di controllo  
  
### Sistemi LTI SISO - analisi della raggiungibilità {#sistemi-lti-siso---analisi-della-raggiungibilità heading="Sistemi LTI SISO - analisi della raggiungibilità"}  
  
L'analisi sulla raggiungibilità di un sistema a singolo ingresso può  
essere fatta a partire dalle matrici di stato e degli ingressi. A  
partire da queste, si può costruire la *matrice di raggiungibilità* del  
sistema e fare un test su questa per determinare se il sistema sia  
completamente raggiungibile o meno.  
  
Nel caso di un sistema con un *singolo ingresso*, la matrice di  
raggiungibilità ha la forma:\  
[]{.math .math-block .is-loaded}dove []{.math .math-inline .is-loaded} è  
la []{.math .math-inline .is-loaded} della []{.math .math-inline  
.is-loaded} a cui appartiene []{.math .math-inline .is-loaded}, ovver la  
*dimensione del sistema*, cioè il numero di equazioni di stato /  
variabili di stato.\  
Quando questa matrice ha *rango pari ad []{.math .math-inline  
.is-loaded}*, il sistema è completamente raggiungibile.  
  
::: {.callout callout-metadata="" callout-fold="" callout="info"}  
::: {.callout-title}  
::: {.callout-icon}  
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAYAAABXAvmHAAAAAXNSR0IArs4c6QAAAxlJREFUaEPVmkvITkEYx3+fpVwXJGX1ReQWO8WSPityyXVBCkVsiKUlfTZEIWLhmkusiCVlR24RWSmJhWuW6K85b+PpnPfMmTOnzCzfb55nnt/Mc5s53wCZj4HM7ScVwEhgMbAAmAsMApOAUW6DfgAfgLfAE+AhcA/42XYD2wIsAzYCK6HxZvwGrgPngVuxILEA64E9wLzYhY3cY+AwcLGpvqYAs4BhYKjpQoHz7wB7geeB8xsd+1bgRB9XeQXcdf79AngHfHWGjAWmADNdnCwBplcYKdfaDpwKgQg9gYPAvgqF54AzwIOQBb05C4EtwKYKuUPA/jqdIQDHgB0lim4AB4BndYvU/H2207OiZN5xYGc/+TqAqp3XEZ9sabgV3+Zc1P7e9yT6AcjnrZHvgTUR7hLKKre6Akw2AoIrjYkqAGWbpyZgZbyyT1uXqYORSykb+RAK7Dll2akK4HZJqlzU4c5bKJ3EffOjoJbaiWUAKlIXzMQufL7uJMpiYoMtdmUAj0yFVbZRq9B0bAYUgCNcOjzdVIFrNfzspIo939djAdTb3DQLyfdi/P4jMMHp+gKMjwBQPCgW/bHc750swFVglTdbRUo7GTNSAGjds6bYXQNWFwb5AGqJ1fb6v7UJ3BQuJDttQCsjqU3/24r7xlr3UW8zI2brO5B5aXqnnhv5ALbqHgV2d2BMjMojwC5PsFedfQCb+9cBl2NW60BmLXDJ09urCT7Aa2CqNyk2+3RgPzYbvQGm2Rj4Boz2VlfaU/qLHUUQS16tuLJJ7BgHfPaEvwNjLMAvE9QqQIr42OGn0U/AxFhFzi7ZVwzZJfv+yUKpASx8Xevej0+ytQCpXSglQJALpQ7ilABBQZw6jaYECEqjqQtZSoCgQpa6lUgJENRKpG7mUgEEN3NKYynb6VQAwe20ALq60MQWssYXGkGkvlK2aSX0et3oSqnFsr/UCyLrZxUBZP+wJYisnxaLzjDrx90CIuvn9bqT0N//+w8cBUTWn5gKiKw/8vlXvmw/s9p7a7Yfui1Itv9q0OKlJI1om6eONBa01PIHFkPgMVZmjRcAAAAASUVORK5CYII=){width="24"  
height="24"}  
:::  
  
::: {.callout-title-inner}  
Info  
:::  
:::  
  
::: {.callout-content}  
**Rango e come non calcolarlo**\  
Il rango di una matrice è il numero di righe (o colonne) linearmente  
indipendenti.  
  
In pratica, significa che prendendo le righe (colonne) della matrice e  
trattandole come vettori separati, usandoli come una base, si può creare  
uno spazio vettoriale (combinando linearmente questi vettori) di  
dimensione pari al rango.\  
Rimuovendo dalla base un vettore non linearmente indipendente (quindi  
che si può creare come combinazione lineare degli altri), lo spazio  
vettoriale generato non cambia, in quanto quel vettore che ora è stato  
rimosse non è mai davvero stato necessario alla generazione.  
  
Il rango di una matrice si può vedere \"ad occhio\" nel momento in cui è  
palese il rapporto che esiste tra le righe. Per esempio, in []{.math  
.math-block .is-loaded}Il rango è []{.math .math-inline .is-loaded}, in  
quanto la prima e la terza colonna sono evidentemente linearmente  
indipendenti, mentre la colonna centrale è ricavabile moltiplicando la  
prima per []{.math .math-inline .is-loaded}.\  
A volte però non è ben visibile questo rapporto, per cui il metodo più  
comune per il calcolo del rango prevede la riduzione della matrice  
(mediante mosse di Gauss).  
  
Nel nostro caso, non è nemmeno necessario calcolare esplicitamente il  
rango.\  
L\'unica informazione di cui abbiamo bisogno è sapere se questa matrice  
[]{.math .math-inline .is-loaded} abbia rango []{.math .math-inline  
.is-loaded} oppure no.\  
Dato che la matrice []{.math .math-inline .is-loaded} ha di per sè  
[]{.math .math-inline .is-loaded} righe, perchè si abbia rango []{.math  
.math-inline .is-loaded} è necessario che si abbia rango massimo (che  
quindi tutte le sue righe / colonne siano linearmente indipendenti).\  
Una conseguenza della presenza di righe o colonne non linearmente  
indipendenti è che il determinante della matrice va a []{.math  
.math-inline .is-loaded}. Quindi a noi basterà semplicemente verificare  
che la matrice non sia singolare.  
:::  
:::  
  
Nel caso invece di un sistema con più di un ingresso, la matrice di  
raggiungibilità si costruisce come []{.math .math-block .is-loaded}dove  
[]{.math .math-inline .is-loaded} è il rango di []{.math .math-inline  
.is-loaded} (che generalmente è più semplice calcolare, ma non si sa mai  
davvero). In effetti, il caso con un solo ingresso ha []{.math  
.math-inline .is-loaded}.  
  
::: {.callout callout-metadata="" callout-fold="" callout="matlab"}  
::: {.callout-title}  
::: {.callout-icon}  
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAYAAABXAvmHAAAAAXNSR0IArs4c6QAAAaFJREFUaEPtmj1OBDEMhb+lgJoCLkBNBXeh5hD8XAG4AhI1d4GKmgtAQ7s0IK82UhQxY2eNN4o2aR0nfvZ7SUaeBZ2PRefxYwVwBVwAp8B+MOhv4A14Bh60vTQAJ+uFzrSFguyv68S9T62vAXgBWgWfYhYQ55sAENrcB2W2dtnrKTrNVaDM/hNwA3zW7l45/wi4Ay4zv8kqzAFYFoI93kLwKWYB8ZEBEGEf/JWIOQA/hYOml8pEq9NN++80AOGocFXK7RmiKdGWaCwf4RUQjnqDTwELCNHYAFCTge4p5OG9xTdcA5YgPHMGAFMGPClWfE37ey6yJOI94BZ4LALy2sMB5PfAF3BYAPDaBwAtA16KaP7a/quCezQQqN/V0gOAKQOBZTDtv9MU0kRotUsRm38PeO+B5t8DmwDQOK7Z3ceolSJTTw0tQM3uBuA9gLQANfsAMCpQZKC8k8Ip1L2Io9/74RXwAsj9m1xkXgol/2ZPCe8ppPmHU0gLwGt3A+i+wdF9i6n7Jp9wuOs2qwDovtGdTpJufzXwHoXh/ttunf47oF/K77oxiwFYAgAAAABJRU5ErkJggg==){width="24"  
height="24"}  
:::  
  
::: {.callout-title-inner}  
Matlab  
:::  
:::  
  
::: {.callout-content}  
![Pasted image  
20240206191842.png](/home/gchemise/cache_uni/obs_conaut_publish/Pasted%20image%2020240206191842.png){.internal-embed}  
  
![Pasted image  
20240206191849.png](/home/gchemise/cache_uni/obs_conaut_publish/Pasted%20image%2020240206191849.png){.internal-embed}  
  
La matrice di raggiungibilità si può calcolare direttamente con il  
comando `ctrb(A)`.  
:::  
:::  
  
Realizzazione di una funzione di trasferimento secondo la forma canonica di raggiungibilità {#realizzazione-di-una-funzione-di-trasferimento-secondo-la-forma-canonica-di-raggiungibilità heading="Realizzazione di una funzione di trasferimento secondo la forma canonica di raggiungibilità"}  
-------------------------------------------------------------------------------------------  
  
Sostanzialmente la domanda è:  
  
-   se ho una funzione di trasferimento []{.math .math-inline  
    .is-loaded} o []{.math .math-inline .is-loaded}, posso costruire un  
    sistema che la implementa?\  
    Sì, lo puoi fare ma ne esistono infiniti. Noi facciamo che scriverne  
    uno solo, quello *in forma canonica di raggiungibilità*, che tra  
    l\'altro sarà *per definizione completamente raggiungibile*.\  
    Praticamente si costruisce \"per ispezione\" nel senso che guardi la  
    funzione di trasferimento e scrivi.  
  
Il procedimento è questo - abbastanza stupido:  
  
![Pasted image  
20240206194208.png](/home/gchemise/cache_uni/obs_conaut_publish/Pasted%20image%2020240206194208.png){.internal-embed}  
