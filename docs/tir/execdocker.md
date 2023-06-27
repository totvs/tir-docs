# Execução via Docker

É possível a execução do TIR via Docker. Para isso é necessário que:

1. Baixe os exemplos dos arquivos que serão necessários para a execução na pasta [basic tamplate](https://github.com/totvs/tir-script-samples/tree/master/basic_template).
2. No powershell acessar a pasta onde descompactou os arquivos 
3. Execute o comando:
>#### docker pull totvsengpro/tir
4. Em seguida, execute o comando conforme exemplo abaixo:
>####
    docker run --rm -ti 
    -v ${PWD}:/local 
    -v /etc/passwd:/etc/passwd 
    -v /etc/groups:/etc/groups 
    -e DISPLAY=:0 
    -u $(id -u):$(id -g) 
    totvsengpro/tir:latest python3 /local/ATFA036TESTSUITE.py

As imagens estão disponíveis em [Docker Hub](https://hub.docker.com/r/totvsengpro/tir).