---
layout: post
title: "Post di prova"
categories: misc
---

### Introduzione

In questo post provo a riassumere **alcuni** dei più importanti concetti che discuto durante le lezioni del corso di *Fondamenti di Programmazione*. Mi sembra corretto sottolineare che questo breve documento non ha le pretese di essere esaustivo o di sostituire le lezioni e/o la lettura di un buon libro. Per imparare un linguaggio di programmazione - che alla fine, nonostante le iniziali difficoltà, risulterà particolarmente gratificante - non è importante solo conoscere la sintassi ma la creatività e la determinazione, tra le altre cose, risulteranno fattori non secondari.

### Livello 0: iniziamo

Probabilmente, al momento, il tuo livello di conoscenza del C è pari a **0** e forse è la prima volta che ti avvicini alla programmazione. A mio parere non esitono fondamentali prerequisiti per avvicinarsi alla programmazione e spero che il contenuto di questo post possa aiutarti a superare le iniziali difficoltà. Perché "Livello 0"? Il numero 0 è particolarmente importante in C. Con il tempo il tuo livello cambierà, migliorerà, grazie all'aggiunta di maggiorni competenze e lo "scostamento" (*offset*) dal livello iniziale crescerà. Tieni presente questo aspetto quando discuteremo gli *array*, in quel momento capirai che partire da 0 è particolarmente rilevante!

La prima cosa da fare per iniziare a programmare è **configurare nel tuo personal computer un ambiente di sviluppo** (IDE). Non è un'attività particolarmente complessa e il mio consiglio è di iniziare a fare un piccolo sforzo e provare a farlo in autonomia. In seguito, in un altro post, proverò a spigare passo-passo come procedere in alcune specifiche situazioni. La configurazione non è infatti indipendente dal sistema operativo e inoltre esistono tanti e diversi IDE. Per iniziare a farti un'idea ti consiglio di cercare sul web "IDE C language". Svolgere in autonomia questa fase ti consentirà di capire meglio quali sono i prerequisiti per avere un ambiente di programmazione funzionante e ti consentirà di migliorare la tua dimestichezza verso lo strumento. Se sei particolarmente pigro puoi sempre usare degli IDE (come per esempio, *replit* o *codeboard*) che funzionano direttamente dal browser e quindi già pronti all'uso.

Adesso che sei pronto prova questo "semplice" programma. Devi solo inserire queste poche righe di codice all'interno del tuo file sorgente (con estensione .c), compilarlo ed eseguirlo.

```c
//My first program
#include <stdio.h>
int main() {
  printf("Hello world");
  return 0;
}
```

Tutto dovrebbe andare a buon fine e nella finestra del terminale vedrai comparire la frase "*Hello world*". Se ciò avviene, allora complimenti, hai appena realizzato il tuo primo programma in C.

Prima di andare avanti e vedere qualcosa di decisamente più interessante proviamo a capire il significato del codice appena scritto. Un aspetto essenziale e troppo spesso trascurato in programmazione è ignorare le basi. Se ambisci a capire aspetti avanzati non puoi commettere questo errore. A tal proposito è essenziale da subito comprendere la **struttura di un programma in C**. Ora che il programma è semplice e breve questa compresensione risulta decisamente facile.

La prima riga `//My first program` rappresenta un **commento** e viene ignorata dal compilatore. Ciò nonostante i commenti sono molto importanti. Ti consentono di descrivere il funzionamento del tuo programma e saranno di enorme aiuto quando dovrai rimettere mano al codice. I commenti possono risultare utili anche in fase di debug (quando cerchi errori nel tuo codice) in quanto ti consentono di isolare alcune porzioni di codice. Per tutti questi motivi non essere avaro di commenti...

La riga `#include <stdio.h>` consente di includere una libreria esterna e quindi fornisce al tuo programma una serie di funzionalità che non devi implementare ma che sono già disponibili (*built-in*). In questo caso la libreria `stdio.h` (standard input and output) ti consente di utilizzare la funzione `printf` (ma non solo). Se non *includi* la libreria non sarà riconosciuta la funzione `printf` e quindi riceverai un messaggio di errore in fase di compilazione.

