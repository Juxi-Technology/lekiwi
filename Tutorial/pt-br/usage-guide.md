[English](../en/usage-guide.md) | [简体中文](../zh-hans/usage-guide.md) | [繁體中文](../zh-hant/usage-guide.md) | [Deutsch](../de/usage-guide.md) | [Español](../es/usage-guide.md) | [Français](../fr/usage-guide.md) | [Italiano](../it/usage-guide.md) | [日本語](../ja/usage-guide.md) | [한국어](../ko/usage-guide.md) | Português (BR) | [Português (PT)](../pt-pt/usage-guide.md)

<title>Guia de uso do robô móvel Lekiwi</title>

<callout emoji="💡">
O braço líder preto usa uma fonte de alimentação de 5V 6A, e o braço seguidor branco usa uma fonte de alimentação de 12V 5A.
</callout>

<figure view-type="Card">[Anexo: lerobot.zip](../en/images/lerobot.zip)</figure>

O código neste repositório de tutorial é mantido na versão estável e testada do LeRobot anterior a 1º de outubro de 2026. Desde então, a Hugging Face realizou uma atualização muito grande no LeRobot, adicionando uma grande quantidade de novos recursos. Se você quiser experimentar o tutorial mais recente, consulte a [documentação oficial](https://huggingface.co/docs/lerobot/lekiwi).



[Lekiwi](https://github.com/SIGRobotics-UIUC/LeKiwi) é um projeto de carro robô totalmente de código aberto iniciado pela [SIGRobotics-UIUC](https://github.com/SIGRobotics-UIUC). Ele inclui arquivos detalhados de impressão 3D e instruções de operação, e foi projetado para ser compatível com o framework de aprendizado por imitação [LeRobot](https://github.com/huggingface/lerobot/tree/main). Ele suporta o braço robótico SO101, permitindo um fluxo de trabalho completo de aprendizado por imitação.

[*No CAD online do Fusion360*](https://a360.co/4k1P8yO)* você pode visualizar as posições exatas dos componentes.*

[Arquivo URDF](https://gitcode.com/gh_mirrors/le/LeKiwi/tree/main)

Pré-visualização online do URDF https://urdf.d-robotics.cc/

![Imagem mostrando um modelo 3D do robô móvel Lekiwi. Seu corpo é cinza e ele tem rodas brancas com banda de rodagem preta. Um braço robótico está montado em cima, com uma câmera na sua extremidade. Uma área azul na parte inferior é provavelmente onde ficam a bateria ou a eletrônica. A imagem está relacionada à introdução do guia de uso do robô móvel Lekiwi, mostrando a aparência e a estrutura do robô para ajudar os usuários a entender melhor seu projeto.](../en/images/d01-01.png)

## Principais recursos

1. **Código aberto e baixo custo**: o [Lekiwi](https://github.com/SIGRobotics-UIUC/LeKiwi) oferece uma solução de carro robô de código aberto e baixo custo.
2. **Integração com o LeRobot**: projetado para integração com a [plataforma LeRobot](https://github.com/huggingface/lerobot).
3. **Recursos de aprendizado abrangentes**: recursos de aprendizado abrangentes de código aberto, incluindo guias de montagem e calibração, além de tutoriais para testes, coleta de dados, treinamento e implantação, ajudando os usuários a começar rapidamente e a criar aplicações robóticas.
4. **Compatível com Nvidia**: pode ser usado com o reComputer Mini J4012 Orin NX 16 GB.
5. **Aplicações em vários cenários**: adequado para educação, pesquisa científica, produção automatizada e robótica, ajudando os usuários a obter uma operação robótica eficiente e precisa em uma variedade de tarefas complexas.

<callout emoji="⚠️">
A JUXI é responsável apenas pela qualidade do próprio hardware. Este tutorial é atualizado estritamente de acordo com a documentação oficial. Se você encontrar problemas de software ou de dependência de ambiente que realmente não consiga resolver, reporte-os prontamente à [plataforma LeRobot](https://github.com/huggingface/lerobot) ou ao [canal Discord do LeRobot](https://discord.gg/8TnwDdjFGU).
</callout>

<callout emoji="🔥">
**Observação**
- Todos os servos do chassi do Lekiwi exigem alimentação de 12V. Para usuários com um braço robótico de 5V, fornecemos um módulo conversor abaixador de 12V para 5V. Note que você precisará modificar a fiação por conta própria.
- Fonte de alimentação de 12V — você pode selecionar esta opção no checkout, se necessário. Se você já tem uma fonte de alimentação de 12V, basta converter o conector de saída dela para um plugue DC 5521.
- Controlador Raspberry Pi e câmeras — devem ser adquiridos separadamente na página do pedido.
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

Depois de configurar a Raspberry Pi, você deve habilitar e configurar o [SSH](https://www.raspberrypi.com/news/coding-on-raspberry-pi-remotely-with-visual-studio-code/) (Secure Shell) para poder fazer login na Raspberry Pi a partir do seu notebook sem conectar tela, teclado e mouse à Pi. Você pode encontrar um ótimo tutorial [aqui](https://www.raspberrypi.com/documentation/computers/remote-access.html#ssh). Você pode fazer login na Raspberry Pi pelo prompt de comando (cmd) ou, se usar o VSCode, pode usar [esta](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) extensão.

## Guia de impressão 3D

### Peças

Fornecemos arquivos STL imprimíveis para as seguintes peças impressas em 3D. Essas peças podem ser impressas em impressoras FDM de nível de consumidor usando filamento PLA de uso geral. Nós as testamos em uma impressora Bambu Lab P1S. Para cada componente, simplesmente o carregamos no Bambu Studio, deixamos que ele gire e organize automaticamente, habilitamos os suportes recomendados, se houver, e imprimimos.

<sheet sheet-id="jIOIj0" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

### Configurações de impressão

Os arquivos STL fornecidos podem ser impressos diretamente em muitas impressoras FDM. Abaixo estão as configurações testadas e recomendadas; outras configurações também podem funcionar.

- Material: PLA+
- Diâmetro e precisão do bico: bico de 0,2mm de diâmetro, altura de camada de 0,2mm
- Densidade de preenchimento: 15%
- Velocidade de impressão: 150 mm/s
- Se necessário, envie o G-code (arquivo fatiado) para a impressora e imprima

# A. Instalação do LeRobot na Raspberry Pi

Na sua Raspberry Pi:

### 1. [Instalar o Miniconda](https://docs.anaconda.com/miniconda/install/#quick-command-line-install):

```Python
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

### 2. Reiniciar o shell

Copie e cole o seguinte comando no seu shell: `source ~/.bashrc`, ou, para usuários de Mac: `source ~/.bash_profile` ou `source ~/.zshrc` (se você usar o zshell).

### 3. Criar e ativar um novo ambiente Conda para o LeRobot

```Python
conda create -y -n lerobot python=3.10
```

Em seguida, ative o seu ambiente Conda (você precisa fazer isso sempre que abrir um shell para usar o LeRobot!):

```Bash
conda activate lerobot
```

### 4. Clonar o LeRobot:

```Bash
git clone https://github.com/huggingface/lerobot.git ~/lerobot
```

### 5. Instalar o ffmpeg no seu ambiente:

Ao usar o `miniconda`, instale o `ffmpeg` no seu ambiente:

```PowerShell
conda install ffmpeg -c conda-forge
```

<callout emoji="💡">
Isso geralmente instala o ffmpeg 7.X compilado com o codificador libsvtav1 para a sua plataforma. Se o libsvtav1 não for suportado (você pode verificar os codificadores suportados com `ffmpeg -encoders`), você pode:
[Para todas as plataformas] Instalar explicitamente o ffmpeg 7.X:
`conda install ffmpeg=7.1.1 -c conda-forge`
[Apenas Linux] Instalar as dependências de compilação do ffmpeg e compilar o ffmpeg com suporte a libsvtav1 a partir do código-fonte, e garantir que o executável do ffmpeg em uso seja o correto, o que você pode confirmar com `which ffmpeg`.
Se você encontrar o erro abaixo, os comandos acima também podem corrigi-lo.
</callout>

![Imagem mostrando um erro encontrado na seção de instalação do LeRobot do guia de uso do robô móvel Lekiwi. O erro mostra um ValueError gerado ao executar o código do robô Lekiwi, indicando que nenhum arquivo de entrada válido pôde ser encontrado no processo 0 do worker do DataLoader. O erro ocorre na função `_get_item` de `torch.utils.data.fetch.py` e na função `_query_videos` de `torch.utils.data.fetch.py`, indicando um arquivo de entrada inválido. Este erro está relacionado aos erros mencionados no contexto que podem ocorrer ao instalar o LeRobot.](../en/images/d01-02.png)

### 6. Instalar o LeRobot com a dependência do motor feetech:

```Bash
cd ~/lerobot && pip install --no-binary=av -e ".[feetech]"
pip install -e ".[lekiwi]"
```

### 7. Definir o tempo de conexão

Encontre o config_lekiwi.py no diretório `lerobot\src\lerobot\robots\lekiwi`.

 connection_time_s: int = 7200 # ou seja, 2 horas

![Imagem mostrando o código do arquivo de configuração `config_lekiwi.py` do robô móvel Lekiwi. A parte principal é `connection_time_s`, cujo valor é 7200, ou seja, 2 horas, usado para definir o tempo de conexão da aplicação. A imagem está relacionada à seção "Definir o tempo de conexão", mostrando onde o tempo de conexão é definido e o valor específico, para ajudar os usuários a entender como configurá-lo no arquivo.](../en/images/d01-03.png)

# B. Instalação do LeRobot em um notebook

Se você já instalou o LeRobot no seu notebook, pode pular esta etapa; caso contrário, siga os **mesmos passos** que usamos na Raspberry Pi.

> [!Tip] Usaremos o prompt de comando (cmd) com frequência. Se você não estiver familiarizado com o cmd, ou quiser revisar o uso da linha de comando, consulte: [Curso intensivo de linha de comando](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Environment_setup/Command_line)

No seu computador:

### 1. [Instalar o Miniconda](https://docs.anaconda.com/miniconda/install/#quick-command-line-install):

anaconda.com/download/success

Ou clique neste link para baixar o instalador diretamente

https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe

<grid>
<column width-ratio="0.500000">
![](../en/images/d01-04.png)
</column>
<column width-ratio="0.500000">
![](../en/images/d01-05.png)
</column>
</grid>

## Alterando as fontes de pacotes do conda

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

Copie e cole o seguinte comando no seu shell: `source ~/.bashrc`, ou, para usuários de Mac: `source ~/.bash_profile` ou `source ~/.zshrc` (se você usar o zshell).

![Imagem mostrando a interface para encontrar o aplicativo Anaconda Prompt em um computador: após digitar "Anaconda Prompt" na caixa de pesquisa, "Anaconda Prompt app" aparece em "Best match" e é destacado com um retângulo vermelho. Isso está relacionado ao fluxo de instalação do LeRobot no notebook, onde os comandos devem ser copiados e colados no shell após a etapa de reiniciar o shell. Mostra como abrir o aplicativo Anaconda Prompt para que você execute os comandos seguintes e se prepare para criar e ativar um novo ambiente Conda para o LeRobot.](../en/images/d01-06.png)

### 3. Criar e ativar um novo ambiente Conda para o LeRobot

```Bash
conda create -y -n lerobot python=3.10
```

Em seguida, ative o seu ambiente Conda (você precisa fazer isso sempre que abrir um shell para usar o LeRobot!):

```Bash
conda activate lerobot
```

### 4. Clonar o LeRobot:

```Bash
git clone https://github.com/huggingface/lerobot.git ~/lerobot
```

### 5. Instalar o ffmpeg no seu ambiente:

Ao usar o `miniconda`, instale o `ffmpeg` no seu ambiente:

```PowerShell
conda install ffmpeg -c conda-forge
```

<callout emoji="💡">
Isso geralmente instala o ffmpeg 7.X compilado com o codificador libsvtav1 para a sua plataforma. Se o libsvtav1 não for suportado (você pode verificar os codificadores suportados com `ffmpeg -encoders`), você pode:
[Para todas as plataformas] Instalar explicitamente o ffmpeg 7.X:
`conda install ffmpeg=7.1.1 -c conda-forge`
[Apenas Linux] Instalar as dependências de compilação do ffmpeg e compilar o ffmpeg com suporte a libsvtav1 a partir do código-fonte, e garantir que o executável do ffmpeg em uso seja o correto, o que você pode confirmar com `which ffmpeg`.
Se você encontrar o erro abaixo, os comandos acima também podem corrigi-lo.
</callout>

![Imagem mostrando uma mensagem de erro: ValueError: Caught ValueError in Dataloader worker process 0. O erro ocorre em vários arquivos, como "/home/gengwei/lerobot/src/lerobot/lib/python3.10/runpy.py", e envolve módulos como "torch.utils.data.dataloader". Este erro está relacionado ao contexto de instalação do LeRobot em um notebook, onde erros como "no valid stream found in Input file" podem ser resolvidos instalando explicitamente o ffmpeg 7.X ou compilando o ffmpeg com suporte a libsvtav1 a partir do código-fonte.](../en/images/d01-07.png)

### 6. Instalar o LeRobot com a dependência do motor feetech:

```Bash
cd ~/lerobot && pip install --no-binary=av -e ".[feetech]"
pip install -e ".[lekiwi]"
```

# C. Configuração dos motores

<grid>
<column width-ratio="0.473717">
![Imagem mostrando o braço robótico do robô móvel Lekiwi. O braço é composto por várias peças de plástico branco, cada uma marcada com um número gerado automaticamente. As duas peças na extremidade frontal do braço estão numeradas 1 e 2, as peças do meio 3 e 4, e a extremidade oposta 5 e 6. Esta imagem está relacionada à seção "Configuração dos motores", ajudando a explicar como identificar as peças do braço robótico ao localizar a porta USB associada a ele, em preparação para a configuração dos motores.](../en/images/d01-08.png)
</column>
<column width-ratio="0.526283">
![Imagem mostrando a estrutura do chassi do robô móvel Lekiwi, com as posições de ID de três motores rotuladas. ID = 7 (esquerda) está no lado esquerdo do chassi.](../en/images/d01-09.png)
</column>
</grid>

### **1. Localizar a porta USB associada ao braço robótico**

Para encontrar a porta correta de um motor individual, execute o seguinte script utilitário duas vezes:

```Bash
lerobot-find-port
```

Saída de exemplo (por exemplo, `/dev/tty.usbmodem575E0031751` no Mac, ou possivelmente `/dev/ttyACM0` no Linux):

Saída de exemplo (por exemplo, `/dev/tty.usbmodem575E0032081` no Mac, ou possivelmente `/dev/ttyACM1` no Linux):

Solução de problemas: no Linux, talvez você precise conceder acesso à porta USB com os seguintes comandos:

```Bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

### **2. Configurar seus motores (pule esta etapa para uma unidade pronta)**

Conecte cada motor do seu chassi um de cada vez e execute o seguinte script. Ele primeiro inicializa os servos do braço robótico (ID 6..1), depois inicializa os servos do chassi, definindo seus IDs como (ID 9..7). Se você já calibrou o braço robótico, pode simplesmente pressionar Enter para sobrescrever e pular:

```Bash
lerobot-setup-motors \
    --robot.type=lekiwi \
    --robot.port=/dev/tty.usbmodem58760431551 # <- paste here the port found at previous step
```

![Imagem mostrando a estrutura do chassi do robô móvel Lekiwi, com as posições de ID de quatro motores rotuladas. ID = 7 (esquerda) está no lado esquerdo.](../en/images/d01-10.png)

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

![Imagem mostrando a página "Access Tokens" do site da Hugging Face. À esquerda há um avatar de usuário e informações como "Zihao Zhang TommyZihao", com opções como Profile e Account abaixo. À direita há "User Access Tokens" com um botão "+ Create new token" destacado por um retângulo vermelho. Na parte inferior da página está escrito "You have no Access Token." Esta imagem está relacionada à etapa "Criar um Token", orientando os usuários a criar um novo token no site da Hugging Face.](../en/images/d01-11.png)

![Imagem mostrando a interface para criar um novo Access Token na Hugging Face. À esquerda há um avatar de usuário e opções como "Profile". À direita é exibido o título "Create new Access Token", com as opções "Fine-grained", "Read" e "Write" em Token type, das quais "Write" está destacada por um retângulo vermelho. A seção Token tem um campo de entrada "Token name" com o exemplo "ierobot_zhao_token", com uma nota abaixo de que este token tem permissões de leitura e escrita. Na parte inferior há um botão verde "Create token". Esta imagem está relacionada à etapa ①, Criar um Token, na seção "Configurar o espelho da Hugging Face na China", mostrando a interface de configurações para criar um token.](../en/images/d01-12.png)

#### ② Registrar o Token

![](../en/images/d01-13.png)

#### ③ Vincular o Token

```Shell
hf auth login

hf auth whoami
```

![Imagem de uma janela de terminal durante o login com a ferramenta de linha de comando da Hugging Face no Mac. À esquerda é mostrado o comando "hf auth login"; a saída à direita indica que o token foi salvo, que o token é "lerobot_zihao_token" e que o token atualmente ativo também é "lerobot_zihao_token". Na parte inferior o usuário aparece como "TommyZihao". Esta imagem corresponde à parte de criação de token da etapa "Configurar o espelho da Hugging Face na China", mostrando o retorno do terminal após um token ser criado com sucesso.](../en/images/d01-14.png)

#### ④ Criar um Repositório de Dataset

**Anote o Owner e o nome do Dataset, ou seja, o <hf_username> e o <dateset_repo_id> de que você precisará mais tarde**

<grid>
<column width-ratio="0.480604">
![Imagem mostrando a interface da plataforma Hugging Face. Há um ícone de avatar no canto superior direito; ao clicá-lo, abre-se um menu suspenso no qual a opção "New Dataset", localizada na parte inferior da metade do menu, está destacada por um retângulo vermelho. Esta imagem corresponde à etapa "Criar um Repositório de Dataset", orientando os usuários a criar um dataset na plataforma Hugging Face, e é uma das instruções de operação no fluxo "Configurar o espelho da Hugging Face na China".](../en/images/d01-15.png)
</column>
<column width-ratio="0.519396">
![Imagem mostrando a interface para criar um novo repositório de dataset na plataforma Hugging Face. "Owner" está definido como TommyZihao, "Dataset name" está preenchido com "lerobot_zihao_dataset_a", "License" está definido como mit e a opção "Public" está marcada. Um botão "Create dataset" está na parte inferior. Esta imagem está relacionada à etapa "Criar um Repositório de Dataset", registrando informações como o Owner e o nome do Dataset ao criar um dataset, e é uma etapa necessária antes de enviar arquivos.](../en/images/d01-16.png)
</column>
</grid>

![Imagem mostrando uma página de Dataset na plataforma Hugging Face. A página mostra o nome do dataset "TommyZihao/lezrobot_zihao_dataset_a" e abas como "Files and versions", "Community" e "Settings". À esquerda há uma seção "Getting started with your dataset" com opções como "Complete dataset information" e "Edit Dataset Card". À direita há uma área "Push your dataset files" que oferece vários métodos de upload — CLI, Python, Git, HTTPS, SSH — junto com uma nota de que a CLI da Hugging Face deve estar instalada e com login feito. Esta imagem está relacionada à etapa "Configurar o espelho da Hugging Face na China", orientando os usuários a trabalhar com um Dataset na plataforma Hugging Face.](../en/images/d01-17.png)

### 4. Atualizar a configuração!!!

Os arquivos de configuração no LeKiwi LeRobot e no notebook devem permanecer consistentes. Primeiro, precisamos encontrar o **endereço IP** da Raspberry Pi que controla o braço móvel. Este é o mesmo endereço IP usado para o SSH. Também precisamos encontrar a **porta USB** da placa controladora de servos do braço líder no notebook e a **porta da placa controladora de servos no LeKiwi**. Você pode encontrar essas portas com o seguinte script.

No Linux, talvez você precise conceder acesso à porta USB executando os seguintes comandos:

```Bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

Importante: agora que você tem a porta do braço líder e o endereço IP do braço do Lekiwi, atualize o **ip** na configuração de rede, a **port** na configuração do braço líder, e a **port, remote_ip** na configuração do LeKiwi.

Modifique estes quatro arquivos no diretório example\lekiwi

![Imagem mostrando o diretório que contém os arquivos que devem ser modificados ao configurar os motores do robô móvel Lekiwi. O caminho são as pastas "examples" e "lekiwi" dentro da pasta do robô "ler" na pasta "软件" do disco D. O diretório mostra quatro arquivos-fonte Python — evaluate.py, record.py, replay.py e teleoperate.py — todos com data de modificação de 24 de abril de 2026, 11:45, todos arquivos-fonte Python, com tamanhos de 6KB, 6KB, 3KB e 3KB respectivamente. Esta imagem corresponde ao conteúdo anterior sobre modificar quatro arquivos no diretório example\lekiwi.](../en/images/d01-18.png)

#### ① Modificar teleoperate.py

remote_ip: o endereço IP da Raspberry Pi

port: o número da porta quando o braço líder está conectado ao computador ou ao Linux

![Imagem mostrando parte do arquivo teleoperate.py sendo modificado ao configurar os motores do robô móvel Lekiwi. A informação principal é o parâmetro robot_config na linha 30, cujo remote_ip está definido como "172.18.134.136" e cujo id é "my_lekiwi"; e o parâmetro teleop_arm_config na linha 31, cuja port está definida como "/dev/tty.usbmodem585A0077581" e cujo id é my. Esses parâmetros configuram a conexão entre o robô e o braço líder, estão relacionados ao conteúdo sobre atualizar a configuração e são uma parte importante da etapa de modificação do arquivo.](../en/images/d01-19.png)

#### ② Modificar record.py

HF_REPO_ID: [nome de usuário e nome do dataset da Hugging Face](https://juxitech.feishu.cn/wiki/A2orwQ9xzidMCjk10SVcAAWVnhd?fromScene=spaceOverview#share-TYrIdHmPPobd1mx9xB7c75WEn0d)

remote_ip: o endereço IP da Raspberry Pi

port: o número da porta quando o braço líder está conectado ao computador ou ao Linux

![Imagem mostrando a configuração do record.py](../en/images/d01-20.png)

#### ③ Modificar replay.py

remote_ip: o endereço IP da Raspberry Pi

<hf_username>/<dataset_repo_id>, ou seja, o [nome de usuário e nome do dataset da Hugging Face](https://juxitech.feishu.cn/wiki/A2orwQ9xzidMCjk10SVcAAWVnhd?fromScene=spaceOverview#share-TYrIdHmPPobd1mx9xB7c75WEn0d)

![Imagem mostrando o código do replay.py sendo modificado no guia de uso do robô móvel Lekiwi. No código, o parâmetro robot_config na linha 29 é modificado para incluir remote_ip e id, onde remote_ip é "172.18.134.136" e id é "lekiwi"; o parâmetro dataset na linha 36 é modificado para incluir <hf_username>/<dataset_repo_id>, ou seja, o [nome de usuário e nome do dataset da Hugging Face].](../en/images/fix-01.png)

# D. Calibração

Agora precisamos calibrar o braço líder e o braço seguidor. Os servos das rodas omnidirecionais não precisam de calibração.

### Calibração do braço seguidor (montado na base do Lekiwi)

Execute o seguinte comando no seu computador para calibrar o braço líder. Observação: as imagens mostradas aqui são exemplos para o modelo SO101.

```Bash
lerobot-calibrate \
    --teleop.type=so100_leader \
    --teleop.port=/dev/tty.usbmodem58760431551 \ # change to the port you found
    --teleop.id=my_awesome_leader_arm
```

Agora execute o seguinte comando na sua Raspberry Pi para calibrar o braço seguidor no LeKiwi. Ignore sua posição atual sobre a mesa — a calibração adequada deve ser feita com ele montado no chassi do Lekiwi.

```Bash
lerobot-calibrate \
    --robot.type=lekiwi \
    --robot.id=my_awesome_kiwi
```

Padronizamos o método de calibração na maioria dos robôs. Primeiro, precisamos mover o robô de modo que cada junta esteja no **meio de sua faixa de movimento**, e então pressionar o botão. Em segundo lugar, movemos todas as juntas por toda a sua **faixa de movimento** uma vez. Você pode encontrar um vídeo do mesmo processo de calibração para o SO101 [aqui](https://huggingface.co/docs/lerobot/en/so101#calibration-video) `Enter`.

# E. Teleoperação

Abra um novo Anaconda Prompt

![Imagem mostrando a interface para abrir um novo Anaconda Prompt. Mostra uma janela do Anaconda Prompt já aberta e a lista que aparece após clicar na seta suspensa à direita do "+" no canto superior direito; uma seta vermelha aponta para a opção "Anaconda Prompt (miniconda3)" nessa lista. Esta imagem está relacionada ao conteúdo sobre abrir um novo Anaconda Prompt para a teleoperação do robô móvel Lekiwi, mostrando os passos específicos para abrir o Anaconda Prompt e ajudar os leitores a entender o processo.](../en/images/d01-21.png)

> Se você estiver usando um Mac, talvez precise conceder permissão de "Terminal" para acessar o teclado para a teleoperação. Vá em "Preferências do Sistema" > "Segurança e Privacidade" > "Monitoramento de Entrada" e marque a caixa "Terminal".

Para teleoperar, faça login na sua Raspberry Pi via SSH, execute o seguinte comando para ativar o ambiente `conda activate lerobot` e então execute o seguinte script:

```Bash
python -m lerobot.robots.lekiwi.lekiwi_host --robot.id=my_awesome_kiwi
```

![Imagem mostrando a interface após ativar o ambiente `conda activate lerobot` e executar o script em um notebook. No topo aparece "Anaconda PowerShell Prompt" e, abaixo, "WARNING:root:No command available" é repetido várias vezes, terminando com "WARNING:root:Command not received for more than 500 milliseconds. Stopping the base." Isso está relacionado às etapas de teleoperação, mostrando as informações sobre a conexão com o robô remoto e o fluxo de vídeo que aparecem após ativar o ambiente e executar o script, em preparação para mover o braço de controle e conduzir o robô com o teclado.](../en/images/d01-22.png)

Em seguida, no seu notebook, execute também o seguinte comando para ativar o ambiente `conda activate lerobot` e então execute o seguinte script:

```Bash
python examples/lekiwi/teleoperate.py
```

A tela do seu notebook deve exibir algo como: `[INFO] Connected to remote robot at tcp://172.17.133.91:5555 and video stream at tcp://172.17.133.91:5556.` Agora você pode mover o braço de controle e usar as teclas (W, A, S, D) do teclado para conduzir o robô para frente, para a esquerda, para trás e para a direita. Use as teclas (Z, X) para girar o robô para a esquerda ou para a direita. Use as teclas (R, F) para aumentar ou diminuir a velocidade do robô. Há três modos de velocidade; veja a tabela abaixo:

<sheet sheet-id="vJeIqV" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

<sheet sheet-id="iR6oYP" token="Z4UGs2S65hWsWBtzlT8c80yCnqc"></sheet>

<callout emoji="💡">
Se você usar um teclado diferente, pode alterar o atalho de tecla para cada comando em [`LeKiWiClientConfig`](https://github.com/huggingface/lerobot/blob/main/src/lerobot/robots/lekiwi/config_lekiwi.py).
</callout>

## Solução de problemas de comunicação

Se você tiver dificuldade para conectar o robô móvel SO101, siga as etapas abaixo para diagnosticar e corrigir o problema.

### 1. Verificar a configuração do endereço IP

Certifique-se de que o endereço IP correto da Raspberry Pi esteja definido no arquivo de configuração. Para verificar o endereço IP da Raspberry Pi, execute o seguinte comando (na linha de comando da Pi):

```Bash
hostname -I
```

### 2. Verificar se o notebook/PC consegue alcançar a Pi

Tente fazer ping na Raspberry Pi a partir do notebook:

```Bash
ping <your_pi_ip_address>
```

Se o ping falhar:

- Certifique-se de que a Pi esteja ligada e conectada à mesma rede.
- Verifique se o SSH está habilitado na Pi.

### 3. Tentar uma conexão SSH

Se você não conseguir fazer login na Pi via SSH, a conexão pode estar incorreta. Use o seguinte comando:

```Bash
ssh <your_pi_user_name>@<your_pi_ip_address>
```

Por exemplo, `ssh pi@192.168.0.106`

Se você receber um erro de conexão:

- Certifique-se de que o SSH esteja habilitado na Pi; você pode executar o seguinte comando:

```Bash
sudo raspi-config
```

- Em seguida, navegue até: **Interfacing Options -> SSH** e habilite-o.

### 4. Consistência dos arquivos de configuração!!!

Certifique-se de que os arquivos de configuração no notebook/PC e na Raspberry Pi sejam exatamente iguais.

# F. Gravação de um dataset

Depois que você estiver confortável com a teleoperação, você pode usar o LeKiwi para gravar seu primeiro dataset.

Para iniciar o programa no LeKiwi, conecte-se à sua Raspberry Pi via SSH e execute os seguintes comandos para ativar o ambiente e iniciar o script:

```Bash
conda activate lerobot

python -m lerobot.robots.lekiwi.lekiwi_host --robot.id=my_awesome_kiwi
```

Se você quiser usar o Hugging Face Hub para enviar datasets e nunca tiver feito login antes, certifique-se de fazer login com um token de acesso de escrita, que você pode gerar nas [configurações da Hugging Face](https://huggingface.co/settings/tokens):

```Bash
hf auth login
```

Armazene o nome do seu repositório da Hugging Face em uma variável para executar o seguinte comando:

```Bash
hf auth whoami
```

Em seguida, execute o seguinte comando no seu notebook para gravar 2 episódios e enviar o dataset para o Hub:

```Bash
python examples/lekiwi/record.py
```

# G. Visualização de um dataset

Se você enviou o dataset, pode [visualizar seu dataset online](https://huggingface.co/spaces/lerobot/visualize_dataset); copie e cole o ID do repositório produzido pelo seguinte comando:

```Bash
echo ${HF_USER}/my_lekiwi_dataset
```

Se você não enviou o dataset, também pode visualizá-lo localmente (a ferramenta de visualização abre em uma janela do navegador em `http://127.0.0.1:9090`):

```Bash
python lerobot/scripts/visualize_dataset_html.py \
  --repo-id ${HF_USER}/lekiwi_test \
  --local-files-only 1
```

### Visualizar um dataset (opcional, vale a pena tentar)

```Bash
echo ${HF_USER}/my_lekiwi_dataset
```

Se você enviou o dataset, também pode visualizá-lo localmente com o seguinte comando:

```Python
lerobot-dataset-viz \
  --repo-id ${HF_USER}/my_lekiwi_dataset \
```

Se você não enviou o dataset, também pode visualizá-lo localmente com o seguinte comando:

```Python
lerobot-dataset-viz \
  --repo-id juxi/my_lekiwi_dataset \
```

Aqui, `juxi` é um nome de `repo_id` personalizado definido durante a coleta de dados.



#### Dicas de coleta de dados

Depois que você estiver confortável com a gravação de dados, poderá criar datasets maiores para treinamento. Uma boa tarefa inicial é pegar objetos de diferentes posições e colocá-los em um recipiente. Recomendamos gravar pelo menos 50 episódios, 10 por posição. Mantenha a posição da câmera fixa e mantenha o movimento de agarrar consistente durante toda a gravação. Além disso, certifique-se de que os objetos que você está manipulando estejam claramente visíveis no quadro da câmera. Uma regra prática simples: você deve conseguir concluir a tarefa apenas observando o feed da câmera.

Nas seções seguintes, você treinará sua rede neural. Depois de obter um desempenho de agarrar confiável, você pode começar a introduzir mais variação na coleta de dados, como adicionar posições de agarrar, usar diferentes técnicas de agarrar e alterar as posições da câmera.

Evite adicionar variação demais rápido demais, pois isso pode prejudicar seus resultados.

Se você quiser se aprofundar neste tópico importante, confira nossa [publicação no blog sobre o que faz um bom dataset.](https://huggingface.co/blog/lerobot-datasets#what-makes-a-good-dataset)

#### Solução de problemas:

No Linux, se as teclas de seta esquerda/direita e a tecla Esc não funcionarem durante a gravação de dados, certifique-se de que a variável de ambiente `$DISPLAY` esteja definida. Veja as [limitações do pynput](https://pynput.readthedocs.io/en/latest/limitations.html#linux)

# H. Reprodução de um episódio

Agora tente reproduzir o primeiro episódio no seu robô:

```Bash
python examples/lekiwi/replay.py
```

Parabéns 🎉 — seu robô está pronto para aprender tarefas por conta própria. Siga a seção de treinamento deste tutorial para começar a treiná-lo: [Introdução aos robôs do mundo real](https://huggingface.co/docs/lerobot/il_robots)

# I. Avaliação da sua política

Certifique-se de alterar remote_ip, port, HF_MODEL_ID

### Modificar evaluate.py

HF_MODEL_ID="<hf_username>/<model_repo_id>" altere isto para o nome do dataset enviado à Hugging Face após o treinamento (se você o enviou à Hugging Face), ou para o diretório local onde o modelo foi exportado após o treinamento

HF_DATASET_ID="<hf_username>/<eval_dataset_id>" altere isto para o nome de usuário que você criou e o nome do dataset eval_

remote_ip: o endereço IP da Raspberry Pi

![Imagem mostrando parte do arquivo evaluate.py no código de avaliação do robô móvel Lekiwi. A informação principal é a variável HF_MODEL_ID na linha 32, cujo valor é "<hf_username>/model_repo_id", e a variável HF_DATASET_ID na linha 33, cujo valor é "<hf_username>/eval_dataset_repo_id". Essas variáveis especificam os nomes do modelo e do dataset e devem ser alteradas para corresponder à sua situação: o nome do dataset enviado à Hugging Face após o treinamento (ou o diretório local), e o seu nome de usuário e o nome do dataset eval_. Esta imagem está relacionada à modificação do evaluate.py na seção de avaliação acima e serve como referência.](../en/images/d01-23.png)

Em seguida, execute o seguinte comando:

```Bash
python examples/lekiwi/evaluate.py
```

1. O nome do dataset começa com `eval` para refletir que você está executando uma inferência (por exemplo, `${HF_USER}/eval_act_lekiwi_test`).
2. Se durante a avaliação você encontrar `File exists: 'home/xxxx/.cache/huggingface/lerobot/xxxxx/juxi/eval_xxxx'`, primeiro exclua a pasta cujo nome começa com `eval_` e execute o programa novamente.



Para treinamento em simulação, consulte

https://github.com/Ekumen-OS/lekiwi/tree/main

https://github.com/SIGRobotics-UIUC/LeKiwi-sim



## Ajuda 🙋‍

Para problemas de hardware, entre em contato com o atendimento ao cliente. Para dúvidas de uso, entre no Discord.

[plataforma LeRobot](https://github.com/huggingface/lerobot)

[canal Discord do LeRobot](https://discord.gg/8TnwDdjFGU)

#   
  
Instalação do Miniconda no Mac

## Conceder permissões

![](../en/images/d01-24.png)

## Instalar o Miniconda

https://www.anaconda.com/download

## Alterando a fonte de pacotes do pip

```Shell
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple
```

## Alterando a fonte de pacotes do conda

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
