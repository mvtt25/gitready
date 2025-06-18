# 2. Concetti Fondamentali

Per usare Git in modo efficace, non basta memorizzare comandi: è essenziale **capire cosa succede dietro le quinte**. Git è uno strumento potente, e padroneggiarlo significa sviluppare una vera **mentalità da “versionamento”**.


- [2.1 Repository](#21-repository)  
  - [2.1.1 Repository Locale](#211-repository-locale)  
  - [2.1.2 Repository Remota](#212-repository-remota)  
- [2.2 Commit, Stage, Stash](#22-commit-stage-stash)  
  - [2.2.1 Commit](#221-commit)  
  - [2.2.2 Stage](#222-stage)  
  - [2.2.3 Stash](#223-stash)  
- [2.3 Branch, Merge, Rebase](#23-branch-merge-rebase)  
  - [2.3.1 Branch](#231-branch)  
  - [2.3.2 Merge](#232-merge)  
  - [2.3.3 Rebase](#233-rebase)  
  - [2.3.4 Merge vs Rebase](#234-merge-vs-rebase)  
- [2.4 Utilities](#24-utilities)  
  - [2.4.1 Tag](#241-tag)  
  - [2.4.2 HEAD](#242-head)  
- [2.5 Working Directory, Staging Area e Repository](#25-working-directory-staging-area-e-repository)



## 2.1 Repository

Un **repository (o “repo”)** è il contenitore centrale del tuo progetto in Git. Tiene traccia di:

- tutti i file e le cartelle,
- ogni modifica fatta nel tempo,
- i commit (punti di salvataggio),
- i branch (linee parallele di sviluppo),
- i tag (versioni rilasciate),
- e molto altro.

### 2.1.1 Repository Locale

È quello presente sul tuo computer, e **funziona completamente offline**. Quando esegui comandi come `git commit`, `git log`, `git branch`, stai lavorando solo sulla copia locale.

```bash
git commit
git log
git branch
```

### 2.1.2 Repository Remota

È una copia condivisa del progetto, ospitata su una piattaforma come **GitHub**, **GitLab**, **Bitbucket**. Serve per la collaborazione tra più sviluppatori.

>
>💡 **Repository Locale → Commit → Repository Remoto → Pull** 
>

## 2.2 Commit, Stage, Stash

### 2.2.1 Commit

Un **commit** è una fotografia del tuo progetto in un certo momento. Quando effettui un commit, salvi lo stato dei file tracciati con un messaggio che descrive cosa hai fatto.

Ogni commit ha:

- un **hash** univoco (es. `1a2b3c4`)
- un **autore e timestamp**
- un **messaggio** esplicativo
- un **puntatore** al commit precedente (storia lineare o ramificata)

```bash
git commit -m "Aggiunge validazione alla login form"
```

### 2.2.2 Stage

Lo stage è una “**zona intermedia**” tra la working directory e il repository.

Immagina:

- Stai lavorando su 10 file.
- Vuoi fare commit solo di 3.
- **Li aggiungi allo stage** con `git add`, poi fai `git commit` solo di quelli.

```bash
git add file1.py file2.py ## Scrivi il . per inserirli tutti
git commit -m "Messaggio di Commit"
```

### 2.2.3 Stash

Lo stash è un **nascondiglio temporaneo** per le modifiche non ancora committate.

Ti serve quando vuoi:

- passare a un altro branch velocemente,
- ma non vuoi ancora fare commit del tuo lavoro in corso.

```bash
git stash         # Salva modifiche
git switch main   # Vai su un altro branch
git stash pop     # Recupera le modifiche salvate

## Altri comandi utili
git stash save "Stash Pippo" # Per dare il nome ad uno Stash
git stash list               # Per Vedere la lista degli Stash
git stash apply stash@{index_stash}    # Per applicare uno specifico Stash
```


## 2.3 Branch, Merge, Rebase

### 2.3.1 Branch

Un **branch** è una linea indipendente di sviluppo.

Il branch `main` (o `master`) è quello principale.

Ad esempio, puoi crearne altri per:

- feature (`feature/login`)
- bugfix (`fix/logout-crash`)
- test  (`spike/refactoring`)

```bash
git branch feature/nuova-funzionalità
git switch feature/nuova-funzionalità
```

> 
> 💡 Branchare ti permette di lavorare in parallelo **senza rischiare** di rompere il codice stabile.
>

### 2.3.2 Merge

Il **merge** unisce due branch. È come dire: “porta tutto ciò che c'è in `feature` dentro `main`”.

```bash
git switch main
git merge feature/nuova-funzionalità
```

Se i file sono stati modificati in entrambi i branch, Git può chiederti di **risolvere i conflitti** manualmente.

Ci sono vari tipi di merge:

- **Fast-forward**: nessun commit parallelo → Git sposta semplicemente il puntatore
- **No fast-forward**: Git crea un nuovo commit di merge (preferito per chiarezza)

### 2.3.3 Rebase

Il **rebase** riscrive la storia del tuo branch, come se i tuoi commit fossero nati “sopra” un altro branch.

```bash
git switch feature/nuova-funzionalità
git rebase main
```

Vantaggi:

- Storia più lineare
- Nessun commit di merge

>
>   ⚠️ Non fare il rebase di repository pubbliche
>

### 2.3.4 Merge vs Rebase

- `rebase` per mantenere la tua storia pulita *prima* di fare `merge` in `main`
- `merge` per preservare la cronologia completa in ambienti collaborativi


## 2.4 Utilities

### 2.4.1

Un **tag** è un’etichetta che assegni a un commit specifico.

Utile per:

- indicare una **versione rilasciata** (`v1.0.0`)
- tenere traccia di **milestone**

```bash
git tag v1.0.0
git push origin v1.0.0
```

### 2.4.2 HEAD

`HEAD` è un **puntatore speciale** che indica:

- su quale branch sei,
- e a quale commit stai lavorando.

Ogni volta che ti sposti di branch (`git switch`), HEAD cambia.

```bash
git switch main   # HEAD → main
```



## 2.5 Working Directory, Staging Area e Repository

Per capire come funziona Git, dobbiamo distinguere tra **tre aree principali**:

- **Working Directory** → È la cartella del tuo progetto sul tuo computer, dove modifichi i file. È qui che lavori attivamente.
- **Staging Area (o Index)** → È un'area temporanea dove prepari le modifiche che vuoi includere nel prossimo commit. Serve per dire a Git *"voglio salvare queste modifiche, non tutte"*.
- **Repository (local)** → È il database locale dove Git salva in modo permanente la cronologia del progetto (i commit). Questo non è ancora il repository remoto!
- **Repository remoto (remote)** → È una copia del repository (come su GitHub, GitLab, ecc.) che può essere condivisa con altri.

```bash
echo "Hello Git" >> hellogit.txt   # Working Directory 
git add hellogit                   # Staging Area 
git commit -m "Add Minchiate"      # Aggiungi alla Repository Locale
git push                           # Aggiungi alla Repository Remota
```

