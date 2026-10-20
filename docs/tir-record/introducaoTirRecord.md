# Bem-vindo ao TIR Record 3.0.0

TIR Record é um projeto que visa facilitar a criação de scripts para o [TIR](https://github.com/totvs/tir), o TIR Record não substitui
a necessidade de entender e compreender como o TIR funciona (recomendamos que leiam a [documentação](https://totvs.github.io/tir/) e o [README do projeto](https://github.com/totvs/tir)).

A partir da versão 3.0.0 o TIR Record reconhece ações tanto nas telas **WebApp (Smartclient+HTML)** quanto nas telas **PO-UI**, gerando os métodos correspondentes em cada contexto.

## Ações suportadas

As ações suportadas variam conforme o tipo de interface utilizada. Abaixo estão separadas por **WebApp** e **PO-UI**.

### WebApp

* `Preenchimento de campos (SetValue)`
* `Cliques em botões (SetButton)`
* `Marcar itens / checkbox (ClickBox)`
* `Clicar em pastas (ClickFolder)`
* `Clicar em textos (ClickLabel)`
* `Clicar em um item de menu (ClickMenuPopUpItem)`
* `Interagir com o componente "Tree" (ClickTree)`
* `Checar o resultado (CheckResult)`
* `Pesquisar uma rotina (Program)`
* `Pesquisar uma rotina utilizando o menu lateral (SetLateralMenu)`
* `Pressionar uma tecla (SetKey)`
* `Realizar uma pesquisa (SearchBrowse)`
* `Adicionar o comando LoadGrid`
* `Aguardar processamento (WaitProcessing)`
* `Aguardar exibição de um texto (WaitShow)`
* `Validar se as operações foram verdadeiras (AssertTrue)`
* `Validar se as operações foram falsas (AssertFalse)`
* `Método de configuração da classe (SetupClass → Setup e Program)`
* `Finalizar o ambiente (TearDown)`

### PO-UI

* `Preenchimento de campos (InputValue)`
* `Cliques em botões (ClickButton)`
* `Clicar em ícones (ClickIcon)`
* `Clicar no avatar (ClickAvatar)`
* `Clicar em um menu (ClickMenu)`
* `Clicar em popup (ClickPopup)`
* `Selecionar valor em combo (ClickCombo)`
* `Selecionar valor em select (ClickSelect)`
* `Marcar checkbox (ClickCheckBox)`
* `Selecionar radio (ClickRadio)`
* `Alternar switch (ClickSwitch)`
* `Interagir com tabelas (ClickTable)`
* `Interagir com widgets (ClickWidget)`
* `Navegar em abas (POtabs)`
* `Realizar pesquisa (POSearch)`
* `Checar o resultado (CheckResult)`
* `Pesquisar uma rotina (Program)`
* `Aguardar processamento (WaitProcessing)`
* `Aguardar exibição de um texto (WaitShow)`
* `Validar se as operações foram verdadeiras (AssertTrue)`
* `Validar se as operações foram falsas (AssertFalse)`
* `Finalizar o ambiente (TearDown)`
