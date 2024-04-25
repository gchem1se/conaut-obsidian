---  
dg-publish: true  
share: true  
tags:  
  - continuare  
---  
## Criterio di Nyquist  
Ora come ora la struttura completa del sistema controllato è questa:  
  
![Pasted image 20240207175903.png](./img/Pasted%20image%2020240207175903.png)  
  
Per cui la FdT è:  
- *a catena aperta / ad anello aperto*: $G_a(s)=C(s)F(s)$  
- *a catena chiusa / ad anello chiuso*: $W(s)=y(s)/r(s)$  
  
La **stabilità del sistema** la abbiamo fino ad ora identificata tramite il *criterio di Routh* in TC e il *criterio di Jury* in TD.   
Cioè, il senso era, dato che per essere asintoticamente stabile un sistema deve avere tutti i modi propri associati alla matrice $A$ del sistema LTI sono convergenti, ovvero che *tutte le radici del polinomio caratteristico di $A$, quello le cui radici sono gli autovalori, quindi tutti gli autovalori, avessero parte reale strettamente negativa nel caso TC e strettamente minore di 1 nel caso TD*. Invece di andare a trovare gli autovalori esplicitamente, però, cercavamo di carpire solo le informazioni che ci interessavano, appunto i segni delle parti reali o i moduli. Per farlo sfruttavamo questi criteri che ci davano condizioni necessarie e sufficienti affinchè si verificasse quella condizione, senza necessità del calcolo esplicito.  
  
Alternativamente, dato che qui non abbiamo le matrici ma abbiamo le funzioni di trasferimento (e sicuramente si può trovare la funzione di trasferimento partendo dalle matrici, ma partendo dalla funzione di trasferimento ne trovi infinite di matrici che la implementano), andavamo a fare una verifica analitica, ovvero:  
- in TC, controllavamo che *i poli* della $H(z)$ avessero tutti parte reale strettamente negativa  
- in TD, controllavamo che i poli avessero tutti modulo strettamente minore di 1.  
  
**Questo metodo non ha senso però quando siamo in fase di progetto di controllore.**  
Infatti questi metodi ci dicono che il sistema è asintoticamente stabile, ma non ci danno hint sul progetto del controllore (su quale debba essere $C(s)$ affinchè $y(s)/r(s)$ sia asintoticamente stabile nel suo complesso), e inoltre non ci informano in nessun modo sulla **robustezza** di tale stabilità (che succede se la funzione di trasferimento della catena aperta non ha parametri di guadagno e fase fissi ma variabili, perchè magari è stata realizzata fisicamente male oppure perchè era necessario avere guadagno e/o fase variabili? *Resta stabile o no se il controllore lo realizzo di merda?*).  
  
Invece, il **criterio di Nyquist** ci da queste informazioni.  
Il criterio di Nyquist ci dice se la FdT in catena chiusa ($y(s)/r(s)$) è asintoticamente stabile facendo alcune considerazioni sul diagramma di Nyquist della *FdT in catena aperta* $G_a(s)$. In particolare, ci dice che perchè la FdT in catena chiusa sia asintoticamente stabile, ovvero *perchè il numero di poli instabili (parte reale positiva) della FdT in catena chiusa sia $n_{\text{i, c}}=0$* è necessario che *il numero di giri completi compiuti in senso orario - il numero di giri completi compiuti in senso antiorario dal diagramma di Nyquist della $G_a(j\omega)$ attorno a $(-1,0)$ (detto **punto critico di Nyquist**) sia $N=-n_{\text{i, a}}$*, ossia uguale all'opposto del numero di poli instabili della stessa $G_a(j\omega)$.  
In pratica, **i giri in senso antiorario, netti, devono compensare i poli instabili**.  
  
***N.B.: se il diagramma di Nyquist di $G_a(j\omega)$ passa proprio per il punto critico, non puoi applicare il criterio.**  
  
![Pasted image 20240425004449.png](./img/Pasted%20image%2020240425004449.png)  
  
![Pasted image 20240425004534.png](./img/Pasted%20image%2020240425004534.png)  
### Guadagno variabile per la FdT a catena aperta  
Se la FdT della catena aperta ha un guadagno variabile rischia di portare la catena chiusa ad essere stabile solo per alcuni valori di quel guadagno. Infatti il grafico potrebbe, variando di guadagno, crescere e finire ad includere o toccare il punto critico (guadagno = raggio della circonferenza, remember).  
$$G_a(s)=K_cG_{a,f}(s)$$  
dove $K_c$ è una variabile. **Per non dover disegnare duecentotrentamila diagrammi di Nyquist** piuttosto disegnamo *diverse scale* sulle ascisse, in modo quindi che il punto critico abbiamo posizione $\left(-\frac{1}{K_c}, 0\right)$ e si muova liberamente sulle ascisse.  
#### Sistemi con retroazione negativa  
![NyquistGuadagnoApertaVariabile.excalidraw](./img/Excalidraw/NyquistGuadagnoApertaVariabile.svg)  
  
