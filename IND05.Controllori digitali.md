---  
share: true  
---  
I controllori digitali sono **algoritmi** che simulano quello che farebbe un controllore analogico come quelli che abbiamo trattato fino ad ora ma lo fanno via software (sono filtri software) - è come fare un passabasso con MATLAB mettendogli i poli e facendo una funzione di trasferimento invece che prendere delle merde di resistenze e condensatori e fare una fisica rete LC che poi magari si brucia pure.  
  
Il senso è: mando il segnale, uso un A/D, mando il risultato di questo (digitale) all'elaboratore, questo me lo elabora, me lo sputa (digitale), uso un D/A che me lo sputa di nuovo in analogico e stop.  
Si può sempre fare se opero con un campionamento giusto perchè non perdo niente. Solo che nel modno reale qualcosa per forza la spacchi.  
  
Dobbiamo quindi passare al **dominio discreto del tempo**: e in buona sostanza questo significa che il segnale analogico di ingresso deve essere **campionato**. Quindi dobbiamo **scegliere il passo di campionamento**.  
  
## Discretizzazione di $C(s)$ in MATLAB  
![Pasted image 20240211214254.png](./img/Pasted%20image%2020240211214254.png)  
![Pasted image 20240211214323.png](./img/Pasted%20image%2020240211214323.png)  
![Pasted image 20240211214332.png](./img/Pasted%20image%2020240211214332.png)  
![Pasted image 20240211214337.png](./img/Pasted%20image%2020240211214337.png)  
![Pasted image 20240211214422.png](./img/Pasted%20image%2020240211214422.png)  
![Pasted image 20240211214429.png](./img/Pasted%20image%2020240211214429.png)  
  
- **Cazzo è la $ZOH$?**