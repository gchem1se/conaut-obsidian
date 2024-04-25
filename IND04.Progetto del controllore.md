---  
dg-publish: true  
share: true  
tags:  
  - continuare  
---  
Fondamentalmente si tratta di questo:  
in uno schema di un sistema di controllo completo come:  
  
![Pasted image 20240211195053.png](./img/Pasted%20image%2020240211195053.png)  
  
Devi progettare unicamente la FdT del controllore ovvero $C(s)$.  
  
Da qui in poi, considereremo sempre $C(s)=\frac{K_c}{s^h}C'(s)$ dove i vincoli statici (tempo di salita $t_s$, sovraelongazione massima) saranno dettati da $K_C$ e $1/s^h$ ($h$ il numero di integratori).  
- Le specifiche su $t_s$ portano ad individurare un valore desiderato della pulsazione di crossover $\omega_{c,\text{des}}$  
- Le specifiche sulla sovraelongazione massima o sul picco di risonanza portano ad individuare un valore minimo del margine di fase $m_{\varphi,\min}$. La $C'(s)$ viene allora costruita in modo che $G_a(s)$ abbia $\omega_c\approx\omega_{c,\text{des}}$ e $m_\varphi\ge m_{\varphi,\min}$.  
- Per costruire $C'(s)$ accordingly, prima di tutto la poni $C'(s)=1$ e vedi di quanto ti discosti da ciò che volevi:  
	- $G_{a, 1}(s) = \frac{K_c}{s^h}F(s)$  
	- Valutiamone modulo e fase per $\omega=\omega_{c,\text{des}}$  
		- Otteniamo una $\Delta m_{dB}$ (*variazione di modulo*) definita come il numero di Decibel (si può anche fare in unità naturali) necessarie a portare la pulsazione di crossover di $G_{a,1}$ a $\omega_{c,\text{des}}$  
			- $\Delta m_{dB}=-|G_{a,1}(j\omega_{c, \text{des}})|_{dB}$  
			- Sì perchè in sostanza a $\omega_{c,\text{des}}$ dovrei avere modulo $0$ dB per avere che quella sia veramente la pulsazione di crossover, quindi devo sicuramente mettere il $-$ davanti (devo operare un movimento opposto).  
		- Otteniamo un $\Delta\varphi$ (*variazione di fase*) definita come il numero di gradi o radianti necessari ad ottenere $m_\varphi>m_{\varphi,\min}$ alla pulsazione $\omega_{c,\text{des}}$  
			- Anche qui, alla pulsazione di crossover hai che corrisponde esattamente il margine di fase  
			- se è positivo allora la variazione di fase che va introdotta è un *anticipo*, se è negativa è un *ritardo*  
	- Una volta valutati gli scostamenti da ciò che la specifica richiede usando $C'(s)=1$, si può procedere a cercare di capire come effettivamente $C'(s)$ deve essere fatto: in pratica, $C'(s)$ è la FdT di un complesso di **reti di compensazione**.  
## Principali reti di compensazione  
### Anticipatrici o derivative  
Una rete anticipatrice ha una FdT del tipo  
$$R_d(s)=\frac{1+\tau_ds}{1+\frac{\tau_d}{m_d}s}$$  
con $\tau_d>0,\ m_d>1$, uno zero in $s=-1/\tau_d$ e un polo in $s=-m_d/\tau_d$.  
- I valori di $m_d$ che considereremo sono sempre $\in[2,16]$.  
- All'aumentare di $m_d$ cresce *l'anticipo di fase* e anche il modulo nella pulsazione di crossover  
	- $m_d=\frac{1+\sin(\varphi_\max)}{1-\sin(\varphi_\max)}$  
	- $\varphi_\max=\arcsin\left(\frac{m_d-1}{m_d+1}\right)$  
	- La $\tau_d$ si trova da $\omega_{c,\text{des}}\tau_d=\sqrt{m_d}$  
	- $\text{AumentoModulo}=\left|R_d\left(j\frac{\sqrt{m_d}}{\tau_d}\right)\right|$  