L'istruzione `printf("Hello world");` consente di stampare sullo standard output (il monitor) la frase contenuta all'interno dei `""`. Ovviamente sei libero di scrivere ciò che vuoi o che ritieni più opportuno nel contesto del tuo programma.

Adesso viene la parte più complessa di questo programma. Ogni programma scitto in C ha una **funzione principale** che si chiama `main`. So che probabilmente non sai cosa sia una funzione ma, a differenza di altri linguaggi, in C quasta non può mai mancare. Giusto per capirci, in *Python* lo stesso programma può essere scritto in una riga di codice: `print("Hello world")`. Più avanti vedremo in maggior dettaglio le funzioni, ma come dicevo in realtà le userai da subito. Qui di seguito vedi la definizione di una funzione che si chiama `main`, che non prende nessun argomento in ingresso (le parentesi `()` non contengono parametri) e che restituisce un valore intero (come indicato con `int` prima del nome della funzione e con il `return 0;` posto al suo interno):

```c
int main() {  
  return 0;
}
```

Le parentesi `{}` definiscono il *blocco* della funzione e al suo interno sei libero di inserire tutte le istruzioni che vuoi che vengano eseguite quando la funzione verrà eseguita.

### Livello 1: le variabili

Adesso sei pronto per usare le *variabili*. Pensa ad una variabile come ad un contenitore (un blocco della memoria centrale) che può contenere i dati da usare nel tuo programma. La cosa interessante è che per far riferimento a quel contenitore ci basta usare un'etichetta (nome della variabile). L'etichetta o il nome della variabile lo puoi scegliere tu a piacimento (esistono poco eccezioni) ma il mio consiglio è quello di individuare dei nomi che possano essere esplicativi di ciò che vuoi memorizzare in quella variabile.

In C, per poter usare una variabile è necessario *dichiararla* esplicitamente. In fase di dichiarazione dobbiamo indicare, oltre al nome, il *tipo*. Immagino sia abbastanza intuitivo capire che un dato può essere di diversi tipi (un carattere, un numero o altri tipi meno semplici che vedremo in seguito). **La scelta del tipo è cruciale** in quanto da tale scelta dipende *(i)* la dimensione - in byte - del blocco di memoria, *(ii)* l'insieme dei possibili valori - finiti - che la variabile potrà assumere e *(iii)* le operazioni che potranno essere eseguite su quella specifica variabile. Questo è un esempio di dichiarazione di variabile: 

```c
int number;
```

La variabile di nome `number` è di tipo `int` (intero). Quello che succede è che un blocco di memeria verrà reso disponibile (allocato) per il tuo programma e che tu potrai far riferimento a questo blocco di memoria utilizzando il nome assegnato. Ti stai chiedendo quanto è grande questo blocco di memoria e che cosa contiene? Puoi calcolare facilmente la dimensione usando una funzione *built-in* che si chiama `sizeof` e che restituisce il numero di *byte* occupati da una variabile o da (una variabile di) uno specifico *tipo*:

```c
#include <stdio.h>
int main() {
  int number;
  
  // Quanto spazio occupa la variabile number?
  printf("\nOccupa %ld byte",sizeof(number));
  //oppure
  printf("\nOccupa %ld byte",sizeof(int));
  // Che valore contiene la variabile number?
  printf("\nContiene %d",number);
}
```

Come vedi, la funzione `printf` può "stampare" a video il valore di una variabile, il risultato di un'espressione o il valore restituito da una funzione. Attraverso dei particolari caratteri (in questo caso `%ld` e `%d`), che variano a seconda del tipo di dato, è possibile "inserire" tali valori (elencati dopo la `,`) all'interno della stringa che verrà stampata a video. In questo esempio `%ld` e `%d` servono ad indicare rispettivamente un `long int` e un `int`. Il carattere `\n` consente di inserire una nuova linea e ha l'unico scopo di evitare che l'output sia tutto sulla stessa riga.
Per quanto riguarda il valore contenuto all'interno della variabile `number` invece non è possibile fare una previsione. Il contenuto (sequanza di 0 e 1) del blocco di memoria allocato per tale variabile verrà interpretato come numero intero e quindi non è possibile conoscerne in anticipo il valore. Occorre prestare massima attenzione all'uso di variabili non inizializzate (alle quali quindi non abbiamo assegnato uno specifico valore).

