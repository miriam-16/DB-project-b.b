# DB-project-b.b
Progetto consistente nel creare un database per servizio di affitto di alloggi
# 1. Progettazione concettuale
## 1.1 Requisiti iniziali
Si vuole realizzare una base di dati per un servizio che permette di affittare e prenotare alloggi di vario tipo ad esempio interi appartamenti, stanze private (con camera privata e spazi in comune) e stanze condivise (spazi e camere condivise).
Gli utenti si registrano al servizio fornendo indirizzo email, password, nome, cognome, numero o numeri di telefono. Se l’utente fornisce la foto della carta d’identità, viene riconosciuto come verificato. Inoltre, l’utente deve indicare un metodo di pagamento per poter prenotare. Gli utenti possono essere ospiti o “host” ovvero possono a loro volta ospitare altri utenti del servizio in uno o più alloggi di loro proprietà. Inoltre gli “host” possono diventare “superhost” se soddisfano i seguenti requisiti: 
- Devono aver completato almeno 10 soggiorni, per un totale di almeno 100 notti. 
- Devono aver conservato un tasso di cancellazione dell'1% (una cancellazione ogni 100 prenotazioni) massimo. 
- Devono aver mantenuto una valutazione complessiva di 4,8 considerando tutti i soggiorni in tutte le case di sua proprietà. 
Gli utenti superhost ricevono un badge sul loro profilo.

Gli alloggi sono descritti indicando un nome, l’indirizzo (visibile all’ospite solo quando la prenotazione è confermata, altrimenti è visibile solo il comune), una descrizione, il prezzo per notte per persona e i costi di pulizia, delle foto, i servizi (ad esempio, cucina, wi-fi, lavatrice, ecc.), numero di letti, _numero di ospiti, numero di bagni_, orario di check-in e check-out oltre all’host a cui appartiene, il rating medio, il numero di recensioni _e le recensioni stesse, inclusi la media di voti ottenuti in campi come qualità/prezzo, comunicazione, posizione e pulizia_.

Gli utenti possono aggiungere alcune case tra i preferiti. Gli utenti possono avere diverse liste, ad esempio in base al viaggio che vogliono compiere. 

Gli utenti possono prenotare degli alloggi di qualsiasi tipo indicando un intervallo di date per il soggiorno e il numero degli ospiti. Se gli ospiti sono a loro volta utenti del servizio, se ne possono indicare i nominativi. La prenotazione deve essere confermata o rifiutata dall’host. La prenotazione ha un costo totale e se confermata viene eseguito il pagamento. Inoltre, la prenotazione può essere cancellata sia dall’ospite che dall’host.

Al termine del soggiorno, gli ospiti e gli host si possono valutare a vicenda. La recensione fatta dagli ospiti comprende due testi (uno per l’appartamento e uno per l’host) e una serie di punteggi in una scala da 1 a 5 su dimensioni come pulizia, comunicazione, posizione, qualità/prezzo. La valutazione complessiva del soggiorno è una media delle valutazioni ricevute sulle singole dimensioni. Le recensioni degli host comprendono solo un commento testuale. Le recensioni possono essere visibili o non visibili. Diventano visibili quando entrambi hanno fatto la recensione oppure se uno dei due non ha fatto la recensione, l’altra diventa visibile dopo 7 giorni dalla fine del soggiorno. Gli host e gli ospiti possono commentare più volte le review in cui sono coinvolti, creando un thread di discussione. Le recensioni sono visibili sui profili degli utenti suddivise in base a quelle ricevute come ospite e come host.

La base di dati deve supportare le seguenti operazioni: 
- Una volta a settimana viene effettuato un calcolo per aggiornare il tasso di cancellazione di ciascun host. 
- Una volta al giorno si controllano le condizioni per la qualifica di superhost e viene aggiornato lo status degli host. 
- Una volta al mese viene calcolata la classifica degli alloggi più graditi.


