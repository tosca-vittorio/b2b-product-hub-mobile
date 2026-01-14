# README.md - Marullo Product Doc Center

## 1. Overview

**Marullo Product Doc Center (DEMO)** è un **Proof of Concept** mobile (iOS/Android) sviluppato in **React Native (Expo)** per consultare rapidamente un **catalogo prodotti** e accedere alle relative **schede/documenti** (in formato schermata o PDF), con la possibilità di inviare **richieste rapide** (info/campioni) tramite e-mail precompilata.

Il progetto è pensato per contesti B2B (Business-to-Business), cioè interazioni e flussi informativi tra aziende (es. commerciale, buyer/ufficio acquisti, distributori, clienti professionali). In questi scenari, la rapidità di consultazione del catalogo e l’accesso alla documentazione tecnica rappresentano un requisito operativo.

> **Nota importante (Demo Dataset):** i contenuti inclusi nel progetto sono **sintetici e dimostrativi**. Non sono documenti ufficiali e non contengono dati reali utilizzabili a fini commerciali o alimentari.

---

## 2. Obiettivo

* Ridurre l’attrito nella consultazione di informazioni prodotto (schede, formati, note).
* Centralizzare documentazione e riferimenti in un’unica app.
* Abilitare un flusso rapido di contatto (“Richiedi info/campione”) senza backend.

---

## 3. Funzionalità (MVP)

### 3.1 Catalogo

* Lista prodotti DEMO con ricerca testuale.
* Filtri per categoria (es. Semilavorati / Ho.Re.Ca / GDO / Altro – personalizzabile).

### 3.2 Dettaglio prodotto

* Informazioni principali: nome, categoria, formati, descrizione breve, impiego consigliato.
* Sezioni tecniche in formato “card” (dati DEMO).

### 3.3 Documenti

* Accesso a documenti associati (PDF DEMO o schermata “scheda tecnica”).
* Possibilità di condivisione/esportazione (opzionale, se utile).

### 3.4 Richiesta rapida

* Pulsante **“Richiedi info/campione”** che apre una e-mail precompilata con:

  * prodotto selezionato
  * formati
  * note
  * riferimento cliente (se inserito nelle impostazioni)

---

## 4. Non obiettivi (per tenere il progetto rapido)

* Nessuna integrazione diretta con ERP/CRM.
* Nessun ordering / carrello.
* Nessuna gestione lotti “reale” o tracciabilità ufficiale.
* Nessun login / multi-tenant nell’MVP.

Questi aspetti sono considerati **evoluzioni** eventuali.

---

## 5. User Flow (come si usa)

1. Home → scegli categoria o cerca prodotto
2. Lista → apri prodotto
3. Dettaglio → leggi scheda / apri documento
4. “Richiedi info/campione” → e-mail precompilata → invia

---

## 6. Dataset e contenuti DEMO

Il catalogo è alimentato da un file locale (`products.demo.json`) strutturato in modo da essere **compatibile con future integrazioni** (import/export CSV/JSON).

Ogni prodotto include:

* metadati (nome, categoria, formati)
* sezioni scheda tecnica (campi demo)
* documenti associati (asset locali)

---

## 7. Stack Tecnologico

* **React Native + Expo**
* Navigazione: React Navigation (Stack)
* Persistenza (necessaria per preferenze): AsyncStorage
* Gestione asset documenti: PDF local assets (o schermata nativa “scheda”)

---

## 8. Struttura progetto (proposta)

* `src/screens/` (Home, ProductList, ProductDetail, Documents)
* `src/components/` (ProductCard, SectionCard, FilterChips, SearchBar)
* `src/data/` (`products.demo.json`)
* `src/domain/` (types/interfaces + mapper)
* `src/services/` (email composer, storage preferences)
* `assets/docs/` (PDF DEMO)

---

## 9. Evoluzione per piccoli step (roadmap)

La roadmap è pensata per aggiungere valore senza riscrivere nulla.

### v0.1 — MVP (core)

* Catalogo + ricerca
* Dettaglio prodotto
* Documenti (apertura)
* Email precompilata

### v0.2 — UX & Quality (piccola evolutiva)

* Filtri persistenti (categoria)
* Preferiti (star)
* Empty states e gestione errori (doc mancante, dataset vuoto)

### v0.3 — “Supporto al commerciale” (evolutiva)

* Profilo cliente (nome azienda, email, note) salvato localmente
* Template email più completo (richiesta campione / richiesta scheda)

### v0.4 — “Integrazione light” (evolutiva)

* Import catalogo da CSV/JSON (file locale)
* Export richieste in CSV (log richieste inviate)

---

## 10. Bugfix policy (come gestiamo fix e stabilità)

Per mantenere l’app stabile e dimostrare metodo professionale:

* Ogni bug è tracciato come issue con:

  * **Steps to reproduce**
  * **Expected vs Actual**
  * **Scope**
  * **Fix strategy**
* Regola: **prima test riproducibile**, poi fix.
* I fix non introducono feature “di nascosto”.
* Ogni fix viene documentato in `CHANGELOG.md` (entry breve, data, commit).

---

## 11. Criteri di Done (per chiudere in fretta)

Il progetto è “chiudibile” quando:

* l’app parte e naviga senza crash
* almeno 10 prodotti demo sono consultabili
* ogni prodotto ha almeno 1 documento demo o scheda in-app
* l’azione “Richiedi info/campione” genera correttamente l’e-mail
* README + screenshots presenti

---

# DOCUMENTAZIONE INIZIALE AGGIUNTIVA (per repo “serio”)

## 1) docs/PROJECT_CHARTER.md (1 pagina)

Contiene:

* obiettivo
* stakeholder (commerciale/cliente)
* vincoli (demo dataset, no dati reali)
* out-of-scope
* milestone v0.1–v0.4

## 2) docs/REQUIREMENTS.md

* requisiti funzionali (MVP)
* requisiti non funzionali (offline, performance, accessibilità base)

## 3) CHANGELOG.md

* v0.1: initial MVP
* v0.2: evolutive e bugfix

## 4) docs/BUGFIX_WORKFLOW.md

Template issue bug e regole commit.

---

# Proposta di “piccole evolutive” sensate (senza perdere tempo)

Le evolutive che danno massimo valore con minimo costo:

1. **Preferiti** (star)
2. **Ricerca migliorata** (debounce, highlights)
3. **Filtri persistenti**
4. **Profilo cliente** per email precompilata
5. **Log richieste** (anche solo locale)

Sono feature piccole ma fanno sembrare l’app “vera”.

---

# Nota importante

Per evitare problemi:

* usa AI per creare **prodotti DEMO** con **struttura simile**, contenuti **nuovi** e **dichiarati demo**.
* non copiare testi identici o troppo vicini alle schede originali.
* evita loghi o marchi se non autorizzati; basta nominare “PoC ispirato a scenario B2B”.

---

## Se vuoi, il prossimo step lo faccio io “a pacchetto”

Nel prossimo messaggio posso generarti:

1. una bozza di `products.demo.json` con **10 prodotti demo** (campi puliti, coerenti),
2. i template dei file `PROJECT_CHARTER.md`, `REQUIREMENTS.md`, `BUGFIX_WORKFLOW.md`,
3. una mini-roadmap con **task checklist** per arrivare a v0.1 velocissimo.

Dimmi solo una cosa: preferisci che i “documenti” siano **PDF demo** oppure una **schermata scheda tecnica** (più rapida e senza sbatti PDF)?
