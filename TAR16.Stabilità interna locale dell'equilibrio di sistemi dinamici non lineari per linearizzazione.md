---  
share: true  
---  
Per un sistema non lineare non potrai mai dire che l'intero sistema sia stabile o meno dato che serve la condizione di sistema LTI per parlare di "stabilità del sistema". L'unica cosa che si può determinare è la stabilità di alcuni movimenti nominali dello stato.  
  
È di particolare interesse, nel caso di sistemi non lineari, il caso dei movimenti di equilibrio, ovvero di quei movimenti nominali dello stato del sistema che mantengono un valore costante nel tempo e pari allo stesso stato iniziale, per ingressi costanti anch'essi.  
Sono di particolare interesse perchè effettuare una linearizzazione del sistema non lineare nell'intorno di un suo movimento di equilibrio (o meglio di un suo punto di equilibrio) ci da come risultato un sistema non solo lineare, ma perfino LTI (e quindi facilmente rappresentabile tramite le matrici di stato $A,B,C,D$).  
  
Analizzando la stabilità interna del sistema linearizzato ottenuto, che ben approssima il sistema non lineare nell'intorno di quel punto di funzionamento di equilibrio che abbiamo deciso di usare, possiamo concludere sulla stabilità del movimento di equilibrio considerato:  
- se il sistema linearizzato risulta asintoticamente stabile (i suoi autovalori sono tutti a parte reale strettamente negativa nel caso TC, o a modulo strettamente minore di 1 nel caso TD) allora il movimento di equilibrio considerato è anch'esso un movimento asintoticamente stabile.  
- se il sistema linearizzato risulta instabile, allora possiamo concludere che anche il movimento di equilibrio considerato è instabile.  
- se il sistema linearizzato risulta solo *semplicemente* stabile, allora **tramite questo metodo non si può concludere nulla sulla stabilità locale del sistema linearizzato, quindi sulla stabilità del movimento d'equilibrio considerato.**  
  
Questo metodo è detto **metodo indiretto di Lyapunov**.  
  
![Pasted image 20240215202139.png](./img/Pasted%20image%2020240215202139.png)  
