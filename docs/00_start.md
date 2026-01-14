## 0. Intro
L'esistenza di **React Native** rende React una delle competenze più preziose che si possano apprendere, poiché circa il **75% di ciò che si sa già** sulla creazione di siti web si trasferisce allo sviluppo mobile. Attualmente, React Native è paragonabile a **Next.js per il mobile**, permettendo di gestire routing basato su file, architettura guidata dai componenti e persino **React Server Components**. 

In questo corso imparerai a costruire un app cinematografica completa con una funzione "top trends" alimentata da un algoritmo scritto con lo strumento open source **Appwrite**. Imparerai anche la navigazione a schede personalizzata, una schermata di ricerca e una pagina dei dettagli del film per ottenere tutte le informazioni necessarie. 

Questo corso non tratta solo la creazione di un app, ma anche come crearla nel giusto modo scrivendo codice scalabile, manutenibile e pulito.

## 1. Perché React Native?
Prima di React Native, lo sviluppo per piattaforme multiple richiedeva basi di codice separate per iOS e Android, ciò significava il doppio del lavoro, costi più elevati e cicli di sviluppo più lenti. Con React Native è possibile scrivere un **unico codice** che funzioni perfettamente su entrambi rendendo lo sviluppo più veloce, economico e più efficiente. Grandi aziende come Meta, Discord, Microsoft, Tesla e Amazon utilizzano questa React Native per costruire le loro app mobile. 

### 1.1 JSI (JavaScript Interface)
Con la nuova architettura, le prestazioni sono migliorate significativamente grazie alla **JSI (JavaScript Interface)**, che sostituisce il vecchio ponte consentendo a JavaScript di comunicare direttamente con il codice nativo per un prestazioni più fluide e veloci. 

### 1.2 Turbo Modules
Inoltre, i nuovi **Turbo Modules** caricano i moduli nativi solo quando necessario riducendo tempo di avvio e utilizzo della memoria. 

### 1.3 Fabric
Infine una nuova feature chiamata **Fabric**, che ottimizza il rendering dell'interfaccia utente creando animazioni, gesti e aggiornamenti più rapidi ed efficienti; 

### 1.4 Caricamento Rigido (Hot Reloading)
con JSI, TurboModules e Fabric, le react-native app sono ora veloci e fluide come le app native. A parte la sua nuova architettura, supporto multipiattaforma e componenti nativi, React-Native è dotato anche del **ricaricamento rigido (Hot Reloading)** permettendoti di vedere le modifiche codificate immediatamente oltre a disporre di una comunità enorme che semplicemente continua crescere. La curva di apprendimento di React-Native è semplice se si dispone di conoscenze di JavaScript e React.js

### 1.5 Expo: build react-native application
**Expo** è il framework raccomandato ufficialmente per iniziare, poiché semplifica la configurazione dell'ambiente gestendo dipendenze native e componenti predefiniti per navigazione, fotocamera e mappe. Analogamente, Expo è uno strumento simile a Vite ma dedicato solo a React-Native; fornisce molti strumenti e servizi che semplificano lo sviluppo e aiutano a creare la mobile app più velocemente. Expo gestisce le impostazioni dell'ambiente di sviluppo, ciò significa che non è necessario installare separatamente dipendenze native di Android Studio; supporta anche gli aggiornamenti **over-the-air**, permettendo agli utenti di ricevere l'ultimo codice senza dover attendere l'approvazione degli App Store e distribuire la propria mobile app in pochi minuti.

Se pensi ancora che React-Native CLI sia l'opzione migliore, pensaci due volte.

## 2. React Native Fundamentals
Se si è ha familiarità con React.js è evidente la similarità con la sintassi di React-Native, ma ovviamente ci sono alcune differenze da notare e di cui essere consapevoli. 

Quando si programma in React-Native si usa JavaScript proprio come React ma invece di renderizzare elementi HTML come `<div>` o `<p>`, si renderizzano componenti mobile nativi come **View** e **Text** utilizzando la sintassi JSX che rende super facile creare e visualizzare i nostri componenti nativi.
```jsx
import React from 'react';
import { View, Text } from 'react-native';

const App = () => {
    return(
        <View>
            <Text>Hello World from React-Native!</Text>
        <View>
    );
};
```

