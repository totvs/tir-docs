# Execução via Docker Compose

É possível executar o TIR em Docker apontando para um ambiente externo do Protheus. Este procedimento usa o [Docker Desktop](https://www.docker.com/products/docker-desktop/) e Docker Compose.

## Arquivos necessários

Crie um diretório para armazenar os arquivos da execução. Nesse diretório, mantenha o `compose.yaml`, o `config.json`, a suíte de testes indicada no Compose e a pasta de saída dos screenshots.

Crie um arquivo `compose.yaml` com a estrutura abaixo:

```yaml
services:
  tir:
    image: totvsengpro/tir:latest
    working_dir: /local
    volumes:
      - .:/local
      - /etc/passwd:/etc/passwd:ro
      - /etc/group:/etc/group:ro
    environment:
      DISPLAY: "${DISPLAY:-:0}"
      HOME: /tmp
    user: "${USER_ID:-1000}:${GROUP_ID:-1000}"
    stdin_open: true
    tty: true
    command: python3 /local/ATFA036TESTSUITE.py
```

> **Importante:** o valor de `command` deve apontar para uma suíte existente no mesmo diretório do `compose.yaml`. Caso a sua suíte tenha outro nome, altere `ATFA036TESTSUITE.py` para o nome correto.

Os mounts `/etc/passwd` e `/etc/group`, assim como as variáveis `USER_ID` e `GROUP_ID`, são destinados a ambientes Linux/WSL. No Docker Desktop executado apenas no Windows, avalie se esses itens são necessários para o seu ambiente. Para execução sem interface gráfica, mantenha `"Headless": true` no `config.json`.

## Executar o TIR

1. Configure o `config.json` com os dados do ambiente externo. O campo `Url` deve conter a URL do WebApp Protheus que será acessado pelo container. Para a execução no Docker, recomendamos habilitar o modo sem interface gráfica:

   ```json
   {
     "Headless": true
   }
   ```

   Consulte a descrição dos demais parâmetros em [config.json](https://totvs.github.io/tir/configjson.html).
2. No PowerShell, execute os comandos no diretório que contém o `compose.yaml`:

   ```powershell
   docker compose pull
   docker compose up --abort-on-container-exit
   ```

   Para executar os mesmos comandos de outro diretório, informe o arquivo Compose com `-f`:

   ```powershell
   docker compose -f <caminho-para-o-compose.yaml> pull
   docker compose -f <caminho-para-o-compose.yaml> up --abort-on-container-exit
   ```

O volume `.:/local` torna os arquivos do diretório do Compose disponíveis no container e preserva no host os screenshots e outros arquivos gerados pela execução.

As imagens estão disponíveis no [Docker Hub](https://hub.docker.com/r/totvsengpro/tir).
