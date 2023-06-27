# Configurando o TIR
Após seguir os passos de instalação do serviço e do portal agora vamos configurar o TIR.

## Config.json
O arquivo que realiza as configurações do TIR é nomeado como config.json, se trata de um arquivo no qual vamos informar alguns dados nescessários sendo eles:

    - NewLog: Habilita o novo log
    - MotExec: Específica o motivo da execução
    - ExecId: Específica um id para execução sendo geralmente a data atual
    - LogUrl1: Url do serviço

>### Exemplo de configuração:
```json
"NewLog": true,
"MotExec": "HOMOLOGAÇÃO_TIR",
"ExecId": "20201007",
"LogUrl1": "http://127.0.0.1:3333/log/"
```

Para mais informações acesse a documentação completa sobre o [arquivo de configuração do TIR (config.json)](https://totvs.github.io/tir/configjson).