### 2.1 <Text>
Il **componente Text** è abbastanza semplice, viene utilizzato per visualizzare il testo in App. È possibile personalizzarla usando la stessa sintassi CSS come in React; si può impostare la dimensione del carattere, il colore e lo spessore utilizzando il prop `style`.
```jsx
import React from 'react';
import { View, Text } from 'react-native';

const App = () => {
    return(
        <View>
            <Text 
                style={{ fontSize: 24, color: 'blue' }}
                >Hello World from React-Native!</Text>
        <View>
    );
};
```

### 2.2 StyleSheet Utility
React-Native offre anche StyleSheet Utility che consente di definire degli stili creando un singolo oggetto Javascript.
```jsx
import { Text, StyleSheet } from 'react-native';

const App = () => {
    return <Text >Hello World from React-Native!</Text>
};

const styles = StyleSheet.create({
    text: {
        fontSize: 24,
        color: "blue",
        fontWeight: "bold",
    },
});

export default App;
```

Questo è molto utile in applicazioni più grandi poiché ottimizza le prestazioni. 


### 2.3 NativeWind
Come sappiamo TailwindCSS sta diventando sempre più popolare ma nel mondo di React-Native è entrato in scena NativeWind che permette di scrivere gli stili inline come TailwindCSS all'interno di React-Native. Per lo styling, oltre al foglio di stile standard, si può usare **NativeWind**, che permette di scrivere stili simili a **Tailwind CSS** direttamente nei componenti mobili.
```jsx
import { Text } from 'react-native';

const App = () => {
    return <Text className="text-[24px] text blue font-bold"> Hello, world!</Text>
}

export default App;
```

Sembra di codificare una normale web application ma invece si sta sviluppando una mobile app.

### 2.4 <View>
Il **componente View** agisce come un contenitore, o box, che contiene altri componenti. È simile e paragonabile all'elemento HTML `<div>` ma con alcune funzionalità aggiuntive specifiche per le mobile app. Il componente View è spesso utilizzato per creare strutture di layout per altri componenti. Ha molti e differenti props che possono essere utilizzati per controllare l'aspetto e il comportamento. 

Una cosa da notare è che il componente View utilizza il layout **Flexbox di default**, rendendo facile controllare la disposizione dei figli tramite proprietà come `flexDirection`, `justifyContent` e `alignItems` per raggiungere qualsiasi layout desiderato. 

### 2.5 Componenti Interattivi: **componenti toccabili (touchable components)**
Per l'interattività esistono componenti per la creazione di pulsanti, link e altri elementi interattivi;

#### 2.5.1 <TouchableOpacity>
e si utilizzano componenti "touchable" come **TouchableOpacity**, che offre spazio per la personalizzazione e risponde alla pressione tramite la prop `onPress`. 
```jsx
import React from 'react';
import { TouchableOpacity, Text } from 'react-native';

function MyButton(props) {
    return (
        <TouchableOpacity onPress={props.onPress}>
            <Text>{props.label}</Text>
        </TouchableOpacity>

        <TouchableOpacity onPress={() => alert('Pressed!')}>
            <Text>Press Me</Text>
        </TouchableOpacity>
    );
};
```

#### 2.5.2 <TouchableHighlight>
Il secondo componente simile è chiamato **TouchableHighlight** che consente alle View (viste) di rispondere al tocco in modo unico.
```jsx
import React from 'react';
import { TouchableHighlight, Text } from 'react-native';

function MyButton(props) {
    return (
        <TouchableHighlight onPress={props.onPress}>
            <Text>{props.label}</Text>
        </TouchableHighlight>

        <TouchableHighlight onPress={() => alert('Pressed!')}>
            <Text>Press Me</Text>
        </TouchableHighlight>
    );
};
```

#### 2.5.3 <TouchableWithoutFeedback>
Il terzo componente è chiamato **TouchableWithoutFeedback** che risponde alla necessità di creare un elemento cliccabile ma senza un feedback visivo quando premuto. È molto utile quando si vuole creare link o immagini che necessitano di alcun effetto aggiuntivo.
```jsx
import React from 'react';
import { TouchableWithoutFeedback, Text } from 'react-native';

function MyLink(props) {
    return (
        <TouchableWithoutFeedback onPress={props.onPress}>
            <Text style={{ textDecorationLine: 'underline' }}>{props.label}</Text>
        </TouchableWithoutFeedback>
    );
};
```

