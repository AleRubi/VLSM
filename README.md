# VLSM
Variable Length Subnet Masking e esempio in packet tracer

## Descrizione generale
Subnetting: si tratta di un approccio per suddividere una rete più grande in reti più piccole utilizzando prefissi di lunghezza variabile nell'indirizzo IP. La subnet mask determina quali bit vengono utilizzati per rappresentare l'ID di rete e quali vengono utilizzati per rappresentare l'ID host. 
VLSM (Variable Length Subnet Masking): viene utilizzato per dividere una rete già esistente in molteplici reti più piccole mediante la modifica della subnet mask. VLSM consente un utilizzo più efficiente degli indirizzi IP mediante la creazione di subnet più piccole e mirate senza la necessità di ulteriori informazioni di routing o informazioni di prefisso di rete. Ciò significa che possiamo suddividere una rete in reti più piccole, ognuna con una diversa subnet mask, per organizzare, ottimizzare e gestire meglio la rete. Però non possiamo dividerli come vogliamo, ci sono delle regole da seguire. Ecco un esempio di come si puo dividere una rete in questo modo:
---VLSM.png---

*Attenzione anche al CIDR, /31 su Cisco Packet Tracer non si riesce a realizzare!*

## Descrizione soluzione 
In questo dovevamo riprodurre su Cisco Packet Tracer un esempio di VLSM di una rete fornitoci dal prof, per riprodurre l'esempio abbiamo usato: 3 router, 6 switch e 6 PC. Fatto ciò iniziamo a collegare ogni PC con il rispettivo switch e ogni router vedrà collegarsi 3 switch, per fare ciò dovremmo aprire la GUI del router e aggiungere un'altra porta FastEthernet (CFE) così facendo riusciamo a collegare tutti gli switch. Fatto ciò ci rimane da collegare i 2 router con il terzo, in modo che quest'ultimo possa mettere in comunicazione i due, però provando a collegarli tra loro notiamo che cisco userà un cavo diverso dal solito, per risolvere questo problema ci basterà rimuovere dai 2 router tutte le porte superflue e aggiungerne un'altra del tipo FGE in modo che viene utilizzato il giusto cavo. Impostaremo poi i vari gateway, ip, subnet mask secondo l'immagine sotto riportata
---GoogleSheet.png---
Ora non rimane altro che mandare un ping da un PC ad un altro; notiamo che però quando si tenta di mandare un ping all'esterno il router ci rispedice il messaggio indietro, dobbiamo quindi settare la Routing Table dei nostri 3 router. 
---RoutingTable.png---

In "Network" dovremmo andare ad inserire l'ID di rete del PC che vogliamo raggiungere.

In "Mask" ci andrà la Subnet Mask della rete da raggiungere.

In "Next Hop" ci andrà invece il router successivo, anche in esso bisognerà andare a settare la Routing Table
