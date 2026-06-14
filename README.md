# UrlTriage

UrlTriage e' un'applicazione Windows per analizzare URL e catene di redirect
in un browser isolato, raccogliere evidenze e produrre indicazioni sui domini
da bloccare, da non bloccare o da sottoporre a verifica.

L'applicazione:

- segue redirect e navigazioni controllate;
- chiude popup, banner e overlay comuni;
- acquisisce screenshot delle pagine e delle homepage dei domini osservati;
- separa nel report gli screenshot della navigazione standard da quelli dei
  domini base e li adatta alle dimensioni dello schermo;
- rileva categorie di contenuto, form sensibili e segnali di rischio;
- protegge servizi condivisi, social, URL shortener, CDN e domini noti;
- protegge i domini della Tranco Top 1M, i motori di ricerca e i principali
  servizi di tracking, spostandoli tra i domini da non bloccare;
- aggiorna automaticamente la cache Tranco e usa anche categorie, rank e data
  di creazione restituiti da VirusTotal;
- raccoglie DNS completo e informazioni RDAP/WHOIS, mostrando nel report HTML
  la motivazione della decisione per ogni dominio;
- blocca NSFW e malevolenza confermata anche quando il dominio e' popolare;
- distingue i rilevamenti VT dalle sole categorie descrittive, protegge
  `r2.dev` e blocca prudenzialmente i domini non popolari registrati da non
  oltre 15 giorni;
- segnala errori di chiave, quota, rate limit o rete VirusTotal e consente di
  interrompere l'analisi;
- mostra DNS, RDAP/WHOIS e dettagli VirusTotal anche nel riepilogo complessivo;
- puo' integrare i risultati di VirusTotal;
- genera report HTML, testuali, JSON e CSV.

## Download

Aprire la sezione [Releases](https://github.com/AlessioMobilia/UrlTriage-Releases/releases/latest)
e scegliere uno dei pacchetti:

- `UrlTriage-Setup-x64.exe`: versione consigliata, installata per il solo
  utente corrente e aggiornata automaticamente;
- `UrlTriage-Portable-win-x64.zip`: versione portable, da estrarre
  completamente prima dell'avvio.

I file `.sha256` permettono di verificare l'integrita dei download.

## Installazione

1. Scaricare `UrlTriage-Setup-x64.exe`.
2. Avviare l'installer.
3. Lasciare selezionata la creazione del collegamento sul desktop.
4. Avviare UrlTriage dal desktop o dal menu Start.

L'installazione non richiede privilegi amministrativi. Windows SmartScreen
puo' mostrare un avviso perche' il pacchetto non e' firmato digitalmente.

## Versione portable

1. Scaricare `UrlTriage-Portable-win-x64.zip`.
2. Estrarre tutto lo ZIP in una cartella.
3. Avviare `UrlTriage.App.exe`.

Non spostare il solo eseguibile: la cartella `.playwright` inclusa deve
rimanere accanto all'applicazione.

## Utilizzo

1. Incollare gli URL oppure importarli da un file.
2. Controllare gli URL estratti e scegliere quelli da analizzare.
3. Configurare il profilo e la cartella di output.
4. Inserire una chiave VirusTotal oppure disabilitare il relativo controllo.
5. Avviare l'analisi.
   L'interfaccia mostra i passaggi di navigazione, analisi locale,
   enrichment esterno e completamento.
   La chiave VirusTotal puo' essere salvata in forma cifrata per l'utente
   Windows corrente.
6. Nella scheda Analisi selezionare un dominio navigato per riaprirlo nel
   browser e completare eventuali CAPTCHA o challenge.
7. Aprire `report.html` per il report visuale o `report_rapido.txt` per il
   riepilogo testuale.

Nel report HTML gli screenshot possono essere ingranditi e sfogliati con i
pulsanti Avanti/Indietro o con le frecce della tastiera. Le informazioni
principali sono mostrate subito; form, segnali e altri dettagli sono raccolti
in una sezione espandibile.

## Output

Ogni sessione puo' includere:

- `report.html`: report completo e visuale;
- `report_rapido.txt`: riepilogo leggibile e defangato;
- `results.json`: dati strutturati della sessione;
- `to_block_domains.csv`: domini consigliati per il blocco;
- `do_not_block_domains.csv`: domini da proteggere dal blocco;
- `screenshots`: immagini raccolte durante la navigazione;
- `session.db`: stato persistente della sessione.

## Sicurezza

UrlTriage supporta il lavoro dell'analista ma non sostituisce una valutazione
umana. Eseguire l'applicazione in una VM o in un ambiente isolato quando si
analizzano URL potenzialmente malevoli. Non inserire credenziali, dati
personali o informazioni di pagamento nelle pagine visitate.