#### 2.5.4 <ActivityIndicator> 
Oltre a questi **componenti toccabili (touchable components)** ci sono anche **indicatori di attività (ActivityIndicator)** che consentono di mostrare uno spinner, o indicatore di caricamento, all'interno della mobile app.
```jsx
import { View, ActivityIndicator, StyleSheet } from 'react-native';

const App = () => {
    return (
        <View style={styles.container}>
            <ActivityIndicator size="large" color="#0000ff" />
        </View>
    );
};
```

#### 2.5.5 <Button>
È presente anche il classico componente **Button** che consente di impostare proprietà come il contenuto, il colore e anche chiamare una funzione onPress quando il pulsante viene premuto.
```jsx
import { View, Button, StyleSheet } from 'react-native';

const App = () => {
    
    const handlePress = () => {
        console.log('Button Pressed!');
    };

    return (
        <View style={styles.container}>
            <Button title="Press me" onPress={handlePress} />
        </View>
    );
};
```

Ogni volta che si ha bisogno di uno stile o un comportamento più avanzato si prevede l'utilizzo frequente dei componenti toccabili poiché offrono maggiore flessibilità.

### 2.6 <FlatList>
Ora, il prossimo super componente importante chiamato **FlatList**. Per gestire  e renderizzare lunghe liste di elementi, il componente **FlatList** è ideale poiché ottimizza le prestazioni di scorrimento e la memoria tramite il rendering pigro. È come la funzione map() in React ma con qualche funzionalità extra come la separazione degli elementi.
```jsx
import { View, FlatList, Text, StyleSheet } from 'react-native';

const App = () => {
    return (
        <View style={styles.container}>
            <FlatList
                data={DATA}
                renderItem={({ item }) => (
                    <View style={styles.item}>
                        <Text style={styles.title}>{item.title}</Text>
                    </View>
                )}
                keyExtractor={item => item.id}
            />
        </View>
    );
};

export default App;
```

Per utilizzarlo è necessario importarlo da `react-native`:
```jsx
import {View, FlatList, Text } from `react-native`;
```

Successivamente si definiscono alcuni dati come una serie di oggetti che si vogliono mappare:
```jsx
const DATA = [
    { id: '1', title: 'Item 1' },
    { id: '2', title: 'Item 2' },
    { id: '3', title: 'Item 3' },
    { id: '4', title: 'Item 4' },
    { id: '5', title: 'Item 5' },
];
```

e poi viene utilizzata una vista con all'interno una chiamata all'elemento <FlatList>; che accetta di default alcuni props come l'oggetto `data` al quale viene passato l'array di dati che si vuole mappare, e poi un oggetto props di rendering chiamato `renderItem` che permette di definire esattamente come si vuole rappresentare ogni elemento nell'array
```jsx
import { View, FlatList, Text } from 'react-native';

const DATA = [
    { id: '1', title: 'Item 1' },
    { id: '2', title: 'Item 2' },
    { id: '3', title: 'Item 3' },
    { id: '4', title: 'Item 4' },
    { id: '5', title: 'Item 5' },
];

const App = () => {
    return (
        <View>
            <FlatList
                data={DATA}
                renderItem={({ item }) => (
                    <View>
                        <Text>{item.title}</Text>
                    </View>
                )}
                keyExtractor={item => item.id}
            />
        </View>
    );
};

export default App;
```

La questione è:

* Quando dovresti usare FlatList?
* Quando dovresti usare la funzione map?

Per grandi liste in cui si vuole avere uno scorrimento fluido è consigliato l'utilizzo e l'adozione di FlatList; mentre  la funzione map è più adeguata per elenchi più piccoli.

### 2.7 <ScrollView>
C'è anche qualcosa conosciuto come <ScrollView>. Lo si può vedere come un contenitore/box scorrevole che può contenere più componenti e viste. **ScrollView** è un contenitore di scrolling generico adatto a quantità minori di contenuti come la proprietà di scorrimento **overflow** di un elemento <div> in HTML che consente di navigare facilmente attraverso un elenco di articoli o grandi quantità di contenuti.
```jsx
import { View, ScrollView, Text, StyleSheet } from `react-native`;

const App = () => {
    return (
        <View style={styles.container}>
            <ScrollView contentContainerStyle={styles.scrollViewContent}>
                <Text style={styles.text}> Text 1 </Text>
                <Text style={styles.text}> Text 2 </Text>
                <Text style={styles.text}> Text 3 </Text>
                <Text style={styles.text}> Text 4 </Text>
                <Text style={styles.text}> Text 5 </Text>
                <Text style={styles.text}> Text 6 </Text>
                <Text style={styles.text}> Text 7 </Text>
                <Text style={styles.text}> Text 8 </Text>
                <Text style={styles.text}> Text 9 </Text>
                <Text style={styles.text}> Text 10 </Text>
            </ScrollView>
        </View>
    );
};
```

