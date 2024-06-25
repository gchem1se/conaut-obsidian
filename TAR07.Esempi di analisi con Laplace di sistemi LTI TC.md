---  
share: true  
---  
**Trovi i procedimenti fatti in esempi sul quadernetto.**  
  
## Calcolare l'inversa di $(sI_n-A)$  
$$(sI_n-A)^{-1}=\frac{1}{\text{det}(sI-A)}\text{Adj}(sI-A)$$  
La matice strana che compare nella formula è la *matrice aggiunta*, ovvero la *trasposta della matrice dei complementi algebrici* di $(sI-A)$;  
i complementi algebrici sono   
Questo funziona con qualunque dimensione e qualunque matrice.  
In particolare, in una matrice $2\times2$ la matrice aggiunta è calcolabile scambiando di *posto* gli elementi sulla diagonale e scambiando di *segno* gli elementi sulla antidiagonale.  
In generale, invece, la matrice dei complementi algebrici ha come generico elemento   
$$c_{i,j}=(-1)^{i+j}\text{det}(\small{\text{sottomatrice che si ottiene eliminando riga i e colonna j dalla matrice $(sI-A)^T$}})$$  
## Scomposizione in fratti semplici  
Questa cosa è essenziale perchè non vuoi davvero fare la trasformata di Laplace di funzioni complicate, quelle cose le fa MATLAB se pure ci va bene. Quindi noi cerchiamo di semplificarci la vita e davanti ad una funzione del genere:  
$$F(s)=\frac{b_ms^m++b_{m-1}s^{m-1}+\text{...}+b_1s+b_0}{s^n+a_{n-1}s^{n-1}+\text{...}+a_1s+a_0}=\frac{N_F(s)}{D_F(s)}$$  
possiamo cercare di *scriverla in fratti semplici (sviluppo di Heaviside)*, che saranno ognuno molto semplice da trasformare con Laplace.  
Nei seguenti paragrafi si considera già di non avere radici comuni tra numeratore e denominatore (si semplificano).  
### FdT strettamente propria + poli reali + poli di molteplicità unitaria  
$$F(s)=\frac{b_ms^m+b_{m-1}s^{m-1}+\text{...}+b_1s+b_0}{(s-p_1)(s-p_2)\text{...}(s-p_n)}=$$  
$$=\frac{R_1}{s-p_1}+\frac{R_2}{s-p_2}+\text{...}+\frac{R_n}{s-p_n}=\sum_{i=1}^{n}\frac{R_i}{s-p_i}$$  
Con $R_i$ detto *residuo associato all'$i$-esimo polo*.  
Ogni residuo si calcola come $$\lim_{s\to p_i}(s-p_i)F(s)$$Con quella moltiplicazione semplifico il fattore $s-p_i$ che ho al denominatore, evitando che il denominatore vada a $0$ nel limite e che tutto tiri su ad infinito.   
### FdT strettamente propria + poli anche complessi + poli di molteplicità unitaria   
$$F(s)=\frac{b_ms^m+b_{m-1}s^{m-1}+\text{...}+b_1s+b_0}{(s-p_1)(s-\sigma_0-j\omega_0)(s-\sigma_0+j\omega_0)\text{...}(s-p_n)}=$$  
$$=\frac{R_1}{s-p_1}+\frac{R_2}{(s-\sigma_0-j\omega_0)}+\frac{R_2^*}{(s-\sigma_0+j\omega_0)}+\text{...}+\frac{R_n}{s-p_n}$$  
Cambia solo che i due residui associati alla coppia di poli complessi coniugati saranno l'uno il coniugato dell'altro (pertanto basterà calcolare uno dei due) e successivamente, in fase di anti-trasformazione, si può usare questa formula per anti-trasformare la somma dei due in un colpo solo: $$\mathcal{L}^{-1}\left\{\frac{R_2}{(s-\sigma_0-j\omega_0)}+\frac{R_2^*}{(s-\sigma_0+j\omega_0)}\right\}=2|R_2|e^{\sigma_0t}\cos(\omega_0t+\angle R_2)$$  
con $|R_2|$ e $\angle R_2$ che si fanno facili con la calcolatrice.  
### FdT strettamente propria + poli anche complessi + poli multipli  
Nel caso di polo di molteplicità $\mu_i$ cambia il modo in cui si calcolano i residui (o meglio, la formula si generalizza):  
$$R_{i, k} = \lim_{s\to p_i}\frac{1}{(\mu_i-k)!}\frac{d^{\mu_i-k}}{ds^{\mu_i-k}}\left[(s-p_i)^{\mu_i}F(s)\right]$$  
Nel caso di molteplicità unitaria si ricade nella vecchia formula e in particolare in caso di molteplicità doppia si ha:  
$$R_{i,1}=\lim_{s\to p_i}\frac{d}{ds}[(s-p_i)^{\mu_i}F(s)]\implies \frac{R_{i,1}}{(s-p_i)}$$  
$$R_{i,2}=\lim_{s\to p_i}[(s-p_i)^{\mu_i}F(s)]\implies \frac{R_{i,2}}{(s-p_i)^2}$$  
### FdT strettamente impropria + poli anche complessi + poli multipli  
Se si ha $m=n$ prima di procedere come sopra si effettua la divisione tra i polinomi $N_F(s)$ e $D_F(s)$.  
## Matlab  
### Calcolo dei residui della scomposizione in fratti semplici  
```MATLAB  
[R, p, k] = residue(num, den);  
```  
con   
- `num, den`: numeratore, denominatore polinomiali della F(s)  
- `R`: vettore dei residui  
- `p`: radici del denominatore  
- `K`: quoziente della divisione tra numeratore e denominatore di F(s)  
