---
lab:
    title: 'Lab 2. Come creare un’app canvas, parte 1'
    module: 'Modulo 3. Introduzione a Power Apps'
---

# Modulo 3. Introduzione a Power Apps

## Lab: Come creare un'app canvas, parte 1

# Scenario

Il Bellows College è un'organizzazione didattica con più edifici nel proprio campus. Le visite al campus sono attualmente registrate su documenti cartacei. Le informazioni non vengono acquisite in modo coerente e non esiste un sistema per raccogliere e analizzare i dati sulle visite in tutto il campus. 

L'amministrazione del campus vorrebbe modernizzare il proprio sistema di registrazione dei visitatori, facendo controllare l'accesso agli edifici dal personale addetto alla sicurezza e richiedendo una preregistrazione di tutte le visite da parte degli ospiti.

Durante questo corso verranno sviluppate applicazioni e si useranno le funzionalità di automazione per consentire al personale amministrativo e addetto alla sicurezza del Bellows College di gestire e controllare l'accesso agli edifici del campus.  

Nella parte 1 di questo lab si progetterà un'app canvas di Power Apps che potrà essere usata dal personale del college per gestire le visite degli ospiti.

# Procedura generale per il lab

Verrà usata la sequenza seguente per progettare l'app canvas:

-   Creare l'app dai dati tramite il modello per il fattore di forma telefono
-   Configurare una pagina di dettagli con info sulle visite
-   Configurare una pagina di modifica per creare le visite
-   Configurare un controllo raccolta per visualizzare le visite
-   Aggiungere una funzione di filtro all'origine dati della raccolta per visualizzare solo le visite future

## Prerequisiti

* Completamento del **lab 0 del modulo 0 - Convalidare l'ambiente lab**
* Completamento del **lab 1 del modulo 2 - Introduzione a Microsoft Dataverse**

## Aspetti da considerare prima di iniziare

-   Qual è il fattore di forma prevalente per i destinatari?
-   Stimare il numero di record nel sistema 
-   Come limitare i record selezionati per migliorare le prestazioni dell'app e promuoverne l'adozione da parte degli utenti

# Esercizio 1. Creare l'app canvas per il personale

**Obiettivo:** in questo esercizio si creerà un'app canvas da un modello e poi la si modificherà per includere i dati richiesti.

## Attività 1. Creare un'app canvas

In questa attività verrà creata un'app canvas con il modello di layout per il telefono basato su Microsoft Dataverse. Usando la tabella Visit da Dataverse, il modello genererà un'app di raccolta, visualizzazione e modifica per gestire le visite del campus.

1.  Come iniziare a creare un'app dai dati

    -   Accedere a <https://make.powerapps.com>.

    -   Selezionare l'**ambiente** in alto a destra se non è già impostato
        sull'ambiente Practice.

    -   Selezionare l'icona **Dataverse** in **Inizia dai dati** nella schermata iniziale.

2.  Connessione alla tabella Visite
    
    -   Selezionare **+ Nuova connessione**.

    -   Selezionare **Microsoft Dataverse** e fare clic su **Crea**.

    -   Individuare e selezionare la tabella **Visite**.

    -   Selezionare **Connetti**.

3.  Potrebbe essere visualizzata la finestra **Benvenuto in Power Apps Studio**. Fare clic su **Ignora**.

4.  Salvare l'applicazione

    -   Fare clic su **File \> Salva**.

    -   Immettere [cognome] Campus Staff come **Nome app**.

    -   Fare clic su **Salva**.

## Attività 2. Configurare il modulo dei dettagli delle visite

In questa attività si configurerà il modulo dei dettagli per visualizzare informazioni sui singoli record delle visite.

1. Selezionare la freccia **Indietro** in alto a sinistra per tornare alla definizione dell'app.

2. Espandere **DetailScreen1** in **Visualizzazione struttura ad albero**

3.  Selezionare **DetailForm1**

4.  Selezionare **Modifica campi** accanto a **Campi** nel pannello a destra.

5.  Fare clic su **Aggiungi campo**

6.  Selezionare i campi seguenti:

    * Actual End
    
    * Actual Start
    
    * Building 
    
    * Code
    
    * Scheduled End
    
    * Scheduled Start
    
    * Visitor
    
