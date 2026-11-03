# SaaS Web QA Skill

[한국어](README.md) | [English](README.en.md) | [日本語](README.ja.md) | [Tiếng Việt](README.vi.md) | [Español](README.es.md) | [Português](README.pt.md) | [Français](README.fr.md) | [Deutsch](README.de.md) | Italiano

Una sola skill per verificare il funzionamento di siti e servizi SaaS, interfacce responsive e accessibilità. Adatta in modo selettivo i flussi di lavoro di skill pubbliche di Anthropic, Vercel, Microsoft e altre fonti QA. Istruzioni e liste di controllo sono incluse; le skill originali e i loro strumenti non vengono installati.

In base alla richiesta, aiuta anche a pianificare la QA in base al rischio, verificare le API, esaminare test Playwright o Cypress esistenti e analizzare gli errori. Consulta [fonti e ambito](skills/saas-web-qa/references/sources.md).

Le verifiche dopo l'accesso distinguono ruolo e spazio di lavoro autorizzati, elenchi e filtri pertinenti e ambito della verifica di persistenza. Sessioni browser separate possono comunque condividere dati sul server.

Nella QA per profili, dieci utenti simulati esplorano il servizio in un browser reale. Quando possibile, subagenti raccolgono risultati e schermate; se vengono richieste correzioni, i percorsi vengono ripetuti. Consulta la [procedura](skills/saas-web-qa/references/persona-journeys.md).

## Flusso QA

- **Diagnosi, correzione e nuova verifica:** Sia nella QA generale sia in quella per profili, le correzioni richieste vengono effettuate nell'ambito previsto e il comportamento originale viene verificato di nuovo quando il servizio attivo ha recepito le modifiche. Se non è possibile, vengono indicati il motivo e ciò che resta non verificato.
- **Percorsi distinti:** Se vengono richieste più funzioni, si definiscono punto di partenza e criterio di successo per ciascun percorso. La QA per profili distingue i risultati e registra, per ogni problema, quanti profili hanno potuto valutare il passaggio e quanti lo hanno riscontrato. I problemi sono ordinati per frequenza, evidenziando separatamente quelli gravi.
- **Prima e dopo l'accesso:** Se l'accesso è bloccato ma esiste una sessione autorizzata, le funzioni riservate possono essere verificate separatamente. Non si dichiara riuscito l'intero percorso senza interruzioni.

## Skill QA pubbliche e pratiche incorporate

I flussi delle sette skill o raccolte seguenti sono stati adattati in modo selettivo in un'unica `saas-web-qa`. I pacchetti originali, le regole complete, gli script e gli strumenti non sono inclusi né installati. Consulta link e ambito nelle [fonti](skills/saas-web-qa/references/sources.md).

| Skill o raccolta pubblica | Pratica incorporata |
| --- | --- |
| Anthropic `webapp-testing` | Esame delle pagine renderizzate prima di verificare azioni e risultati. |
| Vercel `web-design-guidelines` | Revisione di UI, usabilità, interazioni e accessibilità. |
| Microsoft `playwright-cli` | Flussi di interazione con il browser e automazione. |
| `qa-skills` | Pianificazione basata sul rischio, QA esplorativa, verifica API e segnalazione dei difetti. |
| `e2e-skills` | Revisione della qualità dei test E2E esistenti e analisi degli errori. |
| TestDino `playwright-skill` | Test del browser con la configurazione Playwright esistente del progetto. |
| `cypress-agent-skill` | Test del browser con la configurazione Cypress esistente del progetto. |

## Chiedere a un agente di installare ed eseguire la skill

Invia una richiesta come questa al tuo agente di sviluppo. Il repository deve essere pubblicato su GitHub e accessibile all'agente.

```text
Installa la skill saas-web-qa da https://github.com/Fhwang0926/saas-qa-skills
nel progetto corrente, leggi le istruzioni ed esegui la seguente QA.
Se è già installata, verifica che supporti l'attività richiesta prima di usarla.

Obiettivo: pagina di accesso del progetto corrente
Ambito: visualizzazione desktop e mobile, accesso e accessibilità
```

Per la sola installazione, richiedi l'installazione senza chiedere la QA. L'agente potrebbe richiedere una nuova sessione per rilevare la skill; se può leggere i file installati, può seguirne le istruzioni nella sessione corrente.

### Istruzioni per gli agenti

1. Identifica il progetto e l'agente e leggi le istruzioni dell'utente e del progetto. Se `saas-web-qa` è installata, leggi `SKILL.md` e i riferimenti pertinenti e verifica che supportino l'attività; il nome non prova che sia aggiornata. Riutilizzala se sufficiente. Altrimenti controlla la fonte accessibile di questo repository, l'origine dell'installazione e le modifiche locali; aggiorna secondo le regole senza sovrascrivere lavoro che non può essere sostituito in sicurezza. Se l'aggiornamento non è sicuro, usa direttamente le istruzioni della fonte quando possibile. Segnala fonti non accessibili o funzioni mancanti.
2. Se serve l'installazione, esegui il comando seguente nel progetto di destinazione. Se la selezione interattiva non è disponibile e l'agente è noto, seleziona solo quell'agente; per Codex aggiungi `--agent codex -y`. Non aggiungere `-g` senza una richiesta di installazione globale. Rispetta permessi e regole degli strumenti dell'ambiente.
3. Controlla risultato e percorso di installazione, poi leggi `SKILL.md` e i file pertinenti in `references/`. Se la skill non è registrata nella sessione ma i file sono leggibili, segui direttamente le istruzioni. Non eseguire QA se è stata richiesta solo l'installazione.
4. Usa preferibilmente il servizio già attivo e il browser disponibile. Rispetta le regole dell'utente e del progetto per build, test, avvio dei server, database e servizi esterni. Se mancano strumenti o accessi, comunica il blocco e il lavoro svolto; non dichiarare un successo non verificato.

## Installazione diretta

Dopo la pubblicazione del repository, esegui il comando nel progetto di destinazione. È richiesto Node.js 22.20 o successivo; seleziona l'agente quando richiesto.

```bash
npx skills add Fhwang0926/saas-qa-skills --skill saas-web-qa
```

Per installare da una copia locale, sostituisci il percorso con la posizione effettiva:

```bash
npx skills add /path/to/saas-qa-skills --skill saas-web-qa
```

Per impostazione predefinita l'installazione riguarda il progetto. Aggiungi `-g` per un'installazione globale. Se necessario, riavvia l'agente per rilevare la skill.

## Utilizzo

```text
$saas-web-qa Verifica la pagina di accesso su desktop e mobile e segnala i problemi riproducibili.
```

### Diagnosi, correzione e nuova verifica in una richiesta

```text
$saas-web-qa Verifica il servizio attivo con dieci profili utente simulati.
Quando possibile usa subagenti separati e controlla in un browser reale le pagine
pubbliche e le funzioni principali dopo l'accesso con un account autorizzato.
Acquisisci schermate dei punti confusi o bloccanti e indica, per ogni problema,
quanti profili hanno raggiunto il passaggio e quanti lo hanno riscontrato.
Correggi insieme i problemi confermati, ripeti i percorsi in condizioni comparabili
e comunica cosa è stato risolto e cosa rimane.
```

La skill fornisce istruzioni, non un browser, Playwright, un'applicazione attiva o account. Le verifiche reali richiedono ambiente e accessi appropriati. Prevalgono le regole dell'utente e del progetto.
