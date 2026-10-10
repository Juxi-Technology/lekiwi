[English](../en/usage-guide.md) | [简体中文](../zh-hans/usage-guide.md) | [繁體中文](../zh-hant/usage-guide.md) | [Deutsch](../de/usage-guide.md) | [Español](../es/usage-guide.md) | [Français](../fr/usage-guide.md) | [Italiano](../it/usage-guide.md) | [日本語](../ja/usage-guide.md) | [한국어](../ko/usage-guide.md) | [Português (BR)](../pt-br/usage-guide.md) | Português (PT)

<title>Guia de utilização do robot móvel Lekiwi</title>

<callout emoji="💡">
O braço líder preto utiliza uma fonte de alimentação de 5V 6A e o braço seguidor branco utiliza uma fonte de alimentação de 12V 5A.
</callout>

<figure view-type="Card">[Anexo: lerobot.zip](../en/images/lerobot.zip)</figure>

O código neste repositório de tutorial é mantido na versão estável e testada do LeRobot anterior a 1 de outubro de 2026. Desde então, a Hugging Face realizou uma atualização muito grande do LeRobot, adicionando uma enorme quantidade de novas funcionalidades. Se quiser experimentar o tutorial mais recente, consulte a [documentação oficial](https://huggingface.co/docs/lerobot/lekiwi).



[Lekiwi](https://github.com/SIGRobotics-UIUC/LeKiwi) é um projeto de carro robot totalmente de código aberto iniciado pela [SIGRobotics-UIUC](https://github.com/SIGRobotics-UIUC). Inclui ficheiros detalhados de impressão 3D e instruções de funcionamento, e foi concebido para ser compatível com o framework de aprendizagem por imitação [LeRobot](https://github.com/huggingface/lerobot/tree/main). Suporta o braço robótico SO101, permitindo um fluxo de trabalho completo de aprendizagem por imitação.

[*No CAD online do Fusion360*](https://a360.co/4k1P8yO)* pode visualizar as posições exatas dos componentes.*

[Ficheiro URDF](https://gitcode.com/gh_mirrors/le/LeKiwi/tree/main)

Pré-visualização online do URDF https://urdf.d-robotics.cc/

![Imagem que mostra um modelo 3D do robot móvel Lekiwi. O corpo é cinzento e tem rodas brancas com banda de rodagem preta. Em cima está montado um braço robótico, com uma câmara na extremidade. Uma área azul na parte inferior é provavelmente onde se encontram a bateria ou a eletrónica. A imagem está relacionada com a introdução do guia de utilização do robot móvel Lekiwi e mostra a aparência e a estrutura do robot, para ajudar os utilizadores a compreender melhor o seu design.](../en/images/d01-01.png)

## Principais características

1. **Código aberto e baixo custo**: o [Lekiwi](https://github.com/SIGRobotics-UIUC/LeKiwi) oferece uma solução de carro robot de código aberto e baixo custo.
2. **Integração com o LeRobot**: concebido para integração com a [plataforma LeRobot](https://github.com/huggingface/lerobot).
3. **Recursos de aprendizagem completos**: recursos de aprendizagem abrangentes de código aberto, incluindo guias de montagem e calibração, bem como tutoriais para testes, recolha de dados, treino e implementação, que ajudam os utilizadores a começar rapidamente e a criar aplicações robóticas.
4. **Compatível com Nvidia**: pode ser utilizado com o reComputer Mini J4012 Orin NX 16 GB.
5. **Aplicações em múltiplos cenários**: adequado para educação, investigação científica, produção automatizada e robótica, ajudando os utilizadores a obter uma operação robótica eficiente e precisa numa variedade de tarefas complexas.

<callout emoji="⚠️">
A JUXI é responsável apenas pela qualidade do próprio hardware. Este tutorial é atualizado em estrita conformidade com a documentação oficial. Se encontrar problemas de software ou de dependências de ambiente que realmente não consiga resolver, comunique-os prontamente à [plataforma LeRobot](https://github.com/huggingface/lerobot) ou ao [canal Discord do LeRobot](https://discord.gg/8TnwDdjFGU).
</callout>

<callout emoji="🔥">
**Nota**
- Todos os servos do chassi do Lekiwi requerem alimentação de 12V. Para utilizadores com um braço robótico de 5V, fornecemos um módulo conversor redutor de 12V para 5V. Note que terá de modificar a cablagem por sua conta.
- Fonte de alimentação de 12V — pode selecionar esta opção ao finalizar a compra, se necessário. Se já tiver uma fonte de alimentação de 12V, basta converter o conector de saída numa ficha DC 5521.
- Controlador Raspberry Pi e câmaras — têm de ser adquiridos separadamente na página do pedido.
</callout>

## Lista de materiais (BOM)

<sheet sheet-id="MNu6oT" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

## Ambiente inicial do sistema

**Para Ubuntu x86:**

- Ubuntu 22.04
- CUDA 12+
- Python 3.10
- Torch 2.6

**Para Jetson Orin:**

- Jetson JetPack 6.0
- Python 3.10
- Torch 2.3+

**Para Raspberry Pi:**

- Raspberry Pi 5, 4G\~16G

### Configuração do SSH

Depois de configurar a Raspberry Pi, deve ativar e configurar o [SSH](https://www.raspberrypi.com/news/coding-on-raspberry-pi-remotely-with-visual-studio-code/) (Secure Shell) para poder iniciar sessão na Raspberry Pi a partir do seu portátil sem ligar um ecrã, teclado e rato à Pi. Pode encontrar um excelente tutorial [aqui](https://www.raspberrypi.com/documentation/computers/remote-access.html#ssh). Pode iniciar sessão na Raspberry Pi através da linha de comandos (cmd) ou, se utilizar o VSCode, pode usar [esta](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) extensão.

## Guia de impressão 3D

### Peças

Fornecemos ficheiros STL imprimíveis para as seguintes peças impressas em 3D. Estas peças podem ser impressas em impressoras FDM de nível de consumidor com filamento PLA de uso geral. Testámo-las numa impressora Bambu Lab P1S. Para cada componente, limitámo-nos a carregá-lo no Bambu Studio, deixámos que este o rodasse e organizasse automaticamente, ativámos os suportes recomendados, se aplicável, e imprimimos.

<sheet sheet-id="jIOIj0" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

### Configurações de impressão

Os ficheiros STL fornecidos podem ser impressos diretamente em muitas impressoras FDM. Abaixo estão as configurações testadas e recomendadas; outras configurações também podem funcionar.

- Material: PLA+
- Diâmetro e precisão do bico: bico de 0,2mm de diâmetro, altura de camada de 0,2mm
- Densidade de preenchimento: 15%
- Velocidade de impressão: 150 mm/s
- Se necessário, envie o G-code (ficheiro fatiado) para a impressora e imprima

# A. Instalar o LeRobot na Raspberry Pi

Na sua Raspberry Pi:

### 1. [Instalar o Miniconda](https://docs.anaconda.com/miniconda/install/#quick-command-line-install):

```Python
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

### 2. Reiniciar o shell

Copie e cole o seguinte comando no seu shell: `source ~/.bashrc`, ou, para utilizadores de Mac: `source ~/.bash_profile` ou `source ~/.zshrc` (se utilizar o zshell).

### 3. Criar e ativar um novo ambiente Conda para o LeRobot

```Python
conda create -y -n lerobot python=3.10
```

Em seguida, ative o seu ambiente Conda (tem de o fazer sempre que abrir um shell para utilizar o LeRobot!):

```Bash
conda activate lerobot
```

### 4. Clonar o LeRobot:

```Bash
git clone https://github.com/huggingface/lerobot.git ~/lerobot
```

### 5. Instalar o ffmpeg no seu ambiente:

Ao utilizar o `miniconda`, instale o `ffmpeg` no seu ambiente:

```PowerShell
conda install ffmpeg -c conda-forge
```

<callout emoji="💡">
Normalmente, isto instala o ffmpeg 7.X compilado com o codificador libsvtav1 para a sua plataforma. Se o libsvtav1 não for suportado (pode verificar os codificadores suportados com `ffmpeg -encoders`), pode:
[Todas as plataformas] Instalar explicitamente o ffmpeg 7.X:
`conda install ffmpeg=7.1.1 -c conda-forge`
[Apenas Linux] Instalar as dependências de compilação do ffmpeg e compilar o ffmpeg com suporte para libsvtav1 a partir do código-fonte, e garantir que o executável do ffmpeg em utilização é o correto, o que pode confirmar com `which ffmpeg`.
Se encontrar o erro abaixo, os comandos acima também podem corrigi-lo.
</callout>

![Imagem que mostra um erro encontrado na secção de instalação do LeRobot do guia de utilização do robot móvel Lekiwi. O erro mostra um ValueError gerado ao executar o código do robot Lekiwi, indicando que não foi encontrado nenhum ficheiro de entrada válido no processo 0 do worker do DataLoader. O erro ocorre na função `_get_item` de `torch.utils.data.fetch.py` e na função `_query_videos` de `torch.utils.data.fetch.py`, indicando um ficheiro de entrada inválido. Este erro está relacionado com os erros mencionados no contexto que podem ocorrer ao instalar o LeRobot.](../en/images/d01-02.png)

### 6. Instalar o LeRobot com a dependência do motor feetech:

```Bash
cd ~/lerobot && pip install --no-binary=av -e ".[feetech]"
pip install -e ".[lekiwi]"
```

### 7. Definir o tempo de ligação

Encontre o config_lekiwi.py no diretório `lerobot\src\lerobot\robots\lekiwi`.

 connection_time_s: int = 7200 # ou seja, 2 horas

![Imagem que mostra o código do ficheiro de configuração `config_lekiwi.py` do robot móvel Lekiwi. A parte principal é `connection_time_s`, cujo valor é 7200, ou seja, 2 horas, utilizado para definir o tempo de ligação da aplicação. A imagem está relacionada com a secção "Definir o tempo de ligação" e mostra onde o tempo de ligação é definido e o valor específico, para ajudar os utilizadores a compreender como configurá-lo no ficheiro.](../en/images/d01-03.png)

# B. Instalar o LeRobot num portátil

Se já instalou o LeRobot no seu portátil, pode saltar esta etapa; caso contrário, siga os **mesmos passos** que utilizámos na Raspberry Pi.

> [!Tip] Vamos utilizar com frequência a linha de comandos (cmd). Se não estiver familiarizado com o cmd, ou quiser rever a utilização da linha de comandos, pode consultar: [Curso intensivo de linha de comandos](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Environment_setup/Command_line)

No seu computador:

### 1. [Instalar o Miniconda](https://docs.anaconda.com/miniconda/install/#quick-command-line-install):

anaconda.com/download/success

Ou clique nesta ligação para descarregar o instalador diretamente

https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe

<grid>
<column width-ratio="0.500000">
![](../en/images/d01-04.png)
</column>
<column width-ratio="0.500000">
![](../en/images/d01-05.png)
</column>
</grid>

## Alterar as fontes de pacotes do conda

```Shell
# First clear the existing source configuration (to avoid conflicts)
conda config --remove-key channels

# Replace conda's default sources and common third-party sources with the Tsinghua mirror
# Add the default package sources (main/r/msys2)
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2/

# Add common third-party sources
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/

# Show the download source, so installing packages displays the specific download URL
conda config --set show_channel_urls yes

# Clear the index cache so the new sources take effect
conda clean -i

# Show the current configuration (to verify the sources were added successfully)
conda config --show-sources
```

### 2. Reiniciar o shell

Copie e cole o seguinte comando no seu shell: `source ~/.bashrc`, ou, para utilizadores de Mac: `source ~/.bash_profile` ou `source ~/.zshrc` (se utilizar o zshell).

![Imagem que mostra a interface para encontrar a aplicação Anaconda Prompt num computador: depois de escrever "Anaconda Prompt" na caixa de pesquisa, surge "Anaconda Prompt app" em "Best match", realçado por um retângulo vermelho. Isto está relacionado com o fluxo de instalação do LeRobot no portátil, no qual os comandos têm de ser copiados e colados no shell depois da etapa de reiniciar o shell, e mostra como abrir a aplicação Anaconda Prompt para executar os comandos seguintes e preparar a criação e a ativação de um novo ambiente Conda para o LeRobot.](../en/images/d01-06.png)

### 3. Criar e ativar um novo ambiente Conda para o LeRobot

```Bash
conda create -y -n lerobot python=3.10
```

Em seguida, ative o seu ambiente Conda (tem de o fazer sempre que abrir um shell para utilizar o LeRobot!):

```Bash
conda activate lerobot
```

### 4. Clonar o LeRobot:

```Bash
git clone https://github.com/huggingface/lerobot.git ~/lerobot
```

### 5. Instalar o ffmpeg no seu ambiente:

Ao utilizar o `miniconda`, instale o `ffmpeg` no seu ambiente:

```PowerShell
conda install ffmpeg -c conda-forge
```

<callout emoji="💡">
Normalmente, isto instala o ffmpeg 7.X compilado com o codificador libsvtav1 para a sua plataforma. Se o libsvtav1 não for suportado (pode verificar os codificadores suportados com `ffmpeg -encoders`), pode:
[Todas as plataformas] Instalar explicitamente o ffmpeg 7.X:
`conda install ffmpeg=7.1.1 -c conda-forge`
[Apenas Linux] Instalar as dependências de compilação do ffmpeg e compilar o ffmpeg com suporte para libsvtav1 a partir do código-fonte, e garantir que o executável do ffmpeg em utilização é o correto, o que pode confirmar com `which ffmpeg`.
Se encontrar o erro abaixo, os comandos acima também podem corrigi-lo.
</callout>

![Imagem que mostra uma mensagem de erro: ValueError: Caught ValueError in Dataloader worker process 0. O erro ocorre em vários ficheiros, como "/home/gengwei/lerobot/src/lerobot/lib/python3.10/runpy.py", e envolve módulos como "torch.utils.data.dataloader". Este erro está relacionado com o contexto de instalação do LeRobot num portátil, no qual erros como "no valid stream found in Input file" podem ser resolvidos instalando explicitamente o ffmpeg 7.X ou compilando o ffmpeg com suporte para libsvtav1 a partir do código-fonte.](../en/images/d01-07.png)

### 6. Instalar o LeRobot com a dependência do motor feetech:

```Bash
cd ~/lerobot && pip install --no-binary=av -e ".[feetech]"
pip install -e ".[lekiwi]"
```

# C. Configuração dos motores

<grid>
<column width-ratio="0.473717">
![Imagem que mostra o braço robótico do robot móvel Lekiwi. O braço é composto por várias peças de plástico branco, cada uma marcada com um número gerado automaticamente. As duas peças na extremidade frontal do braço estão numeradas 1 e 2, as peças do meio 3 e 4 e a extremidade oposta 5 e 6. Esta imagem está relacionada com a secção "Configuração dos motores" e ajuda a explicar como identificar as peças do braço robótico ao localizar a porta USB associada a ele, em preparação para a configuração dos motores.](../en/images/d01-08.png)
</column>
<column width-ratio="0.526283">
![Imagem que mostra a estrutura do chassi do robot móvel Lekiwi, com as posições de ID de três motores etiquetadas. ID = 7 (esquerda) está do lado esquerdo do chassi.](../en/images/d01-09.png)
</column>
</grid>

### **1. Localizar a porta USB associada ao braço robótico**

Para encontrar a porta correta de um motor individual, execute o seguinte script utilitário duas vezes:

```Bash
lerobot-find-port
```

Saída de exemplo (por exemplo, `/dev/tty.usbmodem575E0031751` no Mac, ou possivelmente `/dev/ttyACM0` no Linux):

Saída de exemplo (por exemplo, `/dev/tty.usbmodem575E0032081` no Mac, ou possivelmente `/dev/ttyACM1` no Linux):

Resolução de problemas: no Linux, pode ser necessário conceder acesso à porta USB com os seguintes comandos:

```Bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

### **2. Configurar os seus motores (salte esta etapa para uma unidade já pronta)**

Ligue cada motor do seu chassi, um de cada vez, e execute o seguinte script. Primeiro, inicializa os servos do braço robótico (ID 6..1) e, em seguida, inicializa os servos do chassi, definindo os respetivos IDs como (ID 9..7). Se já calibrou o braço robótico, pode limitar-se a premir Enter para sobrescrever e avançar:

```Bash
lerobot-setup-motors \
    --robot.type=lekiwi \
    --robot.port=/dev/tty.usbmodem58760431551 # <- paste here the port found at previous step
```

![Imagem que mostra a estrutura do chassi do robot móvel Lekiwi, com as posições de ID de quatro motores etiquetadas. ID = 7 (esquerda) está do lado esquerdo.](../en/images/d01-10.png)

### 3. Configurar o espelho da Hugging Face na China

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Add at the end of the file
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

# Add at the end of the file
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Output
# https://hf-mirror.com
```

#### ① Criar um Token

https://huggingface.co/settings/tokens

![Imagem que mostra a página "Access Tokens" do site da Hugging Face. À esquerda há um avatar de utilizador e informações como "Zihao Zhang TommyZihao", com opções como Profile e Account abaixo. À direita há "User Access Tokens", com um botão "+ Create new token" realçado por um retângulo vermelho. Na parte inferior da página lê-se "You have no Access Token." Esta imagem está relacionada com a etapa "Criar um Token" e orienta os utilizadores na criação de um novo token no site da Hugging Face.](../en/images/d01-11.png)

![Imagem que mostra a interface de criação de um novo Access Token na Hugging Face. À esquerda há um avatar de utilizador e opções como "Profile". À direita é apresentado o título "Create new Access Token", com as opções "Fine-grained", "Read" e "Write" em Token type, das quais "Write" está realçada por um retângulo vermelho. A secção Token tem um campo de entrada "Token name" com o exemplo "ierobot_zhao_token", com uma nota abaixo de que este token tem permissões de leitura e escrita. Na parte inferior há um botão verde "Create token". Esta imagem está relacionada com a etapa ①, Criar um Token, da secção "Configurar o espelho da Hugging Face na China", e mostra a interface de configuração para criar um token.](../en/images/d01-12.png)

#### ② Registar o Token

![](../en/images/d01-13.png)

#### ③ Associar o Token

```Shell
hf auth login

hf auth whoami
```

![Imagem de uma janela de terminal durante o início de sessão com a ferramenta de linha de comandos da Hugging Face no Mac. À esquerda é apresentado o comando "hf auth login"; a saída à direita indica que o token foi guardado, que o token é "lerobot_zihao_token" e que o token atualmente ativo também é "lerobot_zihao_token". Na parte inferior, o utilizador aparece como "TommyZihao". Esta imagem corresponde à parte de criação de token da etapa "Configurar o espelho da Hugging Face na China" e mostra o retorno do terminal depois de um token ser criado com sucesso.](../en/images/d01-14.png)

#### ④ Criar um Repositório de Dataset

**Anote o Owner e o nome do Dataset, ou seja, o <hf_username> e o <dateset_repo_id> de que vai precisar mais tarde**

<grid>
<column width-ratio="0.480604">
![Imagem que mostra a interface da plataforma Hugging Face. Há um ícone de avatar no canto superior direito; ao clicá-lo, abre-se um menu pendente no qual a opção "New Dataset", situada na parte inferior da metade do menu, está realçada por um retângulo vermelho. Esta imagem corresponde à etapa "Criar um Repositório de Dataset" e orienta os utilizadores na criação de um dataset na plataforma Hugging Face, sendo uma das instruções de operação do fluxo "Configurar o espelho da Hugging Face na China".](../en/images/d01-15.png)
</column>
<column width-ratio="0.519396">
![Imagem que mostra a interface de criação de um novo repositório de dataset na plataforma Hugging Face. "Owner" está definido como TommyZihao, "Dataset name" está preenchido com "lerobot_zihao_dataset_a", "License" está definido como mit e a opção "Public" está assinalada. Na parte inferior há um botão "Create dataset". Esta imagem está relacionada com a etapa "Criar um Repositório de Dataset" e registra informações como o Owner e o nome do Dataset ao criar um dataset, sendo uma etapa necessária antes de carregar ficheiros.](../en/images/d01-16.png)
</column>
</grid>

![Imagem que mostra uma página de Dataset na plataforma Hugging Face. A página apresenta o nome do dataset "TommyZihao/lezrobot_zihao_dataset_a" e separadores como "Files and versions", "Community" e "Settings". À esquerda há uma secção "Getting started with your dataset" com opções como "Complete dataset information" e "Edit Dataset Card". À direita há uma área "Push your dataset files" que oferece vários métodos de carregamento — CLI, Python, Git, HTTPS, SSH — juntamente com uma nota de que a CLI da Hugging Face tem de estar instalada e com sessão iniciada. Esta imagem está relacionada com a etapa "Configurar o espelho da Hugging Face na China" e orienta os utilizadores no trabalho com um Dataset na plataforma Hugging Face.](../en/images/d01-17.png)

### 4. Atualizar a configuração!!!

Os ficheiros de configuração no LeKiwi LeRobot e no portátil têm de se manter consistentes. Primeiro, precisamos de encontrar o **endereço IP** da Raspberry Pi que controla o braço móvel. É o mesmo endereço IP utilizado para o SSH. Precisamos também de encontrar a **porta USB** da placa controladora de servos do braço líder no portátil e a **porta da placa controladora de servos no LeKiwi**. Pode encontrar estas portas com o seguinte script.

No Linux, pode ser necessário conceder acesso à porta USB executando os seguintes comandos:

```Bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

Importante: agora que tem a porta do braço líder e o endereço IP do braço do Lekiwi, atualize o **ip** na configuração de rede, a **port** na configuração do braço líder e a **port, remote_ip** na configuração do LeKiwi.

Modifique estes quatro ficheiros no diretório example\lekiwi

![Imagem que mostra o diretório que contém os ficheiros que têm de ser modificados ao configurar os motores do robot móvel Lekiwi. O caminho são as pastas "examples" e "lekiwi" dentro da pasta do robot "ler", na pasta "软件" do disco D. O diretório mostra quatro ficheiros de código-fonte Python — evaluate.py, record.py, replay.py e teleoperate.py — todos com data de modificação de 24 de abril de 2026, 11:45, todos ficheiros de código-fonte Python, com tamanhos de 6KB, 6KB, 3KB e 3KB, respetivamente. Esta imagem corresponde ao conteúdo anterior sobre modificar quatro ficheiros no diretório example\lekiwi.](../en/images/d01-18.png)

#### ① Modificar teleoperate.py

remote_ip: o endereço IP da Raspberry Pi

port: o número da porta quando o braço líder está ligado ao computador ou ao Linux

![Imagem que mostra parte do ficheiro teleoperate.py a ser modificado ao configurar os motores do robot móvel Lekiwi. A informação principal é o parâmetro robot_config na linha 30, cujo remote_ip está definido como "172.18.134.136" e cujo id é "my_lekiwi"; e o parâmetro teleop_arm_config na linha 31, cuja port está definida como "/dev/tty.usbmodem585A0077581" e cujo id é my. Estes parâmetros configuram a ligação entre o robot e o braço líder, estão relacionados com o conteúdo sobre atualizar a configuração e são uma parte importante da etapa de modificação do ficheiro.](../en/images/d01-19.png)

#### ② Modificar record.py

HF_REPO_ID: [nome de utilizador e nome do dataset da Hugging Face](https://juxitech.feishu.cn/wiki/A2orwQ9xzidMCjk10SVcAAWVnhd?fromScene=spaceOverview#share-TYrIdHmPPobd1mx9xB7c75WEn0d)

remote_ip: o endereço IP da Raspberry Pi

port: o número da porta quando o braço líder está ligado ao computador ou ao Linux

![Imagem que mostra a configuração do record.py](../en/images/d01-20.png)

#### ③ Modificar replay.py

remote_ip: o endereço IP da Raspberry Pi

<hf_username>/<dataset_repo_id>, ou seja, o [nome de utilizador e nome do dataset da Hugging Face](https://juxitech.feishu.cn/wiki/A2orwQ9xzidMCjk10SVcAAWVnhd?fromScene=spaceOverview#share-TYrIdHmPPobd1mx9xB7c75WEn0d)

![Imagem que mostra o código do replay.py a ser modificado no guia de utilização do robot móvel Lekiwi. No código, o parâmetro robot_config na linha 29 é modificado para incluir remote_ip e id, em que remote_ip é "172.18.134.136" e id é "lekiwi"; o parâmetro dataset na linha 36 é modificado para incluir <hf_username>/<dataset_repo_id>, ou seja, o [nome de utilizador e nome do dataset da Hugging Face].](../en/images/fix-01.png)

# D. Calibração

Agora precisamos de calibrar o braço líder e o braço seguidor. Os servos das rodas omnidirecionais não precisam de calibração.

### Calibração do braço seguidor (montado na base do Lekiwi)

Execute o seguinte comando no seu computador para calibrar o braço líder. Nota: as imagens aqui apresentadas são exemplos para o modelo SO101.

```Bash
lerobot-calibrate \
    --teleop.type=so100_leader \
    --teleop.port=/dev/tty.usbmodem58760431551 \ # change to the port you found
    --teleop.id=my_awesome_leader_arm
```

Agora execute o seguinte comando na sua Raspberry Pi para calibrar o braço seguidor no LeKiwi. Ignore a sua posição atual sobre a mesa — a calibração adequada deve ser feita com ele montado no chassi do Lekiwi.

```Bash
lerobot-calibrate \
    --robot.type=lekiwi \
    --robot.id=my_awesome_kiwi
```

Padronizámos o método de calibração na maioria dos robots. Primeiro, precisamos de mover o robot de modo a que cada junta fique no **meio da sua amplitude de movimento** e, em seguida, premir o botão. Depois, movemos todas as juntas ao longo de toda a sua **amplitude de movimento** uma vez. Pode encontrar um vídeo do mesmo processo de calibração para o SO101 [aqui](https://huggingface.co/docs/lerobot/en/so101#calibration-video) `Enter`.

# E. Teleoperação

Abra um novo Anaconda Prompt

![Imagem que mostra a interface para abrir um novo Anaconda Prompt. Apresenta uma janela do Anaconda Prompt já aberta e a lista que surge depois de clicar na seta pendente à direita do "+" no canto superior direito; uma seta vermelha aponta para a opção "Anaconda Prompt (miniconda3)" nessa lista. Esta imagem está relacionada com o conteúdo sobre abrir um novo Anaconda Prompt para a teleoperação do robot móvel Lekiwi e mostra os passos específicos para abrir o Anaconda Prompt, para ajudar os leitores a compreender o processo.](../en/images/d01-21.png)

> Se estiver a utilizar um Mac, pode precisar de conceder permissão ao "Terminal" para aceder ao teclado durante a teleoperação. Vá a "Preferências do Sistema" > "Segurança e Privacidade" > "Monitorização de Entrada" e assinale a caixa "Terminal".

Para teleoperar, inicie sessão na sua Raspberry Pi através de SSH, execute o seguinte comando para ativar o ambiente `conda activate lerobot` e, em seguida, execute o seguinte script:

```Bash
python -m lerobot.robots.lekiwi.lekiwi_host --robot.id=my_awesome_kiwi
```

![Imagem que mostra a interface depois de ativar o ambiente `conda activate lerobot` e de executar o script num portátil. No topo aparece "Anaconda PowerShell Prompt" e, abaixo, "WARNING:root:No command available" é repetido várias vezes, terminando com "WARNING:root:Command not received for more than 500 milliseconds. Stopping the base." Isto está relacionado com as etapas de teleoperação e mostra as informações sobre a ligação ao robot remoto e o fluxo de vídeo que aparecem depois de ativar o ambiente e executar o script, em preparação para mover o braço de controlo e conduzir o robot com o teclado.](../en/images/d01-22.png)

Em seguida, no seu portátil, execute também o seguinte comando para ativar o ambiente `conda activate lerobot` e depois execute o seguinte script:

```Bash
python examples/lekiwi/teleoperate.py
```

O ecrã do seu portátil deve apresentar algo como: `[INFO] Connected to remote robot at tcp://172.17.133.91:5555 and video stream at tcp://172.17.133.91:5556.` Agora pode mover o braço de controlo e utilizar as teclas (W, A, S, D) do teclado para conduzir o robot para a frente, para a esquerda, para trás e para a direita. Utilize as teclas (Z, X) para rodar o robot para a esquerda ou para a direita. Utilize as teclas (R, F) para aumentar ou diminuir a velocidade do robot. Existem três modos de velocidade; consulte a tabela abaixo:

<sheet sheet-id="vJeIqV" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

<sheet sheet-id="iR6oYP" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

<callout emoji="💡">
Se utilizar um teclado diferente, pode alterar a tecla de atalho de cada comando em [`LeKiWiClientConfig`](https://github.com/huggingface/lerobot/blob/main/src/lerobot/robots/lekiwi/config_lekiwi.py).
</callout>

## Resolução de problemas de comunicação

Se tiver dificuldades em ligar o robot móvel SO101, siga as etapas abaixo para diagnosticar e corrigir o problema.

### 1. Verificar a configuração do endereço IP

Certifique-se de que o endereço IP correto da Raspberry Pi está definido no ficheiro de configuração. Para verificar o endereço IP da Raspberry Pi, execute o seguinte comando (na linha de comandos da Pi):

```Bash
hostname -I
```

### 2. Verificar se o portátil/PC consegue alcançar a Pi

Tente fazer ping à Raspberry Pi a partir do portátil:

```Bash
ping <your_pi_ip_address>
```

Se o ping falhar:

- Certifique-se de que a Pi está ligada e conectada à mesma rede.
- Verifique se o SSH está ativado na Pi.

### 3. Experimentar uma ligação SSH

Se não conseguir iniciar sessão na Pi via SSH, a ligação pode estar incorreta. Utilize o seguinte comando:

```Bash
ssh <your_pi_user_name>@<your_pi_ip_address>
```

Por exemplo, `ssh pi@192.168.0.106`

Se receber um erro de ligação:

- Certifique-se de que o SSH está ativado na Pi; pode executar o seguinte comando:

```Bash
sudo raspi-config
```

- Em seguida, navegue até: **Interfacing Options -> SSH** e ative-o.

### 4. Consistência dos ficheiros de configuração!!!

Certifique-se de que os ficheiros de configuração no portátil/PC e na Raspberry Pi são exatamente iguais.

# F. Gravar um dataset

Depois de se sentir à vontade com a teleoperação, pode utilizar o LeKiwi para gravar o seu primeiro dataset.

Para iniciar o programa no LeKiwi, ligue-se à sua Raspberry Pi através de SSH e execute os seguintes comandos para ativar o ambiente e iniciar o script:

```Bash
conda activate lerobot

python -m lerobot.robots.lekiwi.lekiwi_host --robot.id=my_awesome_kiwi
```

Se quiser utilizar o Hugging Face Hub para carregar datasets e nunca tiver iniciado sessão antes, certifique-se de que inicia sessão com um token de acesso de escrita, que pode gerar nas [configurações da Hugging Face](https://huggingface.co/settings/tokens):

```Bash
hf auth login
```

Guarde o nome do seu repositório da Hugging Face numa variável para executar o seguinte comando:

```Bash
hf auth whoami
```

Em seguida, execute o seguinte comando no seu portátil para gravar 2 episódios e carregar o dataset para o Hub:

```Bash
python examples/lekiwi/record.py
```

# G. Visualizar um dataset

Se carregou o dataset, pode [visualizar o seu dataset online](https://huggingface.co/spaces/lerobot/visualize_dataset); copie e cole o ID do repositório produzido pelo seguinte comando:

```Bash
echo ${HF_USER}/my_lekiwi_dataset
```

Se não carregou o dataset, também pode visualizá-lo localmente (a ferramenta de visualização abre numa janela do navegador em `http://127.0.0.1:9090`):

```Bash
python lerobot/scripts/visualize_dataset_html.py \
  --repo-id ${HF_USER}/lekiwi_test \
  --local-files-only 1
```

### Visualizar um dataset (opcional, vale a pena experimentar)

```Bash
echo ${HF_USER}/my_lekiwi_dataset
```

Se carregou o dataset, também pode visualizá-lo localmente com o seguinte comando:

```Python
lerobot-dataset-viz \
  --repo-id ${HF_USER}/my_lekiwi_dataset \
```

Se não carregou o dataset, também pode visualizá-lo localmente com o seguinte comando:

```Python
lerobot-dataset-viz \
  --repo-id juxi/my_lekiwi_dataset \
```

Aqui, `juxi` é um nome de `repo_id` personalizado definido durante a recolha de dados.



#### Dicas de recolha de dados

Depois de se sentir à vontade com a gravação de dados, pode criar datasets maiores para treino. Uma boa tarefa inicial é apanhar objetos de diferentes posições e colocá-los num recipiente. Recomendamos gravar pelo menos 50 episódios, 10 por posição. Mantenha a posição da câmara fixa e o movimento de agarrar consistente durante toda a gravação. Além disso, certifique-se de que os objetos que está a manipular estão claramente visíveis na imagem da câmara. Uma regra prática simples: deve conseguir concluir a tarefa apenas a observar a imagem da câmara.

Nas secções seguintes, vai treinar a sua rede neuronal. Depois de obter um desempenho de agarrar fiável, pode começar a introduzir mais variação na recolha de dados, por exemplo, adicionando posições de agarrar, utilizando diferentes técnicas de agarrar e alterando as posições da câmara.

Evite introduzir variação a mais demasiado depressa, pois pode prejudicar os seus resultados.

Se quiser aprofundar este tópico importante, consulte a nossa [publicação no blogue sobre o que faz um bom dataset.](https://huggingface.co/blog/lerobot-datasets#what-makes-a-good-dataset)

#### Resolução de problemas:

No Linux, se as teclas de seta esquerda/direita e a tecla Esc não funcionarem durante a gravação de dados, certifique-se de que a variável de ambiente `$DISPLAY` está definida. Consulte as [limitações do pynput](https://pynput.readthedocs.io/en/latest/limitations.html#linux)

# H. Reproduzir um episódio

Agora experimente reproduzir o primeiro episódio no seu robot:

```Bash
python examples/lekiwi/replay.py
```

Parabéns 🎉 — o seu robot está pronto para aprender tarefas sozinho. Siga a secção de treino deste tutorial para começar a treiná-lo: [Introdução aos robots do mundo real](https://huggingface.co/docs/lerobot/il_robots)

# I. Avaliar a sua política

Certifique-se de que altera remote_ip, port, HF_MODEL_ID

### Modificar evaluate.py

HF_MODEL_ID="<hf_username>/<model_repo_id>" altere isto para o nome do dataset carregado na Hugging Face depois do treino (se o tiver carregado na Hugging Face), ou para o diretório local onde o modelo foi exportado depois do treino

HF_DATASET_ID="<hf_username>/<eval_dataset_id>" altere isto para o nome de utilizador que criou e o nome do dataset eval_

remote_ip: o endereço IP da Raspberry Pi

![Imagem que mostra parte do ficheiro evaluate.py no código de avaliação do robot móvel Lekiwi. A informação principal é a variável HF_MODEL_ID na linha 32, cujo valor é "<hf_username>/model_repo_id", e a variável HF_DATASET_ID na linha 33, cujo valor é "<hf_username>/eval_dataset_repo_id". Estas variáveis especificam os nomes do modelo e do dataset e têm de ser alteradas de acordo com a sua situação: o nome do dataset carregado na Hugging Face depois do treino (ou o diretório local) e o seu nome de utilizador e o nome do dataset eval_. Esta imagem está relacionada com a modificação do evaluate.py na secção de avaliação acima e serve como referência.](../en/images/d01-23.png)

Em seguida, execute o seguinte comando:

```Bash
python examples/lekiwi/evaluate.py
```

1. O nome do dataset começa por `eval` para refletir que está a executar uma inferência (por exemplo, `${HF_USER}/eval_act_lekiwi_test`).
2. Se durante a avaliação encontrar `File exists: 'home/xxxx/.cache/huggingface/lerobot/xxxxx/juxi/eval_xxxx'`, elimine primeiro a pasta cujo nome começa por `eval_` e execute o programa novamente.



Para treino em simulação, consulte

https://github.com/Ekumen-OS/lekiwi/tree/main

https://github.com/SIGRobotics-UIUC/LeKiwi-sim



## Ajuda 🙋‍

Para problemas de hardware, contacte o serviço de apoio ao cliente. Para dúvidas de utilização, junte-se ao Discord.

[plataforma LeRobot](https://github.com/huggingface/lerobot)

[canal Discord do LeRobot](https://discord.gg/8TnwDdjFGU)

#   
  
Instalar o Miniconda num Mac

## Conceder permissões

![](../en/images/d01-24.png)

## Instalar o Miniconda

https://www.anaconda.com/download

## Alterar a fonte de pacotes do pip

```Shell
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple
```

## Alterar a fonte de pacotes do conda

```Shell
# Clear the existing .condarc configuration (optional, to avoid conflicts)
echo "" > ~/.condarc

# Write the Tsinghua mirror configuration
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

# Clear the cache to apply the configuration
conda clean -i
```