I contenuti possono essere inseriti all'interno di una **vista (View)** chiamata **vista di scorrimento (ScrollView)** che renderizza gli elementi al suo interno. Utilizzando il componente di visualizzazione a scorrimento (ScrollView) ci si assicura che gli utenti possano esplorare facilmente tutti i contenuti rendendo la mobile app più intuitiva.
```jsx
import { View, ScrollView, Text } from `react-native`;

const App = () => {
    return (
        <View>
            <ScrollView>
                <Text> Apple </Text>
                <Text> Banana </Text>
                <Text> Cherry </Text>
                <Text> Date </Text>
                <Text> Elderberry </Text>
                <Text> Fig </Text>
                <Text> Grape </Text>
                <Text> Honeydew </Text>
                <Text> Iced Tea </Text>
                <Text> Jackfruit </Text>
            </ScrollView>
        </View>
    );
};
``` 

### 2.8 <SafeAreaView>
Inoltre c'è un altro componente essenziale con il quale si lavora spesso, chiamato **SafeAreaView**. Esso fornisce una zona sicura per il rendering evitando che il contenuto sia coperto da notch, indicatori home o barre di stato; è ottimo per costruire app supportate su diversi dispositivi aventi differenti forme e dimensioni dello schermo.
```jsx
import { SafeAreaView, ScrollView, Text, StyleSheet } from `react-native`;

const App = () => {
    return (
        <SafeAreaView style={styles.container}>
            <ScrollView contentContainerStyle={styles.scrollViewContent}>
                <Text style={styles.text}> Text 1 </Text>
                <Text style={styles.text}> Text 2 </Text>
                <Text style={styles.text}> Text 3 </Text>
                <Text style={styles.text}> Text 4 </Text>
                <Text style={styles.text}> Text 5 </Text>
                <Text style={styles.text}> Text 6 </Text>
                <Text style={styles.text}> Text 7 </Text>
                <Text style={styles.text}> Text 8 </Text>
                <Text style={styles.text}> Text 9 </Text>
                <Text style={styles.text}> Text 10 </Text>
            </ScrollView>
        </SafeAreaView>
    );
};
```


Il modo in cui viene usato ogni volta è correlato alle preferenze delle dimensioni del contenuto; quando si pensa che qualcosa potrebbe essere troppo lungo, o posizionato in modo scomodo allora lo si avvolge semplicemente dentro un'**area di visualizzazione sicura (SafeAreaView)** che lavora e funziona meglio rispetto all'area di visualizzazione predefinita (di default) che per la maggior parte dei casi non è all'altezza di alcuni dispositivi rendendola quindi una scelta non ottimale. 

#### 2.8.1 `react-native-safe-area-context`
Spesso viene utilizzato un pacchetto chiamato `react-native-safe-area-context` che funziona su tutti i dispositivi, anche per barra inferiore. 
```jsx
import { SafeAreaView } from `react-native-safe-area-context`;

function SomeComponent() {
    return (
        <SafeAreaView style={{ flex: 1, backgroundColor: 'red' }}>
            <View style={{ flex: 1, backgroundColor: 'blue' }} />
        </SafeAreaView>
    );
};
```

### 2.9 <Image>
Bisogna sapere quali componenti esistono in modo da poterli utilizzare successivamente, ad esempio quando si ha l'esigenza di mostrare alcune immagini all'interno della mobile app. Fortunatamente ancora una volta è super simile a come appare in React.js, ovvero viene semplicemente usato il **componente immagine (Image)** fornito da React-Native; è necessario passargli l'oggetto props `source` che può essere un percorso (path) o un URL.
```jsx
import { View, Image, StyleSheet } from `react-native`;

const App = () => {
    return(
        <View style={styles.container}>
            <Image 
                source = { { uri: 'https:77via.placeholder.com/200'} }
                style = {styles.image}
            />
        </View>
    );
};

export default App;
```