![NyquistCatenaApertaGuadagnoVariabileNegativo.excalidraw](./img/Excalidraw/NyquistCatenaApertaGuadagnoVariabileNegativo.svg)  
  
  
#### Sistemi con retroazione positiva  
**TUTTO AL CONTRARIO**. Cioè il punto critico nel caso di retroazione positiva con guadagno unitario è $(+1,0)$ quindi il resto della trattazione resta uguale.  
## Margini di stabilità  
Formalizziamo la cosa di dire che "il guadagno può stare sta $0$ e $K_{\text{critico}}$ e il sistema resta stabile" ecc.  
Sostanzialmente, definiamo i **margini di stabilità**.  
### Margine di guadagno  
Sia $Ga(j\omega) = Kc G_{a,f}(j\omega)$, $G_{a,f}(j\omega)$ a guadagno stazionario positivo (nel senso se fai limite per $s\to0$ ecc), priva di poli a parte reale positiva (ovvero è **a minima rotazione di fase**), e sia il suo diagramma polare tale da attraversare una sola volta il semiasse reale negativo in un punto alla destra del punto critico.  
  
> Nsomma così:  
> ![marginediguadagnofacile.excalidraw](./img/Excalidraw/marginediguadagnofacile.svg)  
  
Allora magari è stabile finchè il guadagno non cresce troppo  
  
![Pasted image 20240425004550.png](./img/Pasted%20image%2020240425004550.png)  
  
e si definisce $m_G$ il modulo del reciproco dell'ascissa dell'intersezione tra il diagramma di Nyquist e l'asse reale negativo.  
Si può anche leggere *dai diagrammi di Bode* (ma in Decibel) come $-$ il modulo che la FdT a catena aperta $G_a(j\omega)$ assume in corrispondenza della particolare $\omega_{\pi}$ per cui $\angle G_a(j\omega_\pi)=-180\degree$.  
  
![Pasted image 20240208155257.png](./img/Pasted%20image%2020240208155257.png)  
  
In definitiva,   
$$m_G=-|G_a(j\omega_\pi)|_{\text{dB}}\text{ dai diagrammi di Bode}$$  
$$m_G=\frac{1}{|x_A|}\text{ dal diagramma di Nyquist}$$  
(questo sempre **sotto le ipotesi che abbiamo fatto sopra.**)  
### Margine di fase  
**Stiamo agendo ancora sotto quelle ipotesi.**  
  
La fase la si vede dal diagramma di Nyquist come *l'angolo che si forma tra l'asse reale e la retta che passa per l'intersezione tra il grafico **del diagramma polare soltanto** e la circonferenza a modulo unitario, in senso orario*. La pulsazione del punto di intersezione è detta *pulsazione di crossover* $\omega_c$*.  
  
![Pasted image 20240425004610.png](./img/Pasted%20image%2020240425004610.png)  
  
Come formula sarebbe:  
$$m_\varphi=180\degree-\angle G_a(j\omega_c)$$  
  
Dal diagramma di Bode anche si può vedere: è la fase che si ha in corrispondenza della stessa pulsazione per cui hai che il modulo di $G_a(s)=1$ *in unità naturali*, ovvero l'intersezione con l'asse delle ascisse praticamente perchè modulo $=1$ vuol dire $0$ dB.  
  
![Pasted image 20240208160707.png](./img/Pasted%20image%2020240208160707.png)  
### Dai margini di stabilità alla stabilità effettiva  
**Sempre agendo sotto quelle ipotesi** se sia $m_G$ che $m_\varphi$ sono $>0$ **allora il sistema è asintoticamente stabile**.  
Per questo tipo di sistemi, praticamente si può dire se la FdT di catena chiusa sia stabile o meno **semplicemente guardando i diagrammi di Bode della FdT in catena aperta**. In particolare, un sistema che sia stabile per qualunque valore positivo del guadagno non superiore alla soglia $m_G$ è detto *a stabilità regolare*.  
  
