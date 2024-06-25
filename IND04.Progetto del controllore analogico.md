---  
share: true  
---  
Lo scopo del progetto del controllore è costruire una $C(s)$ tale che se inserita a precedere (e comandare) il sistema porti la catena aperta ad essere innanzitutto stabile, e poi a soddisfare le specifiche.  
Il metodo che utilizziamo per il progetto consiste nell'imposizione di due fondamentali parametri della catena aperta: il margine di fase e la pulsazione di crossover. Specifiche su questi due parametri non ci vengono praticamente mai date esplicitamente: piuttosto ci vengono date specifiche *correlabili*, le quali ci permettono di determinare i vincoli su questi due parametri tramite le relazioni approssimate che abbiamo visto [qui](./IND03.Analisi%20approfondita%20delle%20specifiche%20di%20progetto.mdrelazioni-approssimate-supponendo-comportamento-dominante-del-secondo-ordine).  
Tendenzialmente, una volta riusciti a posizionare correttamente la pulsazione di crossover tramite l'inserimento del blocco $C(s)$ nella catena aperta e aver garantito un certo margine di fase, si potrà vedere la stabilità e il rispetto delle specifiche della catena chiusa.  
Potrebbe però non funzionare qualcosa. Dopo vedremo come risolvere eventuali magagne, ma prima, una presentazione del metodo che utilizziamo per il progetto di $C(s)$, che è fondamentalmente costituito da due macro componenti, le cui funzioni di trasfeimento vanno moltiplicate: una parte statica (che va ad essere formata da un guadagno statico e un certo numero di poli nell'origine, integratori) e da una parte dinamica (formata dalla cascata di particolari blocchi detti *reti*). Lo scopo della parte statica è quella di garantire il soddisfacimento delle specifiche statiche sulla catena chiusa, quali l'inseguimento e la reiezione di disturbi polinomiali.  
La parte dinamica invece porta la pulsazione di crossover nella frequenza voluta e impone il margine di fase desiderato.  
## Progetto della parte statica del controllore  
  
## Progetto della parte dinamica del controllore  
  
### Reti anticipatrici o derivative  
Una rete anticipatrice ha una FdT del tipo  
$$R_d(s)=\frac{1+\tau_ds}{1+\frac{\tau_d}{m_d}s}$$  
### Reti attenuatrici o integrative  
Una rete attenuatrice ha una FdT del tipo:  
$$R_i(s)=\frac{1+\frac{\tau_i}{m_i}s}{1+\tau_is}$$  
### Progetto della cascata di anticipatrici e attenuatrici  
## Introduzione di zeri reali al posto di reti derivatrici  
**Solo nel caso nel controllore sia stato necessario aggiungere almeno un polo reale**, si può pensare (ed è molto conveniente nella gran parte delle situazioni, specialmente quando si vuole contenere l'aumento di modulo) di posizionare coerentemente uno zero reale negativo nel controllore invece di progettare delle reti derivatrici.  
La *rete zero* ha come FdT semplicemente   
$$R_z(s) = 1 + \tau_z s $$  
## Workflow  
  
## Magagne fantastiche e come risolverle  
- Sovraelongazione o picco di risonanza non accettabile  
	- Se il tuo margine di fase non è già astronomico (es. maggiore di $60/65 °$) punta ad alzarlo un po', alzando le $m_d$ delle reti derivatrici oppure spostando la pulsazione di lavoro $x_d$ (o $x_z$, se sei con uno zero reale).  
	- Se il tuo margine di fase è già alto, controlla il diagramma di Nyquist della tua attuale funzione di catena aperta: potresti trovare che la forma della funzione ti consigli più che altro di alzarne il guadagno per evitare la circonferenza corrispondente al picco di risonanza da evitare.  
- Tempo di salita non accettabile  
	-   
- Attività sul comando troppo alta  
	-   
- Sensibilità in corrispondenza della pulsazione indicata troppo alta  
	-   
- Banda passante non accettabile  
	-   