### 2.10 <ImageBackground>
Ma se si vuole visualizzare un'immagine come sfondo di background bisogna usare il componente **ImageBackground** che funziona allo stesso modo ma rende l'immagine come sfondo di background. È specificamente progettato per consentire ad altri di sovrapporsi ad esso mentre il componente **Image** è pensato per la singola visualizzazione di un immagine. Entrambi i componenti possono gestire diversi formati di immagine, come .png, .jpeg, .gif, .webp; ma non supportano i file .svg a causa di alcune limitazioni di rendering nativo.
```jsx
import { View, ImageBackground, Text, StyleSheet } from `react-native`;

const App = () => {
    return(
        <View style={styles.container}>
            <ImageBackground 
                source = { { uri: 'https://via.placeholder.com/200'} }
                style = {styles.imageBackground}
            >
                <Text style={styles.text}> Hello, Image Background!</Text>
            </ImageBackground>
        </View>
    );
};

export default App;
```

#### 2.10.1 `react-native-svg`
Se si vuole usare i file .svg esiste un pacchetto di terze parti chiamato `react-native-svg`.
```jsx
<View>
    <Svg height="50%" width="50%" viewBox="0 0 100 100">
        <Circle 
            cx="50"
            cy="50"
            r="45"
            stroke="blue"
            strokeWidth="2.5"
            fill="green"
        />

        <Rect 
            x="15"
            y="15"
            width="70"
            height="70"
            stroke="red"
            strokeWidth="2"
            fill="yellow"
        />
    </Svg>
</View>
```

### 2.11 <Modal>
Fortunatamente React-Native possiede componenti per le **modali (Modal)**. 
```jsx
import { View, Text, Modal } from `react-native`;

const App = () => {
    <Modal
        visible={true}
        animationType="slide"
        onRequestClose={() => console.log('Modal closed')}
    >

        <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
            <Text> This is a Modal </Text>
        </View>
    </Modal>
};

export default App;
```

### 2.12 <Alert>
Esiste anche un componente nativo di **avviso (alert)** il quale è sempre importabile da 'react-native'.
```jsx
import { Alert } from `react-native`;

const App = () => {
    Alert.alert(
        'Alert title',  // titolo
        'My alert message', // messaggio 
        [   // funzioni da eseguire per "Cancel" e "Ok"
            { text: 'Cancel', onPress: () => console.log('Ok Pressed'), style: 'cancel' },
            { text: 'OK', onPress: () => console.log('OK pressed') }
        ]
    );
};

export default App;
```

### 2.13 <Switch>
Se si sta sviluppando un Form (modulo) si potrebbe creare in qualche modo un interruttore; in React-Native è possibile utilizzare il **componente nativo Switch**. Anche in questo caso è davvero super semplice importare e creare uno stato per questo componente, allo stesso modo come in React.js; si crea una funzione che gestisce il componente e il suo stato.
```jsx
import { Switch, View } from `react-native`;

const App = () => {
    const [isEnabled, setIsEnabled] = useState(false);
    const toggleSwitch = () => setIsEnabled(previousState => !previousState);

    return (
      <View>
        <Switch 
            trackColor={{ false: '#767577', true: '#81b0ff' }}
            thumbColor={isEnabled ? '#f5dd4b' : '#f4f3f4' }
            onValueChange={toggleSwitch}
            value={isEnabled}
        />
      </View>
    );
};

export default App;
```

### 2.14 <StatusBar>
C'è un altro componente che viene spesso utilizzato: **StatusBar**. Sia React-Native sia Expo hanno le proprie versioni che consentono di controllare come la barra di stato dovrebbe apparire per ciascuna schermata della mobile app.

Si consiglia di usare la versione di Expo: è possibile definire una vista con all'interno del contenuto testuale e subito dopo codificare una barra di stato.
```jsx
import React from 'react';
import { Text, View } from `react-native`;
import { StatusBar } from 'expo-status-bar';

export default function App() {
    return (
        <View style={styles.container}>
            <Text style={{ color: '#000' }}> Notice that the status bar has dark text!</Text>
            <StatusBar style="dark" />
        </View>
    );
};
```