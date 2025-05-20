# 4. Branch + Workflow

Uno dei punti di forza di Git è il supporto avanzato al *branching*, che consente ai team di lavoro di sviluppare funzionalità, correggere bug o sperimentare in ambienti isolati. I *branch* (rami) permettono di lavorare in parallelo senza compromettere la stabilità del codice principale. Una gestione efficace dei branch, insieme alla conoscenza dei principali flussi di lavoro collaborativi, è fondamentale per lo sviluppo software moderno.

---

---

## 4.1 Branch

Git rende semplice creare, elencare e passare da un branch all’altro. 

### 4.1.1 Creazione

Il comando crea un nuovo branch che punta allo stesso commit del branch corrente.

```bash
git branch nuovo-branch
```

### 4.1.2 Passaggio

Puoi utilizzare due comandi molto comuni per passare da un branch all’altro

```bash
git checkout nuovo-branch
git checkout -b nuovo-branch # Creazione e passaggio al nuovo branch 
```

Oppure, questo : 

```bash
git switch nuovo-branch
git switch -c nuovo-branch # Creazione e passaggio al nuovo branch
```

### 4.1.3 Elenco

Puoi visualizzare l’elenco dei branch, mediante il comando 

```bash
git branch
```

---

## 4.2 Merge

Il *merge* è l’operazione con cui si unisce il contenuto di due branch. Può avvenire in diversi modi, che vediamo di seguito.

### 4.2.1 Fast-Forward Merge

Se il branch di destinazione non ha nuovi commit rispetto al branch da unire, Git semplicemente sposta il puntatore in avanti 

```bash
git merge --ff nome-branch 
```

### 4.2.2 No Fast-Forward Merge

Anche se sarebbe possibile un fast-forward, Git crea un merge commit per mantenere traccia esplicita della fusione. 

```bash
git merge --no-ff nome-branch
```

### 4.2.3 Merge Conflicts

Se ci sono modifiche incompatibili tra i branch, Git non può unire automaticamente e richiede l’intervento manuale. I conflitti vanno risolti modificando i file coinvolti e poi : 

```bash
git add file-conflittuali 
git commit
```

---

## 4.3 Rebase

Il comando `git rebase` consente di “riscrivere” la cronologia spostando i commit di un branch sopra un altro. Questo può produrre una cronologia più lineare rispetto al merge, ma deve essere usato con attenzione, soprattutto su branch condivisi.

In pratica, è l’alternativa al Merge. 

- Esempio :
    
    ```bash
    git checkout feature
    git rebase main
    ```
    

### 4.3.1 Merge vs Rebase

| Merge | Rebase |
| --- | --- |
| Crea un commit di Merge | Riscrive la cronologia |
| Mantiene traccia della divergenza | Crea una cronologia lineare |
| Più sicuro su Branch Condivisi | Migliore leggibilità della Storia |

---

## 4.4 Common Workflow

A seconda della dimensione del team, della frequenza di rilascio e dello stile di sviluppo, si possono adottare diversi workflow.

### 4.4.1 Git Flow

E’ un modello robusto e strutturato per team che hanno rilasci regolari e ben pianificati. 

- **Branch principali →** `main` ,`develop`
- **Branch di supporto →** `feature/*` ,`release/*` ,`hotfix/*`
- **Filosofia di Lavoro →** Separazione chiara tra sviluppo, testing e produzione
- **Vantaggi →** Buona separazione tra Sviluppo e Produzione
- **Svantaggi →** Può risultare complesso per piccoli team o per Sviluppo Continuo

### 4.4.2 GitHub Flow

Flusso leggero e adatto a progetti con deploy frequenti, usato spesso in progetti open-source.

- **Branch principale →** `main`
- **Branch di Lavoro →** Uno per ogni feature o fix
- **Filosofia di Lavoro →** Si usano le *feature branch* e *pull request*
- **Utilizzo del Merge →** Eseguito dopo Revisione del Codice e Test Automatici
- **Vantaggi →** Agile, Collaborativo, adatto a Sviluppo Continuo
- **Svantaggi →** Meno adatto a rilasci pianificati complessi

### 4.4.3 Trunk Based Development

Modello minimalista che incentiva l’Integrazione Continua.

- **Branch principale →** `main` , anche detto “trunk”
- **Branch di Lavoro →** Piccoli Branch a breve durata, oppure commit su `main`
- **Filosofia di Lavoro →** Merge Frequenti e codice sempre Integrato
- **Vantaggi →** Rilasci Rapidi, cronologia semplice
- **Svantaggi →** Richiede test automatici robusti e team disciplinati

---