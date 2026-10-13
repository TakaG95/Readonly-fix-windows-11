# Sblocco sola lettura Windows

Un mio amico si è trovato con un problema singolare: tutto il PC in sola lettura. Dischi, cartelle, file. Toglieva la spunta e quella tornava. Creare una cartella nuova faceva comparire la richiesta di amministratore.

Dopo averle provate tutte, con il vibecoding ho scritto un PowerShell che sistemasse proprio questo. E ha funzionato.

Qui sotto c’è la guida breve per rilanciarlo su un altro PC Windows.

## Guida breve

Ti servono Windows 10 o 11 e questi due file, nella stessa cartella:

- `Sblocca-SolaLettura.bat`
- `Fix-SolaLettura.ps1`

1. Copiali sul PC, per esempio sul Desktop.
2. Doppio clic su `Sblocca-SolaLettura.bat`.
3. Conferma la finestra di controllo account.
4. Leggi cosa fa il programma.
5. **1. Accetto** avvia la funzione completa. **2. Rifiuto** chiude il programma senza modifiche.

La funzione completa sistema i permessi per creare cartelle e toglie la sola lettura da dischi e file. Può durare parecchio. A fine lavoro sul Desktop resta un log `Fix-SolaLettura-....log`.

Per controllare: crea una cartella sul Desktop e una in `C:`, da Esplora file, senza usare Esegui come amministratore. Poi apri un file, modificalo e salvalo.

Dentro `Windows` e `Programmi` la richiesta di amministratore resta. È la protezione di Windows, non un resto del guasto.

La casella **Sola lettura** su una cartella, in Proprietà, può tornare piena da sola. Windows la ridisegna ogni volta. Il controllo vero è sul file, o sul fatto che riesci a salvarlo.

## Disclaimer

Questo progetto non è un programma Microsoft e non è un intervento ufficiale. L’ho fatto per il PC di un amico, dopo una serie di tentativi, e su quella macchina ha risolto il problema. Un altro PC può essere bloccato per un motivo diverso.

All’avvio lo script spiega cosa fa e chiede una scelta. **1. Accetto** significa che hai letto quelle righe e sollevi l’autore da ogni responsabilità per quell’avvio, incluse perdite di dati. **2. Rifiuto** chiude il programma e non cambia nulla.

Con l’accettazione il programma può:

- cambiare i permessi, così l’account normale crea cartelle sul Desktop, in Documenti, in Download, nella radice di `C:` e sugli altri dischi
- togliere l’attributo sola lettura dai file, anche da quelli che lo erano di proposito
- azzerare `WriteProtect` nel registro, se è attivo

Non è una promessa che ogni file torni modificabile. Non apre `Windows` e `Programmi` agli utenti normali. Non sistema CD, DVD e, di base, i dischi di rete. Un criterio aziendale può rimettere i blocchi al riavvio.

Usalo solo su un computer di cui hai il permesso di modificare il sistema. Se il PC è di qualcun altro, avvisa prima.
