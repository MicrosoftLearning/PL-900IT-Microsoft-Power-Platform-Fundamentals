---
lab:
    title: 'Lab 6. Come creare una soluzione automatizzata'
    module: 'Modulo 4. Introduzione a Power Automate'
---

# Modulo 4. Introduzione a Power Automate
## Lab: Come creare una soluzione automatizzata

## Scenario

Il Bellows College è un'organizzazione didattica con più edifici nel proprio campus. I visitatori del campus sono attualmente registrati su documenti cartacei. Le informazioni non vengono acquisite in modo coerente e non esiste un sistema per raccogliere e analizzare i dati sulle visite in tutto il campus. 

L'amministrazione del campus vorrebbe modernizzare il proprio sistema di registrazione dei visitatori, facendo controllare l'accesso agli edifici dal personale addetto alla sicurezza e richiedendo una preregistrazione di tutte le visite da parte degli ospiti.

Durante questo corso verranno sviluppate applicazioni e si useranno le funzionalità di automazione per consentire al personale amministrativo e addetto alla sicurezza del Bellows College di gestire e controllare l'accesso agli edifici del campus. 

In questo lab verranno creati flussi di Power Automate per automatizzare le varie parti della gestione del campus. 

# Procedura generale per il lab

Per completare il progetto sono stati identificati i requisiti seguenti:

* Il codice univoco assegnato a ogni visitatore deve essere reso disponibile al visitatore prima della visita.
* Il personale addetto alla sicurezza deve ricevere notifica nel caso i visitatori prolunghino la visita oltre il periodo pianificato.

## Prerequisiti

* Completamento del **lab 0 del modulo 0 - Convalidare l'ambiente lab**
* Completamento del **lab 1 del modulo 2 - Introduzione a Microsoft Dataverse**
* App Campus Staff creata nel **lab 2 del modulo 3 - Come creare un'app canvas, parte 2** (per i test)
* Il contatto John Doe creato con l'indirizzo e-mail personale nel **lab 4 del modulo 3 - Come creare un'app basata su modello** (per i test)

## Aspetti da considerare prima di iniziare

-   Qual è il meccanismo di distribuzione più appropriato per i codici dei visitatori?
-   Come si possono misurare i prolungamenti delle visite e applicare criteri rigidi?

# Esercizio 1. Creare il flusso di notifica per le visite

**Obiettivo:** in questo esercizio verrà creato un flusso di Power Automate che implementa il requisito. Il visitatore deve ricevere un'e-mail con il codice univoco assegnato alla visita.

## Attività 1. Creare il flusso

1.  Aprire la soluzione Campus Management.

    -   Accedere a <https://make.powerapps.com>

    -   Selezionare l'**ambiente**.

    -   Selezionare **Soluzioni**.

    -   Fare clic per aprire la soluzione **Campus Management**.

2.  Fare clic su **Nuovo** e selezionare **Automazione**, **Flusso cloud** e **Automatizzato**. L'editor di flussi Power Automate verrà aperto in una nuova finestra.

3. In **Scegliere il trigger del flusso** cercare **Microsoft Dataverse**.

4. Selezionare il trigger **Quando una riga viene aggiunta, modificata o eliminata** e fare clic su **Crea**.

   * Selezionare **Aggiunta** per **Tipo di modifica**
   
   * Selezionare **Visit** per **Nome tabella**.
   
   * Selezionare **Organizzazione** per **Ambito**.
   
   * Nel passaggio del trigger fare clic sui puntini di sospensione (**...**) e fare clic su **Rinomina**. Rinominare il trigger **"Quando viene creata una visita"**. Questa è una procedura consigliata, per consentire all'utente e agli altri editor del flusso di comprendere lo scopo del passaggio senza dover esaminare i dettagli.

5. Selezionare **Nuovo passaggio**. Questo passaggio è necessario per recuperare le informazioni sui visitatori, incluso l'indirizzo e-mail.

6. Cerca **Microsoft Dataverse**.

7. Selezionare l'azione **Recupera una riga tramite ID**. 

   * Selezionare **Contatti** per **Nome tabella**.
   
   * Nel campo **ID riga** selezionare **Visitor (Valore)** nell'elenco del contenuto dinamico.
   
   * In questa azione fare clic sui puntini di sospensione (**...**) e scegliere **Rinomina**. Rinominare l'azione **"Get the Visitor"**. Questa è una procedura consigliata, per consentire all'utente e agli altri editor del flusso di comprendere lo scopo del passaggio senza dover esaminare i dettagli.

8. Fare clic su **Nuovo passaggio**. Questo è il passaggio che creerà e invierà l'e-mail al visitatore.

