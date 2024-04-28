---  
share: true  
---  
Per *equilibrio di un sistema dinamico* si intende uno specifico *movimento che permane nel tempo identico allo stesso stato iniziale*, se gli ingressi sono costanti. Anche l'uscita del sistema sarà quindi costante.  
  
Tali parametri sono detti *ingresso di equilibrio* $\overline{u}\in\mathbb{R}^p$, *uscita di equilibrio* $\overline{y}\in\mathbb{R}^q$ e *stato di equilibrio* $\overline{x}\in\mathbb{R}^n$; la coppia $(\overline{x},\overline{u})$ è detta *punto di equilibrio*.  
## Condizione di equilibrio per sistemi TC  
Dalle equazioni differenziali che caratterizzano un qualsiasi sistema dinamico a tempo continuo:   
$$\dot{x}(t)=f(x(t), u(t))$$  
$$y(t)=g(x(t), u(t))$$  
Si nota che $\dot{x}(t)=\dot{\overline{x}}=0$ dato che $\overline{x}$ è costante; dunque *il punto di equilibrio è quello che annulla il secondo membro dell'equazione di stato del sistema*:  
$$f(\overline{x},\overline{u})=0$$  
e *a tali valori corrispondono le uscite di equilibrio*:  
$$\overline{y}=g(\overline{x}, \overline{u})$$  
  
## Condizione di equilibrio per sistemi LTI TC  
Un sistema dinamico LTI TC presenta questa forma specifica di equazioni rappresentative:  
$$\dot{x}(t)=Ax(t)+Bu(t)$$  
$$y(t)=Cx(t)+Du(t)$$  
Qui gli stati di equilibrio $\overline{x}$ corrispondenti all'ingresso di equilibrio $\overline{u}$ annullano ancora la prima equazione, in particolare:  
$$A\overline{x}+B\overline{u}=0,\ \forall t\ge0$$  
$$A\overline{x}=-B\overline{u}$$  
Le soluzioni di questo sistema di equazioni generano le corrispondenti uscite di equilibrio secondo:  
$$\overline{y}=C\overline{x}+D\overline{u}$$  
A seconda che la matrice $A$ degli stati sia invertibile (determinante $\ne0$) o singolare (determinante $=0$) si ha la corrispondenza di *uno ed un unico stato di equilibrio* nel primo caso oppure di *infiniti o di nessuno* nel secondo caso, a seconda delle caratteristiche specifiche delle matrici del sistema.  
  
In particolare, l'unico stato di equilibrio (detto *isolato*) per una matrice invertibile è  
$$\overline{x}=-A^{-1}B\overline{u}$$  
e ad esso corrisponde un'unica uscita di equilibrio  
$$\overline{y}=(-CA^{-1}B+D)\overline{u}$$  
## Condizione di equilibrio per sistemi LTI TD  
Il tutto è analogo per sistemi a tempo discreto.  
In particolare, si ha che non si deve annullare il secondo membro dell'equazione di stato, perchè quello valeva nel tempo continuo che ha equazioni differenziali come equazioni di stato: in quel caso stavamo annullando la derivata del movimento dello stato, per dire quindi che $\overline{x}$ fosse costante nel tempo.  
  
Nel caso TD invece abbiamo un'equazione alle differenze del tipo   
$$x(k+1)=Ax(k)+Bu(k)$$  
e qui la condizione "$x={\overline{x}}$ è costante nel tempo" si esprime dicendo che $x(k+1)=x(k)$.  
Da qui ne esce che   
$$\overline{x}=A\overline{x}+B\overline{u}$$  
$$(I_n-A)\overline{x}=B\overline{u}$$  
$$\overline{x}=(I_n-A)^{-1}B\overline{u}$$  
Dipende dall'invertibilità ($\det\ne0$) o invece dalla singolarità ($\det=0$) della matrice $I_n-A$ l'asserire che il sistema abbia uno stato isolato di equilibrio o che invece ne abbia infiniti/nessuno.  
  
Nel caso sia invertibile, l'unico stato di equilibrio sarebbe:  
$$\overline{x}=(I_n-A)^{-1}B\overline{u}$$  
e l'uscita di equilibrio ad esso corrispondente sarebbe:  
$$\overline{y}=(C(I_n-A)^{-1}B+D)\overline{u}$$