# Como instalar/configurar/usar o `virtualenv` no `Linux Ubuntu` pelo `Terminal Emulator`

Neste documento estão contidos os principais comandos e configurações para instalar/configurar/usar o `virtualenv` no `Linux Ubuntu`.

## _Abstract_

_This document contains the main commands and settings to install/configure/use the `virtualenv` on `Linux Ubuntu`._

## Descrição

### `virtualenv`

O `virtualenv` é uma ferramenta para criar ambientes virtuais isolados para projetos `Python`.
Ele permite que você tenha diferentes versões de pacotes e dependências para cada projeto, sem 
interferir com o sistema global do `Python`.

## Pré-requisitos

[![Git](https://img.shields.io/badge/Git-installed-F05032?logo=git&logoColor=white)](https://git-scm.com/)

[![GitHub SSH](https://img.shields.io/badge/GitHub-SSH%20key%20configured-181717?logo=github&logoColor=white)](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

[![Repository](https://img.shields.io/badge/GitHub-edftechnology%2Fshell_scripts-181717?logo=github&logoColor=white)](https://github.com/edftechnology/shell_scripts)

# 1 Configurar/Instalar/Usar o `virtualenv` no `Linux Ubuntu` pelo `Terminal Emulator`

Para configurar/instalar/usar o `shell_scripts`, siga os passos abaixo:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```


2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:
    ```bash
    sudo apt clean
    ```

    2.2 Remover pacotes `.deb` antigos ou duplicados do `cache` local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando:
    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando:
    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt update
    ```

    2.5 **Corrigir pacotes quebrados**: Isso atualizará a lista de pacotes disponíveis e tentará corrigir pacotes quebrados ou com dependências ausentes:
    ```bash
    sudo apt --fix-broken install
    ```

    2.6 Limpar o `cache` do gerenciador de pacotes `apt` novamente:
    ```bash
    sudo apt clean
    ```

    2.7 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt list --upgradable
    ```

    2.8 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update`. Digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt full-upgrade -y
    ```


3. Se quiser garantir que o `pip` esteja atualizado (boa prática):

    ```bash
    python3 -m pip install --upgrade pip
    ```

4. **Instalar o `virtualenv`**: Execute o comando:

    ```bash
    python3 pip install -m virtualenv
    ```


## 2. Comandos do `virtualenv`

### 2.1 Criar o ambiente virtual

**ATENÇÂO:**

- Somente criar o ambiente virtual se este **NÃO** existir. **NÂO** se assuste caso tenha executado este código, pois, possivelmente será criado um ambiente virtual com o mesmo nome e deverá ser instalos o(s) pacote(s) e suas dependências, ver Seção **Instalar as dependências a partir do arquivo requirements**.

- Executar o código abaixo somente se for instalar as dependências do ambiente virtual já criado.

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. Acessar a pasta do seu projeto:

    ```bash
    cd <caminho_ate_o_projeto>
    ```

3. Criar a pasta para `venvs` para ambientes virtuais (opcional):

    ```bash
    mkdir -pv /venvs
    ```

4. Instalar o(s) pacote(s) abaixo no gerenciador `pip`:

    ```bash
    python3.8 -m venv "<nome_do_projeto>/"  # Você também pode usar a versão do `python` como sendo
    # o nome do ambiente virtual, por exemplo: `python3.8env`
    ```


### 2.2 Congelar os pacotes de um projeto no arquivo `requirements.txt`

Para congelar os pacotes de um projeto no arquivo `requirements.txt`, siga os passoa abaixo:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. Acessar a pasta do seu projeto:

    ```bash
    cd <caminho_ate_o_projeto>
    ``` 

3. Congelar os pacotes de um projeto no arquivo `requirements.txt`:

    ```bash
    pip freeze > "requirements.txt"
    ```

### 2.3 Ativar um ambiente virtual

Para ativar um ambiente virtual, siga os passos abaixo:

#### 2.3.1 `Linux Ubuntu`

Para ativar um ambiente virtual no `Linux Ubuntu`, siga os passos abaixo:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. Acessar a pasta do seu projeto:

    ```bash
    cd <caminho_ate_o_projeto>
    ``` 

3. Ativar o ambiente virtual no `Linux Ubuntu`:

    ```bash
    source "/caminho/ate/o/projeto/venvs/bin/activate"
    ```

    Perceber que, depois de `/caminho/ate/o/projeto`, existe a pasta `/venvs` (caso você tenha
    optado por criá-la) e o comando `/bin/activate`

### 2.3.2 `Windows`

Para ativar um ambiente virtual no `Windows`, siga os passoa abaixo:

1. Abrir o `Terminal`; Você pode fazer isso pressionando:

    ```cmd
    Win + R
    ```

2. Acessar a pasta do seu projeto:

    ```cmd
    cd <caminho_ate_o_projeto>
    ```

3. Ativar o ambiente virtual no `Windows`:

    ```cmd
    venvs\Scripts\activate
    ```

## 2.4 Instalar as dependências a partir do arquivo requirements.txt

**ATENÇÃO:** Executar o código abaixo somente se for instalar as dependências do ambiente virtual já criado. **NÂO** se assuste caso tenha executado este código, pois será verificado a(s) versão(ões) do(s) pacote(s).

1. Abrir o `Terminal`; Você pode fazer isso pressionando:

    ```cmd
    Win + R
    ```

2. Acessar a pasta do seu projeto:

    ```cmd
    cd <caminho_ate_o_projeto>
    ```

3. Instalar todas as dependências necessárias executando o comando:

    ```cmd
    pip install -r "{freeze_file_path}"
    ```

## Compatibilidade

- Testado em `Linux Ubuntu` (recomendado `22.04+`).
- Deve funcionar em `Debian` e `WSL`, desde que o `Git` e o `Bash` estejam disponíveis.


## Licença

Este repositório inclui o arquivo `LICENSE.txt`.



## Contato e suporte

Para dúvidas ou problemas, abra uma issue no repositório do `GitHub`.


# Referências

[1] MATTHEUS, E.. **_Python Crash Course: A Hands-On, Project-Based Introduction to Programming (2nd ed.)_**. No Starch Press, 2019.

[2] OPENAI. ***Instalar o `virtualenv` no `linux ubuntu` pelo `terminal emulator`***. Disponível em: <https://chatgpt.com/c/69aedf3c-7c04-8331-8a36-66e1fc2bffa4>. ChatGPT. Acessado em: 10/03/2026.

