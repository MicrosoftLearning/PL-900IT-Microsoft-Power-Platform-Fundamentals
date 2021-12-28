---
lab:
    title: 'Lab. Convalidare l’ambiente lab'
    module: 'Modulo 0. Introduzione al corso'
---

Modulo 0. Introduzione al corso
=================================

Scenario
--------

Il Bellows College è un'organizzazione didattica con più edifici nel proprio campus. I visitatori del campus sono attualmente registrati su documenti cartacei. Le informazioni non vengono acquisite in modo coerente e non esiste un sistema per raccogliere e analizzare i dati sulle visite in tutto il campus.

L'amministrazione del campus vorrebbe modernizzare il proprio sistema di registrazione dei visitatori, facendo controllare l'accesso agli edifici dal personale addetto alla sicurezza e richiedendo una preregistrazione di tutte le visite da parte degli ospiti.

Durante questo corso verranno sviluppate applicazioni e si useranno le funzionalità di automazione per consentire al personale amministrativo e addetto alla sicurezza del Bellows College di gestire e controllare l'accesso agli edifici del campus.

In questo lab del modulo 0 si acquisirà un tenant di prova di Power Platform e si accederà all'interfaccia di amministrazione di Power Platform. Nell'interfaccia di amministrazione verrà creato l'ambiente **Practice** in cui verrà eseguita la maggior parte delle operazioni dei lab.

## Esercizio 1. Configurazione

### Attività 1. Acquisire il tenant di prova di Microsoft Power Platform

1. Copiare le **credenziali di Microsoft 365** dal provider di servizi di hosting per i lab autorizzato.

2. Passare a <https://powerapps.microsoft.com> e fare clic su **Prova gratis**.

3. In **Iniziamo** immettere l'indirizzo e-mail delle credenziali di Microsoft 365 nella casella di testo **Per iniziare, immetti l'account aziendale o dell'istituto di istruzione**.

4. Viene visualizzato un messaggio per confermare che si dispone di un account Microsoft esistente. Selezionare **Accedi**.

5. Immettere la password fornita dal provider di servizi di hosting per i lab autorizzato. 

6. Selezionare **Sì** per mantenere l'accesso.

7. Completare le informazioni dell'account e selezionare **Attività iniziali** per registrarsi per la propria versione di valutazione di Microsoft Power Platform.  

### Attività 2. Creare l'ambiente

1. Passare a <https://admin.powerplatform.microsoft.com> e accedere con le credenziali di Microsoft 365 se richiesto di nuovo.

2. Selezionare **Ambienti** e fare clic su **+Nuovo**.

    - In **Nome** immettere **Practice [iniziali]**. Ad esempio: Practice BL.
    
    - In **Tipo** selezionare **Versione di valutazione**. Non selezionare l'opzione Versione di valutazione (basata su abbonamento).
    
    - Impostare l'interruttore per **Creare un database per questo ambiente?** su **Sì**.
    
    - Lasciare le impostazioni predefinite per tutte le altre opzioni e fare clic su **Avanti**.
    
    - Nella scheda successiva lasciare le impostazioni predefinite per tutte le opzioni e fare clic su **Salva**.

3. L'ambiente **Practice** dovrebbe ora comparire nell'elenco Ambienti. 

    > Per il provisioning dell'ambiente potrebbero essere necessari alcuni minuti. Aggiornare la pagina se necessario.

# Esercizio 2. Effettuare il provisioning di un portale Power Apps

**Obiettivo:** effettuare il provisioning di un portale Power Apps può richiedere tempo. In questo esercizio si creerà un portale Power Apps nell'ambiente in modo da poter avviare il processo di provisioning. Questo portale verrà usato in un lab successivo.

## Attività 1. Creare un portale di Power Apps

1.  Accedere a <https://make.powerapps.com>

2.  Se l'**ambiente** visualizzato in alto a destra non è l'ambiente Practice, fare clic per selezionare l'ambiente corretto.

3.  Nella home page fare clic sul pannello **Portale da modello vuoto** in **Crea app personalizzata**

    > Se questa opzione non è visibile provare a ridurre la visualizzazione.

4.  Specificare i dettagli del nuovo portale

    -   Immettere **```Bellows College Visitors```** come **Nome** del portale.

    -   Specificare un URL univoco (**nome_univoco**.powerappsportals.com). Se il nome risulta già usato, sceglierne uno diverso.

    -   Selezionare la **Lingua** di base del portale.

    -   Fare clic su **Crea**.

    > Il processo di provisioning del portale verrà eseguito per 30-45 minuti. Non occorre aspettare, perché il processo continuerà anche mentre si procede con il prossimo modulo.