- Quindi le reti anticipatrici si usando quando *si vuole recuperare fase e si vuole recuperare modulo*, qunidi $\Delta m_{dB}>0$ e $\Delta\varphi>0$. Se il recupero di fase da soddisfare non è maggiore di $60\degree$ allora se ne può usare una sola, altrimenti sarebbe opportuno utilizzare due o più reti anticipatrici. Tuttavia l'aumento del modulo può pregiudicare il poter utilizzare questo metodo (nel caso in cui sia $\text{AumentoModulo}>\Delta m_{dB}$).   
- Se si decide di optare per una rete anticipatrice e $\Delta m_{dB}$ ancora non viene completamente compensato dal recupero che la rete offre, si può agire direttamente su $K_c$ per avere $|G_a(j\omega)|=1$ in unità naturali per $\omega=\omega_{c,\text{des}}$.  
- **Cazzo è la frequenza di lavoro?**  
### Attenuatrici o integrative  
Una rete attenuatrice ha una FdT del tipo:  
$$R_i(s)=\frac{1+\frac{\tau_i}{m_i}s}{1+\tau_is}$$  
con $\tau_i>0,\ m_i>1$, uno zero in $s=-m_i/\tau_i$ e un polo in $s=-1/\tau_i$.  
All'aumentare di $m_i$ cresce *il ritardo di fase* e *diminuisce l'attenuazione del modulo* nella pulsazione di crossover   
	- $m_i$ si trova da $m_i=|G'_a(j\omega_{c,\text{des}}|$ con $G'_a$ la FdT a catena aperta prima dell'inserimento della rete integrativa  
	- La $\tau_i$ si trova da $\omega_{c,\text{des}}\tau_i=X_i$ dove $X_i$ è la frequenza di lavoro per cui l'attenuazione e la perdita di fase coincidano con le specifiche (non troppo grande altrimenti costante di tempo molto grande => risposta troppo lenta)  
- Quindi le reti attenuatrici si usando quando *si vuole attenuare il modulo senza troppo toccare la fase*.   
- **Cazzo è la frequenza di lavoro?**  
### Integro-derivative o lead-lag  
La loro FdT è:  
$$R_{id}(s)=R_i(s)R_d(s)$$  
Cioè sono frutto del collegamento in serie di una integrativa e di una derivativa, quindi forniscono in un colpo solo *attenuazione di modulo* e *recupero di fase* alla frequenza $\omega_{c,\text{des}}$.  
- Si progetta prima la derivativa, per garantire un recupero di fase maggiore di quello necessario, poichè la integrativa comporterà una perdita della stessa.  
	- Se l'anticipo è molto alto, usare più derivative in serie.  
- Si progetta poi la rete integrativa scegliendo $m_i$ in modo da avere l'attenuazione di modulo richiesta ed una perdita di fase sopportabile.  
  
## Altre reti di compensazione  
### Filtro risonatore  
È possibile **annullare ogni disturbo** se tutti i disturbi agenti sul sistema sono alla medesima e unica pulsazione nota $\omega_R$.   
Si fa aggiungendo un filtro risonatore a monte del disturbo attivo.  
![Pasted image 20240211211446.png](./img/Pasted%20image%2020240211211446.png)  
### Filtro notch  
Stessa cosa del filtro risonatore ma invece di metterlo a monte del disturbo attivo lo metti a valle dell'ultimo disturbo attivo.  
![Pasted image 20240211211544.png](./img/Pasted%20image%2020240211211544.png)  
### Compensatore PI  
**Se le specifiche di precisione impongono una catena aperta di tipo 1**, allora il controllore dovrebbe contenere un polo nell'origine ($h=1$).  
**Se in tali casi serve anche un buon anticipo di fase** può essere conveniente "aggiungere uno zero reale" ovvero avere un controllore con funzione di trasferimento  
$$C(s)=C_{\text{PI}}(s)=\frac{1+\tau s}{s}$$ Si può usare quindi al posto di una rete derivativa.  
- **Come cazzo determino $\tau$?**  
### Introduzione di poli reali instabili  
> Esiste un controllore $C(s)$, internamente stabile se il sistema presenta un numero pari di poli tra ciascuna coppia di zeri sul semiasse reale non negativo  
  