## 1.2 Glossario termini
Termine|Descrizione|Sinonimi|Collegamenti
:----:|:-----:|:-----:|:-----:
Utenti|Soggetti che affittano alloggi|Ospiti|Prenotazione, Commenti, Recensioni
Host|Utenti che mettono a disposizione alloggi|Proprietario|Alloggio, Prenotazione
Alloggi| Alloggi offerti dall'host<br/> in cui l'ospite risiederà| Case, appartamenti | Prenotazioni, Host, Utenti
Prenotazione | Informazione sull'occupazione<br/>dell'alloggio | | Utenti, Alloggi
Recensione| Valutazione del soggiorno<br/>secondo vari criteri| Review, Commenti testuali, testi | Utente, Host, Alloggio, Commento
Commento| Risposta alle recensioni||Recensioni, Utenti

## 1.3 Requisiti rivisti e strutturati in gruppi di frasi omogenee
### Frasi di carattere generale
Si vuole realizzare una base di dati per un servizio che permette di affittare e prenotare alloggi.

### Frasi relative agli alloggi
Per gli alloggi rappresentiamo nome, indirizzo (visibile all'ospite solo quando ha confermato la prenotazione, altrimenti si indica il comune), descrizione dell'alloggio, prezzo per notte e costi di pulizia a persona, foto dell'alloggio, numero di letti, numero di ospiti, numero di bagni, servizi che offre, orario check-in e check-out, rating medio alloggio, numero di recensioni che ha riceuto l'alloggio da parte degli utenti, nonché le recensioni stesse. 

Ci sono vari tipi di alloggi:
- appartamenti interi
- stanze private (camera privata e spazi comuni)
- stanza condivisa (spazio in comune e camera condivisa)

### Frasi relative agli utenti
Per gli utenti rappresentiamo indirizzo email, password, nome, cognome. Possono aggiungere numero/i di telefono, metodo/i di pagamento (necessario per poter prenotare), carta di identità (per risultare verificato), una foto e una breve descrizione.
Bisogna rappresentare anche il numero di recensioni ricevute e le recensioni stesse.
Gli utenti possono inserire degli alloggi in liste da loro create. 
Gli utenti possono evelversi in host.

### Frasi relative a tipi specifici di utente (host)
Per gli utenti che sono host, bisogna rappresentare gli alloggi di sua proprietà. Gli host possono diventare superhost.

### Frasi relative a tipi specifici di host (superhost)
Per i superhost, bisogna rappresentare il badge sul loro profilo. Un host può ottenere il titolo di superhost se sono soddisfatte tali condizioni:
- Devono aver completato almeno 10 soggiorni, per un totale di almeno 100 notti. 
- Devono aver conservato un tasso di cancellazione dell'1% (una cancellazione ogni 100 prenotazioni) massimo. 
- Devono aver mantenuto una valutazione complessiva di 4,8 considerando tutti i soggiorni in tutte le case di sua proprietà. 

### Frasi relative alle prenotazioni
Per le prenotazioni rappresentiamo intervallo di date per il soggiorno, numero ospiti, costo totale, l'alloggio in cui si risiederà, l'utente che effettua la prenotazione e gli eventuali utenti che partecipano alla prenotazione. 
Lo stato della prenotazione può essere accettata o rifiutata. 

### Frasi relative a tipi specifici di prenotazioni (accettata)
Per le prenotazioni accettate rappresentiamo la data di addebito del costo totale della prenotazione. 

### Frasi relative a tipi specifici di prenotazioni (rifiutata)
Per le prenotazioni rifiutate rappresentiamo la data di invio del rifiuto.

### Frasi relative e tipi specifici di prenotazioni accettate
Per le recensioni acettate che vengono rifiutate, bisogna rapprensentare la data d'invio della cancellazione e colui che la disdice, in quanto può essere l'host o l'utente che l'ha effettuata.

### Frasi relative alle recensioni
Per le recensioni, possiamo rappresentare data e autore.
Le recensioni possono essere visibili o no:
- sono visibili quando:
	- entrambi hanno fatto la recensione
	- trascorsi 7 giorni e una delle parti ha recensito
Le recensioni si dividono in recensioni verso ospite, recensioni verso l'host, recensioni verso l'alloggio.

### Frasi relative a tipi specifici di recensioni (recensione_verso_alloggio)
Per le recensioni sull'alloggio bisogna rapprensentare un testo sull'alloggio e i punteggi da 1 a 5 totalizzati per categorie come pulizia, comunicazione, posizione, qualità/prezzo.

### Frasi relative a tipi specifici di recensioni (recensione_verso_host)
Per le recensioni da parte dell'ospite bisogna rappresentare una recensione testuale sull'host.

### Frasi relative a tipi specifici di recensioni (recensione_verso_ospite)
Per le recensioni da parte dell'host bisogna rappresentare una recensione testuale sull'ospite.

### Frasi relative a commento
Per i commenti bisogna rapprensentare la data in cui è stato effettuato il commento, il testo riportante e l'autore.

## 1.4 Business Rules
### Dizionario dei dati (Entità)
![alt text][[(https://github.com/miriam-16/DB-project-b.b/blob/main/Immagini/Pasted%20image%2020220617202038.png)|550]]
<br>
![[Pasted image 20220617202053.png|550]]  


### Dizionario dati (Relazioni)
![[Pasted image 20220609171920.png|550]]


## Vincoli di integrità
- La somma del numero di ospiti per prenotazione di un alloggio non può superare il numero di ospiti consentito per alloggio per una stessa data;
- _data_arrivo_(prenotazione) deve essere minore di _data_partenza_(prenotazione); 
- _data_recensione_ è deve essere maggiore rispetto a  _data_partenza_(prenotazione);
- _data_commento_(commento) deve essere maggiore di _data_recensione_(recensione);
- _data_addebbito_, _data_rifiuto_ e _data_cancellazione_ non possono essere superiori a _data_arrivo_(prenotazione);
- la recensione verso l'host e verso l'alloggio può essere scritta solo dall'ultente che ha effettuato la prenotazione;
- in _recensione_verso_alloggio_, i voti per valutare l'alloggio vanno da 1 a 5;
- il thread di commenti riguarda esclusivamente l'ospite e l'host per un determinato soggiorno;
- l'utente può scrivere una recensione entro 14 giorni da _data_partenza_(prenotazione).

### Vincoli di derivazione
- _rating_medio_(alloggio) è la media aritmetica dei voti ricevuti dagli ospiti tramite le recensioni;
- _costo_totale_(prenotazione) si ottiene da (_prezzo_notte_+ _prezzo_pulizia_)$\times$ _numero_ospiti_prenotazione_;
- _numero_recensioni_(alloggio) si ottiene dalle occorrenze dell'associazione voto con recensioni;
- _n_recensioni_ricevute_(utente) si ottiene dalle occorrenze di valutazione.

# 2 Progettazione logica
## 2.1 Tavola dei volumi
Nome|Tipo|Volume|Descrizione
:---:|:---:|:---:|:---:
Utente|E|$2\,000\,000$|Supponiamo che ci saranno 2 milioni 
Host|E|$500\,000$|Supponiamo che sui 2 milioni di utenti solo 500 mila saranno host e gli altri ospiti
Superhost|E|$50\,000$|Su 500 mila host, abbiamo pensato che 50 mila saranno superhost
Alloggio|E|$1\,000\,000$|Ogni host, compresi i superhost, ha almeno 2 alloggi 
Appartamento|E|$600\,000$|Gli appartamenti sono il 60% degli alloggi
Stanza privata|E|$300\,000$|Le stanze private sono il 30% degli alloggi
Stanza condivisa|E|$100\,000$|Le stanze condivise sono il 10% degli alloggi
Prenotazione|E|$24\,000\,000$|Abbiamo supposto che ogni utente fa almeno 2 prenotazioni al mese
Prenotazione Rifiutata|E|$480\,000$|Su 24 milioni di prenotazioni, il 5% vengono rifiutate
Prenotazione Accettata|E|$23\,520\,000$|Il 95% delle prenotazioni vengono accettate
Prenotazione Cancellata|E|$470\,400$|Il 5% delle prenotazioni accettate vengono cancellate
Recensione|E|$67\,032\,000$|Ogni prenotazione accettata ha 3 recensione, ma supponiamo che almeno il 5% degli utenti non lascerà una recensione
Recensione_verso_host|E|$23\,461\,200$|Tutti gli utenti lasciano una prenotazione sull'host
Recensione_verso_utente|E|$20\,109\,600$|Il 95% degli host lascia una recensione all'utente
Recensione_verso_alloggio|E|$23\,461\,200$|Tutti gli utenti lasciano una prenotazione sull'alloggio
Commento|E|$40\,386\,780$|Supponiamo che il 90% degli utenti risponda alla recensione dell'host e che il 95% degli host risponda alla recensione degli utenti
Proprietario|R|$1\,000\,000$|É il massimo tra il volume di host e il volume di alloggio
Preferiti|R|$6\,000\,000$|É il massimo tra il volume di alloggio e il volume di utente
Ordine|R|$24\,000\,000$|É il massimo tra il volume di utente e il volume di prenotazione
Partecipazione|R|$36\,000\,000$|É il massimo tra il volume di utente e il volume di prenotazione, quando un utente partecipa ad una prenotazione 
Luogo|R|$24\,000\,000$|É il massimo tra il volume di alloggio e il volume di prenotazione
Voto|R|$23\,461\,200$|É il massimo tra il volume di prenotazione e il volume di alloggio
Valutazione|R|$67\,032\,000$|É il massimo tra il volume di utente e il volume di recensione
Thread|R|$40\,386\,780$|É il massimo tra il volume di recensione e il volume di commento
Risposta|R|$40\,386\,780$|É il massimo tra il volume di utente e il volume di commenti, quando l'utente commenta la recensione dell'altro

## 2.2 Tavola delle operazioni

Operazione|Tipo|Frequenza| Motivo
:----|:----:|:-----:|:----
1: Osservare un alloggio|I|$7\,200\,000$/giorno|Supponiamo che il 60% degli utenti sia attivo e controlli in media 6 alloggi al giorno
2: Controllo prezzo totale della prenotazione|I|$140\,000$/giorno|Calcolo derivato dalla visualizzazione al giorno di $24\,000\,000$ prenotazione (considerando ripetizioni)
3: Visualizzare rencensioni di un alloggio|I|$12\,500$/giorno|Calcolo raggiunto facendo una stima sulle prenotazioni al giorno e sui commenti  
4: Registrazione di un nuovo utente|I|397/giorno|Mediante calcoli temporali basati sull'esampio di airb&b, abbiamo ottenuto il seguente risultato
5: Aggiunta di un nuovo alloggio|I|198/giorno|Partendo dal numero di alloggi stimati, abbiamo ricavato gli alloggi che vengono aggiunti al database su base giornaliera
6: Rendere visibili le recensioni|I|3/giorno|Si suppone che la maggior parte delle recensioni vengano caricate sulla piattaforma in tre fasce orarie maggiori
7: Controllare condizioni per la qualifica di superhost ed eventuale aggiornamento|I|1/giorno|Da testo
8: Calcola tasso cancellazione di ciascun host|B| 1/settimana|Da testo
9: Aggiornare il rating medio dell'alloggio|B|1/settimana|Ritenuta un'operazione rilevante
10: Calcolo classifica degli alloggi con<br/> valutazione più alta|B|1/mese|Da testo

## 2.3 Ristrutturazione dello schema E-R
### 2.3.1 Analisi delle ridondanze
Nello schema E-R vi sono delle ridondanze:
- attributi derivabili da altre entità
	- _costo_totale_(prenotazione) si può ottenere da $(prezzo\_notte + prezzo\_pulizia) \times numero\_ospiti$(alloggio)
	- _rating_medio_(alloggio) si può ottenere dalla media $\frac{voto\_qp + voto\_pulizia + voto\_comunicazione + voto\_posizione}{numero\_recensioni\_verso\_alloggio}$(recensione_alloggio)
- attributi derivabili da un conteggio
	- _n_rec_ricevute_(utente) è deducibile dal conteggio delle occorrenze di _recensione_verso_ospite_ (+ _recensione_verso_host_ se l'utente è anche host);
	- _numero_recensioni_(alloggio) è deducibile dalle occorrenze di _recensione_verso_alloggio_
- ridondanza dovuta a cicli
		-  l'entità _utente_ è collegata a recensione e a commento, e queste ultime tra di loro sono collegate

#### Analisi di una ridondanza
##### Schema di navigazione
![[Pasted image 20220617004235.png|550]]

Concetto|Tipo|Volume
----|:-----:|:----
Prenotazione|E|$24\,000\,000$
Alloggio|E|$1\,000\,000$
Luogo|R|$24\,000\,000$


##### Tavola degli accessi 
Operazione: Controllo prezzo totale della prenotazione($140\,000$/giorno).
###### Presenza di ridondanza
![[Pasted image 20220617004631.png|550]]

Concetto|Costrutto|Accessi|Tipo
----|----|---|---
Prenotazione|E|1|L


###### Assenza di ridondanza
![[Pasted image 20220617004511.png|550]]

Concetto|Costrutto|Accessi|Tipo
----|------|-----|-----
Prenotazione|E|1|L
Alloggio|E|1|L
Luogo|R|1|L

Operazione con ridondanza:
- accessi in lettura $140\,000$

Operazione senza ridondanza:
- accessi in lettura $420\,000$

#### Costo aggiuntivo in termini di spazio (con ridondanza)
- Ipotizziamo che costo_totale venga memorizzato in 4 byte.
- Spazio totale necessario : 4 * $140\,000$ = $560\,000$ byte( circa 560KB)

Con ridondanza|Senza ridondanza
-------|-------
$140\,000$|$420\,000$
560 KByte di spazio aggiuntivi|0 Mbyte di spazio aggiuntivi

Dati i risultati ottenuti, è evidente che conviene mantenere la ridondanza, se si considera tale operazione che riguarda solo la lettura, in caso di scrittura è meglio rimuovere l'attributo. 

### 2.3.2 Eliminazione delle generalizzazioni
Nel nostro schema E-R sono presenti sei generalizzazioni.
- Le generalizzazioni _host_ e _superhost_ sono state accorpate all'entità padre _utente_, così da ridurre il numero di accessi e poter distinguere ogni categoria inserendo l'attributo _tipo_;
- Le generalizzazioni di _alloggio_ sono state accorpate all'entità padre in quanto gli accessi ad alloggio e ai suoi tipi sono contestuali. Anche qui, l'aggiunta dell'attributo _tipo_ consente di distinguere i diversi modelli di alloggio;
- La generalizzazione di _prenotazione_ è stata accorta al padre, mentre la generalizzazione di _accettata_ è diventata una relazione, per distinguere i vari stati che la prenotazione può avere e distinguere i casi in cui la prenotazione è cancellata dall'host o dall'ospite;
- la generalizzazione di _recensioni_ è stata accorpata al padre per ridurre gli accessi, al costo di aumentare il numero di attributi nulli. Questa implementazione ci garantisce di distiguere i vari tipi di prenotazione mediante l'aggiunta dell'attributo _tipo_recensione_ e l'attributo giudizio che cambia in base al tipo selezionato. 

### 2.3.4 Analisi delle ridondanze
Viene introdotto l'attributo _codice_prenotazione_ in prenotazione, per poter sostuire la chiave composta dapprima selezionata, in quanto non semplice, nonostante identifichi un'entità al quanto importante se non essenziale all'interno del database. 
Introdotto inoltre _codice_alloggio_, per rimuovere l'utilizzo dell'indirizzo come identificazione dell'alloggio, in quanto attributo non immediato. 
Utile inserire le chiavi _id_recensione_ in recensione e _id_commento_ in commento per non usare chiavi composte non immediate. 







