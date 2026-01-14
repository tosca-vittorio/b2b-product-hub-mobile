## 3. Project Overview
Una volta visti i concetti e componenti più importanti in React-Native il prossimo step è quello di impostare la mobile app: quali file e cartelle sono coinvolte e tanto altro.

Durante lo sviluppo di questo progetto si avrà l'opportunità di:
- utilizzare molti core-react-native-components (alcuni di essi sono stati trattati in precedenza) come: View, TouchableOpacity, Image, Flatlist, ScrollView, SafeAreaView, TextInput, StatusBar, and more...; 
- personalizzare la navigazione con elementi custom quali StackNavigation e TabNavigation;
- attivare e gestire routing avanzato basato su file, inclusi percorsi nidificati e dinamici;
- creare e utilizzare Hook e font personalizzati per rendere più flessibile la mobile app;
- codificare tipi e interfacce riutilizzabili con TypeScript per una migliore sicurezza dei tipi;
- sviluppare responsive react design per garantire un'ottima visualizzazione in su qualsiasi schermo;
- lavorare e usare TailwindCSS per un design pulito e scalabile;
- progettare il backend con `appwrite` per gestire dati e interazioni degli utenti;
- many other best practices;

Verranno inoltre codificate le seguenti features:
- funzione di ricerca con ottimizzazione delle prestazioni;
- recupero dei dati da un API di terze parti;
- Caricamento fluido e gestione 'aria';
- Trending movies algorithm (un algoritmo che traccia le ricerche degli utenti e aiuta a consigliare i film più popolari basati sull'attività reale degli utenti); si userà `appwrite` per memorizzare le attività degli utenti e per far lavorare l'algoritmo.

## 4. Setup

### 4.1 [Create a project](https://docs.expo.dev/get-started/create-a-project/)
Prima di iniziare la codifica e lo sviluppo della mobile app è necessario configurare l'ambiente di sviluppo.
Per creare una nuova applicazione React-Native è fortemente consigliata la consultazione della [documentazione ufficiale](https://reactnative.dev/docs/environment-setup).

Si nota l'esistenza di diversi modi per creare e inizializzare un progetto React-Native; come già accennato in precedenza, il consiglio è quello di utilizzare il Framework Expo che fornirà molte funzionalità importanti e pronte all'uso, rendendo migliore la nostra esperienza di sviluppo.

Quindi per iniziare a sviluppare un app React-Native con Expo l'unica cosa necessaria da fare è scrivere e avviare questo comando nel terminale:
```shell
npx create-expo-app@latest
```
> **Nota**: per effettuare l'installazione nella directory corrente aggiungere alla fine del comando `./`.

Questo comando scaricherà tutti i pacchetti necessari per eseguire un'applicazione React-Native e creerà la struttura di file e cartelle del progetto; nel momento in cui l'installazione viene completata è possibile eseguire l'applicazione.
Tuttavia è necessario seguire il prossimo step descritto sempre all'interno della [documentazione ufficiale](https://reactnative.dev/docs/environment-setup).

### 4.2 [**Where** would you like to develop?](https://docs.expo.dev/get-started/set-up-your-environment/?mode=expo-go#where-would-you-like-to-develop)
Adesso è necessario configurare il proprio ambiente di sviluppo: non importa quale dispositivo si sta utilizzando. In questo caso si sceglierà un **real Android Device** ma si può anche usare un **real iOS device**; si raccomanda di usare un dispositivo reale per lo sviluppo così da vedere esattamente lo stesso risultato dell'utente finale.

### 4.3 [**How** would you like to develop?](https://docs.expo.dev/get-started/set-up-your-environment/#how-would-you-like-to-develop)
Successivamente bisogna specificare un **ambiente di esecuzione** per avviare e testare l’app durante lo sviluppo. Con Expo esistono due opzioni principali, che rispondono a esigenze diverse:

* **Expo Go (sandbox)**: consente di eseguire il progetto in modo immediato all’interno dell’app Expo Go installata sul dispositivo. È l’opzione più rapida per iniziare, ideale per apprendere, prototipare e sviluppare funzionalità comuni, poiché non richiede alcuna compilazione nativa. Tuttavia, l’app viene eseguita in un ambiente “standard” e può utilizzare solo i moduli nativi già inclusi nel client Expo Go.

* **Development Build (Your app)**: consiste nel generare e installare sul dispositivo una build di sviluppo della propria applicazione, costruita specificamente per il progetto. Questa modalità è necessaria quando si vogliono integrare librerie o funzionalità che richiedono **moduli nativi personalizzati** (non presenti in Expo Go) ed è più vicina al comportamento dell’app finale. In cambio, richiede un passaggio di build e installazione (ad esempio tramite EAS).

In sintesi, **Expo Go** è preferibile nelle fasi iniziali per velocità e semplicità, mentre una **Development Build** diventa la scelta corretta quando il progetto cresce e necessita di integrazioni native avanzate.

Per questa documentazione si procederà con **Expo Go**

### 4.4 [Set up an Android device with Expo Go](https://docs.expo.dev/get-started/set-up-your-environment/#set-up-an-android-device-with-expo-go)
Per configurare un dispositivo **Android reale** con **Expo Go**, il primo passo consiste nell’installare l’app ufficiale dal **Google Play Store**. È possibile farlo in due modi:

* **Scansionando il QR code** presente nella pagina della documentazione Expo, che rimanda direttamente al download.
* In alternativa, **cercando manualmente “Expo Go”** sul Google Play Store e installandola dalla pagina ufficiale dell’app.

Una volta completata l’installazione, Expo Go sarà pronta per aprire i progetti in modalità sandbox e avviarli rapidamente durante lo sviluppo.

### 4.5 [Start developing](https://docs.expo.dev/get-started/start-developing/)
Una volta installata l'applicazione nel proprio dispositivo mobile, scelto e utilizzato per lo sviluppo, è necessario procedere con la creazione di un account.

### 4.6 [Start a development server](https://docs.expo.dev/get-started/start-developing/#start-a-development-server)
Successivamente, la prima cosa da fare è avviare un server di sviluppo eseguendo il comando:
```cmd
npx expo start
```

> **Nota**: Make sure you are on the same Wi-Fi network on your computer and your device.

### 4.7 [Open the app on your device](https://docs.expo.dev/get-started/start-developing/#open-the-app-on-your-device)
A questo punto è possibile vedere una serie di lettere diverse, all'interno della finestra di output del terminale, che consentono di fare operazioni differenti. Si procede, senza il bisogno di premere nessuna di questa lettere, scannerizzando il QRCODE con la camera del dispositivo mobile scelto durante la fase di configurazione: questo processo darà inizio al "bundling" del progetto e in un paio di secondi l'applicazione verrà eseguita all'interno del dispositivo in live.

Grazie a `React-Native + Expo` non c'è il bisogno, o l'esigenza, di fare affidamento su strumenti pesanti come Android Studio o XCode; infatti è possibile utilizzare metodi più semplici (come quello descritto fino ad ora) per sviluppare mobile-app con React-Native, che ovviamente include l'app Expo installata sul dispositivo che permette di interagire con l'applicazione mobile (cambiare tra le diverse pagine, toccare diversi elementi sullo schermo).

### 4.8 [Having problems?](https://docs.expo.dev/get-started/start-developing/#having-problems)
Se non si è riusciti a visualizzare il template standard della mobile-app probabilmente significa che si sta avendo un problema. Fortunatamente esiste una sezione dedicata all'interno della documentazione ufficiale di `React-Native + Expo` contenente diverse correzioni veloci.

> **Nota**: Make sure you are on the same Wi-Fi network on your computer and your device.

Se ancora non funziona potrebbe essere dovuto alle configurazioni router: un problema comune per le reti pubbliche. 
Su iOS si dovrebbe concedere l'autorizzazione di rete locale nell'app Expo Go o provare a usare il comando:
```cmd
npx expo start --tunnel
```

In ogni caso è fortemente consigliato leggere qualunque cosa l'app Expo Go visualizza a schermo e risolverle la problematica step-by-step.

### 4.9 [Make your first change](https://docs.expo.dev/get-started/start-developing/#make-your-first-change)
Adesso ci si prepara ad effettuare il primo cambiamento della mobile-app. In particolare si vuole cambiare il contenuto testuale "Welcome!", dell'elemento <ThemedText>, presente in **app/(tabs)/index.tsx**; le modifiche avvengono istantaneamente.

In questo modo si ha una prova concreta e valida del collegamento stabilito tra il codice e la mobile-app che vive sul nostro dispositivo.

### 4.10 Struttura file e folder
È fondamentale avere una comprensione migliore riguardo ai file e alle cartelle all'interno progetto in modo da essere più sicuri quando si apportano modifiche alla codebase e alla mobile app in un secondo momento.

#### 4.10.1 tsconfig.json
Cominciando dal basso verso l'altro, il primo file è **tsconfig.json**. Contiene le regole che TypeScript utilizzerà per imporre la sicurezza dei tipi in tutto il progetto.

#### 4.10.2 README.md
Il file README.md è un file di testo contenente alcuni informazioni riguardanti il progetto. 

#### 4.10.3 package-lock.json + package.json
Contengono le dipendenze del progetto, degli script e ulteriori metadati.

#### 4.10.4 app.json
Questo file Json contiene le opzioni di configurazione per il progetto e spesso viene chiamata "configurazione dell'app". Queste opzioni cambiano il comportamento del progetto durante lo sviluppo, l'invio e l'aggiornamento della mobile-app.

Tutto inizia con un oggetto expo che rappresenta l'oggetto radice contenente tutta la configurazione dell'app, quindi si avrà:
- **"name"**: Rappresenta l'app-name mostrato nella home screen, molto importante nel caso in cui si vuole renderlo personalizzato.
- **"slug"**: Rappresenta l'unico identificativo del progetto utilizzato da Expo quando si definisce l'URL, nel momento in cui si vuole pubblicare il progetto sul web.
- **"version"**: Rappresenta la versione del progetto
- **"orientation"**: Definisce se la mobile-app dovrebbe inizialmente aprirsi in verticolare "(ritratto/portrait)", "orizzontale (landscape)" oppure nella modalità di orientamento predefinita.
- **"icon"**: Rappresenta il path/percorso completo dell'immagine che si vuole visualizzare
- **"scheme"**: Rappresenta un URL personalizzato per abilitare deep linking, in questo caso lo si imposta "products"; in questo modo, più avanti, si potrà utilizzare una sintassi del tipo "products://path".
- **"userInterfaceStyle"**: Questo determina la modalità scusa o chiara; lo si può lasciare in "automatic".
- **"newArchEnabled"**: Consente l'adozione/l'utilizzo della nuova architettura di React-Native per prestazioni migliori, ottenendo anche le più recenti funzionalità di React come le transizioni animate; Expo supporta nativamente e immediatamente questa nuova architettura.
- **"ios"**: Rappresenta le caratteristiche specifiche da estendere, in particolare, su dispositivi iOS. Ad esempi, si può definire il supporto per dispositivi tablet ("supportsTablet").
- **"android"**: Rappresenta le caratteristiche specifiche da estendere, in particolare, su dispositivi Android; come "adaptiveIcon", quindi path di immagini ("foregroundImage","backgroundImage","monochromeImage"), sfondi colorati ("backgroundColor") e altro.
- **"web"**: Rappresenta le caratteristiche specifiche/opzioni aggiuntive da estendere, in particolare per il Web.

#### 4.10.5 .gitignore
Questo file permette di ignorare alcune variabili d'ambiente e in generale tutto ciò che non vogliamo versionare con Git.

#### 4.10.6 scripts (folder)
Inizialmente la cartella scripts contiene solo il file "reset-project.js" che permette di reimpostare il progetto su il codice minimo indispensabile.

#### 4.10.7 hooks (folder)
Nella cartella hooks si trovano hooks personalizzati.

#### 4.10.8 constants (folder)
In questa specifica cartella risiedono le costanti.

#### 4.10.9 components (folder)
Questa cartella contiene i componenti.

#### 4.10.10 assets (folder)
Contiene le risorse del progetto come ad esempio Fonts e Immagini

#### 4.10.11 app (folder)
La cartella app permette di indirizzare verso schermate/pagine diverse (similmente a Next.js). All'interno di questa cartella vi è una sub-folder chiamata "(tabs)" che rappresenta i gruppi di schede dell'applicativo mobile per gestire i relativi layout.