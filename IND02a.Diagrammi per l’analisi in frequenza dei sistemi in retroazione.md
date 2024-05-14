---  
share: true  
tags:  
  - continuare  
  - controllare  
---  
I principali diagrammi che utilizzeremo per studiare la risposta in frequenza di un sistema sono:  
- I diagrammi di Bode  
- I diagrammi polari  
- I diagrammi di Nyquist  
- I diagrammi di Nichols  
  
Piccolo preambolo sui numeri complessi and shit:  
![Pasted image 20240207130404.png](./img/Pasted%20image%2020240207130404.png)  
  
## Diagrammi di Bode  
I diagrammi di Bode per modulo e fase hanno in ascissa la pulsazione $\omega$ in scala logaritmica e sulle ordinate il modulo $M$ espresso in Decibel oppure la fase $\varphi$ espressa in gradi.  
  
Prendi la funzione di trasferimento; ne fai il modulo in Decibel che vuol dire scrivere una roba del tipo:  
$$20\log_{10}(G(j\omega))=20\log_{10}\left(200\frac{j\omega+0.1}{j\omega(-\omega^2+0.2j\omega+1)(j\omega+10)}\right)=$$  
$$=20\log_{10}(200)+20\log_{10}(j\omega+0.1)-20\log_{10}(j\omega)-20\log_{10}(j\omega(-\omega^2+0.2j\omega+1)-20\log_{10}(j\omega+10)$$  
Quindi ogni quantità dentro i logaritmi deve essere portata nelle forme  
- $K$  
	- Modulo: corrisponde ad una retta orizzontale di quota $20\log_{10}{K}$  
	- Fase: corrisponde ad una retta orizzontale nulla  
- $(j\omega)^N$  
	- Modulo: corrisponde ad una retta di pendenza $+20N$ dB/dec se è al numeratore o $-20N$ dB/dec se è al denominatore, che va da $-\infty$ a $+\infty$ e passa per $\omega=1$.   
	- Fase: corrisponde ad una retta di pendenza $+90N\ \degree$ se è al numeratore e $-90N\ \degree$ se è al denominatore  
- $\left(1+\frac{j\omega}{z_i}\right)^N$  
	- Modulo:  
	- Fase:  
- #continuare   
![Pasted image 20240207132109.png](./img/Pasted%20image%2020240207132109.png)  
## Diagramma polare  
I diagrammi polari di funzioni complesse sono praticamente rappresentazioni grafiche sul piano di Gauss (parte reale sulle ascisse, parte immaginaria sulle ordinate). Le quantità a *modulo costante* si trovano *sulla stessa circonferenza*, quelle alla stessa fase (arctan...), *sulla stessa semiretta*.  
  
I diagrammi polari *li facciamo guardando quelli di Bode*.  
Fondamentalmente, tu del diagramma polare determini "manualmente" soltanto il *comportamento iniziale e finale* quindi per $\omega\to0^+$ e per $\omega\to+\infty$ (e anche questo, guardando Bode) e poi filli la restante parte del diagramma sempre guardando Bode.  
In particolare:  
- **comportamento iniziale**:   
	- se il sistema *non ha poli nell'origine* allora il diagramma polare parte da un punto sull'asse reale, avente quindi fase nulla mi pare di poter dire, e modulo iniziale che posso vedere da Bode.  
	- se il sistema *ha $n$ poli nell'origine* (cioè presenta termini del tipo $K/s^n$) allora il diagramma polare parte da un punto *infinitamente lontano dall'origine*, con *fase iniziale* $$\varphi_{\text{in}}=-\frac{\pi}{2}\cdot n+\angle K$$ dove $\angle K$ è $0$ se $K>0$ oppure $\pm\pi$ se $K<0$ #controllare   
		- $K$ si determina facendo $K=\lim_{s\to0}s^nF(s)$  
		- per determinare il quadrante da cui iniziare a tracciare il diagramma dopo aver calcolato la fase iniziale devi vedere dal diagramma di Bode della fase se essa *diminuisce o aumenta* andando dal valore iniziale al valore finale e tracciare di conseguenza.  
- **comportamento finale**:   
	- **per noi, i sistemi saranno sempre strettamente propri. In questo caso, il diagramma termina sempre nell'origine**.  
	- la *fase finale* è la fase con cui arriva nell'origine ed è multipla di 90 gradi secondo $$\varphi_{\text{fin}}=\varphi_{\text{in}}-90(n_{\text{np}}+m_\text{p})+90(n_\text{p}+m_\text{np})$$ dove $n_\text{np}$ è il numero di poli a parte reale *non positiva* (esclusi quelli nell'origine), $m_\text{p}$ è il numero di zeri a parte reale positiva, ecc.  
  
![Pasted image 20240425004354.png](./img/Pasted%20image%2020240425004354.png)  
  
## Diagramma di Nyquist  
Il diagramma di Nyquist alla fine è un diagramma polare, o meglio una loro estensione, infatti la pulsazione non è più solo positiva qui  ma è $\in[-\infty, +\infty]$. Quindi che succede?  
- Devi **disegnare due volte il diagramma polare**, quando finisci di disegnarlo devi **disegnarlo ribaltato rispetto all'asse reale sullo stesso grafico** e **unire i valori che vanno all'infinito con semi-circonferenze che vanno in senso orario, di raggio infinito**.  
	- Se non hai poli nell'origine, ottieni subito un percorso chiuso.  
	- Se hai $n$ poli nell'origine, **devi fare $n$ semi-circonferenze**.  
  
![Pasted image 20240425004422.png](./img/Pasted%20image%2020240425004422.png)  
  
## Diagramma di Nichols  
> Ma mi serve? Perchè mi sa che non l'abbiamo fatto a lezione. Vabbè...  
  
In pratica è un diagramma di Bode "unico" infatti in ascissa ci sono i gradi e in ordinata i Decibel. Vabbè... okay.  
  
