# Cronoteca — guida a hosting e pubblicazione

## Cosa c'è in questa cartella
- `index.html` — l'app (curiosità locali + estensione Wikipedia + barra laterale trascinabile)
- `manifest.json` — rende l'app installabile come PWA
- `sw.js` — service worker per funzionamento offline di base
- `icons/` — icone dell'app in varie dimensioni

## Passo 1 — Ospitarla online (obbligatorio per tutto il resto)
Consigliato: **GitHub Pages** (gratis per sempre, standard, niente limiti di tempo).

1. Crea un repository pubblico su github.com (es. `cronoteca`)
2. Carica tutti i file di questa cartella (mantenendo la struttura: `index.html`, `manifest.json`, `sw.js`, `icons/`) nella root del repository
3. Impostazioni del repository → Pages → Source: `main` branch, cartella `/ (root)`
4. Dopo un minuto l'app sarà live su `https://TUO-USERNAME.github.io/cronoteca/`

Da lì Wikipedia dovrebbe caricarsi normalmente (niente più blocco da `file://`).

## Passo 2 — Installabile oggi stesso, senza store
Una volta online, aprendo il link da telefono (Android o iOS) e scegliendo
"Aggiungi a schermata Home" dal menu del browser, l'app si installa con la
sua icona, a schermo intero, senza passare da nessuno store. Gratis, immediato,
nessuna revisione da aspettare.

## Passo 3 — Google Play Store
1. Vai su **pwabuilder.com**, incolla l'URL di GitHub Pages, clicca "Start"
2. Clicca "Package for stores" → Android
3. Serve un account sviluppatore Google Play (25$, una tantum): https://play.google.com/console/signup
4. PWABuilder genera un pacchetto (.aab) firmato tramite Trusted Web Activity
5. Va verificato un file `assetlinks.json` nel tuo sito per confermare che l'app Android "appartiene" al tuo dominio — PWABuilder spiega passo passo come generarlo
6. Carichi il pacchetto sulla Google Play Console e invii per la revisione

Nota tecnica (ottobre 2026): Google richiede che le nuove app puntino ad
Android 16 (API level 36). PWABuilder/Bubblewrap dovrebbe già gestirlo, ma
controlla che il pacchetto generato lo rispetti prima di inviarlo.

## Passo 4 — Apple App Store: nota onesta
A differenza di Google, **Apple non accetta semplici PWA "impacchettate"**:
è una politica attuale, non un dettaglio tecnico risolvibile con uno strumento.
Per arrivare sull'App Store servirebbe trasformare l'app in un progetto
nativo o ibrido vero (es. con Capacitor), aggiungendo funzionalità native
reali, oltre a: un Mac con Xcode, un account Apple Developer (99$/anno), e
superare la revisione Apple. È un progetto a parte, non un'estensione di
questo pacchetto — fammi sapere se vuoi che lo affronti.
