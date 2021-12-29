---
lab:
    title: 'Lab 8: Come creare un chatbot di base'
    module: 'Modulo 6: Introduzione a Power Virtual Agents'
---

# Modulo 6: Introduzione a Power Virtual Agents
## Lab: Come creare un chatbot di base

# Scenario

Il Bellows College è un'organizzazione didattica con più edifici nel proprio campus. Le visite al campus sono attualmente registrate su documenti cartacei. Le informazioni non vengono acquisite in modo coerente e non esiste un sistema per raccogliere e analizzare i dati sulle visite in tutto il campus.

Come la maggior parte delle organizzazioni, il Bellows College si trova a dover rispondere velocemente alle preoccupazioni derivanti dalla disinformazione in merito al COVID-19, le misure consigliate, i programmi e altro. In questo lab verrà creato un chatbot di Power Virtual Agents connesso alla pagina del Centro per la prevenzione e il controllo delle malattie (CDC) statunitense in cui sono disponibili domande e risposte sullo stato attuale della pandemia. Il college vuole configurare questo chatbot in modo che possa essere incorporato nel sito del portale, oltre a poter essere reso disponibile all'occorrenza man mano che i dipartimenti gestiscono la riapertura pianificata.

## Procedura generale

Verrà usata la sequenza seguente per creare il chatbot di Portal Virtual Agents:

  - Iscriversi per una versione di valutazione di Power Virtual Agents

  - Creare un bot usando le domande frequenti

  - Testare il bot

  - Modificare il messaggio di saluto predefinito

  - Pubblicare il bot

  - **Sfida bonus:** incorporare il bot nel portale

## Prerequisiti

Per completare il progetto sono stati identificati i requisiti seguenti:

  - Completamento del **lab 0 del modulo 0 - Convalidare l'ambiente lab**

  - Completamento del **lab 1 del modulo 2 - Introduzione a Microsoft Dataverse**

  - Solo esercizio bonus: completamento del **lab 4 del modulo 6 - Introduzione ai portali Power Apps** 

## Aspetti da considerare prima di iniziare

I bot possono essere utili in molti scenari diversi. Sulla base delle informazioni già note sul Bellows College, valutare altri possibili usi di un bot nell'organizzazione.

# Esercizio 1. Iscriversi per PVA e creare un nuovo bot

In questo esercizio ci si iscriverà alla versione di valutazione di Power Virtual Agents.

