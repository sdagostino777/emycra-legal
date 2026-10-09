# Pagine legali di Emycra — come pubblicarle

Questa cartella contiene le pagine legali dell'app, in HTML statico. Non hanno risorse
esterne — un solo `style.css` accanto — quindi si aprono anche da `file://` e si possono
ospitare ovunque, senza build e senza dipendenze.

Serve pubblicarle perché **App Store Connect pretende un URL pubblico** per l'informativa
sulla privacy (obbligatorio in ogni localizzazione) e per l'URL di supporto. Le pagine
dentro l'app non bastano: Apple vuole poterle aprire dal browser.

---

## I file

Per **ognuna delle cinque lingue** (it, en, es, de, fr) ci sono quattro pagine. L'italiano
non ha suffisso; le altre lingue hanno il codice ISO.

| Lingua | Privacy | Termini | Avvertenza | Indice |
| :--- | :--- | :--- | :--- | :--- |
| Italiano | `privacy.html` | `terms.html` | `disclaimer.html` | `index.html` |
| Inglese | `privacy.en.html` | `terms.en.html` | `disclaimer.en.html` | `index.en.html` |
| Spagnolo | `privacy.es.html` | `terms.es.html` | `disclaimer.es.html` | `index.es.html` |
| Tedesco | `privacy.de.html` | `terms.de.html` | `disclaimer.de.html` | `index.de.html` |
| Francese | `privacy.fr.html` | `terms.fr.html` | `disclaimer.fr.html` | `index.fr.html` |

Più `style.css`, condiviso da tutte le pagine, e questo `README.md`.

Ogni pagina ha in fondo il collegamento alle altre tre della **stessa lingua** e alle
quattro lingue alternative: chi arriva dalla scheda tedesca resta in tedesco.

**Il link all'EULA di Apple** (`https://www.apple.com/legal/internet-services/itunes/dev/stdeula/`)
sta nella sezione 7 dei *termini* di tutte e cinque le lingue. Non è decorativo: la stessa
voce deve comparire **anche nella Descrizione** della scheda App Store, altrimenti la
revisione si ferma (linea guida 3.1.2). È il rifiuto già preso una volta: non rimuoverlo.

---

## Dove pubblicarle: GitHub Pages

È il modo già collaudato sull'altra app dello stesso sviluppatore, che ha un repository
dedicato alle sole pagine legali. Per Emycra si fa la stessa cosa con un repository
separato — così le pagine legali hanno una storia di modifiche propria e non si mescolano
al codice dell'app.

1. Crea un repository **pubblico** chiamato `emycra-legal` sull'account GitHub dello
   sviluppatore (`sdagostino777`).
2. Da questa cartella:

   ```bash
   cd /Users/simonedagostino/Documents/DeepSeek/APP/Emycra/Store/legal
   git init
   git add .
   git commit -m "Pagine legali di Emycra"
   git branch -M main
   git remote add origin https://github.com/sdagostino777/emycra-legal.git
   git push -u origin main
   ```

3. Su GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: `main` /
   `/ (root)` → Save**. Dopo un minuto le pagine rispondono.
4. L'indirizzo diventa:

   ```
   https://sdagostino777.github.io/emycra-legal/            → index.html (italiano)
   https://sdagostino777.github.io/emycra-legal/privacy.html
   https://sdagostino777.github.io/emycra-legal/privacy.en.html
   ```

   e così via per le altre lingue.

Gli aggiornamenti si fanno con un commit: Pages ricostruisce da solo. HTTPS è incluso e
non c'è niente da pagare.

### Le alternative

- **Netlify o Cloudflare Pages** — trascini la cartella nel browser e ottieni l'URL. Utile
  se vuoi collegare in seguito un dominio tuo.
- **Dominio proprio** — se un giorno esiste un sito di Simone D'Agostino, i file vanno in
  una sottocartella. L'unica cosa che conta è che gli URL rispondano in HTTPS.

---

## Cosa fare dopo la pubblicazione

1. **Apri ogni URL** e controlla che la pagina si veda con lo stile giusto (fondo scuro,
  testo leggibile): se il CSS non carica, il percorso di `style.css` è sbagliato.
2. **Incolla gli URL** nei file di `Store/metadata/`: al posto dei segnaposto
  gli indirizzi sono già quelli veri: https://sdagostino777.github.io/emycra-legal/
   Finché restano segnaposto, la scheda **non si può inviare**.
3. **In App Store Connect**, nella scheda della versione, compila *URL di supporto* e
   *URL per l'informativa sulla privacy* **per ciascuna delle cinque localizzazioni**,
   usando la pagina della lingua corrispondente (non l'inglese per tutte).
4. Aggiorna la data in cima alle pagine quando cambi qualcosa di sostanziale.

---

## Prima di pubblicare: tre controlli

- L'indirizzo postale nei documenti è `Calle Ollerías 20, 29012 Málaga, Spagna`: deve
  corrispondere a quello dichiarato all'Apple Developer Program e alla normativa DSA.
  Se cambia, va aggiornato in **tutte e venti** le pagine.
- L'email di contatto è `dagostino.simone@icloud.com`: è quella che risponde, e deve
  restare valida per tutto il tempo in cui l'app è in vendita.
- I termini dicono che l'app **non è un dispositivo medico**, che i dati restano sul
  dispositivo e che l'app **non fa richieste di rete**: se un giorno il comportamento
  dell'app cambia, queste pagine vanno riscritte **prima** di pubblicare la versione
  nuova, non dopo.

---

## Nota sulla lingua

Le pagine sono scritte a mano in italiano, inglese, spagnolo, tedesco e francese. Se
modifichi una lingua, controlla le altre quattro: i documenti devono continuare a dire le
stesse cose, perché la revisione Apple confronta la descrizione della scheda con le
pagine collegate e con il comportamento reale dell'app.
