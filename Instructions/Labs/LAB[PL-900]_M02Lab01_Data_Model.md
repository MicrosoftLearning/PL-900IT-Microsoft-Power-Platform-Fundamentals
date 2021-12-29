---
lab:
    title: 'Lab 1. Modellazione dei dati'
    module: 'Modulo 2. Introduzione a Microsoft Dataverse'
---

# Modulo 2. Introduzione a Microsoft Dataverse

# Scenario

Il Bellows College è un'organizzazione didattica con più edifici nel proprio campus. Le visite al campus sono attualmente registrate su documenti cartacei. Le informazioni non vengono acquisite in modo coerente e non esiste un sistema per raccogliere e analizzare i dati sulle visite in tutto il campus. 

L'amministrazione del campus vorrebbe modernizzare il proprio sistema di registrazione dei visitatori, facendo controllare l'accesso agli edifici dal personale addetto alla sicurezza e richiedendo una preregistrazione di tutte le visite da parte degli ospiti.

Durante questo corso verranno sviluppate applicazioni e si useranno le funzionalità di automazione per consentire al personale amministrativo e addetto alla sicurezza del Bellows College di gestire e controllare l'accesso agli edifici del campus. 

In questo lab si accederà all'ambiente predisposto in precedenza e verranno creati un database Microsoft Dataverse e una soluzione per tenere traccia delle modifiche. Verrà anche creato un modello di dati a supporto dei requisiti seguenti:

-   R1. Tenere traccia delle posizioni (edifici) delle visite al campus
-   R2. Registrare informazioni di base per identificare i visitatori e tenerne traccia 
-   R3. Pianificare, registrare e gestire le visite 

Verranno infine importati dati di esempio in Microsoft Dataverse.

# Procedura generale per il lab

Per preparare gli ambienti di apprendimento:

* Verranno creati una soluzione e un autore
* Verranno aggiunti i componenti nuovi ed esistenti necessari per soddisfare i requisiti dell'applicazione. Fare riferimento al [documento del modello di dati](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/blob/master/Allfiles/Campus%20Management.png) per una descrizione dei metadati, ovvero tabelle e relazioni. È possibile tenere premuto CTRL e fare clic o clic con il pulsante destro del mouse sul collegamento per aprire il documento del modello di dati in una nuova finestra.

La soluzione includerà varie tabelle al termine di tutte le personalizzazioni:

-   Contatto
-   Building
-   Visit

## Prerequisiti:

* Completamento del **lab 0 del modulo 0 - Convalidare l'ambiente lab**

## Aspetti da considerare prima di iniziare:

* Convenzione di denominazione

* Tipi di dati e restrizioni (ad esempio, la lunghezza massima di un nome)

* Formattazione dei valori di data/ora a supporto della facilità di localizzazione

# Esercizio 1. Creare la soluzione

## Attività 1. Creare la soluzione e l'editore

1.  Creare la soluzione

    -   Visitare <https://make.powerapps.com>. Potrebbe essere necessario ripetere l'autenticazione. Fare clic su **Accedi** e seguire le istruzioni se richiesto.

    -   Selezionare l'ambiente facendo clic su **Ambiente** nell'angolo in alto a destra sullo schermo e scegliendo l'ambiente dal menu a discesa.

    -   Selezionare **Soluzioni** dal menu a sinistra e fare clic su **Nuova soluzione**.

    -   Immettere **[cognome] Campus Management** in **Nome visualizzato**.

2.  Creare l'editore

    -   Nella sezione **Publisher** selezionare **+ Publisher**.

    -   Nella finestra visualizzata immettere **Bellows College** in **Nome visualizzato**. 

    -   Immettere **BellowsCollege** per **Nome**.
    
    -   Immettere **bc** in **Prefisso**

    -   Fare clic su **Salva**
    
    -   Fare clic su **Fine** nella finestra popup.

3.  Completare la creazione della soluzione.

    -   Fare ora clic nell'elenco a discesa **Editore** e selezionare l'editore **Bellows College**
        appena creato.

    -   Verificare che l'opzione **Versione** sia impostata su **1.0.0.0** 
    
    -   Fare clic su **Crea**.

