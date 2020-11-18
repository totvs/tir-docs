# Serviço
Serviço utilizado para gravação e consulta dos logs dos testes realizados pelo TIR.

O pacote servicelog necessita do pacote do [Node.js](https://nodejs.org/) versão v12+.

## Configuração
[Clique aqui e baixe o arquivo zip](https://github.com/totvs/tir/raw/master/dashboard/servicelog-api-build.zip).
Após realizar o download utilize o arquivo ".env" para realizar a configuração do serviço conforme os parâmetros abaixo.

- databaseType - Tipo de banco de dados que serão armazenados os logs de execuções, podendo receber como parâmetros 'mssql' para Microsoft SQL ou 'sqlite' para SQLITE.
- databaseStorage - Quando informado o banco de dados SQLITE deve ser informado o caminho do banco que por default fica na pasta db do projeto.
- database - Tag database é responsavél pela comunicação do banco e possui os seguintes parâmetros:
	- instanceName - Nome da Instância do banco de dados.
	- host - Ip do servidor que está o banco de dados.
	- username - Usuário do banco de dados.
	- password - Senha do usuário do banco de dados.
	- database - Nome do banco de dados criado para receber os registros.
- pathServer - Informado o caminho da pasta onde será enviado os arquivos json em caso do servidor não conseguir gravar o registro no banco de dados.
- appPort - Porta que será inicializado a aplicação.
- pathProcessed - Pasta de arquivos que já foram processados quando o servidor apresenta uma contigência.
- schedule - Nessa opção é configurado qual será frequência de verificação de arquivos jsons da pasta configurada no "pathServer". 
Ela possui uma sintaxe abaixa

#### Campos permitidos
```
 # ┌────────────── segundos (optional)
 # │ ┌──────────── minutos
 # │ │ ┌────────── horas
 # │ │ │ ┌──────── dias do mês
 # │ │ │ │ ┌────── mês
 # │ │ │ │ │ ┌──── dia da semana
 # │ │ │ │ │ │
 # │ │ │ │ │ │
 # * * * * * *
```

### Valores permitidos

|     campos   | valores permitidos  |
|--------------|---------------------|
|   segundos   |         0-59        |
|   minutos    |         0-59        |
|     hora     |         0-23        |
|  dia do mês  |         1-31        |
|      mês     |     1-12 (or names) |
|dia da semana |    0-7 (nomes ou números, 0 ou 7 domingo à sábado)  |

No padrão está da seguinte forma:
 - \* 7,12,18,23 * * * - Dessa forma será executado o serviço as 7hrs, 12hrs, 18hrs e 23hrs todos os dias.

## Instalação
Depois de extrair os aquivos e configurar o arquivo ".env" localize o diretório "scripts-bats" e execute os scripts utilizando o prompt de comando do windows na sequência abaixo e em modo de administrador.

 - install.bat - Descompactar os pacotes do npm.
 - service-mode.bat - Instalação a api em modo de serviço.
 - run.bat - Inicializa o serviço.

Em caso de necessidade poderá desligar o serviço com o bat abaixo.

 - stop.bat - Desliga o serviço
