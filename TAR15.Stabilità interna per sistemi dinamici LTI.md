---  
share: true  
---  
## Se hai gli autovalori  
 ![Pasted image 20240215195751.png](./img/Pasted%20image%2020240215195751.png)  
 ![Pasted image 20240215195733.png](./img/Pasted%20image%2020240215195733.png)  
## Se hai solo la FdT - criteri di stabilità  
![Pasted image 20240216001650.png](./img/Pasted%20image%2020240216001650.png)  
### TC  
- Se il polinomio denominatore della FdT è di grado 2, basta la **regola di Cartesio**.  
	- Se tutti e 3 i coefficienti hanno segno concorde, allora il sistema è asintoticamente stabile  
		- quindi anche esternamente stabile  
	- In generale, mi dice che il numero di radici reali positive è uguale al numero di variazioni di segno o differisce da questo per un multiplo di due  
	- ![Pasted image 20240216161353.png](./img/Pasted%20image%2020240216161353.png)  
- Se il grado è maggiore di 2, allora serve il **criterio di Routh**, **sebbene Cartesio rimanga una condizione necessaria**  
	- se si rompe Cartesio, è già non asintoticamente stabile (cioè se ha poli a parte reale positiva), però se non si rompe, devi controllare con il criterio di Routh.  
	- dipende dalla prima colonna della **tabella di Routh**  
	- praticamente è una tabella di cui mi interessa solo la prima colonna  
		- questa è fatta da $n+1$ righe con $n$ il grado del polinomio che prendo in considerazione  
		- le prime due righe si fanno semplicemente guardando il polinomio  
		- per la altre righe devi seguire sto schema:  
			- ![Pasted image 20240216161002.png](./img/Pasted%20image%2020240216161002.png)  
		- se la prima colonna della tabella di Routh ha elementi concordi allora il sistema è asintoticamente stabile internamente => anche esternamente stabile. Se la prima colonna non ha elementi nulli, tra l'altro, allora il numero di radici a parte reale positiva è uguale al numero di variazioni di segno nella tabella (come Cartesio).  
### TD  
Devi sempre usare il **criterio di Jury** ma **assieme ad altre tre disuguaglianze**.  
- Per il caso $n=2$ in realtà bastano le tre disuguaglianze  
	- ![Pasted image 20240216161602.png](./img/Pasted%20image%2020240216161602.png)  
	- il criterio di Jury si basa sulla **tabella di Jury** che è costituita da $n-1$ coppie di righe  
		- ![Pasted image 20240216161733.png](./img/Pasted%20image%2020240216161733.png)  
		- ![Pasted image 20240218141033.png](./img/Pasted%20image%2020240218141033.png)  
		- ![Pasted image 20240218141042.png](./img/Pasted%20image%2020240218141042.png)  
		- ![Pasted image 20240218141101.png](./img/Pasted%20image%2020240218141101.png)  
  
  
