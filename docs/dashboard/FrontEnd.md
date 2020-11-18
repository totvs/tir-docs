# INSTALAÇÃO DO PORTAL (Front)

- Esse Portal tem como intuito exibir os gráficos com execuções que ocorreram nos ciclos.

???+ warning "Aviso"
    Após baixar o pacote com o portal deve ser selecionado um servidor web de sua preferência para colocar seu portal, como sugestão existe o Nginx, mas fique a vontade para selecionar o que esteja mais acostumado.

## Como instalar o Nginx:
Entre na página [Nginx](http://nginx.org/en/download.html) na parte de download e selecione o pacote conforme seu sistema operacional e faça o download.
Após isso deve seguir os seguintes passos:

- Descompactar o nginx no caminho desejado.
- Abrir o arquivo conf/nginx.conf localizando o trecho que contém "server {" e colocar e inserir o seguinte trecho:
## nginx.conf
    server {
        listen       8066;
        server_name  localhost;

        location / {
            root   html;
            index  index.html index.htm;
            try_files $uri $uri/ /index.html;
        }
    }
- Baixe os arquivos do portal  ( [Clique aqui para baixar](https://github.com/totvs/tir/raw/master/dashboard/servicelog-front.zip))
- Agora você deve descompactar o arquvio baixado e mover os arquivos para a pasta /html
- Abrir a pasta e executar o arquivo nginx.exe

- Veja o exemplo a seguir:

    ![](./gifs/instalacao.gif)


