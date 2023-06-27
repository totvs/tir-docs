## Configuração:

Instalar o Docker seguindo as orientações da página do desenvolvedor.

1. Baixar arquivo build_dashboard.zip disponível neste  [link](https://github.com/totvs/tir/tree/master/dashboard/docker).
2. Descompactar o .zip para uma pasta e executar o comando "docker-compose up -d" dentro da pasta onde está o arquivo docker-compose.yml
3. Acessar no browser o endereço localhost:8066.

Para subir os logs de execução do TIR basta enviar para a api em localhost:3333

>## Observações:
Caso as portas defaults(3333 ou 8066) estiverem em uso, basta alterar o arquivo docker-compose.yml na seção "ports" conforme o exemplo abaixo:

    "8199:8080"
    "8198:3333"

As imagens estão disponíveis no [Docker hub](https://hub.docker.com/r/totvsengpro/tir-dashboard)