1.  Passare a [Power Virtual Agents](https://powerva.microsoft.com/)

2.  Fare clic su **Avvia versione di valutazione**.

3.  Eseguire l'accesso se richiesto.

4. Verrà visualizzata la finestra **Crea un nuovo bot**.

5. Immettere **Bot crisi** per **Nome** e selezionare una lingua.

6. Selezionare l'ambiente Practice in cui creare il bot e fare clic su **Crea**. Attendere che il bot venga creato. Fare clic su **Esplora bot** se richiesto.

7. Testare il bot. Digitare **Ciao** nella casella del messaggio e fare clic su **Invia**. Il bot saluterà e fornirà indicazioni su cosa può fare.

8. Chiudere la **Chat**.

9. Selezionare **Argomenti**. Il bot include alcuni argomenti utente e argomenti di sistema di esempio. Il messaggio di saluto predefinito proviene dagli argomenti di sistema.

> Nel prossimo esercizio verranno generati alcuni argomenti personalizzati dal sito delle domande frequenti del CDC. Non chiudere questa finestra del browser.

# Esercizio 2. Creare argomenti

In questo esercizio verranno generati alcuni argomenti dal sito delle domande frequenti del CDC.

1.  In una nuova scheda passare al sito delle [domande frequenti del CDC](https://www.cdc.gov/coronavirus/2019-ncov/faq.html) ed esaminarne il contenuto. Gli argomenti verranno generati da queste domande frequenti.

2.  Copiare l'URL.

3.  Tornare a Power Virtual Agents e assicurarsi che sia ancora selezionata la sezione **Argomenti**.

4.  Selezionare la scheda **Suggeriti** sotto **Argomenti**.

5.  Fare clic su **Attività iniziali**.

6.  Incollare l'URL copiato nella casella di testo **Collegamento a contenuto online** e fare clic su **Aggiungi**. Se è stato copiato l'URL completo, https:// verrà elencato due volte. Assicurarsi che l'URL elenchi il protocollo solo una volta.

7.  Fare clic su **Inizia** e attendere. L'operazione potrebbe richiedere alcuni minuti.

8.  Verranno creati alcuni argomenti suggeriti. Fare clic per aprire uno degli argomenti suggeriti.

9.  Verranno visualizzate la frase trigger e la risposta del bot. **Fare clic su Aggiungi ad argomenti.**
    
10.  L'argomento suggerito verrà aggiunto agli argomenti esistenti Selezionare tutti gli argomenti suggeriti e fare clic su **Aggiungi ad argomenti**. 

    > È possibile selezionare tutti gli argomenti con l'icona a sinistra della colonna Nome. Se viene visualizzato un messaggio di errore, riprovare.

11.  Dopo aver aggiunto gli argomenti suggeriti selezionare la scheda **Esistenti**. I nuovi argomenti verranno visualizzati con lo stato Disattivato.

12.  Usare il pulsante interruttore nella colonna **Stato** per impostare alcuni argomenti su **Attivato**. 

13.  Prendere nota della frase trigger di uno dei gli argomenti attivati per poterla usare per i test in seguito.

> Non chiudere questa finestra del browser.

# Esercizio 3. Testare gli argomenti

In questa attività verranno testati gli argomenti aggiunti.

1.  Fare clic su **Test del bot** in alto a sinistra.

2.  Fare clic su **Reimposta**.

3.  Digitare la frase trigger registrata dall'attività precedente e fare clic su **Invia**.

4.  Il bot dovrebbe fornire le informazioni corrette e chiedere se è riuscito a rispondere alla domanda. Fare clic su **Sì**.

5.  Il bot chiederà di valutare l'esperienza. Assegnare una valutazione eccellente.

6.  Il bot chiederà se può essere utile in altro modo. Fare clic su **No, grazie**.

7.  Il bot concluderà la sessione di chat.

8.  Digitare **ciao** e fare clic su **Invia**.

9.  Il bot visualizzerà un saluto e fornirà indicazioni su cosa può fare. Il bot può ora aiutare gli utenti con le domande frequenti sul COVID-19, quindi è necessario modificare il messaggio di saluto nell'attività successiva. Non chiudere questa finestra del browser.

# Esercizio 4. Modificare il messaggio di saluto

In questa attività, il messaggio di saluto verrà sostituito con un messaggio specifico per il COVID-19.

1.  Assicurarsi che sia selezionata la sezione **Argomenti** e selezionare la scheda **Esistenti**.

2.  Comprimere la sezione degli **argomenti utente**.

3.  Fare clic per aprire l'argomento **Saluti di apertura** negli argomenti di sistema. È anche possibile usare la casella di ricerca **Cerca argomenti esistenti**.

4.  L'argomento dei saluti include 52 frasi trigger. Fare clic su **Vai a canvas di creazione**.

5.  Sostituire il primo messaggio con `Hi, I’m a virtual agent. I can tell you about how COVID-19 spreads, how to protect yourself, preparing your home and family for COVID-19, symptoms, testing, and more.`

6.  Fare clic su **Salva**.

7.  Fare clic su **Test del bot** se il bot non è ancora aperto. Fare clic su **Reimposta** per reimpostare la chat.

8.  Digitare ciao e fare clic su **Invia**.

9.  Il bot risponderà con il nuovo messaggio.

# Esercizio 5. Pubblicare il bot

In questo esercizio si pubblicherà il bot.

1.  Selezionare **Pubblica** nella barra di spostamento a sinistra.

2.  Fare clic su **Pubblica**.

3.  Fare di nuovo clic su **Pubblica** e attendere il completamento della pubblicazione.

4.  Espandere **Gestisci** nella barra di spostamento a sinistra e selezionare **Canali**.

5.  Verrà visualizzato un elenco dei canali disponibili per la pubblicazione del bot. Selezionare **Sito Web demo**.

6.  Cambiare il messaggio di benvenuto in `Try my COVID-19 FAQ bot.`

7.  Immettere il testo seguente in **Elementi per avviare la conversazione**:
    ```
     “Who is at higher risk for serious illness from COVID-19”
     “What does more severe illness mean”
     “What is the CDC doing about COVID-19”
    ```
    
8.  Fare clic su **Salva**.

9.  Copiare l'**URL**.

> È possibile condividere l'URL con i colleghi e ricevere feedback da loro. 

10.  Aprire una nuova finestra o scheda del browser e passare all'URL copiato. Il sito Web demo sarà simile a quello illustrato di seguito.

11. Procedere e iniziare a chattare con il bot.  
    
Alla fine, il bot pubblicato dovrebbe essere simile all'immagine seguente:

![Sito Web demo del bot - screenshot](./media/8-image1.png)

# Sfide 
* Incorporare il chatbot nel portale dei visitatori del Bellows College. Altre informazioni su come eseguire questa operazione sono disponibili in **Aggiungere il bot al portale Power Apps** [qui](https://docs.microsoft.com/it-it/power-virtual-agents/publication-connect-bot-to-web-channels).
