---
lab:
    title: 'Lab 4. Come creare un’app basata su modello'
    module: 'Modulo 3. Introduzione a Power Apps'
---

# Modulo 3. Introduzione a Power Apps
## Lab 3. Come creare un'app basata su modello

### Avviso importante (a partire da novembre 2020):
Common Data Service è stato rinominato Microsoft Dataverse. Parte della terminologia in Microsoft Dataverse è stata aggiornata. Ad esempio, i riferimenti a termini come entità (ora **tabella**), campo (ora **colonna**) e record (ora **riga**) potrebbero risultare obsoleti. Tenere presente questo aspetto durante l'esecuzione dei lab. I contenuti verranno completamente aggiornati molto presto.

Per altre informazioni e per un elenco completo dei termini interessati, visitare [Che cos'è Microsoft Dataverse?](https://docs.microsoft.com/it-it/powerapps/maker/common-data-service/data-platform-intro#terminology-updates)

# Scenario

Il Bellows College è un'organizzazione didattica con più edifici nel proprio campus. I visitatori del campus sono attualmente registrati su documenti cartacei. Le informazioni non vengono acquisite in modo coerente e non esiste un sistema per raccogliere e analizzare i dati sulle visite in tutto il campus. 

L'amministrazione del campus vorrebbe modernizzare il proprio sistema di registrazione dei visitatori, facendo controllare l'accesso agli edifici dal personale addetto alla sicurezza e richiedendo una preregistrazione di tutte le visite da parte degli ospiti.

Durante questo corso verranno sviluppate applicazioni e si useranno le funzionalità di automazione per consentire al personale amministrativo e addetto alla sicurezza del Bellows College di gestire e controllare l'accesso agli edifici del campus. 

In questo lab verrà creata un'app basata su modello di Power Apps per consentire al personale di back office del campus di gestire i record delle visite per l'intero campus.

# Procedura generale per il lab

Nell'ambito della creazione dell'app basata su modello verranno eseguite le operazioni seguenti:

-   Creare una nuova app basata su modello denominata Campus Management

-   Modificare la struttura di spostamento dell'app per fare riferimento alle tabelle richieste

-   Personalizzare i moduli e le visualizzazioni delle tabelle richieste per l'app

Verranno usati i componenti seguenti:

- **Visualizzazioni**: le visualizzazioni consentono all'utente di visualizzare i dati esistenti nelle tabelle dei moduli.

- **Moduli**: in questi componenti l'utente crea nuove righe o aggiorna le righe esistenti nelle tabelle.

Entrambi questi componenti verranno integrati nell'app basata su modello per una migliore esperienza utente.

## Prerequisiti

* Completamento del **lab 0 del modulo 0 - Convalidare l'ambiente lab**
* Completamento del **lab 1 del modulo 2 - Introduzione a Microsoft Dataverse**

## Aspetti da considerare prima di iniziare

-   Quali modifiche dobbiamo apportare per migliorare l'esperienza utente?

-   Cosa dobbiamo includere in un'app basata su modello basata sul modello di dati creato?
    
-   Quali personalizzazioni possono essere effettuate nella mappa del sito di un'app basata su modello?


# Esercizio 1. Personalizzare visualizzazioni e moduli

**Obiettivo:** in questo esercizio verranno personalizzati i moduli e le visualizzazioni delle tabelle personalizzate create che verranno usati nell'app basata su modello.

## Attività 1. Modificare il modulo delle visite

1.  Accedere a <https://make.powerapps.com> se l'accesso non è già stato eseguito.

2.  Selezionare l'**ambiente**.

3.  Selezionare **Soluzioni**.

4.  Fare clic per aprire la soluzione **Campus Management**.

5.  Fare clic per aprire l'entità **Visit**.

6.  Selezionare la scheda **Moduli** e fare clic per aprire il tipo di modulo **Main**. 

    > Per impostazione predefinita, il modulo include due campi: Name (campo primario) e Proprietario.
    
7.  Selezionare **+ Campo modulo** e aggiungere i campi seguenti sotto il campo **Proprietario** trascinando le colonne nel modulo o semplicemente facendo clic sui nomi delle colonne:

    * **Building**
    * **Visitor**
    * **Scheduled Start**
    * **Scheduled End**
    * **Actual Start**
    * **Actual End** 
    
8.  Trascinare la colonna **Code** nell'intestazione del modulo. 

    > L'area dell'intestazione è quella in alto a destra nel modulo. Potrebbe essere necessario ridurre al minimo il pannello Proprietà sul lato destro della schermata per visualizzare il campo nel modulo.

9.  Con il campo **Code** ancora selezionato, selezionare la casella di controllo **Sola lettura** nel pannello Proprietà.

10.  Selezionare il campo **Proprietario**. Nel pannello Proprietà impostare la proprietà **Etichetta** del campo su **Host**

11.  Fare clic su **Salva** in alto a destra e attendere il completamento del salvataggio.

12.  Fare clic su **Pubblica** in alto a destra e attendere il completamento della pubblicazione.

13.  Fare clic su **Indietro** in alto a sinistra nella schermata. Si tornerà alla scheda Moduli
     dell'entità Visit.

## Attività 2. Modificare le visualizzazioni per le visite

In questa attività verrà modificata la visualizzazione predefinita Visit attivi/e e si creerà una nuova visualizzazione per le visite del giorno.

1.  Selezionare la scheda **Visualizzazioni** e fare clic per aprire la visualizzazione **Visit attivi/e**.

2.  Aggiungere i campi seguenti alla visualizzazione facendo clic sui campi o trascinandoli:

    *  **Code**
    *  **Visitor**
    *  **Building**
    *  **Scheduled Start** 
    *  **Scheduled End**
    
3.  Fare clic sulla colonna **Data creazione** e selezionare **Rimuovi**. Il campo **Data creazione** verrà ora rimosso dalla visualizzazione.

4.  Fare clic sulla colonna **Name** e selezionare **Rimuovi**. Il campo **Name** verrà ora rimosso dalla visualizzazione.

5.  Nel pannello Proprietà a destra fare clic su **Ordina per** e selezionare **Scheduled Start**. Fare di nuovo clic su **Scheduled Start** per impostare l'ordine decrescente.

6.  Ridimensionare la larghezza delle singole colonne in base ai dati.

7.  Fare clic su **Salva** e attendere che le modifiche vengano salvate.

8.  Fare clic su **Pubblica** e attendere il completamento della pubblicazione.

Vedremo ora come clonare la visualizzazione per creare una nuova visualizzazione per le visite del giorno.

9.  Fare clic sul collegamento **Modifica filtri** nel pannello Proprietà.

10.  Fare clic su **Aggiungi** e selezionare **Aggiungi riga**.

11.  Selezionare il campo **Scheduled Start** e quindi selezionare **Oggi** come condizione nell'elenco a discesa. 

12.  Fare clic su **[...]** nella riga **Stato** e fare clic su **Elimina**. 

13.  Fare clic su **OK** per salvare la condizione. La visualizzazione viene ora filtrata in modo da mostrare solo i record in cui la data Scheduled Start corrisponde alla data odierna.

14.  Aggiungere i campi **Actual Start** e **Actual End** alla visualizzazione. 

> **Nota:** dato che i dati non sono più filtrati in base allo stato, otterremo un elenco delle visite del giorno che include anche quelle completate. Questi campi serviranno a distinguere le visite completate da quelle in corso.

15.  Fare clic sulla **freccia in giù** accanto al pulsante Salva facendo attenzione a non fare clic sul pulsante e selezionare **Salva con nome**.

16.  Modificare il nome in **Today's Visits** e fare clic su **Salva**.

17.  Fare clic su **Pubblica** e attendere il completamento della pubblicazione.

# Esercizio 2. Creare un'applicazione basata su modello

**Obiettivo:** in questo esercizio si creerà l'app basata su modello, si personalizzerà la mappa del sito e quindi si testerà l'app.

> Verranno citati vari campi non presentati durante la creazione dell'applicazione, in particolare nelle procedure per la mappa del sito. Abbiamo scelto di prendere alcune scorciatoie a beneficio dell'esecuzione dei lab. In un'implementazione reale a questi elementi verrebbero assegnati nomi logici.

## Attività 1. Creare l'applicazione

1.  Aprire la soluzione Campus Management se non è già aperta.

    -   Accedere a <https://make.powerapps.com>

    -   Nell'ambiente Practice fare clic per aprire la soluzione **Campus Management**.
    
2.  Creare l'applicazione basata su modello

    -   Fare clic su **Nuovo**, selezionare **App** e quindi selezionare **App basata su modello**. Verrà aperta una nuova scheda.
    
    -   Immettere **[cognome] Campus Management** in Nome.

    -   Selezionare la casella di controllo **Usa soluzione esistente per creare l'app**.

    -   Selezionare **Avanti**.

    -   Selezionare la soluzione **Campus Management**.
    
    -   Fare clic su **Fine**.
    
3.  Fare clic sull'icona a forma di matita accanto a **Mappa del sito**.

4.  Modificare i titoli predefiniti

    -   Selezionare **Nuova area**.

    -   Impostare il titolo della nuova area su **Campus** nel riquadro delle proprietà a destra.

    -   Selezionare **Nuovo gruppo**.

    -   Impostare il titolo del nuovo gruppo su **Security** nel riquadro delle proprietà a destra.
    
5.  Aggiungere la tabella Contatto alla mappa del sito

    -   Selezionare **Nuova area secondaria**.

    -   Nel riquadro **Proprietà** selezionare **Entità** nell'elenco a discesa
        **Tipo**.

    -   Cercare la tabella **Contatto** nell'elenco a discesa **Entità**.
    
6.  Aggiungere la tabella Visit alla mappa del sito

    -   Selezionare il gruppo **Security** e fare clic su **Aggiungi**.

    -   Selezionare **Area secondaria**.

    -   Passare al riquadro **Proprietà**.

    -   Selezionare **Entità** nell'elenco a discesa **Tipo** e cercare
        la tabella **Visit** nell'elenco a discesa **Entità**.
    
7.  Aggiungere la tabella Building alla mappa del sito

    -   Selezionare l'area **Campus** e fare clic su **Aggiungi**.
    
    -   Selezionare **Gruppo**.
    
    -   Immettere **Settings** per **Titolo** nel riquadro **Proprietà**.
    
    -   Con il gruppo **Impostazioni** ancora selezionato, fare clic su **Aggiungi**.
    
    -   Selezionare **Area secondaria**.
    
    -   Passare al riquadro **Proprietà**.
    
    -   Selezionare **Entità** nell'elenco a discesa **Tipo** e cercare la tabella **Building** nell'elenco a discesa **Entità**.

8.  Fare clic su **Salva**. Durante il salvataggio delle modifiche verrà visualizzata la schermata di caricamento.

9.  Fare clic su **Pubblica** per pubblicare la mappa del sito e attendere il completamento della pubblicazione.

10.  Fare clic su **Salva e chiudi** per chiudere l'editor della mappa del sito. 

    > Si noterà che gli asset per le entità aggiunte alla mappa del sito sono ora disponibili nell'applicazione.
     
11.  Fare clic su **Salva** in Progettazione app.

12.  Fare clic su **Convalida** per convalidare le modifiche apportate nell'applicazione. 

>  Verranno visualizzati alcuni avvisi che possono essere ignorati perché non abbiamo aggiunto un riferimento a una visualizzazione e a un modulo specifici per le entità e gli utenti avranno accesso a tutti i moduli e le visualizzazioni per le entità **Visit** e **Building**.
     
13. Fare clic su **Pubblica**.

14.  Fare clic su **Salva e chiudi** per chiudere la finestra di progettazione dell'app.

15.  Fare clic su **Fine**.

16.  Selezionare **Soluzioni** e selezionare **Pubblica tutte le personalizzazioni**.

17.  Selezionare **App**. L'applicazione dovrebbe ora essere inclusa nell'elenco.

## Attività 2. Testare l'applicazione

1.  Avviare l'applicazione

    -   Selezionare **App** e fare clic sull'app **Campus Management**. Se l'app non viene visualizzata potrebbe essere necessario aggiornare il browser.

    -   L'applicazione verrà aperta in una nuova finestra.
    
2.  Creare un nuovo contatto

    -   L'app verrà aperta nella visualizzazione **Contatti attivi**.

    -   Fare clic su **Nuovo** nel menu principale.

    -   Specificare `John` per **Nome** e `Doe` per **Cognome**.

    -   Specificare l'indirizzo e-mail personale per **E-mail**. Questi dati verranno usati in un lab futuro. 
    
    -   Fare clic su **Salva e chiudi**.

    -   Il nuovo contatto creato dovrebbe essere ora visibile nella visualizzazione **Contatti attivi**.
    
3.  Creare un nuovo edificio

    -   Selezionare **Building** nella mappa del sito.

    -   Fare clic su **Nuovo**.

    -   Immettere `Microsoft Building` come **Name**.
        
    -   Fare clic su **Salva e chiudi**. Il nuovo record creato verrà così visualizzato
        nella visualizzazione Building attivi/e.
    
4.  Creare una nuova visita

    -   Selezionare **Visit** nella mappa del sito.
    
    -   Fare clic su **Nuovo**.
    
    -   Compilare i campi come segue 
    
        -   **Name**: `New test visit`
        -   **Building**: selezionare Microsoft Building
        -   **Visitor**: selezionare John Doe
        -   **Scheduled Start**: selezionare la data di domani e le 14.00 come ora di inizio
        -   **Scheduled End**: selezionare la data di domani e le 15.30 come ora di fine
        
    -   Fare clic su **Salva e chiudi**. Verrà così creata la visita che dovrebbe essere
        visibile nella visualizzazione Visit attivi/e.
        
    -   Passare alla visualizzazione **Today's Visits**. La nuova visita non dovrebbe essere più visibile in questa visualizzazione, perché è pianificata per il giorno successivo.
    
5. È possibile aggiungere altri record di prova.

   L'app in esecuzione dovrebbe essere simile alla seguente:

![App basata su modello di esempio](media/3-model-app.png)

# Sfide

* Selezionare visualizzazioni e moduli specifici per Visit e Building.
* Il personale addetto alla sicurezza lavora in genere in un singolo edificio. Come si può fornire un modo semplice per visualizzare solo le visite per un edificio selezionato?
* Limitare l'accesso a entità specifiche, ad esempio la tabella Building dovrebbe essere di sola lettura per tutto il personale ad eccezione degli amministratori.
* Quali dashboard si potrebbero aggiungere all'app?
