---
{"dg-publish":true,"permalink":"/taragna/tar-04-modellistica-di-sistemi-elettromeccanici/"}
---

#continuare 
## Principi fisici di funzionamento
### Forza di Lorentz
Un conduttore in cui scorre una corrente immerso in un campo magnetico subisce una forza $F_L = l\cdot \vec{i}(t)\times\vec{B}(t)$
![Pasted image 20230505104955.png](/img/user/img/Pasted%20image%2020230505104955.png)
Per cui se collego dei conduttori a formare una spira, si avrà una *coppia* $$T_L = i(t)AB(t)\sin(\theta(t))$$con $\theta$ l'angolo tra $\vec{B}$ e $\hat{u_n}$ (vettore normale alla spira).
![Pasted image 20230505105352.png](/img/user/img/Pasted%20image%2020230505105352.png)
Quindi la spira girerà; in particolare, se la spira è perpendicolare al campo magnetico allora il vettore ad essa normale sarà parallelo al campo magnetico, per cui risulterà l'angolo tra essi compreso nullo e la coppia di Lorentz sarà nulla. Invece sarà massima nel caso della spira parallela al campo (-> vettore normale perpendicolare) (come nella figura).
### Forza elettromotrice indotta
In un conduttore elettrico che formi un circuito chiuso e concateni un flusso di campo magnetico che vari per qualunque motivo (quindi per esempio una variazione in modulo o in verso del campo magnetico oppure uno spostamento angolare della spira) si andrà a creare una forza elettromotrice indotta tale da produrre una corrente indotta. Questa corrente indotta tenderà a far muovere (per coppia di Lorentz) la spira fino a compensare la variazione di flusso che si era osservata (legge di Faraday-Neumann-Henry-Lenz-mammata)
$$e(t)=-\frac{d\Phi(t)}{dt}$$
Questo significa che la spira tende a muoversi spontaneamente solo se si trova in posizione diversa da quella ad energia potenziale minore, ovvero quella dove la spira è posta in posizione perpendicolare al campo magnetico (vettore normale parallelo). Nelle altre posizioni il moto generato dalla coppia motrice di Lorentz non è spontaneo e va pagato in termini elettrici di una quantità uguale alla forza elettromotrice indotta.
## Parti principali di un DC-motor
### Statore
Parte esterna; non ruota; genera un campo magnetico (tramite magneti permanenti oppure costruendo un solenoide, qui detto *circuito di eccitazione*, quindi una serie di avvolgimenti alimentati in corrente continua che generi un campo magnetico al suo interno parallelo al suo asse).
![Pasted image 20230505111152.png](/img/user/img/Pasted%20image%2020230505111152.png)
### Rotore
Parte interna, mobile, costituita da un cilindro ferromagnetico lamellato su cui sono posti numerosi avvolgimenti che formano il *circuito di armatura*. Genera un campo magnetico concatenato con quello dello statore.
### Anello di Pacinotti
(= collettore a spazzole) Interruttore rotante collegato all'alimentazione con contatti striscianti (spazzole). Ogni coppia di sezioni conduttrici spazialmente opposte dell'anello è collegata ad una (o più) maglie del rotore. Durante la rotazione del rotore l'anello di Pacinotti interrompe e ripristina continuamente l'alimentazione (che gli arriva tramite le spazzole sotto forma di *corrente di armatura*). Questo permette in ogni momento della rotazione di alimentare solo alcune maglie, ovvero quelle collegate alle sezioni conduttrici dell'anello che in quel momento sono collegate all'alimentazione. In particolare si alimenteranno in ogni momento della rotazione solo le maglie che si troveranno in quel momento parallele al campo magnetico del rotore (per le quali la coppia di Lorentz sarà massima).
Un motore elettrico "fonde" quando gli avvolgimenti del rotore perdono tra loro l'isolamento e quindi si riduce il numero di maglie che al momento opportuno dovrebbero girare.
![Pasted image 20230505112825.png](/img/user/img/Pasted%20image%2020230505112825.png)
### Albero motore
Solidale con il rotore e dotato di un proprio momento d'inerzia, di solito collegato meccanicamente alla carcassa del motore tramite cuscinetti a sfera.
## Modello di un DC-motor
### Modello elettrico
![Pasted image 20230505113640.png](/img/user/img/Pasted%20image%2020230505113640.png)
Il modello elettrico del rotore è descritto in ogni momento dalle maglie che sono alimentate in quel momento, per cui la legge di Kirchoff ci dice $$v_a(t)=R_ai_a(t)+L_a\frac{di_a(t)}{dt}+e(t)$$con $e(t)$ la forza elettromotrice indotta, che è nulla quando il motore è fermo ma durante il moto riduce la caduta di potenziale su $R_a$ e $L_a$, opponendosi quindi al moto. 
Lo statore, invece, nel caso in cui sia composto da avvolgimenti (esiste il circuito di eccitazione) è descritto da $$v_e(t)=R_ei_e(t)+L_e\frac{di_e(t)}{dt}$$Anche se nelle immagini convenzionalmente si disegna all'interno, lo statore sta fuori e avvolge il rotore (ma poi dovresti disegnare una cosa sull'altra e quindi si disegna così); inoltre lo statore ricordiamo che è fermo, mentre il circuito di armatura ruota. Quindi qui non c'è fem indotta.
### Modello meccanico
Il modello meccanico del rotore è invece descritto da $$J\ddot{\theta}(t)=J\dot{\omega}(t)=T_m(t)-T_r(t)-\beta\omega(t)$$
### Conversione di energia
Il fenomeno della conversione elettromeccanica di energia è descritto da $$e(t)=K\Phi(t)\omega(t)$$ (che sarebbe Faraday nello specifico caso del nostro motore)
 $$T_m(t)=K\Phi(t)i_a(t)$$
(che sarebbe un altro modo per scrivere la coppia di Lorentz)
Se lo statore è stato realizzato come un solenoide allora il $\Phi(t)$ ha tipicamente un andamento non lineare rispetto alla corrente di eccitazione, ma noi considereremo intorni di punti di interesse, linearizzandone la caratteristica.
### Comando in armatura
- Il flusso magnetico dello statore è tenuto costante (magneti permanenti o corrente di eccitazione costante)
- Il comando del motore è la tensione variabile $v_a(t)$ applicata al circuito di armatura del rotore
In questo caso $\Phi(t)=\overline{\Phi}$, perchè $i_e(t)=\overline{i_e}$ => l'equazione del circuito di eccitazione è di tipo statico:
$$v_e(t)=R_e\overline{i_e}+L_e\frac{di_e(t)}{dt}=R_e\overline{i_e}=\overline{v_e}$$
### Comando in eccitazione
- La corrente di armatura nel rotore è tenuta costante
- Il comando del motore è la tensione variabile $v_e(t)$ applicata al circuito di eccitazione dello statore => variano sia la corrente di eccitazione $i_e(t)$ sia il flusso magnetico dello statore $\Phi(t)=\Phi(i_e(t))$.
