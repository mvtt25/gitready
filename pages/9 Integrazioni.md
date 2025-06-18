# 9. Integrazioni

Git, in quanto sistema di controllo di versione distribuito, diventa ancora più potente ed efficiente quando integrato con strumenti complementari. Queste integrazioni semplificano i flussi di lavoro, migliorano la collaborazione tra team e automatizzano molti processi di sviluppo.

- [9.1 VS Code](#91-vs-code)
- [9.2 Notion (a pagamento)](#92-notion-a-pagamento)
- [9.3 GitLab CI/CD](#93-gitlab-cicd)
- [9.4 GitHub Projects e Wiki](#94-github-projects-e-wiki)


## 9.1 VS Code

- **Controllo del codice versione integrato →** è possibile eseguire `commit`, `pull`, `push`, risoluzioni di merge e gestire branche direttamente dall’interfaccia grafica.
- **Diff e merge visuali →** strumenti visivi per confrontare versioni dei file e risolvere conflitti.
- **Estensioni avanzate →** estensioni come GitLens forniscono una visualizzazione dettagliata della cronologia dei commit, autore delle modifiche e spiegazioni dei cambiamenti.


## 9.2 Notion (a pagamento)

- **Changelog centralizzati →** salvare manualmente o tramite automazioni (es. webhook o API) i changelog da Git in pagine Notion.
- **Guide e documentazione →** usare Notion per mantenere guide aggiornate su branching strategy, naming convention, setup ambiente, ecc.
- **Flussi di lavoro visivi →** rappresentare processi come release flow o cicli di revisione del codice, rendendoli accessibili e condivisibili all'interno del team.


## 9.3 GitLab CI/CD

- **Build e test automatizzati →** ogni `push` o `pull request` può attivare flussi di build e test.
- **Deploy continuo →** deployment automatico in ambienti di staging, test o produzione.
- **Controlli di qualità →** code formatting, sicurezza e metriche possono essere verificati automaticamente.
- **Workflow personalizzabili →** definizione di pipeline complesse tramite file YAML (`.github/workflows/` o `.gitlab-ci.yml`).


## 9.4 GitHub Projects e Wiki

GitHub non è solo un repository di codice, ma una vera e propria piattaforma di gestione del progetto:

- **Projects →** simili a Kanban board, utili per pianificare sprint, assegnare task e monitorare l’avanzamento.
- **Issues →** gestione dei ticket per bug, nuove feature, discussioni o richieste di miglioramento, facilmente collegabili a commit e pull request.
- **Wiki →** documentazione collaborativa integrata con il repository, utile per guide tecniche, tutorial interni o architettura del progetto.