9. Cercare *posta*, selezionare il connettore **Office 365 Outlook** e l'azione **Invia un messaggio di posta elettronica (v2)**.

   * Se viene richiesto di accettare i termini e le condizioni per usare questa azione, fare clic su **Accetta**.
   
   * Selezionare il campo **A** e selezionare **E-mail** nell'elenco del contenuto dinamico. Si noti che è sotto l'intestazione **Get the Visitor**. Questo significa che si sta selezionando l'indirizzo e-mail correlato al visitatore cercato nel passaggio precedente. 

   * Immettere **Your scheduled visit to Bellows College** nel campo **Oggetto**.

   * Immettere il testo seguente in **Corpo**:  
        
        > Il contenuto dinamico deve essere inserito nei campi con nome tra parentesi graffe. È consigliabile copiare e incollare prima tutto il testo e poi aggiungere il contenuto dinamico nelle posizioni corrette.
   
        ```
        Dear {First Name},

        You are currently scheduled to visit Bellows Campus from {Scheduled Start} until {Scheduled End}.

        Your security code is {Code}, please do not share it. You will be required to produce this code during your visit.

        Best regards,

        Campus Administration
        Bellows College
        ```
   
10.  Selezionare il nome di flusso **Senza titolo** in alto e rinominarlo `Visit notification`

11. Fare clic su **Salva**

    Lasciare questa scheda del flusso aperta per la prossima attività. Il flusso dovrebbe essere simile al seguente:

![immagine](https://user-images.githubusercontent.com/78555251/118340724-ccb13300-b4d9-11eb-96c2-c7b005bb9ac0.png)

## Attività 2. Convalidare e testare il flusso

1.  Aprire una nuova scheda nel browser e passare a <https://make.powerapps.com>

2.  Fare clic su **App** e selezionare l'app **Campus Staff** creata.

3.  Lasciare aperta questa scheda e tornare alla scheda precedente con il flusso. 

4.  Sulla barra dei comandi fare clic su **Test**. Selezionare **Manualmente** e quindi **Salva e verifica**.

5.  Lasciando la scheda del flusso aperta, tornare alla scheda precedente con l'app **Campus Staff**.

6.  Premere **+** per aggiungere un nuovo record di visita.

7.  Immettere **John Doe** come **Name** e scegliere un qualsiasi **Building**

8.  Scegliere **John Doe** come **Visitor**

9.  Scegliere le date preferite nel futuro per **Scheduled Start** e **Scheduled End**.

10.  Fare clic sull'icona a forma di **segno di spunta** per salvare la nuova visita

11.  Tornare alla scheda precedente con il flusso in corso di verifica. Osservare l'esecuzione del flusso. Se si verificano errori, tornare indietro e confrontare il flusso creato con quello dell'esempio precedente. Se l'e-mail è stata inviata correttamente, comparirà nella posta in arrivo. 

12.  Fare clic sulla freccia indietro sulla barra dei comandi

13.  Nella sezione **Dettagli** si noti che **Stato** è impostato su **Sì**. Questo significa che il flusso verrà eseguito ogni volta che viene creata una nuova visita, fino a quando non viene disattivato. Ogni esecuzione del flusso verrà aggiunta all'elenco **Cronologia di esecuzione di 28 giorni**.

14.  Disattivare il flusso facendo clic su **Disattiva** sulla barra dei comandi. Potrebbe essere necessario fare clic sui puntini di sospensione (**...**) per visualizzare questa opzione.

15.  Chiudere questa finestra.

# Esercizio 2. Creare il flusso del controllo di sicurezza

**Obiettivo:** in questo esercizio verrà creato un flusso di Power Automate che implementa il requisito. È necessario eseguire un controllo di sicurezza ogni 15 minuti e il personale addetto alla sicurezza deve ricevere notifica se i visitatori prolungano la visita oltre il periodo pianificato.

## Attività 1. Creare il flusso per recuperare i record

1. Aprire la soluzione Campus Management.

   -   Accedere a <https://make.powerapps.com>

   -   Selezionare l'**ambiente**.

   -   Selezionare **Soluzioni**.

   -   Fare clic per aprire la soluzione **Campus Management**.

2. Fare clic su **Nuovo** e selezionare **Automazione**, **Flusso cloud** e **Pianificato**. L'editor di flussi Power Automate verrà aperto in una nuova finestra.

3. Impostare il flusso per la ripetizione ogni **15** minuti.

4. Fare clic su **Crea**.

5. Fare clic su **Nuovo passaggio**. Cercare *corrente* e selezionare il connettore **Microsoft Dataverse**. Selezionare l'azione **Elenca righe**.

   * Immettere **Visit** per **Nome tabella**.
   
   * Fare clic su **Mostra le opzioni avanzate**

   * Immettere l'espressione seguente in **Filtra righe**

   ```
     statecode eq 0 and bc_actualstart ne null and bc_actualend eq null and Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)
   ```
   
   * Ecco il significato delle singole parti dell'espressione:
       * **statecode eq 0** filtra le visite attive (con Status uguale ad Active)
       * **bc_actualstart ne null** limita le ricerche alle visite in cui esiste un valore per Actual Start, ovvero è stato eseguito il check-in
       * **bc_actualend eq null** limita le ricerche alle visite per cui non è stato eseguito il check-out (nessun valore per Actual End) 
       * **Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)** limita le visite a quelle per cui la fine era prevista 15 minuti prima.

   * In questa azione fare clic sui puntini di sospensione (**...**) e scegliere **Rinomina**. Rinominare l'azione **"List active visits that ended more than 15 minutes ago"**. Questa è una procedura consigliata, per consentire all'utente e agli altri editor del flusso di comprendere lo scopo del passaggio senza dover esaminare i dettagli.

