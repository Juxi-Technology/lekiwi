[English](../en/usage-guide.md) | [简体中文](../zh-hans/usage-guide.md) | [繁體中文](../zh-hant/usage-guide.md) | [Deutsch](../de/usage-guide.md) | [Español](../es/usage-guide.md) | [Français](../fr/usage-guide.md) | Italiano | [日本語](../ja/usage-guide.md) | [한국어](../ko/usage-guide.md) | [Português (BR)](../pt-br/usage-guide.md) | [Português (PT)](../pt-pt/usage-guide.md)

<title>Guida all'uso del robot mobile Lekiwi</title>

<callout emoji="💡">
Il braccio leader nero utilizza un alimentatore da 5V 6A, mentre il braccio follower bianco utilizza un alimentatore da 12V 5A.
</callout>

<figure view-type="Card">[Allegato: lerobot.zip](../en/images/lerobot.zip)</figure>

Il codice in questo repository tutorial è mantenuto alla versione stabile e testata di LeRobot precedente al 1° ottobre 2026. Da allora Hugging Face ha eseguito un aggiornamento molto consistente di LeRobot, aggiungendo moltissime nuove funzionalità. Se si desidera provare il tutorial più recente, seguire la [documentazione ufficiale](https://huggingface.co/docs/lerobot/lekiwi).



[Lekiwi](https://github.com/SIGRobotics-UIUC/LeKiwi) è un progetto di auto robotica completamente open source avviato da [SIGRobotics-UIUC](https://github.com/SIGRobotics-UIUC). Include file dettagliati per la stampa 3D e istruzioni operative, ed è progettato per essere compatibile con il framework di apprendimento per imitazione [LeRobot](https://github.com/huggingface/lerobot/tree/main). Supporta il braccio robotico SO101, consentendo un flusso di lavoro completo di apprendimento per imitazione.

[*Nel CAD online Fusion360*](https://a360.co/4k1P8yO)* è possibile visualizzare la posizione esatta dei componenti.*

[File URDF](https://gitcode.com/gh_mirrors/le/LeKiwi/tree/main)

Anteprima URDF online https://urdf.d-robotics.cc/

![Immagine che mostra un modello 3D del robot mobile Lekiwi. Il corpo è grigio e le ruote sono bianche con battistrada nero. Sulla parte superiore è montato un braccio robotico, con una telecamera all'estremità. Un'area blu nella parte inferiore è probabilmente dove si trovano la batteria o l'elettronica. L'immagine è relativa all'introduzione della guida all'uso del robot mobile Lekiwi e mostra l'aspetto e la struttura del robot per aiutare gli utenti a comprenderne meglio il design.](../en/images/d01-01.png)

## Caratteristiche principali

1. **Open source e a basso costo**: [Lekiwi](https://github.com/SIGRobotics-UIUC/LeKiwi) offre una soluzione di auto robotica open source e a basso costo.
2. **Integrazione con LeRobot**: progettato per l'integrazione con la [piattaforma LeRobot](https://github.com/huggingface/lerobot).
3. **Ricche risorse di apprendimento**: risorse di apprendimento open source complete, tra cui guide di assemblaggio e di calibrazione e tutorial per test, raccolta dati, addestramento e distribuzione, che aiutano gli utenti a iniziare rapidamente e a sviluppare applicazioni robotiche.
4. **Compatibile con Nvidia**: può essere utilizzato con il reComputer Mini J4012 Orin NX 16 GB.
5. **Applicazioni multi-scenario**: adatto a istruzione, ricerca scientifica, produzione automatizzata e robotica, aiutando gli utenti a ottenere un funzionamento robotico efficiente e preciso in una varietà di compiti complessi.

<callout emoji="⚠️">
JUXI è responsabile unicamente della qualità dell'hardware stesso. Questo tutorial viene aggiornato rigorosamente in linea con la documentazione ufficiale. Se si incontrano problemi di software o di dipendenze dell'ambiente che non si riescono davvero a risolvere, si prega di segnalarli prontamente alla [piattaforma LeRobot](https://github.com/huggingface/lerobot) o al [canale Discord di LeRobot](https://discord.gg/8TnwDdjFGU).
</callout>

<callout emoji="🔥">
**Nota**
- Tutti i servo nel telaio del Lekiwi richiedono un'alimentazione a 12V. Per gli utenti con un braccio robotico da 5V, forniamo un modulo convertitore step-down da 12V a 5V. Si noti che sarà necessario modificare il cablaggio autonomamente.
- Alimentatore da 12V – è possibile selezionare questa opzione al momento dell'ordine, se necessario. Se si dispone già di un alimentatore da 12V, è sufficiente convertire il connettore di uscita di alimentazione in una spina DC 5521.
- Controller Raspberry Pi e telecamere – devono essere acquistati separatamente tramite la pagina dell'ordine.
</callout>

## Distinta base (BOM)

<sheet sheet-id="MNu6oT" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

## Ambiente di sistema iniziale

**Per Ubuntu x86:**

- Ubuntu 22.04
- CUDA 12+
- Python 3.10
- Torch 2.6

**Per Jetson Orin:**

- Jetson JetPack 6.0
- Python 3.10
- Torch 2.3+

**Per Raspberry Pi:**

- Raspberry Pi 5, 4G\~16G

### Configurazione di SSH

Dopo aver configurato il Raspberry Pi, è opportuno abilitare e configurare [SSH](https://www.raspberrypi.com/news/coding-on-raspberry-pi-remotely-with-visual-studio-code/) (Secure Shell), così da potersi collegare al Raspberry Pi dal proprio laptop senza collegare allo Pi uno schermo, una tastiera e un mouse. Qui è disponibile un ottimo tutorial. (link) È possibile accedere al Raspberry Pi tramite il prompt dei comandi (cmd) oppure, se si utilizza VSCode, si può usare [questa](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) estensione.

## Guida alla stampa 3D

### Componenti

Forniamo file STL stampabili per i seguenti componenti stampati in 3D. Questi componenti possono essere stampati su stampanti FDM di fascia consumer utilizzando filamento PLA generico. Li abbiamo testati su una stampante Bambu Lab P1S. Per ogni componente, ci limitiamo a caricarlo in Bambu Studio, lasciamo che lo ruoti e lo disponga automaticamente, abilitiamo gli eventuali supporti consigliati e stampiamo.

<sheet sheet-id="jIOIj0" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

### Impostazioni di stampa

I file STL forniti possono essere stampati direttamente su molte stampanti FDM. Di seguito sono riportate le impostazioni testate e consigliate; anche altre impostazioni possono funzionare.

- Materiale: PLA+
- Diametro dell'ugello e precisione: diametro ugello 0.2mm, altezza layer 0.2mm
- Densità di riempimento: 15%
- Velocità di stampa: 150 mm/s
- Se necessario, caricare il G-code (file slicato) sulla stampante e avviare la stampa

# A. Installazione di LeRobot sul Raspberry Pi

Sul Raspberry Pi:

### 1. [Installare Miniconda](https://docs.anaconda.com/miniconda/install/#quick-command-line-install):

```Python
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

### 2. Riavviare la shell

Copiare e incollare il comando seguente nella shell: `source ~/.bashrc`, oppure per gli utenti Mac: `source ~/.bash_profile` o `source ~/.zshrc` (se si usa zshell).

### 3. Creare e attivare un nuovo ambiente Conda per LeRobot

```Python
conda create -y -n lerobot python=3.10
```

Quindi attivare l'ambiente Conda (è necessario farlo ogni volta che si apre una shell per usare LeRobot!):

```Bash
conda activate lerobot
```

### 4. Clonare LeRobot:

```Bash
git clone https://github.com/huggingface/lerobot.git ~/lerobot
```

### 5. Installare ffmpeg nell'ambiente:

Quando si utilizza `miniconda`, installare `ffmpeg` nel proprio ambiente:

```PowerShell
conda install ffmpeg -c conda-forge
```

<callout emoji="💡">
Di solito viene installato ffmpeg 7.X compilato con l'encoder libsvtav1 per la propria piattaforma. Se libsvtav1 non è supportato (è possibile verificare gli encoder supportati con `ffmpeg -encoders`), si può:
[Per tutte le piattaforme] Installare esplicitamente ffmpeg 7.X:
`conda install ffmpeg=7.1.1 -c conda-forge`
[Solo Linux] Installare le dipendenze di compilazione di ffmpeg e compilare ffmpeg dal sorgente con supporto a libsvtav1, assicurandosi che l'eseguibile ffmpeg in uso sia quello corretto, cosa che si può verificare con `which ffmpeg`.
Se si verifica l'errore riportato di seguito, anche i comandi sopra riportati possono risolverlo.
</callout>

![Immagine che mostra un errore riscontrato nella sezione di installazione di LeRobot della guida all'uso del robot mobile Lekiwi. L'errore mostra un ValueError sollevato durante l'esecuzione del codice del robot Lekiwi, che indica che non è stato possibile trovare alcun file di input valido nel processo worker 0 di DataLoader. L'errore si verifica nella funzione `_get_item` di `torch.utils.data.fetch.py` e nella funzione `_query_videos` di `torch.utils.data.fetch.py`, a indicare un file di input non valido. Questo errore è correlato agli errori menzionati nel contesto che possono verificarsi durante l'installazione di LeRobot.](../en/images/d01-02.png)

### 6. Installare LeRobot con la dipendenza per i motori feetech:

```Bash
cd ~/lerobot && pip install --no-binary=av -e ".[feetech]"
pip install -e ".[lekiwi]"
```

### 7. Impostare il tempo di connessione

Individuare config_lekiwi.py nella directory `lerobot\src\lerobot\robots\lekiwi`.

 connection_time_s: int = 7200 # i.e. 2 hours

![Immagine che mostra il codice del file di configurazione `config_lekiwi.py` del robot mobile Lekiwi. La parte chiave è `connection_time_s`, il cui valore è 7200, ovvero 2 ore, utilizzato per impostare il tempo di connessione dell'applicazione. L'immagine è relativa alla sezione «Impostare il tempo di connessione» e mostra dove viene impostato il tempo di connessione e il valore specifico, per aiutare gli utenti a capire come configurarlo nel file.](../en/images/d01-03.png)

# B. Installazione di LeRobot su un laptop

Se si è già installato LeRobot sul proprio laptop, è possibile saltare questo passaggio; in caso contrario, seguire gli **stessi passaggi** che abbiamo usato sul Raspberry Pi.

> [!Tip] Utilizzeremo spesso il prompt dei comandi (cmd). Se non si ha familiarità con cmd, o se si desidera rivedere l'uso della riga di comando, si può fare riferimento a questo: [Corso introduttivo sulla riga di comando](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Environment_setup/Command_line)

Sul proprio computer:

### 1. [Installare Miniconda](https://docs.anaconda.com/miniconda/install/#quick-command-line-install):

anaconda.com/download/success

Oppure fare clic su questo link per scaricare direttamente il programma di installazione

https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe

<grid>
<column width-ratio="0.500000">
![](../en/images/d01-04.png)
</column>
<column width-ratio="0.500000">
![](../en/images/d01-05.png)
</column>
</grid>

## Modifica delle sorgenti dei pacchetti di conda

```Shell
# Per prima cosa cancellare la configurazione delle sorgenti esistente (per evitare conflitti)
conda config --remove-key channels

# Sostituire le sorgenti predefinite di conda e le comuni sorgenti di terze parti con il mirror di Tsinghua
# Aggiungere le sorgenti dei pacchetti predefinite (main/r/msys2)
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2/

# Aggiungere le comuni sorgenti di terze parti
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/

# Mostrare la sorgente di download, così l'installazione dei pacchetti visualizza l'URL di download specifico
conda config --set show_channel_urls yes

# Cancellare la cache dell'indice affinché le nuove sorgenti abbiano effetto
conda clean -i

# Mostrare la configurazione corrente (per verificare che le sorgenti siano state aggiunte correttamente)
conda config --show-sources
```

### 2. Riavviare la shell

Copiare e incollare il comando seguente nella shell: `source ~/.bashrc`, oppure per gli utenti Mac: `source ~/.bash_profile` o `source ~/.zshrc` (se si usa zshell).

![Immagine che mostra l'interfaccia per individuare l'app Anaconda Prompt su un computer: dopo aver digitato «Anaconda Prompt» nella casella di ricerca, sotto «Best match» compare «Anaconda Prompt app», evidenziata con un riquadro rosso. È relativa al flusso di installazione di LeRobot sul laptop, in cui i comandi devono essere copiati e incollati nella shell dopo il passaggio di riavvio della shell. Mostra come aprire l'app Anaconda Prompt per poter eseguire i comandi successivi e prepararsi a creare e attivare un nuovo ambiente Conda per LeRobot.](../en/images/d01-06.png)

### 3. Creare e attivare un nuovo ambiente Conda per LeRobot

```Bash
conda create -y -n lerobot python=3.10
```

Quindi attivare l'ambiente Conda (è necessario farlo ogni volta che si apre una shell per usare LeRobot!):

```Bash
conda activate lerobot
```

### 4. Clonare LeRobot:

```Bash
git clone https://github.com/huggingface/lerobot.git ~/lerobot
```

### 5. Installare ffmpeg nell'ambiente:

Quando si utilizza `miniconda`, installare `ffmpeg` nel proprio ambiente:

```PowerShell
conda install ffmpeg -c conda-forge
```

<callout emoji="💡">
Di solito viene installato ffmpeg 7.X compilato con l'encoder libsvtav1 per la propria piattaforma. Se libsvtav1 non è supportato (è possibile verificare gli encoder supportati con `ffmpeg -encoders`), si può:
[Per tutte le piattaforme] Installare esplicitamente ffmpeg 7.X:
`conda install ffmpeg=7.1.1 -c conda-forge`
[Solo Linux] Installare le dipendenze di compilazione di ffmpeg e compilare ffmpeg dal sorgente con supporto a libsvtav1, assicurandosi che l'eseguibile ffmpeg in uso sia quello corretto, cosa che si può verificare con `which ffmpeg`.
Se si verifica l'errore riportato di seguito, anche i comandi sopra riportati possono risolverlo.
</callout>

![Immagine che mostra un messaggio di errore: ValueError: Caught ValueError in Dataloader worker process 0. L'errore si verifica in diversi file, come "/home/gengwei/lerobot/src/lerobot/lib/python3.10/runpy.py", e coinvolge moduli come "torch.utils.data.dataloader". Questo errore è correlato al contesto dell'installazione di LeRobot su un laptop, in cui errori come "no valid stream found in Input file" possono essere risolti installando esplicitamente ffmpeg 7.X o compilando ffmpeg dal sorgente con supporto a libsvtav1.](../en/images/d01-07.png)

### 6. Installare LeRobot con la dipendenza per i motori feetech:

```Bash
cd ~/lerobot && pip install --no-binary=av -e ".[feetech]"
pip install -e ".[lekiwi]"
```

# C. Configurazione dei motori

<grid>
<column width-ratio="0.473717">
![Immagine che mostra il braccio robotico del robot mobile Lekiwi. Il braccio è composto da diversi componenti in plastica bianca, ciascuno contrassegnato da un numero generato automaticamente. I due componenti all'estremità anteriore del braccio sono numerati 1 e 2, quelli centrali 3 e 4 e quelli all'estremità più lontana 5 e 6. Questa immagine è relativa alla sezione «Configurazione dei motori» e aiuta a spiegare come identificare i componenti del braccio robotico quando si individua la porta USB ad esso associata, in preparazione alla configurazione dei motori.](../en/images/d01-08.png)
</column>
<column width-ratio="0.526283">
![Immagine che mostra la struttura del telaio del robot mobile Lekiwi, con le posizioni ID di tre motori etichettate. ID = 7 (sinistra) si trova sul lato sinistro del telaio.](../en/images/d01-09.png)
</column>
</grid>

### **1. Individuare la porta USB associata al braccio robotico**

Per individuare la porta corretta per un singolo motore, eseguire due volte il seguente script di utilità:

```Bash
lerobot-find-port
```

Esempio di output (ad esempio, `/dev/tty.usbmodem575E0031751` su Mac, o eventualmente `/dev/ttyACM0` su Linux):

Esempio di output (ad esempio, `/dev/tty.usbmodem575E0032081` su Mac, o eventualmente `/dev/ttyACM1` su Linux):

Risoluzione dei problemi: su Linux, potrebbe essere necessario concedere l'accesso alla porta USB con i seguenti comandi:

```Bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

### **2. Configurare i motori (saltare questo passaggio per un'unità già assemblata)**

Collegare un motore del telaio alla volta ed eseguire il seguente script. Per prima cosa inizializza i servo del braccio robotico (ID 6..1), poi inizializza i servo del telaio, impostando i loro ID su (ID 9..7). Se il braccio robotico è già stato calibrato, è possibile continuare a premere Invio per sovrascrivere e saltare:

```Bash
lerobot-setup-motors \
    --robot.type=lekiwi \
    --robot.port=/dev/tty.usbmodem58760431551 # <- incollare qui la porta individuata nel passaggio precedente
```

![Immagine che mostra la struttura del telaio del robot mobile Lekiwi, con le posizioni ID di quattro motori etichettate. ID = 7 (sinistra) si trova sul lato sinistro.](../en/images/d01-10.png)

### 3. Configurare il mirror cinese di Hugging Face

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Aggiungere in fondo al file
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# Output
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# Aggiungere in fondo al file
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Output
# https://hf-mirror.com
```

#### ① Creare un token

https://huggingface.co/settings/tokens

![Immagine che mostra la pagina «Access Tokens» del sito Hugging Face. A sinistra sono visibili un avatar utente e informazioni come «Zihao Zhang TommyZihao», con opzioni come Profile e Account al di sotto. A destra è mostrato «User Access Tokens» con il pulsante «+ Create new token» evidenziato da un riquadro rosso. In fondo alla pagina è riportato «You have no Access Token». Questa immagine è relativa al passaggio «Creare un token» e guida gli utenti a creare un nuovo token sul sito Hugging Face.](../en/images/d01-11.png)

![Immagine che mostra l'interfaccia per creare un nuovo Access Token su Hugging Face. A sinistra sono visibili un avatar utente e opzioni come «Profile». A destra è visualizzato il titolo «Create new Access Token», con le opzioni «Fine-grained», «Read» e «Write» sotto Token type, di cui «Write» è evidenziata da un riquadro rosso. La sezione Token presenta un campo di input «Token name» con l'esempio «ierobot_zhao_token», con una nota al di sotto che indica che questo token ha permessi di lettura e scrittura. In fondo si trova un pulsante verde «Create token». Questa immagine è relativa al passaggio ①, Creare un token, della sezione «Configurare il mirror cinese di Hugging Face», e mostra l'interfaccia delle impostazioni per creare un token.](../en/images/d01-12.png)

#### ② Registrare il token

![](../en/images/d01-13.png)

#### ③ Associare il token

```Shell
hf auth login

hf auth whoami
```

![Immagine di una finestra di terminale durante il login con lo strumento da riga di comando di Hugging Face su Mac. A sinistra è mostrato il comando «hf auth login»; l'output a destra indica che il token è stato salvato, che il token è «lerobot_zihao_token» e che il token attualmente attivo è anch'esso «lerobot_zihao_token». In fondo l'utente è indicato come «TommyZihao». Questa immagine corrisponde alla parte relativa alla creazione del token del passaggio «Configurare il mirror cinese di Hugging Face» e mostra il riscontro del terminale dopo la corretta creazione di un token.](../en/images/d01-14.png)

#### ④ Creare un repository di dataset

**Annotare l'Owner e il nome del dataset, ovvero <hf_username> e <dateset_repo_id>, che serviranno in seguito**

<grid>
<column width-ratio="0.480604">
![Immagine che mostra l'interfaccia della piattaforma Hugging Face. Nell'angolo in alto a destra è presente un'icona avatar; facendovi clic si apre un menu a discesa in cui l'opzione «New Dataset», situata verso la parte centro-inferiore del menu, è evidenziata con un riquadro rosso. Questa immagine corrisponde al passaggio «Creare un repository di dataset» e guida gli utenti a creare un dataset sulla piattaforma Hugging Face; è una delle istruzioni operative del flusso «Configurare il mirror cinese di Hugging Face».](../en/images/d01-15.png)
</column>
<column width-ratio="0.519396">
![Immagine che mostra l'interfaccia per creare un nuovo repository di dataset sulla piattaforma Hugging Face. «Owner» è impostato su TommyZihao, «Dataset name» è compilato con «lerobot_zihao_dataset_a», «License» è impostato su mit e l'opzione «Public» è selezionata. In fondo si trova un pulsante «Create dataset». Questa immagine è relativa al passaggio «Creare un repository di dataset» e registra informazioni come l'Owner e il nome del dataset al momento della creazione di un dataset; è un passaggio necessario prima di caricare i file.](../en/images/d01-16.png)
</column>
</grid>

![Immagine che mostra una pagina Dataset sulla piattaforma Hugging Face. La pagina riporta il nome del dataset «TommyZihao/lezrobot_zihao_dataset_a» e schede come «Files and versions», «Community» e «Settings». A sinistra è presente una sezione «Getting started with your dataset» con opzioni come «Complete dataset information» e «Edit Dataset Card». A destra è presente un'area «Push your dataset files» che offre diversi metodi di caricamento — CLI, Python, Git, HTTPS, SSH — insieme a una nota secondo cui la CLI di Hugging Face deve essere installata e connessa. Questa immagine è relativa al passaggio «Configurare il mirror cinese di Hugging Face» e guida gli utenti a lavorare con un Dataset sulla piattaforma Hugging Face.](../en/images/d01-17.png)

### 4. Aggiornare la configurazione!!!

I file di configurazione sul LeKiwi LeRobot e sul laptop devono rimanere coerenti. Innanzitutto, dobbiamo individuare l'**indirizzo IP** del Raspberry Pi che pilota il braccio mobile. È lo stesso indirizzo IP utilizzato per SSH. Dobbiamo inoltre individuare la **porta USB** della scheda driver del servo del braccio leader sul laptop e la **porta della scheda driver del servo sul LeKiwi**. È possibile individuare queste porte con il seguente script.

Su Linux, potrebbe essere necessario concedere l'accesso alla porta USB eseguendo i seguenti comandi:

```Bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

Importante: ora che si dispone della porta del braccio leader e dell'indirizzo IP del braccio del Lekiwi, aggiornare l'**ip** nella configurazione di rete, la **port** nella configurazione del braccio leader e **port, remote_ip** nella configurazione del LeKiwi.

Modificare questi quattro file nella directory example\lekiwi

![Immagine che mostra la directory contenente i file che devono essere modificati durante la configurazione dei motori del robot mobile Lekiwi. Il percorso è costituito dalle cartelle «examples» e «lekiwi» all'interno della cartella del robot «ler» nella cartella «软件» sul disco D. La directory mostra quattro file sorgente Python — evaluate.py, record.py, replay.py e teleoperate.py — tutti con data di modifica 24 aprile 2026, 11:45, tutti file sorgente Python, di dimensioni rispettivamente di 6KB, 6KB, 3KB e 3KB. Questa immagine corrisponde ai contenuti precedenti sulla modifica di quattro file nella directory example\lekiwi.](../en/images/d01-18.png)

#### ① Modificare teleoperate.py

remote_ip: l'indirizzo IP del Raspberry Pi

port: il numero di porta quando il braccio leader è collegato al computer o a Linux

![Immagine che mostra parte del file teleoperate.py in fase di modifica durante la configurazione dei motori del robot mobile Lekiwi. Le informazioni chiave sono il parametro robot_config alla riga 30, il cui remote_ip è impostato su «172.18.134.136» e il cui id è «my_lekiwi»; e il parametro teleop_arm_config alla riga 31, la cui port è impostata su «/dev/tty.usbmodem585A0077581» e il cui id è my. Questi parametri configurano il collegamento tra il robot e il braccio leader, sono correlati ai contenuti sull'aggiornamento della configurazione e costituiscono una parte importante del passaggio di modifica del file.](../en/images/d01-19.png)

#### ② Modificare record.py

HF_REPO_ID: [nome utente e nome del dataset di Hugging Face](https://juxitech.feishu.cn/wiki/A2orwQ9xzidMCjk10SVcAAWVnhd?fromScene=spaceOverview#share-TYrIdHmPPobd1mx9xB7c75WEn0d)

remote_ip: l'indirizzo IP del Raspberry Pi

port: il numero di porta quando il braccio leader è collegato al computer o a Linux

![Immagine che mostra la configurazione di record.py](../en/images/d01-20.png)

#### ③ Modificare replay.py

remote_ip: l'indirizzo IP del Raspberry Pi

<hf_username>/<dataset_repo_id>, ovvero il [nome utente e nome del dataset di Hugging Face](https://juxitech.feishu.cn/wiki/A2orwQ9xzidMCjk10SVcAAWVnhd?fromScene=spaceOverview#share-TYrIdHmPPobd1mx9xB7c75WEn0d)

![Immagine che mostra il codice di replay.py in fase di modifica nella guida all'uso del robot mobile Lekiwi. Nel codice, il parametro robot_config alla riga 29 è modificato per includere remote_ip e id, dove remote_ip è «172.18.134.136» e id è «lekiwi»; il parametro dataset alla riga 36 è modificato per includere <hf_username>/<dataset_repo_id>, ovvero il [nome utente e nome del dataset di Hugging Face].](../en/images/fix-01.png)

# D. Calibrazione

Ora dobbiamo calibrare il braccio leader e il braccio follower. I servo delle ruote omnidirezionali non necessitano di calibrazione.

### Calibrazione del braccio follower (montato sulla base del Lekiwi)

Eseguire il seguente comando sul proprio computer per calibrare il braccio leader. Nota: le immagini mostrate qui sono esempi per il modello SO101.

```Bash
lerobot-calibrate \
    --teleop.type=so100_leader \
    --teleop.port=/dev/tty.usbmodem58760431551 \ # change to the port you found
    --teleop.id=my_awesome_leader_arm
```

Ora eseguire il seguente comando sul Raspberry Pi per calibrare il braccio follower sul LeKiwi. Ignorare la sua posizione attuale sul tavolo: una calibrazione corretta va eseguita con il braccio montato sul telaio del Lekiwi.

```Bash
lerobot-calibrate \
    --robot.type=lekiwi \
    --robot.id=my_awesome_kiwi
```

Abbiamo standardizzato il metodo di calibrazione per la maggior parte dei robot. Innanzitutto, dobbiamo muovere il robot in modo che ogni articolazione si trovi al **centro della propria corsa**, quindi premere il pulsante. In secondo luogo, muoviamo tutte le articolazioni attraverso la loro **intera corsa** una volta. È possibile trovare un video dello stesso processo di calibrazione per l'SO101 [qui](https://huggingface.co/docs/lerobot/en/so101#calibration-video) `Enter`.

# E. Teleoperazione

Aprire un nuovo Anaconda Prompt

![Immagine che mostra l'interfaccia per aprire un nuovo Anaconda Prompt. Mostra una finestra di Anaconda Prompt già aperta e l'elenco che compare dopo aver fatto clic sulla freccia a discesa a destra del «+» nell'angolo in alto a destra; una freccia rossa punta all'opzione «Anaconda Prompt (miniconda3)» in quell'elenco. Questa immagine è relativa ai contenuti sull'apertura di un nuovo Anaconda Prompt per la teleoperazione del robot mobile Lekiwi e mostra i passaggi specifici per aprire Anaconda Prompt per aiutare i lettori a comprendere il processo.](../en/images/d01-21.png)

> Se si utilizza un Mac, potrebbe essere necessario concedere a «Terminale» l'autorizzazione ad accedere alla tastiera per la teleoperazione. Andare in «Preferenze di Sistema» > «Sicurezza e privacy» > «Monitoraggio input» e selezionare la casella «Terminale».

Per teleoperare, accedere al Raspberry Pi tramite SSH, eseguire il seguente comando per attivare l'ambiente `conda activate lerobot`, quindi eseguire il seguente script:

```Bash
python -m lerobot.robots.lekiwi.lekiwi_host --robot.id=my_awesome_kiwi
```

![Immagine che mostra l'interfaccia dopo l'attivazione dell'ambiente `conda activate lerobot` e l'esecuzione dello script su un laptop. In alto è mostrato «Anaconda PowerShell Prompt» e, sotto, «WARNING:root:No command available» è ripetuto più volte, terminando con «WARNING:root:Command not received for more than 500 milliseconds. Stopping the base.». È relativa ai passaggi di teleoperazione e mostra le informazioni sulla connessione al robot remoto e sul flusso video che compaiono dopo l'attivazione dell'ambiente e l'esecuzione dello script, in preparazione al movimento del braccio di controllo e alla guida del robot con la tastiera.](../en/images/d01-22.png)

Successivamente, sul proprio laptop, eseguire anch'esso il seguente comando per attivare l'ambiente `conda activate lerobot`, quindi eseguire il seguente script:

```Bash
python examples/lekiwi/teleoperate.py
```

Lo schermo del proprio laptop dovrebbe mostrare qualcosa di simile: `[INFO] Connected to remote robot at tcp://172.17.133.91:5555 and video stream at tcp://172.17.133.91:5556.` Ora è possibile muovere il braccio di controllo e usare i tasti (W, A, S, D) della tastiera per guidare il robot avanti, a sinistra, indietro e a destra. Usare i tasti (Z, X) per far girare il robot a sinistra o a destra. Usare i tasti (R, F) per aumentare o diminuire la velocità del robot. Ci sono tre modalità di velocità; vedere la tabella seguente:

<sheet sheet-id="vJeIqV" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

<sheet sheet-id="iR6oYP" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

<callout emoji="💡">
Se si utilizza una tastiera diversa, è possibile modificare l'associazione dei tasti per ciascun comando in [`LeKiWiClientConfig`](https://github.com/huggingface/lerobot/blob/main/src/lerobot/robots/lekiwi/config_lekiwi.py).
</callout>

## Risoluzione dei problemi di comunicazione

In caso di problemi di connessione con il robot mobile SO101, seguire i passaggi riportati di seguito per diagnosticare e risolvere il problema.

### 1. Verificare la configurazione dell'indirizzo IP

Assicurarsi che nel file di configurazione sia impostato l'indirizzo IP corretto del Raspberry Pi. Per verificare l'indirizzo IP del Raspberry Pi, eseguire il seguente comando (nella riga di comando del Pi):

```Bash
hostname -I
```

### 2. Verificare se il laptop/PC riesce a raggiungere il Pi

Provare a eseguire il ping del Raspberry Pi dal laptop:

```Bash
ping <your_pi_ip_address>
```

Se il ping non riesce:

- Assicurarsi che il Pi sia acceso e collegato alla stessa rete.
- Verificare se SSH è abilitato sul Pi.

### 3. Provare una connessione SSH

Se non è possibile accedere al Pi tramite SSH, la connessione potrebbe non essere corretta. Utilizzare il seguente comando:

```Bash
ssh <your_pi_user_name>@<your_pi_ip_address>
```

Ad esempio `ssh pi@192.168.0.106`

Se si riceve un errore di connessione:

- Assicurarsi che SSH sia abilitato sul Pi; è possibile eseguire il seguente comando:

```Bash
sudo raspi-config
```

- Quindi navigare fino a: **Interfacing Options -> SSH** e abilitarlo.

### 4. Coerenza dei file di configurazione!!!

Assicurarsi che i file di configurazione sul laptop/PC e sul Raspberry Pi siano esattamente identici.

# F. Registrazione di un dataset

Una volta acquisita familiarità con la teleoperazione, è possibile utilizzare il LeKiwi per registrare il primo dataset.

Per avviare il programma sul LeKiwi, collegarsi al Raspberry Pi tramite SSH ed eseguire i seguenti comandi per attivare l'ambiente e avviare lo script:

```Bash
conda activate lerobot

python -m lerobot.robots.lekiwi.lekiwi_host --robot.id=my_awesome_kiwi
```

Se si desidera utilizzare Hugging Face Hub per caricare i dataset e non si è mai effettuato l'accesso in precedenza, assicurarsi di accedere con un token con permessi di scrittura, che è possibile generare in [Hugging Face settings](https://huggingface.co/settings/tokens):

```Bash
hf auth login
```

Memorizzare il nome del repository Hugging Face in una variabile per eseguire il seguente comando:

```Bash
hf auth whoami
```

Quindi eseguire il seguente comando sul proprio laptop per registrare 2 episodi e caricare il dataset su Hub:

```Bash
python examples/lekiwi/record.py
```

# G. Visualizzazione di un dataset

Se è stato caricato il dataset, è possibile [visualizzarlo online](https://huggingface.co/spaces/lerobot/visualize_dataset); copiare e incollare l'ID del repository prodotto dal seguente comando:

```Bash
echo ${HF_USER}/my_lekiwi_dataset
```

Se non è stato caricato il dataset, è possibile visualizzarlo anche localmente (lo strumento di visualizzazione si apre in una finestra del browser all'indirizzo `http://127.0.0.1:9090`):

```Bash
python lerobot/scripts/visualize_dataset_html.py \
  --repo-id ${HF_USER}/lekiwi_test \
  --local-files-only 1
```

### Visualizzare un dataset (opzionale, vale la pena provare)

```Bash
echo ${HF_USER}/my_lekiwi_dataset
```

Se è stato caricato il dataset, è possibile visualizzarlo anche localmente con il seguente comando:

```Python
lerobot-dataset-viz \
  --repo-id ${HF_USER}/my_lekiwi_dataset \
```

Se non è stato caricato il dataset, è possibile visualizzarlo anche localmente con il seguente comando:

```Python
lerobot-dataset-viz \
  --repo-id juxi/my_lekiwi_dataset \
```

Qui, `juxi` è un nome `repo_id` personalizzato impostato durante la raccolta dati.



#### Suggerimenti per la raccolta dati

Una volta acquisita familiarità con la registrazione dei dati, è possibile creare dataset più grandi per l'addestramento. Un buon compito iniziale consiste nel raccogliere oggetti da posizioni diverse e collocarli in un contenitore. Consigliamo di registrare almeno 50 episodi, 10 per posizione. Mantenere fissa la posizione della telecamera e mantenere costante il movimento di presa per tutta la registrazione. Inoltre, assicurarsi che gli oggetti manipolati siano ben visibili nell'inquadratura della telecamera. Una semplice regola empirica: si dovrebbe essere in grado di completare il compito semplicemente osservando il flusso della telecamera.

Nelle sezioni seguenti addestrerai la tua rete neurale. Una volta ottenute prestazioni di presa affidabili, puoi iniziare a introdurre maggiore variabilità nella raccolta dei dati, ad esempio aggiungendo posizioni di presa, utilizzando tecniche di presa diverse e cambiando le posizioni delle telecamere.

Evita di aggiungere troppa variabilità troppo rapidamente, poiché potrebbe compromettere i risultati.

Se desideri approfondire questo importante argomento, consulta il nostro [post del blog su cosa rende buono un dataset.](https://huggingface.co/blog/lerobot-datasets#what-makes-a-good-dataset)

#### Risoluzione dei problemi:

Su Linux, se durante la registrazione dati i tasti freccia sinistra/destra e il tasto Esc non funzionano, assicurarsi che la variabile d'ambiente `$DISPLAY` sia impostata. Vedere i [limiti di pynput](https://pynput.readthedocs.io/en/latest/limitations.html#linux)

# H. Riproduzione di un episodio

Ora prova a riprodurre il primo episodio sul tuo robot:

```Bash
python examples/lekiwi/replay.py
```

Congratulazioni 🎉 — il tuo robot è pronto a imparare i compiti da solo. Segui la sezione di addestramento di questo tutorial per iniziare ad addestrarlo: [Introduzione ai robot del mondo reale](https://huggingface.co/docs/lerobot/il_robots)

# I. Valutazione della tua policy

Assicurati di modificare remote_ip, port, HF_MODEL_ID

### Modificare evaluate.py

HF_MODEL_ID="<hf_username>/<model_repo_id>" modificalo con il nome del dataset caricato su Hugging Face dopo l'addestramento (se è stato caricato su Hugging Face) oppure con la directory locale in cui il modello è stato esportato dopo l'addestramento

HF_DATASET_ID="<hf_username>/<eval_dataset_id>" modificalo con il nome utente creato e il nome del dataset eval_

remote_ip: l'indirizzo IP del Raspberry Pi

![Immagine che mostra parte del file evaluate.py nel codice di valutazione del robot mobile Lekiwi. Le informazioni chiave sono la variabile HF_MODEL_ID alla riga 32, il cui valore è "<hf_username>/model_repo_id", e la variabile HF_DATASET_ID alla riga 33, il cui valore è "<hf_username>/eval_dataset_repo_id". Queste variabili specificano i nomi del modello e del dataset e devono essere modificati in base alla propria situazione: il nome del dataset caricato su Hugging Face dopo l'addestramento (o la directory locale) e il proprio nome utente e il nome del dataset eval_. Questa immagine è relativa alla modifica di evaluate.py nella sezione di valutazione precedente e serve come riferimento.](../en/images/d01-23.png)

Quindi esegui il seguente comando:

```Bash
python examples/lekiwi/evaluate.py
```

1. Il nome del dataset inizia con `eval` per riflettere il fatto che si sta eseguendo l'inferenza (ad es. `${HF_USER}/eval_act_lekiwi_test`).
2. Se durante la valutazione si incontra `File exists: 'home/xxxx/.cache/huggingface/lerobot/xxxxx/juxi/eval_xxxx'`, eliminare prima la cartella il cui nome inizia con `eval_` ed eseguire di nuovo il programma.



Per l'addestramento in simulazione, vedere

https://github.com/Ekumen-OS/lekiwi/tree/main

https://github.com/SIGRobotics-UIUC/LeKiwi-sim



## Assistenza 🙋‍

Per problemi hardware, contattare il servizio clienti. Per domande sull'utilizzo, unirsi a Discord.

[Piattaforma LeRobot](https://github.com/huggingface/lerobot)

[Canale Discord di LeRobot](https://discord.gg/8TnwDdjFGU)

#   
  
Installazione di Miniconda su Mac

## Concessione delle autorizzazioni

![](../en/images/d01-24.png)

## Installare Miniconda

https://www.anaconda.com/download

## Modifica della sorgente dei pacchetti di pip

```Shell
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple
```

## Modifica della sorgente dei pacchetti di conda

```Shell
# Cancellare la configurazione .condarc esistente (opzionale, per evitare conflitti)
echo "" > ~/.condarc

# Scrivere la configurazione del mirror di Tsinghua
cat << EOF > ~/.condarc
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch-lts: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
EOF

# Cancellare la cache per applicare la configurazione
conda clean -i
```
