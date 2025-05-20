# 6. Errori Comuni

Lavorando con Git, è inevitabile imbattersi in errori o situazioni inaspettate: file eliminati accidentalmente, commit sbagliati, conflitti di merge o modifiche da annullare. 

Fortunatamente, Git fornisce strumenti potenti per gestire queste situazioni e ripristinare uno stato coerente del repository. 

---

---

## 6.1 Undo / Rollback

Git offre diversi comandi per “tornare indietro”, ma è importante comprendere le differenze tra i comandi.

### 6.1.1 Restore

Per ripristinare file nella Working Directory o nello Staging Area, utilizziamo il seguente comando 

```bash
git restore nomefile.txt # Per ripristinare un file nella Working Directory
git restore --staged nomefile.txt # Per ripristinare un file nella Staging Area
```

### 6.1.2 Checkout

Veniva usato in precedenza per ripristinare i file e cambiare branch, ora viene sconsigliato per la gestione dei file.

```bash
git checkout HEAD
```

### 6.1.3 Reset

Per modificare lo stato del branch e/o dello Staging Area usiamo questo comando 

```bash
git reset 
```

- Possiamo includere vari valori da aggiungere al nostro comando :
    - `--soft` , conserva le modifiche ma sposta il puntatore HEAD
    - `--mixed` (default), rimuove i file dallo staging area, ma non dalla Working Directory
    - `--hard` (WARNING), annulla completamente le modifiche (working directory e staging)

## 6.2 Ripristino File

Se hai cancellato un file e non hai ancora effettuato il commit, puoi usare il comando :

```bash
git restore nomefile.txt
```

Se il file era stato già tracciato ma eliminato e committato, puoi recuperarlo da un commit precedente : 

1. Cerca il commit tramite `git log` 
2. Ripristina con 
    
    ```bash
    git checkout <commit>
    ```
    

---

## 6.3 Ripristinare Commit Precedenti

Se vuoi tornare ad uno stato precedente, hai due metodi : 

- Per la cronologia locale, usa
    
    ```bash
    git reset --hard <commit>
    ```
    
    ⚠️ WARNING → cancella le modifiche non salvate. Mai usare su branch condivisi
    
- Per ambienti condivisi, usa :
    
    ```bash
    git revert <commit>
    ```
    
    Crea un nuovo commit che “annulla” le modifiche
    

---

## 6.4 Merge Conflict Resolution

I conflitti di merge si verificano quando due rami modificano le stesse linee di codice.

1. Esegui il merge → `git merge nome-ramo` 
2. Git segnala diversi conflitti → `git status` per verifica
3. Risolvi manualmente i conflitti editando i file
4. Aggiungi i file risolti → `git add nomefile` 
5. Completa il merge → `git commit` 

---

## 6.5 Reflog e Cherry-pick

### 6.5.1 Reflog

Questo comando tiene traccia della cronologia locale dei movimenti di HEAD, anche quelli non visibili con `git log` .

Viene utilizzato per : 

- Recuperare branch o commit persi
- Ripristinare uno stato precedente anche dopo un `reset --hard`

```bash
git reflog
git checkout HEAD@{2}
```

### 6.5.2 Cherry-pick

Permette di applicare un singolo commit (o più) da un branch a un altro.

Viene utilizzato quando:

- Vuoi portare una modifica specifica senza fare il merge di tutto il branch
- Hai bisogno di replicare una correzione su più rami

```bash
git cherry-pick <commit>
```

---