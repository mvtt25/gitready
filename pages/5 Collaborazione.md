# 5. Collaborazione

Nel mondo dello sviluppo software moderno, la collaborazione efficace tra membri del team è fondamentale per garantire qualità, velocità e controllo nel ciclo di vita del codice. 

Git, insieme a piattaforme come GitHub e GitLab, rappresenta lo strumento standard per la gestione del codice sorgente e la collaborazione distribuita. 

---

---

## 5.1 Remote Repository

Quando si lavora su un progetto condiviso, il codice è ospitato su un repository remoto, come su GitHub o GitLab.

### 5.1.1 Elenco delle Repository

Per visualizzare l’elenco e la gestione delle repository remote collegate al progetto locale, utilizziamo questo comando 

```bash
git remote
```

### 5.1.2 Fetch

Per scaricare gli aggiornamenti dal Repository Remoto senza fonderli automaticamente nel branch locale, utilizziamo il comando

```bash
git fetch
```

### 5.1.3 Pull

Per scaricare e fondere immediatamente gli aggiornamenti nel branch corrente, utilizziamo il comando 

```bash
git pull
```

### 5.1.4 Push

Invia i Commit dal Branch Locale al corrispondente Branch Remoto

```bash
git push
```

---

## 5.2 Fork & Pull Request

Le piattaforme come GitHub e GitLab, supportano un flusso di lavoro basato su fork e pull/merge request. 

### 5.2.1 Fork

E’ una copia indipendente di un repository. 

Il Fork serve a proporre modifiche senza avere accesso al progetto originale.

### 5.2.2 Pull Request / Merge Request (GitHub / GitLab)

Sono delle richieste formali per integrare modifiche da un Branch (o Fork) a un Branch principale del progetto. 

### 5.2.3 Best Practice

- Bisogna scrivere *Pull Request* chiare e documentate, con descrizioni dei cambiamenti e motivazioni.

---

## 5.3 Code Review

La *Code Review* è un processo in cui altri membri del team esaminano il codice prima che venga integrato : 

- Si effettua direttamente nella *Pull Request*
- Permette di rilevare Bug e migliorare la qualità del codice
- Apertura ai commenti costruttivi e al Feedback

---

## 5.4 Conflict Management

I conflitti nascono quando due o più modifiche toccano la stessa parte di codice.

Per gestirli : 

- Comunicazione continua con il Team
- Usare frequentemente operazioni come `git pull` per ridurre la probabilità di conflitti
- Tenere d’occhio i file conflitti segnalati da Git

---

## 5.5 Branch Protection

Per evitare modifiche non controllare, si possono applicare regole di protezione ai branch : 

- Branch Protetti → Impediscono modifiche dirette sui branch principali
- Pull Request → Obbligano l’approvazione tramite Code Review o Test prima del Merge

### 5.5.1 Best Practice

- Proteggere sempre i branch principali come il `main` e usare branch secondari per features o fix.

---