# Esercizio 2. Aggiungere una tabella esistente e creare nuove tabelle

**Obiettivo:** in questo esercizio si aggiungerà la tabella Contatto standard e verranno create nuove tabelle personalizzate per gli edifici (Building) e le visite (Visit) nella soluzione. 

## Attività 1. Aggiungere una tabella esistente

1.  Fare clic per aprire la soluzione **Campus Management** appena creata.

2.  Fare clic su **Aggiungi esistente** e selezionare **Tabella**.

3.  Individuare la tabella **Contatto** e selezionarla.

4.  Fare clic su **Avanti**.

5.  Fare clic su **Selezionare i componenti** in Contatto.

6.  Selezionare la scheda **Visualizzazioni** e selezionare la visualizzazione **Contatti attivi**. Fare clic su
    **Aggiungi**.
    
7.  Fare di nuovo clic su **Selezionare i componenti**.

8.  Selezionare la scheda **Moduli** e selezionare il modulo **Contatto**.
    
9.  Fare clic su **Aggiungi**.

    > Dovrebbero essere selezionati **1 visualizzazione** e **1 modulo**. 
    
10.  Fare di nuovo clic su **Aggiungi**. La tabella Contatto con la visualizzazione e il modulo selezionati verranno così aggiunti alla nuova soluzione creata.

> La soluzione dovrebbe contenere ora una sola tabella: Contatto.
    
## Attività 2. Creare la tabella Building

1.  Il browser dovrebbe essere ancora aperto nella soluzione Campus Management. In caso contrario, seguire questa procedura per aprire la soluzione Campus Management:

    * Accedere a <https://make.powerapps.com> (se l'accesso non è già stato eseguito)
    
    * Selezionare **Soluzioni** e fare clic per aprire la soluzione **[cognome] Campus Management**
          appena creata.
          
2.  Creare la tabella Building

    -   Fare clic su **Nuovo** e selezionare **Tabella**.
    
    -   Immettere **Building** in **Nome visualizzato**. 
    
    -   Fare clic su **Salva**. Verrà avviato il provisioning della tabella in background e sarà possibile aggiungere altre tabelle e colonne nel frattempo.

## Attività 3. Creare la tabella Visit e le colonne

La tabella **Visit** conterrà informazioni sulle visite al campus, inclusi edificio, visitatore, ora pianificata e ora effettiva di ogni visita. 

Vogliamo assegnare a ogni visita un numero univoco che possa essere immesso e interpretato facilmente da un visitatore quando richiesto durante il processo di check-in per la visita.

> Usiamo il comportamento **Indipendente dal fuso orario** per registrare le informazioni di data e ora, perché l'ora di una visita è sempre locale rispetto alla posizione dell'edificio e non deve cambiare se visualizzata da un fuso orario diverso. 

1.  Il browser dovrebbe essere ancora aperto nella soluzione Campus Management. In caso contrario, seguire questa procedura per aprire la soluzione Campus Management:

    * Accedere a <https://make.powerapps.com> (se l'accesso non è già stato eseguito).
    
    * Selezionare **Soluzioni** e fare clic per aprire la soluzione **[cognome] Campus Management**
          appena creata.

2. Creare la tabella Visit

   * Fare clic su **Nuovo** e selezionare **Tabella**.
   
   * Immettere **Visit** in **Nome visualizzato**. 
   
   * Fare clic su **Salva**. Verrà avviato il provisioning della tabella in background e sarà possibile iniziare ad aggiungere altre colonne.

3. Creare la colonna Scheduled Start

   * Selezionare la tabella **Visit**

   * Assicurarsi che sia selezionata la scheda **Colonne** e fare clic su **Aggiungi colonna**.
   
   * Immettere **Scheduled Start** in **Nome visualizzato**.
   
   * Selezionare **Data e ora** per **Tipo di dati**.
   
   * In **Obbligatorio** selezionare **Obbligatorio**.
   
   * Espandere la sezione **Opzioni avanzate**.
   
   * In **Comportamento** selezionare **Indipendente dal fuso orario**.
   
   * Fare clic su **Fine**.

