---  
share: true  
---  
  
## Definizione di sistema  
Definizione informale: interconnessione di parti per cui vale il principio di azione e reazione (ogni parte agisce su un'altra, che reagisce all'azione della prima). Si denota con $u(\text{...})$ l'ingresso del sistema (azione, causa) e con $y(\text{...})$ l'uscita (la reazione) del sistema (più propriamente, le reazioni / variabili di uscita *di interesse* del sistema, non per forza tutte le reazioni sono di interesse per l'osservatore). Il sistema è una *black box* descritta da un sistema $S$ di equazioni del tipo $y(\text{...}) = u(\text{...})$ (detto *modello matematico*).  
Noi tratteremo nel corso:  
- Sistemi elettrici  
- Meccanici  
- Elettromeccanici  
- Termici  
## Problematiche di interesse nello studio dei sistemi  
- **Previsione** delle uscite dati $u(\text{...})$ e $S$ - spesso tramite un sistema di calcolo es. MATLAB - a mano solo se sono semplici.   
- **Controllo**: dati $S$ e una serie di reazioni *desiderate* $y_{\text{des}}(\text{...})$, trovare quali dovrebbero essere gli $u(\text{...})$ che il sistema di controllo dovrà fornire.  
- **Identificazione** (che cagheremo di meno nel corso): noti $u(\text{...})$ e $y(\text{...})$, determinare $S$ (praticamente reverse engineering della black box).  
## Classificazione dei sistemi  
- Sistema **statico**  
	Il legame tra ingresso e uscita è *statico, algebrico, istantaneo* - il valore dell'uscita dipende esattamente dal valore degli ingressi.   
	$$y(t) = g(u(t))$$  
	Nessun sistema reale si comporta così, ma è un'approssimazione (es. resistore ideale che si comporta secondo la legge di Ohm, che è un modello matematico semplificato del sistema resistore reale - ad alte frequenze, i resistori reali presentano effetti induttivi).  
  
- Sistema **dinamico** (oggetto del controllo automatico)  
	Il legame tra ingresso e uscita non dipende solo dall'ingresso nello stesso istante, ma anche dalla storia precedente del sistema (dallo **stato**).   
	$$y(t) = g(u(]-\infty, t]))$$  
	Es. condensatore reale.  
	Per riassumere la storia passata del sistema si introduce una variabile (detta *di stato*) che condensa la *memoria* del passato:  
	$$y(t) = g(x(\tau), u(]\tau, t])),\ \ \ \ \ \ \forall \ t > \tau$$  
	Nel caso del condensatore reale, il modello prevede:  
	- ingresso:  
		- $$u(t)=i_C(t)=C\frac{dV(t)}{dt}$$  
	- uscita:  
		- $$y(t)=v_C(t)=\frac{1}{C}\int_{-\infty}^t i_C(\sigma)d\sigma$$  
	- variabile di stato:  
		- $$x(\tau)=v_C(\tau)=\frac{1}{C}\int_{-\infty}^\tau i_C(\sigma)d\sigma$$  
		- da cui:  
			- $$y(t)=\frac{1}{C}\int_{-\infty}^t i_C(\sigma)d\sigma=$$  
			- $$=\frac{1}{C}\int_{-\infty}^\tau i_C(\sigma)d\sigma+\frac{1}{C}\int_\tau^t i_C(\sigma)d\sigma=$$  
			- $$=x(\tau)+\frac{1}{C}\int_{-\tau}^t i_C(\sigma)d\sigma$$  
	Ma perchè la variabile di stato è proprio quella? Perchè la variabile di stato è quella che diventa una condizione al contorno per la risoluzione della equazione differenziale, la quale condizione è sempre imposta sulla variabile che viene derivata. Infatti nel caso dell'induttore la variabile di stato è la corrente che vi ci passa.  
