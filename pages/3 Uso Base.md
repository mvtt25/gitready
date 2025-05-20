# 3. Uso Base

In questa sezione vedremo i comandi fondamentali per iniziare a usare Git nella pratica quotidiana. Si tratta delle operazioni essenziali per creare un repository, gestire i file, salvare le modifiche, e navigare nella cronologia del progetto.

---

---

## 3.1 Crea una Repository

Per iniziare ad usare Git in una Directory, basterà utilizzare il comando, che ti permette di inizializzare una nuova repository locale.

```bash
git init
```

- Crea una nuova **cartella `.git`** nella directory corrente, che contiene tutta la cronologia del progetto.
- Si usa quando vuoi iniziare a tracciare un progetto esistente con Git.

---

## 3.2 Clona una Repository

Per copiare una repository remota sulla directory locale, basterà utilizzare il comando 

```bash
git clone https://github.com/utente/repository.git
```

- Crea una copia completa di un repository remoto sul tuo computer.
- Include tutto: codice, cronologia dei commit, rami (`branches`), ecc.
- Si può anche specificare una cartella di destinazione
    
    ```bash
    git clone https://github.com/utente/repository.git {directory_cartella}
    ```
    

---

## 3.3 Aggiungere file

Posso specificare a git quali file aggiungere nel prossimo commit, tramite il comando 

```bash
git add nomefile.txt # Usare . per aggiungere tutti i file nella directory
```

- Indica a Git quali file o modifiche vuoi includere nel **prossimo commit**.
- Git separa il concetto di *modificare un file* da *prepararlo per il commit*.
- Posso aggiungere solo i file tracciati
    
    ```bash
    git add -u
    ```
    
- Posso specificare se mostrare l’output dei file
    
    ```bash
    git add . -v (verbose)
    ```
    

---

## 3.4 Creare Commit

Per salvare una “foto” dello stato dei file aggiunti, si usa il comando commit

```bash
git commit -m "Messaggio"
```

- Crea uno **snapshot** permanente dei file aggiunti con `git add`.
- Il messaggio dovrebbe spiegare chiaramente cosa è stato cambiato.

### 3.4.1 Best Practices

1. Scrivere messaggi chiari e descrittivi 
    
    `Fix login bug` 
    
2. Usa il tempo presente e imperativo
    
    `Add User Authentication` 
    
    `Update README with instructions`
    
3. Limita la lunghezza dei messaggi 
    1. Il titolo (cioè la prima riga) dovrebbe essere intorno ai 50 caratteri (massimi)
    2. Puoi aggiungere una breve descrizione di circa 72 caratteri
4. Fai Commit Piccoli e Atomici
    1. Ogni commit rappresenta una modifica piccola e atomica
    2. Evita commit che includono grandi modifiche
5. Committa Spesso per salvare i tuoi progressi
6. Controlla sempre cosa stai per committare
    1. `git status` o `git diff` per verificarne le modifiche
7. Se disponi l’utilizzo di ticket, includi il codice del ticket nel commit
    1. `Fix #132 login issues` 
8. Rivedi i commit prima di pushare
    1. `git log` o `git show`
9. Evita file inutili o temporanei
    1. Usa il file `.gitignore` 

---

## 3.5 Ignorare File

E’ utile ignorare alcune tipologie di file quando si cerca di pushare in una repository remota.

Utilizziamo un file `.gitignore` da inserire nella repository

```bash
*.log

node_modules/

*.js
```