6.  Fare clic su **Nuovo passaggio**. Cercare *applica* e selezionare l'azione **Applica a ogni** 

7.  Selezionare **value** dal contenuto dinamico del campo **Selezionare un output dai passaggi precedenti**. Si noti che si trova sotto l'intestazione grigia **List active visits that ended more than 15 minutes ago**. Questo significa che si sta selezionando l'elenco di visite cercato nel passaggio precedente. 

8.  Recuperare i dati sull'edificio per il record correlato

    * Fare clic su **Aggiungi un'azione** all'interno del ciclo Applica a ogni.
    
    * Selezionare **Microsoft Dataverse**. 
    
    * Selezionare l'azione **Recupera una riga tramite ID**.
    
    * Selezionare **Building** come **Nome tabella**
    
    * Selezionare **Building (Valore)** come **ID riga** dal contenuto dinamico
    
    * Fare clic su **[...]** accanto a **Recupera una riga tramite ID** e selezionare **Rinomina**. Immettere **Get building** come nome del passaggio
    
9.  Recuperare i dati sul visitatore per il record correlato

    * Fare clic su **Aggiungi un'azione** all'interno del ciclo Applica a ogni.
    
    * Selezionare **Microsoft Dataverse**.
    
    * Selezionare l'azione **Recupera una riga tramite ID**.
    
    * Selezionare **Contatti** per **Nome tabella**.
    
    * Selezionare **Visitor (valore)** come **ID riga** dal contenuto dinamico
    
    * Fare clic su **[...]** accanto a **Recupera una riga tramite ID** e selezionare **Rinomina**. Immettere **Get Visitor** come nome del passaggio
    
10.  Inviare una notifica tramite e-mail

     * Fare clic su **Aggiungi un'azione** all'interno del ciclo Applica a ogni. Aggiungere l'azione **Invia un messaggio di posta elettronica (v2)** dalla connessione **Office 365 Outlook**.

11.  Immettere l'indirizzo e-mail personale in **A**

12.  Immettere il testo seguente nel campo **Oggetto**. **Full Name** indica il contenuto dinamico recuperato dal passaggio **Get visitor**.

   ```
   {Full Name} overstayed their welcome
   ```
   
13.  Immettere il testo seguente nel campo **Corpo**. **Name** indica il contenuto dinamico recuperato dal passaggio **Get building**. Potrebbe essere necessario scorrere alla fine dell'elenco.

   ```
   There is an overstay in building {Name}.
         
   Best,
         
   Campus Security
   ```

14.  Selezionare il nome di flusso **Senza titolo** nell'angolo in alto a sinistra e rinominarlo **Security Sweep**

15.  Fare clic su **Salva**

    Il flusso dovrebbe essere simile al seguente:

![Flusso pianificato del controllo di sicurezza, parte 1](media/4-power-automate-security-sweep-flow.png)

## Attività 2. Convalidare e testare il flusso

In presenza di visite che soddisfano i requisiti definiti nel flusso, il flusso inizierà a inviare e-mail all'indirizzo specificato durante la creazione del contatto John Doe in precedenza.

1. Verificare che esistano record delle visite con:

   1. Stato attivo
   
   2. Un valore nel passato per Scheduled End (più di 15 minuti)
   
   3. Un valore per Actual Start
   
   > **Nota**: per visualizzare questi dati passare a make.powerapps.com in una nuova scheda. Fare clic su Soluzioni nel riquadro sinistro per trovare la soluzione. Selezionare l'entità Visit e quindi selezionare la scheda Dati. Fare clic su Visit attivi/e nell'angolo in alto a destra per visualizzare il selettore della visualizzazione e quindi selezionare Tutte le colonne.
   
2. Passare al flusso **Security Sweep** se non è già attivo.

3. All'apertura del flusso fare clic su **Test**.

4. Selezionare **Manualmente**.

5. Fare clic su **Salva e verifica** e quindi su **Esegui flusso**.

6. Al termine dell'esecuzione del flusso fare clic su **Operazione completata**. 

7. Espandere **Applica a ogni** e quindi espandere il passaggio **Invia una notifica di posta elettronica**. Controllare i valori di **Oggetto** e **Corpo del messaggio**.

8. Selezionare la freccia indietro per tornare ai dettagli del flusso Security Sweep. Selezionare **Disattiva** sulla barra dei comandi. In questo modo si impedisce che il flusso venga eseguito in base a una pianificazione nel sistema di test.

# Sfide

* Aggiungere i valori Actual Start e Scheduled End al corpo dell'e-mail.
* Come ci si può assicurare che venga usata una formattazione delle date appropriata nel corpo dell'e-mail?
* È possibile generare una tabella con informazioni sulle visite prolungate e inviare una sola e-mail?
* È possibile generare un codice a barre per il codice della visita? Potrebbe essere utile?