## Definizione assiomatica di un sistema   
Il sistema dinamico è un ente definito da 6 insiemi:   
$$S(T,U,\Omega,X,Y,\Gamma,\phi,\eta)$$  
- $T$: insieme ordinato dei tempi  
- $U$: insieme dei valori assumibili dall'ingresso $u$  
- $\Omega$: insieme delle funzioni di ingresso $\{u(\text{...}): T \rightarrow U\}$ (insieme dei modi in cui variano)  
- $X$: insieme dei valori assumibili dalla variabile di stato $x$  
- $Y$: insieme dei valori assumibili dalla variabile di uscita $y$  
- $\Gamma$: insieme delle funzioni di uscita $\{y(\text{...}): T \rightarrow Y\}$  
Le due ulteriori funzioni sono particolari:   
- $\phi$: funzione di transizione dello stato - descrive l'evoluzione temporale dello stato (detta anche *movimento dello stato*) - $x(t) = \phi(t,\tau,x(\tau),u(\text{...}))$, con $t$ istante finale, $\tau$ istante iniziale, $x(\tau)$ valore iniziale dello stato del sistema, $u(\text{...})$ funzione di ingresso definita su $[\tau, t]$. Questa funzione soddisfa le proprietà di *consistenza*, *irreversibilità*, *composizione*, *causalità* (il sistema dipende da ciò che è successo, non da ciò che succederà. $\tau <= t$). Questa non è mai una funzione di tipo istantaneo (c'è un integrale tra due istanti di tempo).  
- $\eta$: funzione di uscita (anche detta *movimento dell'uscita*). Lega tra loro l'uscita, la variabile di stato e la variabile di ingresso - $y(t) = \eta(t,x(t),u(t))$. Questo legame è *istantaneo*, tuttavia dipende sia da $x(t)$ e da $u(t)$, e questo sistema questo viene considerato *improprio*, perchè significherebbe che l'ingresso si riverberebbe in maniera istantanea sull'uscita, cosa che solitamente non succede nei sistemi reali. Spesso quindi si considera una $\eta(t, x(t))$, ovvero non dipendente dall'ingresso. In alternativa si può usare il modello improprio, ma solo se si decide di ignorare il tempo di riverbero degli ingressi sulle uscite.  
  La variabile di stato **può coincidere con la variabile di uscita di interesse per l'osservatore**.  
    
Avendo questi parametri si può descrivere il sistema tramite **rappresentazione di ingresso, stato, uscita**.  
  
Se $T$ è un insieme che ha la cardinalità del continuo, allora il sistema è detto *dinamico a tempo continuo* - analogico. Se ha la cardinalità del discreto si parla di un sistema *dinamico a tempo discreto* - digitale. Spesso si usa la lettera *k* per denotare un tempo discreto.  
  
Se $U$ e $Y$ hanno cardinalità del discreto, il sistema è detto *dinamico a ingressi e uscite quantizzate*. Se il sistema ha un'ingresso e un'uscita è detto sistema **SISO**. Altrimenti, **MIMO**.  
  
Se l'insieme $X$ è discreto, allora il sistema è detto *a stati finiti*. Se invece è continuo e contenuto in $R^n$ con $n$ finito, allora il sistema è *a dimensione finita* o *a parametri concentrati* (oggetto del corso). Le equazioni che lo modellano sono differenziali alle derivate ordinarie. Se l'insieme $X$ dei valori dello stato è invece contenuto in $R^n$ con $n$ infinito, allora il sistema è *a dimensione infinita* o *a parametri distribuiti*. Le equazioni che lo modellano sono differenziali alle derivate parziali.   
  
Il sistema è detto *lineare* se tutti gli insiemi che lo definiscono sono spazi vettoriali e $\phi$ e $\eta$ sono lineari nelle loro variabili $x$ e $u$. Altrimenti è *non lineare*.  
> Anche sistemi non lineari possono essere ricondotti a lineari "in intorni di certi punti di funzionamento specifico" per semplificarsi la vita (es. polarizzazione di un transistor in un range di funzionamento, oppure studio di piccolo segnale)  
  
Il sistema è detto *stazionario* o *tempo-invariante* se le funzioni $\phi$ e $\eta$ non dipendono **esplicitamente** dal tempo. Altimenti è detto *non stazionario*, o *tempo-variante*.  
- $y(t)=x(t)$ ha una dipendenza implicita.  
- $y(t)=tx(t)$ ha una dipendenza esplicita.  
### Sistema dinamico a tempo continuo   
Valgono:  
- $x'(t)=\frac{dx(t)}{dt}=f(t,x(t),u(t))$ -> $x$ è soluzione di 1 o eventualmente *n* equazioni differenziali del primo ordine  
- $y(t)=g(t, x(t), u(t))$  
Nel caso del sistema **lineare**, però, le due equazioni si semplificano e si scompongono:  
- $x'(t)=\frac{dx(t)}{dt}=f(t,x(t),u(t))=A(t)x(t)+B(t)u(t)$  
- $y(t)=g(t, x(t), u(t))=C(t)x(t)+D(t)y(t)$  
Se parliamo di sistemi con più variabili di stato, più ingressi, più uscite, allora $x$ e $u$ sono vettori e $A, B, C, D$ sono matrici. In particolare, quindi:  
- $A$ ha dimensione $n\times n$, detta *matrice di stato*  
- $B$ ha dimensione $n\times p$, con $p$ numero di ingressi, detta *matrice degli ingressi*  
- $C$ ha dimensione $q\times n$, con $q$ numero di uscite, detta *matrice delle uscite*  
- $D$ ha dimensione $q\times p$, detta *matrice del legame diretto ingresso-uscita*  
In caso di sistemi tempo-invarianti sparisce la dipendenza da $t$ nelle matrici.  
### Sistema dinamico a tempo discreto  
L’evoluzione temporale dello stato è descritta da un sistema di $n$ *equazioni alle differenze* finite.  
- $x[k+1]=f(k, x[k], u[k])$  
- $y[k]=g(k, x[k], u[k])$  
Facendo le stesse semplificazioni di prima:  
- Lineare:  
	- $x(k+1)=f(k, x(k), u(k))=A(k)x(k)+B(k)u(k)$  
	- $y(k)=g(k, x(k), u(k))=C(k)x(k)+D(k)u(k)$  
- Lineare, tempo-invariante: sparisce la dipendenza da $k$.  
### Riassunto: classificazione sistema  
| classificazione                                                                  | si vede da                                                                     |  
| -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |  
| statico/dinamico                                                                 | statico se $y$ dipende solo da $u$ (non esiste dipendenza tra uscita e stato)  |  
| tempo discreto/continuo                                                          | discreto se ci sono equazioni alle differenze, altrimenti ci sono eq. diff.    |  
| SISO/MIMO                                                                        | se ingressi=uscite=1, allora SISO; else: MIMO                                  |  
| dimensione del sistema                                                           | = numero equazioni di stato, se $n$ finito -> sistema a dimensione finita      |  
| lineare/non lineare                                                              | lineare se **tutte** le equazioni sono combinazioni lineari di $x$ e $u$       |  
| tempo invariante/tempo variante                                                  | tempo invariante se **nessuna** equazione dipende dal tempo **esplicitamente** |  
| proprio/improprio (anche: fisicamente realizzabile/non fisicamente realizzabile) | proprio se $y$ non dipende esplicitamente (e quindi istantaneamente) da $u$.   |  
**Esercizio su quaderno pag 3**  
  
  