Ciò vuol dire che a volte è necessario inserire un polo instabile nel controllore per stabilizzare il  
sistema. È possibile che introdurre anche uno zero per avere un anticipo di fase.  
![Pasted image 20240211212019.png](./img/Pasted%20image%2020240211212019.png)  
![Pasted image 20240211212031.png](./img/Pasted%20image%2020240211212031.png)  
  
- **Anche qui come cazzo determino il tuttecose?**  
## Controllori PID  
Famiglia particolare di controllori, costituiti da una parte Proporzionale, una Integrativa e una Derivativa.  
Per poterli progettare si può scegliere una delle seguenti vie:  
- Utilizzare un *metodo di taratura in anello chiuso* effettuata *retroazionando il sistema con un compensatore statico*  
- Utilizzare un *metodo di taratura in anello aperto* effettuata *sul sistema senza inserire alcun tipo di controllo*   
  
Sono caratterizzati da tre parametri liberi, i quali, una volta individuati, permettono di ottenere il controllore; proprio per questo  
motivo i PID sono utilizzati in situazioni semplici (statiche) e difficilmente riescono ad operare in situazioni più complesse (dinamiche).  
  
![Pasted image 20240211212310.png](./img/Pasted%20image%2020240211212310.png)  
  
- Il termine proporzionale amplifica l’ingresso e non è in grado di garantire errori di inseguimenti nulli  
- Il termine integrale elimina l’errore in regime permanente a fronte di segnali di riferimento costanti (e disturbi additivi costanti sull’uscita. Introduce un ritardo di fase)  
- La parte derivativa può portare ad un’eccessiva attività sul comando  
  
I parametri liberi sono $K_P$, $K_I$ e $K_D$. La FdT di un controllore PID è:  
$$R_{\text{PID}}=K_P+\frac{K_I}{s}+K_Ds=$$  
$$=K_P\left(1+\frac{K_I}{K_Ps}+\frac{K_Ds}{K_P}\right)=K_P\left(1+\frac{1}{T_Is}+T_Ds\right)$$  
con   
- $T_I$ **tempo integrale** $=\frac{K_P}{K_I}$  
- $T_D$ **tempo derivativo** $=\frac{K_D}{K_P}$  
  
La FdT tuttavia se la scrivi per esteso è **improprio quindi irrealizzabile** => va aggiunto un **polo di chiusura** all'interno del blocco derivativo. Quindi la FdT reale di un controllore PID è:  
$$K_P\left(1+\frac{1}{T_Is}+\frac{T_Ds}{1+\frac{T_D}{N}s}\right)$$  
  
![Pasted image 20240211212928.png](./img/Pasted%20image%2020240211212928.png)  
  
Solo che pure questa cosa presenta problemi: in particolare, la parte derivativa ha ora una Delta di Dirac come risposta al gradino.  
Per ovviare si può decidere di modificare lo schema in due modi:  
- applicare la rete derivativa solo sull'uscita e poi sommarla agli altri due contributi (gli zeri dalla catena chiusa diventano l'unione tra quelli del modello matematico del sistema fisico e lo zero della parte integrativa, mentre i poli restano invariati)  
	- ![Pasted image 20240211213348.png](./img/Pasted%20image%2020240211213348.png)  
- per non far comparire lo zero della parte integrativa nella funzione di trasferimento della catena chiusa, si può spostare anche la parte proporzionale (i poli restano comunque invariati)   
	- ![Pasted image 20240211213343.png](./img/Pasted%20image%2020240211213343.png)  
### Metodi di taratura  
Taratura = scegliere i 3 parametri $K_P$, $K_D$, $K_I$.  
#### In anello chiuso - metodo di Ziegler-Nichols  
  
#### In anello aperto - metodo della tangente  
  
#continuare   
