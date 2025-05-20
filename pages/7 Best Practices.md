# 7. Best Practices

Una gestione efficace del controllo versione è fondamentale per garantire la qualità del codice, la collaborazione tra team e la facilità di manutenzione di un progetto. Seguendo alcune best practice nell’uso di Git (o di altri sistemi di versionamento), è possibile migliorare la tracciabilità delle modifiche, ridurre i conflitti e mantenere un flusso di lavoro chiaro e sostenibile. 

---
- [7.1 Commit](#71-commit)
  - [7.1.1 Cosa Evitare?](#711-cosa-evitare)
  - [7.1.2 Benefici](#712-benefici)
- [7.2 Branch Significativi](#72-branch-significativi)
  - [7.2.1 Cosa consigliare?](#721-cosa-consigliare)
- [7.3 Main Always Deployable](#73-main-always-deployable)
- [7.4 Tag per Release](#74-tag-per-release)
- [7.5 Pull Frequenti e Push Programmati](#75-pull-frequenti-e-push-programmati)
- [7.6 .gitignore](#76-gitignore)
- [7.7 Merge tramite Pull Request](#77-merge-tramite-pull-request)
- [7.8 Documentazioni](#78-documentazioni)
---

## 7.1 Commit

- **Obiettivo →** Descrivere in modo preciso le modifiche effettuate
- **Formato Consigliato →** Usare Tempo Presente e Imperativo
- **Lingua →** Preferibilmente usa Lingua Inglese
- **Vantaggi →** Maggiore Leggibilità + Supporto Efficace
- **Esempi →**
    - ✅ |`Fix error in VAT calculation`
    - ✅ |`Refactor Authentication Module`
    - ✅ | `Fix #66 ticket`
    - ❌ |`Update` ,`Fix bug` ,`Varie Modifiche`
        - Troppo vago

### 7.1.1 Cosa Evitare?

- Commit troppo grandi che richiamano a troppe modifiche
- Commit che mescolano `refactoring` ,`bugfix` ,`new features`
- Commit sul `main` branch

### 7.1.2 Benefici

- Facilitare i revert mirati
- Agevolare Code Review
- Rendere il progetto più mantenibile

---

## 7.2 Branch Significativi

- **Obiettivo →** Organizzazione chiara del lavoro in rami e facilitazione del merge
- **Vantaggi →** Chiarezza sui singoli branch + Riduzione dei Conflitti + Gestione Sviluppo
- Branch Name convenzionati :
    - `feature/new-features`
    - `bugfix/description`
    - `hotfix/description`

### 7.2.1 Cosa consigliare?

- Branch per ogni Attività / Task
- Cancellare il Branch dopo il Merge → Solo se non si usa più

---

## 7.3 Main Always Deployable

- Obiettivo → Branch Principale sempre attivo e stabile, pronto per la messa in produzione
- **Formato Consigliato →** Integrazione tramite pull request + Niente sviluppo su `main`
- **Vantaggi →** Deploy affidabili in qualsiasi momento + Minori Rischi in Produzione

---

## 7.4 Tag per Release

- **Obiettivo →** Versionare il progetto per migliorare la gestione dei rilasci e tracciabilità
- **Formato Consigliato →** `v1.0.0` ,`v2.1.3` ,`v3.0.0-beta`
- **Vantaggi →** Navigazione semplice tra versioni + Possibilità di Rollback Rapidi

---

## 7.5 Pull Frequenti e Push Programmati

- **Obiettivo →** Mantenere il codice aggiornato con il lavoro degli altri e salvare i progressi
- **Formato Consigliato →** Pull ogni volta che si inizia a lavorare + Push al termine
- **Cosa Evitare →** Lunghe Sessioni e Commit poco significativi
- **Vantaggi →** Riduzione dei Conflitti in fase di Merge + Lavoro di Squadra

---

## 7.6 .gitignore

- **Obiettivo →** Evitare il commit di file non necessari o sensibili
- **Formato Consigliato →** Aggiornare `.gitignore` costantemente ed includere pattern
- **Pattern Consigliati → `node_modules/` ,`.env` ,`*.log` ,`.DS_Store`**
- **Vantaggi →** Repository pulita e leggera + Meno problemi di Sicurezza e Conflitti

---

## 7.7 Merge tramite Pull Request

- **Obiettivo →** Introdurre controlli di Qualità prima di integrare il codice nel `main` branch
- **Formato Consigliato →** *PR* per ogni branch che si vuole unire + Code Review
- **Code Review →** Assicurati che tutti i test passino prima di fare il merge
- **Vantaggi →** Code Quality + Condivisione Know-How + Riduzione Bug e Regressioni

---

## 7.8 Documentazioni

**Obiettivo →** Uniformare lo stile di lavoro e le regole per tutti i membri del team

**Formato Consigliato →** Documento o file README dedicato alle regole Git

**Vantaggi →** Riduce errori e ambiguità + Facilità ai nuovi membri + Ordine Workflow

**Piattaforme →** GitBook, Notion

---