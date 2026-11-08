# Strumenti COI Vimercate

Pagine statiche ad uso interno per i volontari dell'accoglienza e il direttivo del COI Vimercate. Nessun backend: ogni pagina legge i dati in tempo reale dai fogli Google condivisi (via CSV pubblicato) e li mostra in una vista pensata per il lavoro quotidiano.

Sito pubblicato con GitHub Pages: https://lucavanzetti.github.io/coi-vimercate-strumenti/

## Pagine

- **`index.html`** — indice con i link alle due pagine sotto.
- **`bacheca.html`** — Bacheca Contenuti: corsi, lavoro, bonus e avvisi da segnalare agli studenti. Vista elenco e vista Timeline/Gantt di cosa è attivo ora. I campi riservati (email del segnalante, note interne, ID) sono esclusi dal rendering.
- **`todolist.html`** — stato delle attività del direttivo, in sola lettura.

## Nota privacy — IMPORTANTE

Il repo è **pubblico** (necessario per GitHub Pages gratuito su piano personale) ma le pagine hanno `<meta name="robots" content="noindex, nofollow">` e c'è un `robots.txt` che blocca l'indicizzazione: non compaiono nei motori di ricerca, ma restano raggiungibili da chiunque abbia il link diretto.

`todolist.html` legge un foglio Google pubblicato **in chiaro, senza restrizioni** (il meccanismo "solo account nel dominio" di Google non è utilizzabile da una pagina statica: il browser non porta i cookie di login di Google in una richiesta fatta da un altro sito, quindi quella restrizione impediva il caricamento a tutti, non solo a chi non doveva vedere i dati). Per questo motivo il foglio sorgente è stato ripulito dai dati sensibili prima della pubblicazione:

- la colonna "Responsabile" riporta solo il **nome** (non l'email) di chi segue l'attività;
- le attività con stato "Completato" **non vengono pubblicate** nel CSV collegato alla pagina;
- la colonna "Storico" del foglio può ancora contenere note libere con nome ed email di chi ha scritto l'aggiornamento (es. `luca.vanzetti@coivimercate.org: ...`) — la pagina non la mostra, ma **chi scarica direttamente il CSV la vede**. Se possibile, evita di far comparire l'email nel testo libero dello storico (basta il nome), oppure tienila in una colonna separata esclusa dalla pubblicazione.

Il file CSV pubblicato è raggiungibile da chiunque abbia il link (nessun login richiesto): trattalo come dato pubblico e non inserire nel foglio nulla che non vorresti fosse visibile a chiunque (dati di minori, indirizzi, numeri di telefono, dati sanitari o altre categorie particolari GDPR). Condividi comunque il link della pagina solo con chi deve usarla.

## Aggiornare i link al modulo/foglio

In cima allo `<script>` di `bacheca.html` ci sono due costanti da tenere aggiornate se cambiano:

```js
const SHEET_URL = '...'; // link di modifica del foglio Google (per chi gestisce i contenuti)
const FORM_URL  = '...'; // link al modulo di segnalazione
```

## Pubblicare un aggiornamento

```bash
git add -A
git commit -m "Descrizione della modifica"
git push
```

GitHub Pages ripubblica il sito in automatico (branch `master`, root `/`) in genere entro un minuto.
