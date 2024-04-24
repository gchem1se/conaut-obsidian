---
{"dg-publish":true,"permalink":"/taragna/tar-02-modellistica-di-sistemi-elettrici/"}
---

## Elementi fondamentali
- Resistori ideali
	- Si usa convenzione utilizzatori (verso di corrente = -verso di tensione)
	- equazione costituiva: $v(t)=Ri_R(t)$
	- equazione costituiva nel dominio delle trasformate di Laplace: $V(s)=RI_R(s)$
	- la relazione costituiva è **di tipo statico**, quindi non c'entra con le equazioni di stato del sistema
	- unità di misura: $\Omega$ (Ohm)
- Condensatori ideali
	- Si usa convenzione utilizzatori (verso di corrente = -verso di tensione)
	- equazione costituiva: $i_C(t)=C\frac{dv_C(t)}{dt}$
	- equazione costituiva nel dominio delle trasformate di Laplace: $I_C(s)=sCV_C(s)-CV_C(0^-)$ (trasformata di Laplace *monolatera* da $0^-$)
	- la relazione costituiva è **di tipo dinamico**, con $v_C$ variabile di stato.
	- unità di misura: $F$ (Farad)
	- insieme agli induttori ci danno le equazioni di stato
- Induttori ideali
	- Si usa convenzione utilizzatori (verso di corrente = -verso di tensione)
	- equazione costituiva: $v_L(t)=L\frac{di_L(t)}{dt}$
	- equazione costituiva nel dominio delle trasformate di Laplace: $V_L(s)=sLi_L(s)-Li_L(0^-)$
	- la relazione costituiva è **di tipo dinamico**, con $i_L$ variabile di stato.
	- unità di misura: $H$ (Henry)
	- insieme ai condensatori ci danno le equazioni di stato
- Generatori ideali
	- Si usa convenzione generatori (verso di corrente = verso di tensione)
	- sono gli ingressi del sistema
## Rappresentazione in variabili di stato del sistema
Significa trovare le matrici $A$, $B$, $C$, $D$ in funzione dei parametri del sistema.
(sneak peek: $D$ è una matrice di zeri se il sistema è proprio)
1. Si scrivono le equazioni costituive dei componenti con memoria (condensatori e induttori)
2. Si scrivono le equazioni topologiche (Kirchhoff alle nodi o alle maglie)
3. Si introduce una variabile di stato per ogni componente con memoria (tensioni ai capi dei condensatori e correnti negli induttori). **OCCHIO**: se ci sono reti *degeneri* (maglie con solo generatori di tensione e condensatori, oppure nodi dove arrivano solo correnti provenienti da generatori di corrente e induttori), **va sistemato!** Le variabili di stato devono essere **indipendenti**, altrimenti una o più delle variabili di stato sarebbero combinazioni lineari delle precedenti (inutili). **Se succede**, conviene associare la variabile di stato ad un altro componente del circuito (es. due induttori in serie ad un resistore => conviene considerare la variabile di stato come "corrente nel resistore" (così è singola)). In quei casi il numero di equazioni di stato (= dimensione sistema) è **strettamente minore** del numero di componenti con memoria, e uguale al numero di variabil di stato linearmente indipendenti.
4. Si associa una variabile di ingresso $u_j$ ad ogni generatore ideale
5. Il lavoro è di sostituzione algebrica: bisogna ricavare ogni $x_i(t)$ (tante quante sono le variabili di stato) e ogni $y_k(t)$ in funzione unicamente di variabili di ingresso e stato.
**Esercizi su quaderno.**
