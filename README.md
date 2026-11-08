# Strumenti COI Vimercate

Pagine statiche ad uso interno per i volontari dell'accoglienza e il direttivo del COI Vimercate. Nessun backend: ogni pagina legge i dati in tempo reale dai fogli Google condivisi (via CSV pubblicato) e li mostra in una vista pensata per il lavoro quotidiano.

Sito pubblicato con GitHub Pages: https://lucavanzetti.github.io/coi-vimercate-strumenti/

## Pagine

- **`index.html`** — indice con i link alle due pagine sotto.
- **`bacheca.html`** — Bacheca Contenuti: corsi, lavoro, bonus e avvisi da segnalare agli studenti. Vista elenco e vista Timeline/Gantt di cosa è attivo ora. I campi riservati (email del segnalante, note interne, ID) sono esclusi dal rendering.
- **`todolist.html`** — stato delle attività del direttivo, in sola lettura.

## Nota privacy — IMPORTANTE

Il repo è **pubblico** (necessario per GitHub Pages gratuito su piano personale) ma le pagine hanno `<meta name="robots" content="noindex, nofollow">` e c'è un `robots.txt` che blocca l'indicizzazione: non compaiono nei motori di ricerca, ma restano raggiungibili da chiunque abbia il link diretto.

`todolist.html` mostra nomi ed email dei volontari/direttivo presi dal foglio Google collegato. Il foglio è ora pubblicato con restrizione "solo account nel dominio" (verificato: richiesta anonima → `401`), quindi i dati si caricano solo per chi è collegato nel browser con un account `@coivimercate.org`; a chiunque altro la pagina mostra un errore di accesso. Resta comunque buona norma condividere il link solo con chi deve usarlo.

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
