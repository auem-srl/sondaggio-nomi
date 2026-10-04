# Sondaggio sui nomi

Pagina statica del questionario. Le risposte arrivano in un Foglio Google che resta privato, nel tuo account.

Contenuto della cartella:

- `index.html`: il sondaggio.
- `config.js`: qui incolli l'indirizzo che ottieni al passo 1.
- `apps-script.gs`: il codice che scrive le risposte nel Foglio Google.

## 1. Il Foglio Google che raccoglie le risposte

1. Apri Google Fogli e crea un foglio nuovo, per esempio "Risposte sondaggio".
2. Dal menu scegli **Estensioni → Apps Script**.
3. Cancella il codice che trovi, incolla tutto il contenuto di `apps-script.gs` e premi **Salva**.
4. Premi **Distribuisci → Nuova distribuzione**. Accanto a "Seleziona il tipo" clicca l'ingranaggio e scegli **App web**.
5. Imposta **Esegui come: Me** e **Chi ha accesso: Chiunque**. Premi **Distribuisci**.
6. Google chiede l'autorizzazione: scegli il tuo account. Se compare "App non verificata", premi **Avanzate → Vai a … (non sicuro) → Consenti**. È il tuo stesso script.
7. Copia l'**URL app web**. Finisce con `/exec`.
8. Aprendo quell'URL nel browser deve comparire `{"ok":true,"info":"Il sondaggio è collegato."}`.

Se in futuro modifichi il codice dello script, devi creare una nuova distribuzione (o aggiornare la versione da **Distribuisci → Gestisci distribuzioni**), altrimenti la modifica non è attiva.

## 2. Pubblicazione su GitHub

1. Su github.com premi **New repository**. Scegli un nome neutro che non riveli l'azienda, per esempio `ricerca-nomi`. Lascialo **Public** e non aggiungere README.
2. Nella pagina del repository premi **uploading an existing file** e trascina `index.html`, `config.js` e `README.md`. Premi **Commit changes**. Puoi non caricare `apps-script.gs`.
3. Apri `config.js` dal repository, premi la matita, incolla l'URL del passo 1 tra le virgolette (`endpoint: "https://script.google.com/macros/s/…/exec"`) e premi **Commit changes**.
4. Vai in **Settings → Pages**. Sotto "Build and deployment" scegli **Deploy from a branch**, branch **main**, cartella **/ (root)**, poi **Save**.
5. Dopo circa un minuto in alto compare l'indirizzo, del tipo `https://TUO-UTENTE.github.io/ricerca-nomi/`. È quello da condividere.

## 3. Prova prima di condividere

1. Apri l'indirizzo in una finestra privata del browser.
2. Compila il questionario (puoi anche saltare le domande) fino a "Risposte inviate".
3. Controlla che nel Foglio Google, scheda **Risposte**, sia comparsa una riga. Poi cancellala.

Se la pagina dice "Risposte inviate" ma il foglio resta vuoto, la distribuzione non è su "Chiunque" oppure l'URL in `config.js` è sbagliato. Ripeti i passi 5 e 7 del punto 1.

## Leggere i risultati

Nel Foglio Google ogni riga è una persona. Per Excel: **File → Scarica → Valori separati da virgola (.csv)**. Le colonne seguono le domande D1–D21. La colonna "Ordine dei nomi" indica in quale ordine la persona ha visto i nomi nella prima parte.

## Cose da sapere

- Con GitHub gratuito il repository deve essere pubblico per usare Pages. Chi legge il codice vede nomi e domande. Il file `index.html` chiede ai motori di ricerca di non indicizzarlo.
- L'URL di `config.js` è visibile. Chiunque lo trovi potrebbe inviare risposte false. Se succede, crea una nuova distribuzione del passo 1 e aggiorna `config.js`.
- Il sondaggio non chiede nome né email. Se una persona li scrive nei campi liberi, finiscono nel foglio.
- Un invio ripetuto dalla stessa compilazione non crea doppioni.