7.  Fare clic su **Aggiungi**

8.  Riorganizzare i campi nel riquadro **Campi** trascinando e rilasciando i nomi dei campi verso l'alto o verso il basso. L'ordine consigliato è:
    * Code, Name, Building, Visitor, Scheduled Start, Scheduled End, Actual Start, Actual End
    >**Suggerimento:** è possibile comprimere ogni campo facendo clic sulla freccia verso il basso accanto al nome del campo.

9.  Rimuovere il campo **Data creazione** facendo clic sui puntini di sospensione (**...**) accanto al nome del campo e selezionando **Rimuovi**. 

10.  Chiudere il riquadro **Campi**.
 
11.  Per conservare il lavoro in corso, fare clic su **File** e quindi su **Salva**. Usare la freccia indietro per tornare all'app.

## Attività 3. Configurare il modulo di modifica delle visite

In questa attività si configurerà un modulo per modificare le informazioni per le singole righe delle visite.

1.  Espandere **EditScreen1** in **Visualizzazione struttura ad albero**

2.  Selezionare **EditForm1**

3.  Selezionare il campo **Data creazione** e premere **CANC** per rimuovere il campo

4.  Selezionare **Modifica campi** nel pannello delle proprietà

5.  Fare clic su **Aggiungi campo**

6.  Selezionare i campi seguenti:

    * Building 
    
    * Scheduled End
    
    * Scheduled Start
    
    * Visitor
    
7.  Fare clic su **Aggiungi**

8.  Riorganizzare i campi nel riquadro **Campi** trascinando e rilasciando i nomi dei campi verso l'alto o verso il basso. L'ordine consigliato è:
    
    * Name, Building, Visitor, Scheduled Start, Scheduled End
    >**Suggerimento:** è possibile comprimere ogni campo facendo clic sulla freccia verso il basso accanto al nome del campo. 

9.  Chiudere il riquadro **Campi**.

10.  Per conservare il lavoro in corso, fare clic su **File** e quindi su **Salva**. Usare la freccia indietro per tornare all'app.

La schermata dovrebbe essere simile alla seguente:

![Modulo di modifica canvas](media/2-canvas-edit-form.png)

## Attività 4. Configurare la raccolta delle visite

In questa attività si configurerà la raccolta pregenerata per visualizzare il titolo, la data di inizio e la data di fine della visita. 

1.  Espandere **BrowseScreen1** in **Visualizzazione struttura ad albero**

2.  Selezionare **BrowseGallery1**

3.  Selezionare la proprietà **TemplateSize** nel pannello delle proprietà Avanzate a destra

4.  Sostituire l'espressione con la seguente `Min(150, BrowseGallery1.Height - 60)`. Sarà così garantito spazio sufficiente per ulteriori informazioni.

5.  Nell'anteprima dell'app selezionare il prima campo di data/ora nella raccolta.

6.  Nella barra della formula in alto, sostituire **ThisItem.'Created On'** con `ThisItem.'Scheduled Start'`

7.  Selezionare di nuovo il campo

8.  Premere **CTRL+C** e quindi **CTRL+V** per creare una copia del campo.

9.  Usare il mouse o la tastiera per spostare il controllo copiato verso il basso e allinearlo agli altri controlli nella raccolta, sotto l'altro campo di data/ora.

10.  Nella barra della formula in alto, sostituire **ThisItem.'Scheduled Start'** con `ThisItem.'Scheduled End'`

11.  Per conservare il lavoro in corso, fare clic su **File** e quindi su **Salva**. Usare la freccia indietro per tornare all'app.

## Attività 5. Aggiungere un filtro di data

Considerato il numero di visite in continua crescita, gli utenti hanno bisogno di una funzionalità per filtrare la raccolta delle visite. Ad esempio, potrebbe essere necessario visualizzare solo le visite future. In questa attività verrà aggiunta la possibilità di visualizzare le visite solo dopo la selezione di una data da parte dell'utente.

1. Selezionare **BrowseScreen1**

2. Selezionare il menu **Inserisci** in alto.

