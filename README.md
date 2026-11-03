# Media Fusion - Applicazione Android Flutter

Un'applicazione Android moderna e performante realizzata in Flutter, suddivisa in **3 sezioni principali** accessibili dalla barra di navigazione inferiore.

---

## 📱 Struttura delle 3 Sezioni

### 1. 🎵 Media Player Multimediale Locale
Riproduce file audio e video direttamente dalla memoria interna / scheda SD dello smartphone:
- **Brani**: Elenco completo di tutti i file musicali presenti nel dispositivo, con barra di ricerca in tempo reale (per titolo o artista), copertine e durata.
- **Preferiti**: Gestione dei brani preferiti salvati in memoria locale (`SharedPreferences`). Pulsante rapido per riprodurre tutta la playlist dei preferiti o riprodurla in modalità casuale (Shuffle).
- **Album**: Visualizzazione a griglia di tutti gli album musicali rilevati sul dispositivo con copertine automatiche, conteggio tracce e pagina di dettaglio per ogni album.
- **Video**: Rilevamento automatico di file video nelle cartelle dello smartphone (DCIM, Movies, Download, WhatsApp, ecc.) con player video integrato a schermo intero (controlli touch, scrubber temporale, mute, orientamento).
- **Mini Player Persistente & Player a Schermo Intero**: Barra fluttuante con controlli di riproduzione immediati (Play/Pause, Prossimo, Preferiti) e schermata del player espansa con scrubber interattivo, shuffle, repeat e copertine ad alta risoluzione.

### 2. 📺 YouTube In-App
- Visualizzatore YouTube integrato basato su WebView Flutter ad alte prestazioni.
- Barra di navigazione dedicata con cronologia indietro/avanti, ricarica pagina, pulsante Home per tornare alla home di YouTube e indicatore di avanzamento caricamento.
- Supporto a JavaScript, riproduzione multimediale fluida e controlli touch nativi.

### 3. 🌐 Web Browser Completo
- Browser web incorporato con barra degli indirizzi intelligente (Omnibox).
- Riconosce automaticamente sia URL completi (es. `wikipedia.org`, `https://...`) sia query di ricerca testuali (reindirizza automaticamente a Google).
- Scorciatoie rapide (Speed Dial) per siti popolari (Google, Wikipedia, Reddit, GitHub, Notizie).
- Controlli completi: Indietro, Avanti, Ricarica, Home e indicatore di sicurezza SSL.

---

## 🛠️ Requisiti e Permessi Android

L'applicazione include già tutti i permessi configurati in `android/app/src/main/AndroidManifest.xml`:
- `android.permission.INTERNET` (per YouTube e Navigazione Web)
- `android.permission.READ_MEDIA_AUDIO` (Android 13+)
- `android.permission.READ_MEDIA_VIDEO` (Android 13+)
- `android.permission.READ_EXTERNAL_STORAGE` (Android 12 e versioni precedenti)
- `android.permission.WAKE_LOCK` e `android.permission.FOREGROUND_SERVICE` (per riproduzione continua a schermo spento)

---

## ☁️ Compilazione Automatica su GitHub (Senza installare Flutter in locale)

È già configurato il workflow GitHub Actions in [`.github/workflows/build-apk.yml`](.github/workflows/build-apk.yml).

### Come caricare e scaricare l'APK compilato:

1. Crea un nuovo repository su [GitHub](https://github.com/new) (es. `flutter-media-app`).
2. Trascina o carica tutti i file della cartella `flutter_media_app` sul tuo repository GitHub (inclusa la cartella nascosta `.github`).
3. Appena fatto il push, vai nella scheda **Actions** del repository su GitHub.
4. Vedrai il workflow **"Build Android APK"** partire automaticamente. Puoi anche avviarlo manualmente con il pulsante **"Run workflow"**.
5. Al termine (circa 3-4 minuti), apri la build completata e troverai nella sezione **Artifacts** il file:
   - **`MediaFusion-Android-APK.zip`**
6. Scaricalo, estrai l'APK e installalo direttamente sul tuo telefono!


1. Assicurati di avere installato l'SDK di Flutter sul computer.
2. Posizionati nella cartella del progetto:
   ```bash
   cd flutter_media_app
   ```
3. Scarica le dipendenze:
   ```bash
   flutter pub get
   ```
4. Collega uno smartphone Android (con debug USB abilitato) o avvia un emulatore Android.
5. Avvia l'applicazione:
   ```bash
   flutter run
   ```
6. Per generare l'APK finale da installare sul telefono:
   ```bash
   flutter build apk --release
   ```
   L'APK sarà disponibile in `build/app/outputs/flutter-apk/app-release.apk`.