Invece, **ci sono dei casi particolari**:  
- *esistenza di più pulsazioni per cui la fase della $G_a(j\omega)$ sia $=-180\degree$* (mi da problemi nel trovare $m_G$ perchè ne avrei più di uno)  
	- nel diagramma di Nyquist ho più intersezioni con l'asse reale negativo  
	- nel diagramma di Bode della ho più intersezioni con l'asse $\varphi=-180\degree$  
	- si trovano due "candidati" per $m_G$ e si dice che il sistema in catena chiusa è da considerarsi asintoticamente stabile solo se il guadagno variabile della FdT a catena aperta è *compreso tra le due soglie*.  
	- Le due soglie si possono ancora trovare sia da Bode (esattamente come prima) sia da Nyquist (appunto fai il reciproco del modulo dell'ascissa delle due intersezioni per trovare le due soglie)   
		![Pasted image 20240208162032.png](./img/Pasted%20image%2020240208162032.png)  
- *esistenza di più pulsazioni per cui il modulo della $G_a(j\omega)$ sia $0$ dB* (mi da problemi nel trovare $m_\varphi$ perchè ne avrei più di uno)  
	- nel diagramma di Nyquist ho più intersezioni tra il grafico **del diagramma polare** e la circonferenza a raggio unitario (o comunque raggio = modulo del punto critico)  
	- nel diagramma di Bode del modulo ho più intersezioni con l'asse $|G_a(j\omega)|=0$ dB.   
	- si trovano due o più "candidati" per $m_\varphi$ e:  
		- il margine di fase è definito come *la massima fase che si può perdere*, e continuando con questa definizione, la pulsazione di crossover sarà quella corrispondente al punto del diagramma di Nyquist, che si interseca alla circonferenza a raggio unitario, tra tutti *più vicino all'asse reale*  
			  > Esempio:  
			  > ![Pasted image 20240208163317.png](./img/Pasted%20image%2020240208163317.png)  
			  > Il diagramma polare interseca in $3$ punti la circonferenza a raggio unitario, ma dato che $C$ è il punto più vicino all'asse reale, sul diagramma di Bode devo prendere come $\omega_c$ quella di $C$  
			  > ![Pasted image 20240208163513.png](./img/Pasted%20image%2020240208163513.png)  
			    
		- può succedere che le intersezioni che il diagramma polare ha con la circonferenza unitaria *non abbiano tutte fase $>-180\degree$*, quindi vedrai che alcuni punti di intersezione saranno nei quadranti primo e secondo del piano cartesiano.   
		  ![Pasted image 20240208163856.png](./img/Pasted%20image%2020240208163856.png)  
		  In tal caso, esisteranno **due margini di fase** - uno per la massima perdita di fase e uno per il massimo acquisto di fase. Quindi l'effettivo margine di fase è dato dall'intervallo compreso tra le due soglie.  
- $G_a(j\omega)$ *non a minima rotazione di fase - quindi poli a parte reale $> 0$ - quindi instabile* (il problema è che se la catena aperta è instabile allora bisogna vedere cosa succede a catena chiusa per definire se il sistema in catena chiusa sia stabile o meno).  
	- ![Pasted image 20240208164622.png](./img/Pasted%20image%2020240208164622.png)  
#### Con MATLAB  
`margin` ti da la lettura dei margini solo che funziona solo **con le ipotesi**. Altrimenti fai a mano.  
### Picchi di risonanza della funzione a catena chiusa come margini indiretti di stabilità  
È anche possibile ricavare delle informazioni sulla robustezza stabilità della catena chiusa "indirette", per esempio la presenza di un **"significativo" picco di risonanza** $M_r$ che fanno presupporre che siano, nella FdT di catena chiusa, **almeno due poli complessi coniugati con smorzamento "piccolo"**. Quanto più sono ampi i picchi di risonanza (quindi quanto più sono piccoli gli smorzamenti), tanto più il sistema è vicino alla condizione di instabilità, perchè uno smorzamento piccolo significa poli vicini al semipiano di destra, e quindi poli sempre più vicini ad avere parte reale positiva invece che negativa.  
  
Se la FdT a catena chiusa è $W(s)=y(s)/r(s)=K_rW_y(s)$ e chiamo $W_y(s)=y(s)/y_{\text{des}}(s)=\frac{G_a(s)}{1+G_a(s)}$, allora chiamo $W_r=\max\{|W_y(s)|\}$  
  
$$M_r=\frac{W_r}{|W_y(0)|}=\frac{1}{2\zeta\sqrt{1-\zeta^2}}\qquad\zeta\in(0,1/\sqrt{2})$$  
  
quindi, per esempio, valori tipici sono $M_r$ di qualche dB ($1\div5$) e $\zeta$ è $0.3\div 0.5$. **Valori anomali indicano poca lontananza dall'instabilità, quindi poca robustezza**.  
#### Legame tra picchi di risonanza della FdT di catena chiusa e diagramma di Nyquist della FdT di catena aperta   
**Non ho capito un cazzo del resto**, ma la parte importante sembra essere che **se costruisci le circonferenze descritte dalle equazioni** $$(\mathcal{R}-\mathcal{R}_0)^2+\mathcal{I}^2=\rho^2$$ ovvero circonferenze nel piano complesso di raggio $\rho$ e centro $(\mathcal{R}_0, 0)$, dove $$\mathcal{R}_0=\frac{M^2}{1-M^2},\ \rho=\frac{M}{|1-M^2|}$$  
dove   
$$M(j\omega)=|W_y(j\omega)|=\left|\frac{G_a(j\omega)}{1+G_a(j\omega)}\right|$$  
  
avrò, **al variare di $M$, una serie di circonferenze concentriche (cerchi M)**.  
  
![Pasted image 20240208171758.png](./img/Pasted%20image%2020240208171758.png)  
  
#continuare   
  