4.  Creare la colonna Scheduled End

    * Fare clic su **Aggiungi colonna**.
    
    * Immettere **Scheduled End** in **Nome visualizzato**.
    
    * Selezionare **Data e ora** per **Tipo di dati**.
    
    * In **Obbligatorio** selezionare **Obbligatorio**.
    
    * Espandere la sezione **Opzioni avanzate**.
    
    * In **Comportamento** selezionare **Indipendente dal fuso orario**.
    
    * Fare clic su **Fine**.
    
5.  Creare la colonna Actual Start

    * Fare clic su **Aggiungi colonna**.
    
    * Immettere **Actual Start** in **Nome visualizzato**.
    
    * Selezionare **Data e ora** per **Tipo di dati**.
    
    * In **Obbligatorio** mantenere **Facoltativo**.
    
    * Espandere la sezione **Opzioni avanzate**.
    
    * In **Comportamento** selezionare **Indipendente dal fuso orario**.
    
    * Fare clic su **Fine**.
    
6.  Creare la colonna Actual End

    * Fare clic su **Aggiungi colonna**.
    
    * Immettere **Actual End** in **Nome visualizzato**.
    
    * Selezionare **Data e ora** per **Tipo di dati**.
    
    * In **Obbligatorio** mantenere **Facoltativo**.
    
    * Espandere la sezione **Opzioni avanzate**.
    
    * In **Comportamento** selezionare **Indipendente dal fuso orario**.
    
    * Fare clic su **Fine**.
    
7.  Creare la colonna Code

    * Fare clic su **Aggiungi colonna**.
    
    * Immettere **Code** in **Nome visualizzato**.
    
    * Selezionare **Numerazione automatica** per **Tipo di dati**.
    
    * Selezionare **Numero prefisso data** per **Tipo di numerazione automatica**.
    
    * Fare clic su **Fine**.
    
8.  Fare clic su **Salva tabella**

# Esercizio 3. Creare relazioni

**Obiettivo:** in questo esercizio verranno aggiunte le relazioni tra le tabelle.

## Attività 1. Creare relazioni

1.  Verificare che sia ancora visualizzata la tabella **Visit** della soluzione **Campus Management**. In caso contrario, passare a tale tabella.

2.  Creare la relazione tra le tabelle Visit e Contatto

    * Selezionare la scheda **Relazioni**.
    
    * Fare clic su **Aggiungi relazione** e selezionare **Molti-a-uno**
    
    * Selezionare **Contatto** per **Correlata (uno)** 
    
    * Immettere **Visitor** per **Nome visualizzato della colonna di ricerca** 
    
    * Fare clic su **Fine**.
    
3.  Creare la relazione tra le tabelle Visit e Building

    * Fare clic su **Aggiungi relazione** e selezionare **Molti-a-uno**
    
    * Selezionare **Building** per **Correlata (uno)** 
    
    * Fare clic su **Fine**.
    
4.  Fare clic su **Salva tabella**.

5.  Selezionare **Torna alla pagina delle soluzioni** in alto a sinistra.

6.  Selezionare **Pubblica tutte le personalizzazioni**.

# Esercizio 4. Importare dati

**Obiettivo:** in questo esercizio si importeranno dati di esempio nel database Dataverse.

## Attività 1. Importare la soluzione

In questa attività si importerà una soluzione che contiene il flusso di Power Automate necessario per completare l'importazione dei dati.

1. È necessario avere a disposizione il file **DataImport_managed.zip** archiviato nel desktop. Scaricare la [soluzione di importazione dei dati](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/blob/master/Allfiles/DataImport_managed.zip?raw=true) in caso contrario.

2. Accedere a <https://make.powerapps.com>.

3. Selezionare l'ambiente **[iniziali] Practice** in alto a destra, se non è già selezionato.

4. Selezionare **Soluzioni** nel riquadro di spostamento a sinistra.

5. Fare clic su **Importa** e quindi su **Sfoglia**. Individuare il file **DataImport_managed.zip** sul desktop e selezionarlo, quindi fare clic su **Avanti**.

