# Flexera Agent Update - Readme

## Descrição

Este script atualiza o agente Flexera no ambiente Linux. Ele realiza diversas ações, incluindo clonar um repositório git, instalar um pacote RPM, e configurar opções específicas do agente.

## Pré-requisitos

- Sistema operacional Linux com suporte a RPM
- Acesso ao repositório git que contém o pacote RPM

## Como Usar

**ATENÇÃO**: Antes de rodar este script, certifique-se de que você tem as permissões necessárias e que você compreende o impacto dessas mudanças no seu sistema.

1. Faça o clone do repositório:

    ```bash
    git clone [URL_DO_REPOSITÓRIO]
    ```

2. Entre na pasta do projeto e dê permissões de execução ao arquivo RPM:

    ```bash
    cd flexera-agent-update
    chmod +x managesoft-18.0.0-1.x86_64.rpm
    ```

3. Instale o pacote RPM:

    ```bash
    rpm -Uvh managesoft-18.0.0-1.x86_64.rpm
    ```

4. Navegue até o diretório de binários do Flexera:

    ```bash
    cd /opt/managesoft/bin
    ```

5. Execute o comando de política:

    ```bash
    ./mgspolicy –t machine -o DownloadRootURL=[SUA_URL]
    ```

6. Habilite o agendador:

    ```bash
    /opt/managesoft/bin/ndschedag -e
    ```

7. Rode o tracking com as opções desejadas:

    ```bash
    /opt/managesoft/bin/ndtrack -t machine -o Logging=true -o LogLevel=A-Z -o LogFile=/var/tmp/ndtrack_debug.txt -o LogModules=default -o UploadLocation="[SUA_URL]"
    ```

## Variáveis

- `[URL_DO_REPOSITÓRIO]`: URL do repositório git que contém o pacote RPM.
- `[SUA_URL]`: URL da sua instalação Flexera para download e upload.

## Logs

Os logs de debug serão armazenados em `/var/tmp/ndtrack_debug.txt`.

## Suporte

Para mais informações ou questões, por favor, contacte a equipa SysUnix.

## Autor

Michael Melo

## Contribuições

Contribuições são bem-vindas através de Pull Requests. Certifique-se de atualizar o Readme conforme necessário.
