---
{"dg-publish":true,"permalink":"/taragna/tar-21-stabilita-esterna-e-risposta-a-regime/"}
---

Un sistema dinamico, a dimensione finita (numero finito di variabili di stato), LTI, inizialmente a riposo (quindi che abbia risposta libera $= 0$, o meglio $$y(t)=\mathcal{L}^{-1}\{H(s)U(s)\}$$), è detto **BIBO-stabile** (*bounded input - bounded output*) o **esternamente stabile** se la sua risposta forzata a ingressi limitati è sempre limitata.
Per noi, le condizioni sono:
- sistema con tutte le cancellazioni zero-polo fatte è un *sistema in forma minima*
- un sistema è BIBO-stabile se tutti i poli della funzione di trasferimento hanno parte reale strettamente negativa (nel caso TC) oppure modulo strettamente minore di 1 (nel caso TD)
- essendo i poli della funzione di trasferimento in generale un sottoinsieme degli autovalori della matrice A, si hanno delle implicazioni
	- sistema (internamente) asintoticamente stabile $\implies$ tutti i suoi poli sono nella regione di asintotica stabilità $\implies$ sistema esternamente stabile 
	- sistema esternamente stabile e in forma minima $\implies$ tutti i suoi poli sono nella regione di asintotica stabilità e in più i poli coincidono precisamente con gli autovalori di $A$.
Quindi per capire se è esternamente stabile, per noi è necessario vedere se i poli siano tutti nella zona di asintotica stabilità. Sostanzialmente, capire se la FdT sia asintoticamente stabile.
- se hai gli autovalori in bella vista o facilmente calcolabili generalmente controlli da lì. Controllandoli tutti sai per certo che stai controllando anche i poli, visto che ne sono un sottoinsieme.
- se invece hai solo la FdT... beh devi usare *i criteri* per vedere se sia asintoticamente stabile senza sapere gli autovalori. 
## Risposta in regime permanente
![](/img/user/img/confr_omg_part.png)
Dall'analisi modale si scopre che la $y_\text{omogenea}$, ovvero la risposta libera, è *combinazione lineare dei modi del sistema*. Un sistema asintoticamente stabile tende, all'infinito, ad avere parti reali degli autovalori della matrice di stato nulli, e quindi una risposta libera nulla; per cui per tempi sufficientemente grandi è vero $y(t)=0+y_{\text{particolare}}(t)=y_{\text{forzata}}(t)$.
La risposta di un sistema dinamico asintoticamente stabile (o esternamente stabile e in forma minima) può allora essere divisa in un **transitorio iniziale** e in una **risposta in regime permanente**. 

Per un ingresso di tipo gradino anche la risposta in regime permanente sarà costante. ![](/img/user/img/perm_sin.png)Se l'ingresso è sinusoidale, anche la risposta in regime permanente sarà sinusoidale.
![](/img/user/img/perm_grad.png)
