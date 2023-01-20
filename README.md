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



