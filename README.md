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
    python3 -m pip install virtualenv
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
    mkdir -pv ~/.venvs
    ```

4. Instalar o(s) pacote(s) abaixo no gerenciador `pip`:

    ```bash
    python3.10 -m venv "$HOME/.venvs/<nome_do_projeto>"  # Você também pode usar a versão do `python` como sendo
    # o nome do ambiente virtual, por exemplo: `python3.10env`
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
    source "$HOME/.venvs/<nome_do_projeto>/bin/activate"
    ```

    Perceber que, depois de `~/.venvs/<nome_do_projeto>`, existe a pasta
    `~/.venvs` (caso você tenha optado por criá-la) e o comando
    `/bin/activate`

4. Atualizar `pip`, `setuptools` e `wheel` no ambiente virtual ativo:

    ```bash
    python -m pip install --upgrade pip setuptools wheel
    ```

5. Verificar as versões instaladas:

    ```bash
    python -m pip show pip setuptools wheel
    ```

6. Verificar possíveis conflitos entre as dependências instaladas:

    ```bash
    python -m pip check
    ```



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
    C:\Users\venvs\Scripts\activate
    ```

## 2.4 Instalar as dependências a partir do arquivo `requirements.txt`

**ATENÇÃO:** Executar o código abaixo somente se for instalar as
dependências do ambiente virtual já criado. **NÂO** se assuste caso
tenha executado este código, pois será verificado a(s) versão(ões) do(s)
pacote(s).

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

## 2.5 Consultar se o ambiente virtual correto está ativo

1. No `Linux Ubuntu`, execute os comandos abaixo depois de ativar o ambiente. Substitua `<nome_do_projeto>` pelo nome usado ao criar o ambiente em `~/.venvs/`.

    ```bash
    expected_venv="$HOME/.venvs/<nome_do_projeto>"

    printf 'VIRTUAL_ENV=%s\n' "${VIRTUAL_ENV:-not defined}"
    command -v python3
    python3 -m pip --version

    python3 - "$expected_venv" <<'PY'
    import os
    import sys

    expected = os.path.realpath(os.path.expanduser(sys.argv[1]))
    active = os.path.realpath(sys.prefix)
    is_virtualenv = sys.prefix != sys.base_prefix
    matches_expected = is_virtualenv and active == expected

    print(f"Interpreter: {sys.executable}")
    print(f"sys.prefix: {sys.prefix}")
    print(f"Active virtual environment: {'yes' if is_virtualenv else 'no'}")
    print(f"It's the expected environment: {'yes' if matches_expected else 'no'}")

    raise SystemExit(0 if matches_expected else 1)
    PY
    ```

    `command -v python3` mostra o interpretador encontrado no `PATH`, e 
    `python3 -m pip --version` mostra qual instalação do `pip` será 
    usada. A verificação em `Python` compara o ambiente ativo com o 
    caminho esperado e termina com código `0` quando corresponde; caso 
    contrário, termina com código `1`.


## 2.6 Registrar o ambiente virtual como kernel Jupyter

O registro associa um ambiente virtual já criado ao `Jupyter` para que ele possa executar células de notebooks `.ipynb` e apareça como opção de kernel no `VS Code`. O comando de registro não cria nem ativa o ambiente virtual. Para projetos que executam somente arquivos `.py`, esta etapa não é necessária.

1. Crie e ative o ambiente virtual conforme as Seções **2.1** e **2.3**. Antes de registrar, confirme que o interpretador correto está ativo seguindo a Seção **2.5**.

2. Instale o `ipykernel` dentro desse ambiente, caso ainda não esteja instalado:

    ```bash
    python -m pip install ipykernel
    ```

    Se o projeto tiver um arquivo `requirements.txt`, instale também as dependências do projeto conforme a Seção **2.4**.

3. Com o ambiente ativado, registre-o como kernel. Neste exemplo, substitua `kepler` pelo nome do projeto e ajuste a versão exibida conforme a saída de `python --version`:

    ```bash
    python -m ipykernel install --user \
        --name kepler \
        --display-name "kepler (Python 3.10.12)"
    ```

    O argumento `--name` define o identificador do kernel; `--display-name` define o nome mostrado no `Jupyter` e no `VS Code`. A opção `--user` registra o kernel para o usuário atual.

    Se não quiser ativar o ambiente antes, execute o mesmo registro com o caminho do interpretador desse ambiente:

    ```bash
    "$HOME/.venvs/kepler/bin/python" -m ipykernel install --user \
        --name kepler \
        --display-name "kepler (Python 3.10.12)"
    ```

4. Consulte os kernels registrados:

    ```bash
    jupyter kernelspec list
    ```

    No `VS Code`, abra o notebook `.ipynb`, escolha **Select Kernel** e selecione o nome registrado. Se o kernel ainda não aparecer, atualize a lista de kernels ou reabra o `VS Code`.



## Compatibilidade

- Testado em `Linux Ubuntu` (recomendado `22.04+`).
- Deve funcionar em `Debian` e `WSL`, desde que o `Git` e o `Bash` estejam disponíveis.


## Licença

Este repositório inclui o arquivo `LICENSE.txt`.



## Contato e suporte

Para dúvidas ou problemas, abra uma issue no repositório do `GitHub`.


# Referências

[1] MATTHEUS, E..
**Python Crash Course: A Hands-On, Project-Based Introduction to Programming (2nd ed.)**.
No Starch Press, 2019.

[2] OPENAI.
**Instalar o `virtualenv` no `linux ubuntu` pelo `terminal emulator`**.
Disponível em: <https://chatgpt.com/c/69aedf3c-7c04-8331-8a36-66e1fc2bffa4>.
ChatGPT.
Acessado em: 10/mar/2026.
