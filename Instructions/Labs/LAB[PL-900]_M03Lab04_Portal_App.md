---
lab:
    title: 'Lab 5. Come creare un portale Power Apps'
    module: 'Modulo 3. Introduzione a Power Apps'
---

# Modulo 3. Introduzione a Power Apps

## Lab 4. Come creare un portale Power Apps

### Avviso importante (a partire da novembre 2020):
Common Data Service è stato rinominato Microsoft Dataverse. Parte della terminologia in Microsoft Dataverse è stata aggiornata. Ad esempio, i riferimenti a termini come entità (ora **tabella**), campo (ora **colonna**) e record (ora **riga**) potrebbero risultare obsoleti. Tenere presente questo aspetto durante l'esecuzione dei lab. I contenuti verranno completamente aggiornati molto presto. 

Per altre informazioni e per un elenco completo dei termini interessati, visitare [Che cos'è Microsoft Dataverse?](https://docs.microsoft.com/it-it/powerapps/maker/common-data-service/data-platform-intro#terminology-updates)

# Scenario

Il Bellows College è un'organizzazione didattica con più edifici nel proprio campus. Le visite al campus sono attualmente registrate su documenti cartacei. Le informazioni non vengono acquisite in modo coerente e non esiste un sistema per raccogliere e analizzare i dati sulle visite in tutto il campus.

L'amministrazione del campus vorrebbe fornire ai visitatori informazioni sugli edifici nel campus. I visitatori potranno visualizzare l'elenco degli edifici in un sito Web che verrà creato tramite un portale Power Apps.

In questo lab verrà eseguito il provisioning di un portale Power Apps e si creerà una pagina Web del portale in cui sarà visualizzato un elenco degli edifici nel campus.

# Procedura generale per il lab

Verrà usata la sequenza seguente per progettare il portale Power Apps:

* Effettuare il provisioning di un portale Power Apps nell'ambiente Dataverse
* Creare e configurare una pagina Web per visualizzare un elenco degli edifici
* Creare un nuovo tema e applicarlo al portale

## Prerequisiti

* Completamento del **lab 0 del modulo 0 - Convalidare l'ambiente lab**
* Completamento del **lab 1 del modulo 2 - Introduzione a Microsoft Dataverse**

## Aspetti da considerare prima di iniziare

* Le app portali Power Apps vengono sempre create a partire da un modello anziché da un'applicazione vuota. Il portale dovrebbe essere già stato creato nel modulo 0 lab 0. Dopo il provisioning, il portale includerà già pagine, menu e un tema predefinito. 

# Esercizio 1. Creare una pagina Web del portale

**Obiettivo:** in questo esercizio verrà creata una nuova pagina Web in cui verrà visualizzato del contenuto statico oltre a un elenco degli edifici da Dataverse.

## Attività 1. Passare al portale

1.  Visitare <https://make.powerapps.com>.

2.  Verificare che sia attivo l'ambiente Practice. In caso contrario, cambiare l'ambiente in alto a destra.

3.  Fare clic su **App**.

4.  Individuare l'app in cui per **Tipo** è indicato **Portale**.

5.  Fare clic sul nome dell'app per aprire il portale.

    > Si verrà reindirizzati alla pagina di destinazione del sito Web del portale con un messaggio di benvenuto. Esplorare il portale per scoprire gli elementi creati per impostazione predefinita con il provisioning. 

## Attività 2. Creare una pagina Web

1.  Aprire Studio per i portali Power Apps

    -   Accedere a <https://make.powerapps.com> (potrebbe essere ancora aperto nelle schede)

    -   Selezionare **App**
    
    -   Individuare l'app in cui per **Tipo** è indicato **Portale**

    -   Fare clic sui puntini di sospensione (**...**) a destra del nome dell'app portali e scegliere **Modifica**

    > È ora attivo Studio per i portali Power Apps. Questa è la posizione in cui è possibile modificare e creare il contenuto del portale.

2.  Creare una nuova pagina

    -   Dalla barra dei comandi selezionare **Nuova pagina**

    -   Passare il mouse su **Layout fissi** e scegliere **Pagina con titolo**

3.  Nel riquadro delle proprietà, in **Visualizzazione** cambiare l'impostazione di **Nome** da **Nuova pagina (1)** a `Building Directory`

4.  In **URL parziale** impostare il valore su `building-directory` e premere TAB per avviare il salvataggio automatico

    > Il titolo della pagina dovrebbe ora essere **Building Directory**
    
## Attività 3. Aggiungere contenuto statico

1.  Aggiungere una sezione alla pagina Web

    -   Nel canvas, ovvero l'area in cui è visualizzata la pagina Web, selezionare la sezione **Copia pagina**. Si tratta del riquadro grande attorno alle 2 frasi di testo nel centro della pagina.

    -   Nella barra degli strumenti (sul lato sinistro) selezionare l'icona **Componenti**

    -   Scegliere **Sezione a due colonne** nell'area **Layout sezione**

2.  Aggiungere testo statico

    -   Nel canvas, ovvero l'area in cui è visualizzata la pagina Web, selezionare la colonna sinistra

    -   Nella barra degli strumenti (sul lato sinistro) selezionare l'icona **Componenti**

    -   Scegliere **Testo** nell'area **Componenti del portale**

    -   Immettere il testo seguente nella nuova area di testo:
          ```
          The following is the building directory.
          ```
    -   Selezionare la casella di testo sopra quella appena modificata e fare clic su **Elimina** sulla barra dei comandi per rimuovere il testo predefinito.

3. Aggiungere un'immagine

    -   Nel canvas, ovvero l'area in cui è visualizzata la pagina Web, selezionare la colonna destra

    -   Nella barra degli strumenti (sul lato sinistro) selezionare l'icona **Componenti**

    -   Scegliere **Immagine** nell'area **Componenti del portale**

    -   Nel riquadro delle proprietà fare clic su **Selezionare un'immagine**. Individuare e selezionare l'immagine **Product A.png**
    
    -   Nel riquadro delle proprietà fare clic sull'elenco a discesa della sezione **Formattazione** e impostare il valore di **Larghezza** su 70% (assicurarsi di digitare il simbolo %). Fare un po' di prove con il ridimensionamento dell'immagine fino a ottenere il risultato desiderato.

4.  Fare clic su **Esplora sito Web** per visualizzare la pagina ottenuta finora.  Si noti che il menu principale include ora l'opzione **Building Directory**.

    > Potrebbe essere necessario configurare il browser per consentire i popup.

## Attività 4. Aggiungere un componente elenco

1.  Passare alla scheda precedente e procedere al passaggio 2. Se non è disponibile, procedere come segue per tornare a questa posizione.

    -   Accedere a <https://make.powerapps.com> (potrebbe essere ancora aperto nelle schede)

    -   Individuare l'app in cui per **Tipo** è indicato **Portale**

    -   Fare clic sui puntini di sospensione (**...**) e scegliere **Modifica**
    
    -   Nella barra degli strumenti (sul lato sinistro) scegliere l'opzione **Pagine** 

    -   Individuare e selezionare la pagina **Building Directory** creata in precedenza
    
2.  Aggiungere un componente elenco alla pagina Building Directory

    -   Selezionare la sezione con due colonne.

    -   Nella barra degli strumenti (sul lato sinistro) selezionare l'icona **Componenti**.

    -   Scegliere **Sezione a una colonna** nell'area **Layout sezione**. Verrà visualizzata una sezione sotto l'immagine e il testo nella pagina Web.

    -   Selezionare la nuova sezione a una colonna nel canvas.

    -   Nella barra degli strumenti (sul lato sinistro) selezionare l'icona **Componenti**.

    -   Scegliere **Elenco** nell'area **Componenti del portale**. Nella nuova sezione verrà visualizzato un componente elenco.
    
3.  Configurare il componente elenco

    -   Selezionare il componente elenco nel canvas

    -   Nel riquadro delle proprietà sul lato destro immettere `Buildings List` nel campo **Nome**

    -   Nel campo **Tabella** scegliere **Building (bc_building)** nell'elenco a discesa

    -   In **Visualizzazioni** scegliere **Building attivi/e**

    -   Lasciare le impostazioni predefinite rimanenti
    
4.  Fare clic su **Esplora sito Web** per visualizzare la pagina. 

    > Nella pagina Web dovrebbe essere visualizzato l'elenco degli edifici recuperato dal database Dataverse.

# Esercizio 2. Modificare il tema del portale

**Obiettivo:** in questo esercizio verrà creato un nuovo tema per cambiare la combinazione colori del portale. 

## Attività 1. Applicare e modificare un tema

1.  Passare alla scheda precedente e procedere al passaggio 2. Se non è disponibile, procedere come segue per tornare a questa posizione.

    -   Accedere a <https://make.powerapps.com> (potrebbe essere ancora aperto nelle schede)

    -   Individuare l'app in cui per **Tipo** è indicato **Portale**

    -   Fare clic sui puntini di sospensione (**...**) e scegliere **Modifica**
    
2.  Applicare e personalizzare un tema di base

    -   Nella barra degli strumenti (sul lato sinistro) selezionare l'icona **Temi**
    
    -   Fare clic sull'interruttore **Abilita tema di base** per attivare questa funzionalità.
    
    -   Per una delle impostazioni predefinite fare clic sui puntini di sospensione (**...**) e scegliere **Personalizza**.
    
    -   È stata creata una copia del tema di base. 
    
    -   Nel riquadro delle proprietà sperimentare colori diversi verificando l'impatto delle modifiche sul portale.
    
    -   Rinominare il tema
    
3.  Sulla barra dei comandi fare clic su **Configurazione sincronizzazione**

Il layout dell'app dovrebbe avere una struttura simile alla seguente:

![Portale di esempio](media/9-portallabresult.jpg)

# Sfide

* Creare una visualizzazione diversa per gli edifici che includa solo il nome dell'edificio. Sarà necessario selezionare **Esplora sito Web** da Studio del portale per visualizzare le modifiche.
* Sulla barra degli strumenti fare clic sull'icona **Temi** e modificare il foglio di stile CSS del tema personalizzato.
* Creare una pagina con il componente **Modulo** e modificare un componente **Elenco** per aggiungere o modificare righe di Dataverse con il modulo.
* Selezionare **Abilita autorizzazioni tabella** nelle proprietà **Autorizzazioni** di un componente **Elenco**. Cosa succede ai dati?
* In Studio del portale selezionare l'icona dell'editor del codice sorgente `</>` per visualizzare il codice sorgente della pagina. Se si ha esperienza con il codice HTML, apportare alcune modifiche e visualizzare i risultati.
