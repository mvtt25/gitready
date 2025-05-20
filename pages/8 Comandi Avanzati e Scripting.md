# 8. Comandi Avanzati e Scripting

Dopo aver acquisito familiarità con i comandi di base di Git, è utile conoscere alcune funzionalità avanzate che permettono di automatizzare i processi, migliorare il flusso di lavoro e gestire progetti complessi. 

---
- [8.1 Git Hooks](#81-git-hooks)
  - [8.1.1 Come si Configura?](#811-come-si-configura)
- [8.2 Rewriting History](#82-rewriting-history)
- [8.3 Advanced Git Stash](#83-advanced-git-stash)
- [8.4 Submodule & Subtree](#84-submodule--subtree)
  - [8.4.1 Submodule](#841-submodule)
  - [8.4.2 Subtree](#842-subtree)
- [8.5 Trovare Bug tra i Commit](#85-trovare-bug-tra-i-commit)
- [8.6 Custom Alias](#86-custom-alias)
---

## 8.1 Git Hooks

I Git *hooks* sono script che Git esegue automaticamente in risposta a determinati eventi, come il commit, il push o il merge. Sono strumenti potenti per automatizzare controlli, validazioni o altre azioni ripetitive.

Alcuni esempi sono : 

- **pre-commit** → può essere usato per eseguire test automatici prima di permettere un commit.
- **commit-msg** → verifica che il messaggio del commit rispetti un formato
- **post-commit** → utile per logo o notifiche.

### 8.1.1 Come si Configura?

1. Vai nella directory `.git/hooks/` 
2. Rinomina e modifica lo script desiderato
    1. `pre-commit.sample` → `pre-commit`
3. Rendi lo script eseguibile
    1. `chmod +x .git/hooks/pre-commit` 

---

## 8.2 Rewriting History

Il comando `git rebase -i` (rebase interattivo), permette di riscrivere la cronologia dei commit in modo raffinato. È utile per:

- Unire commit (squash).
- Rinominare messaggi (`reword`).
- Eliminare commit (`drop`).
- Riordinare commit.

```bash
git rebase -i HEAD~3
```

<aside>
⚠️

Non riscrivere la storia pubblica di un branch già condiviso, per evitare conflitti con altri collaboratori.

</aside>

---

## 8.3 Advanced Git Stash

Il comando `git stash` consente di salvare modifiche temporaneamente senza committarle. 

Esistono delle estensioni di questo comando che permettono più funzionalità :

- `git stash -u` → include anche i file non tracciati
- `git stash list` → visualizza tutti gli stash salvati
- `git stash show -p stash@{index}` → mostra le modifiche stivate
- `git stash branch <new-branch>` → crea un branch con le modifiche salvate
- `git stash pop` → rimuove lo stash dopo l’applicazione
- `git stash apply` → conserva lo stash dopo l’applicazione

## 8.4 Submodule & Subtree

Si usano quando un progetto dipende da un’altra repository Git, e puoi gestirla come :

### 8.4.1 Submodule

- Mantiene un riferimento a un commit specifico di un altro repository.
- Ideale per tenere progetti separati ma sincronizzati.
- Comandi principali
    
    ```bash
    git submodule add <link-repo>
    git submodule update --init
    ```
    
    <aside>
    ⚠️
    
    Richiede attenzione nella sincronizzazione e può complicare i flussi CI/CD.
    
    </aside>
    

### 8.4.2 Subtree

- Incorpora un repository come parte del progetto, ma consente di aggiornarlo con `merge` o `pull`.
- Più semplice da gestire rispetto ai submodule.
- Comandi principali
    
    ```bash
    git subtree add --prefix=<cartella> <repo> <branch> --squash
    git subtree pull --prefix=<cartella> <repo> <branch> --squash
    ```
    

---

## 8.5 Trovare Bug tra i Commit

Esiste un comando per automatizzare la ricerca binaria per trovare il commit che ha introdotto bug. 

```bash
git bisect start      # Inizio la ricerca
git bisect bad        # Il commit attuale è cattivo
git bisect good       # Un commit precedente funzionante
```

Git esegue il checkout a commit intermedi. A ogni passo, confermi se il commit è “good” o “bad”. Alla fine, Git indica il commit colpevole.

Si possono abbinare script con test automatici all’interno del comando stesso.

---

## 8.6 Custom Alias

Gli alias Git permettono di semplificare comandi lunghi o complessi. Si definiscono nel file `.gitconfig`

```bash
[alias]
  co = checkout
  ci = commit
  st = status
  l  = log --oneline --graph --decorate

```