>   Potrebbe essere visualizzato un messaggio simile al seguente:
>
>   Dipendenze mancanti. Installare le soluzioni seguenti prima di installare questa...
>
>   Questo messaggio indica che il modello di dati non completo, che il
>   prefisso dell'editore non è **bc** o che i nomi delle tabelle **Building** e **Visits**
>   sono diversi dai nomi indicati nelle procedure precedenti.

6. Fare clic su **Avanti**. Verrà richiesto di ristabilire le connessioni. 

7. Espandere l'elenco a discesa **Seleziona una connessione** e selezionare **+ Nuova connessione**.

8. Verrà aperta una nuova finestra o scheda del browser. Selezionare **Crea** quando richiesto per la connessione. Accedere se necessario per completare la creazione della connessione.

9. Chiudere la scheda corrente in modo da poter tornare alla scheda precedente **Importa soluzione**.

10. Verificare che sia selezionata la connessione appena creata. Se la connessione non viene visualizzata, fare clic su **Aggiorna** per aggiornare l'elenco di connessioni. 

11. Fare clic su **Importa**.

12. Attendere il completamento dell'importazione.

## Attività 2. Importare dati  

1. Aprire la soluzione **Data Import**.

2. Controllare lo **Stato** del flusso **Import Data**.

3. Se lo **Stato** è **Disattivato** selezionare **[...]** accanto a **Import Data** e quindi selezionare **Attiva**.

   > **Importante:** se viene visualizzato un messaggio di errore, verificare che le tabelle e le colonne create corrispondano alle istruzioni sopra indicate.

4. Aprire il componente **Import Data**. Power Automate verrà aperto in una nuova scheda. 

5. Fare clic su **Per iniziare** se viene visualizzato un popup. 

6. Fare clic su **Esegui** e quindi fare clic su **Esegui flusso** quando richiesto.

7. Fare clic su **Fine**.

8. Attendere il completamento dell'esecuzione dell'istanza del flusso. È possibile aggiornare la tabella **Cronologia di esecuzione di 28 giorni** per verificare quando è stato eseguito il flusso. 

    > Lo scopo di questo flusso era generare dati di esempio per i prossimi lab. Nella prossima attività si verificherà che l'importazione dei dati sia riuscita. 

## Attività 3. Verificare l'importazione dei dati

1. Tornare alla scheda di Power Apps precedente. Fare clic su **Fine** nel popup. 

2. Selezionare **Soluzioni** nella barra di spostamento a sinistra e aprire la soluzione **Campus Management**.

2. Fare clic per aprire la tabella **Visit** e quindi selezionare la scheda **Dati**.

3. Fare clic su **Active Visits** nell'angolo in alto a destra per visualizzare il selettore della visualizzazione e quindi selezionare **Tutte le colonne**. Verrà così cambiata la visualizzazione usata per mostrare i dati della tabella Visit. 

    > Se la visualizzazione **Active Visits** non è visibile a causa di una risoluzione inferiore, nella stessa posizione dovrebbe essere disponibile un'icona a forma di occhio.

    > Se l'importazione è riuscita verrà visualizzato un elenco di righe di visite.

4. Fare clic su un valore qualsiasi nella colonna **Building** e verificare che il modulo Building venga aperto in una finestra separata. 

5. Chiudere la finestra aperta di recente.

6. Fare clic un valore qualsiasi nella colonna **Visitor** (potrebbe essere necessario scorrere verso destra) e verificare che il modulo Contatto venga visualizzato in una finestra separata.

7. Chiudere la finestra aperta di recente.

# Sfide

* Si potrebbe prendere in considerazione l'uso di un impegno di tipo *appuntamento* come parte della soluzione? Cosa cambierebbe?
* Come si potrebbe imporre che la data di fine pianificata sia successiva all'inizio pianificato? 
* Come si potrebbe aggiungere il supporto per più riunioni durante una singola visita?
* Come si potrebbe proteggere l'accesso agli edifici non solo per i contatti esterni ma anche per il personale interno?
* Come si potrebbe imporre l'approvazione della direzione per le visite a determinati edifici? Quali modifiche introdurrebbe il processo di approvazione nel modello di dati?

