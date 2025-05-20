# 1. Installazione e Configurazione

---

---

## 1.1 Come installare Git

Puoi scaricare Git in diversi sistemi operativi : 

- **Windows** (sconsigliato)
    1. Scarica l’installer dal [**sito ufficiale**](../Git%20Ready%201f41263a0cbc80f8adeff4f528841521.md)
    2. Avvia l’installazione e segui i passaggi guidati
    3. Puoi accettare le impostazioni predefinite, ma assicurati che : 
        1. Git Bash venga installato
        2. Git venga aggiunta alla `PATH` di Sistema
- **macOS**
    1. E’ consigliato utilizzare [**Homebrew**](https://docs.brew.sh/Installation)
        
        ```bash
        brew install git
        ```
        
- **Linux**
    - Debian/Ubuntu
        
        ```bash
        sudo apt update && sudo apt install git
        ```
        
    - Fedora/RHEL/CentOS
        
        ```bash
        sudo dnf install git # yum al posto di dnf per CentOS 7
        ```
        
    - Arch
        
        ```bash
        sudo pacman -S git
        ```
        

---

## 1.2 Configurazione Iniziale

Dopo l’installazione, bisogna configurare git fornendo alcune informazioni.

### 1.2.1 Nome Utente & E-mail

Questi dati verranno mostrati quando si farà un commit.

Puoi configurare nome utente ed e-mail, tramite:

```bash
git config --global user.name "Tuo Nome"
git config --global user.email "name@email.com"
```

### 1.2.2 Utilities

- Impostare Editor di Testo
    
    ```bash
    git config --global core.editor "code --wait"   # Visual Studio Code
    
    git config --global core.editor "nvim" # Nvim
    
    ```
    
- Abilitare colori dell’output dei comandi
    
    ```bash
    git config --global color.ui auto
    ```
    
- Aggiungere alias per comandi complessi o utilizzati frequentemente
    
    ```bash
    git config --global alias.st status
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.ci commit
    ```
    

---

## 1.3 SSH vs HTTPS

Quando interagisci con un repository remoto (es. GitHub, GitLab, Bitbucket), Git può autenticarti in due modi principali: **HTTPS** e **SSH**. Ogni metodo ha vantaggi e svantaggi.

### 1.3.1 HTTPS - Semplice, ma scomodo

- **Vantaggi**
    - Più facile da configurare se si è alle prime armi
    - Funziona dietro la maggior parte dei proxy/firewall
- **Svantaggi**
    - Richiede l’inserimento di nome utente e password/token ad ogni operazione remota
    - Richiede l’uso di un **Personal Access Token (PAT)** al posto della password su GitHub e GitLab
- **Esempio**
    
    ```bash
    https://github.com/username/repository.git
    ```
    

### 1.3.2 SSH - Avanzato, ma efficiente

- **Vantaggi**
    - Autenticazione Automatica e Sicura
    - Nessun inserimento di credenziali
- **Svantaggi**
    - Configurazione Tecnica Iniziale
    - Alcuni Firewall Aziendali potrebbero bloccarlo
- **Esempio**
    
    ```bash
    git@github.com:username/repository.git
    ```
    

### 1.3.3 Configurazione con SSH

1. Genera una chiave SSH
    
    ```bash
    ssh-keygen -t ed25519 -C "name@email.com"
    ```
    
    - Ti chiederà dove salvare la chiave
        - Il percorso di default è `~/.ssh/id_ed25519`
    - Puoi inserire una passphrase (consigliato)
2. Aggiungi la chiave creata all’agente
    
    ```bash
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_ed25519 # Percorso dove hai salvato la chiave
    ```
    
3. Aggiungi la chiave al tuo account Git remoto
    - Copia la chiave pubblica
        
        ```bash
        cat ~/.ssh/id_ed25519.pub
        ```
        
    - GitHub
        - Settings
            - SSH and GPG Keys
                - New SSH Key → Incolla la Chiave
4. Verifica la connessione SSH 
    
    ```bash
    ssh -T git@github.com
    ```
    

---