3. Fare clic su **Input** e selezionare **Selezione data**.

4. Usare la tastiera o il mouse per posizionare il controllo sotto la casella di ricerca.

5. Selezionare **BrowseGallery1** 

6. Ridimensionare e spostare il controllo raccolta in modo da posizionarlo sotto la selezione data e in modo da coprire lo schermo. Per ottenere questo risultato, fare clic sull'icona di ridimensionamento in alto al centro del controllo raccolta e ridimensionare il controllo in modo che inizi dopo la selezione data.

7. Con il controllo **BrowseGallery1** selezionato fare clic sulla scheda **Avanzate** del riquadro Proprietà.

8. Trovare la proprietà **Items** e fare clic nella casella di testo.

9. Trovare **[@Visits]** nell'espressione e sostituire con `Filter(Visits,'Scheduled End' >= DatePicker1.SelectedDate)`. L'espressione completa sarà simile alla seguente:

   ```
   SortByColumns(
   	Search(
        Filter(
        	Visits,
            'Scheduled End' >= DatePicker1.SelectedDate
           ),
           TextSearchBox1.Text,
       	"bc_code","bc_name"
       ),
     "bc_scheduledstart",
     If(SortDescending1, Descending, Ascending)
   )
   ```
   
10. Per conservare il lavoro in corso, fare clic su **File** e quindi su **Salva**. Usare la freccia indietro per tornare all'app.

La schermata dovrebbe essere simile alla seguente:

![Raccolta con filtro nell'app canvas](media/2-canvas-browse.png)

# Esercizio 2. Completare l'app

In questo esercizio l'applicazione verrà testata e verrà poi aggiunta alla soluzione.

## Attività 1. Testare l'app

1.  Avviare l'applicazione

    -   Selezionare **BrowseScreen1** e premere **F5** oppure fare clic sull'icona **Esegui** nell'angolo in alto a destra per visualizzare l'app in anteprima.
    
    -   L'applicazione dovrebbe essere caricata e visualizzare un elenco di visite. 
    
    -   Testare il filtro selezionando date diverse nel controllo selezione data.
    
    -   Selezionare una visita e verificare che il modulo di visualizzazione funzioni correttamente.
    
    -   Tornare alla raccolta e premere **+** per creare una nuova visita. Verificare che il modulo di modifica contenga le colonne richieste, inclusi il visitatore, l'edificio e le date di inizio e fine.
    
    -   Compilare le informazioni e inviare il modulo. Verificare che il nuovo record venga visualizzato nella raccolta.
    
    -   Creare almeno altre 2 visite.
    
    -   Premere **ESC** o fare clic sull'icona **X** per chiudere la modalità di anteprima.

2.  Salvare e pubblicare l'applicazione

    -   Fare clic su **File** e se il pulsante Salva è visualizzato fare clic su **Salva**.

    -   Fare clic su **Pubblica**.

    -   Fare clic su **Pubblica questa versione**.

    -   Fare clic sulla freccia **Indietro** per tornare all'app.

    -   Chiudere la finestra o la scheda del browser della **finestra di progettazione**.

    -   Fare clic su **Esci** se viene visualizzata una richiesta quando si tenta di chiudere la finestra del browser.

## Attività 2. Aggiungere l'app alla soluzione e pubblicare 

1. Aprire la soluzione Campus Management.

   * Accedere a <https://make.powerapps.com>
   
   * Se l'ambiente visualizzato in alto a destra non è l'ambiente Practice, selezionarlo in **Ambiente**. 
   
   * Selezionare **Soluzioni**.
   
   * Fare clic per aprire la soluzione **Campus Management**.
   
2. Selezionare **Aggiungi esistente**, quindi fare clic su **App** e infine su **App canvas**.

3. Selezionare la scheda **Outside Dataverse**.

4. Selezionare l'app **Campus Staff** e fare clic su **Aggiungi**.

5. Selezionare **Pubblica tutte le personalizzazioni**.

# Sfide

* Visualizzazione calendario di tutte le visite e filtro per intervallo di date
* Possibilità di creare e gestire contatti come parte dell'app
* Come visualizzare più riunioni durante una singola visita