Torniamo alla dichiarazione di una variabile. In C esistono sostanzialmente 4 tipi base: `int` (numero intero), `float` (numero reale), `double` (numero reale con precisione doppia) e `char` (carattere). Scoprirai più avanti che è possibile definire dei nuovi tipi di dato. La scelta del tipo dipende dal contesto del nostro programma e quindi da ciò che vogliano fare con una determinata variabile.

Il C mette a disposizione degli operatori aritmetici molto intuitivi (`+`, `-`, `* ` e `/`) che possono essere utilizzati per costruire delle semplici espressioni. Il simbolo `=` viene usato come *assegnazione*, vedi esempio: 

```c
#include <stdio.h>
int main() {
  int number; //variabile di tipo intero
  long int num_byte; //variabile di tipo intero lungo 

  num_byte = sizeof(int); //alla variabile num_byte viene assegnato il valore restituito dalla funzione sizeof()
  printf("\nAn integer need %ld byte",num_byte); // il valore di num_byte viene stampato a video
}
```

Si presti massima attenzione a non confondere il simbolo di assegnazione `=` con il simbolo `==` utilizzato invece come operatore relazionale (*uguale a*). Se usi `=` al posto di `==` commetti un errore molto grave e non direttamente rilevabile in fase di compilazione. Quindi il programma funzionerà ma non farà ciò che ti aspetti... 


### Livello 2: input e output

E' evidente che il tuo programma ha necessità di comunicare con l'esterno, sia per visualizzare dei risultati (vedi `printf`) sia per prendere in ingresso dei valori. Per quest'ultima funzionalità il C mette a disposizione un'altra funzione che prende il nome di `scanf`. La funzione `scanf` è simile alla `printf` in quanto fa uso degli stessi caratteri speciali che consentono di specificare il tipo di dato e consente di inserire all'interno del programma dei valori letti dallo *standard input* (la tastiera). Vediamo un primo semplice esempio: 

```c
//Programma che calcola l'area di un rettangolo leggendo da tastiera la base e l'altezza
#include <stdio.h>
int main() {
  int base, height; //due variabili di tipo int
  printf("Insert the base: ");
  scanf("%d", &base); //carica in "base" il numero intero inserito da tastiera
  printf("Insert the height: ");
  scanf("%d", &height); //carica in "height" il numero intero inserito da tastiera
  printf("The area is: %d\n",base * height); //Calcola e stampa a video l'area del rettangolo
  printf("Memory address for base is %p and for height is: %p\n",&base, &height); //Visualizza gi indirizzi di memoria delle due variabili
}
```

Da notare che è necessario nella chiamata alla `scanf` far precedere al nome della variabile il simbolo `&`. Questo simbolo consente di far riferimento all'indirizzo di memoria della variabile. Quindi se con `base` ci riferiamo al valore, con `&base` ci riferiamo all'indirizzo di memoria. Questo aspetto è di fondamentale importanza in quanto in C il passaggio dei parametri (il meccanismo che consente di mettere in comunicazione una funzione con il `main` - o più in generale con la funzione chiamante) avviene sempre *per valore* e quindi la funzione lavora su una copia del dato e non sul dato stesso. Per consentire alla funzione `scanf` di caricare il valore letto da tastiera esattamente nella porzione di memoria usata per la variabile `base` è quindi indispensabile passare alla funzione l'indirizzo di base (`&base`) e non il suo valore (`base`). Nell'esempio i due indirizzi vengono visualizzati tramite l'uso del carattere `%p`. Successivamente riprenderemo questo discorso all'interno del post.
