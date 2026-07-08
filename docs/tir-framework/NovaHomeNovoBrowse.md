# Nova Home e Novo Browse (POUI) — Guia de Adaptação

> Válido a partir da release **12.1.2610**, mantendo compatibilidade com a **12.1.2510**.

A partir dessa release, o Protheus passa a contar com duas novidades visuais e de navegação:

- **Nova Home**: uma nova forma de acessar as rotinas do sistema.
- **Novo Browse (POUI)**: uma nova grade de listagem de registros, com botões e comportamentos diferentes do modelo tradicional (WebApp).

O TIR já foi preparado para lidar com essas mudanças na maioria dos casos, de forma automática. Esta página explica o que muda na prática e traz exemplos de como adaptar seus scripts quando for necessário.

## Nova Home

### O que muda

A Nova Home altera a forma como o usuário chega até uma rotina. Na prática, isso pode afetar scripts que navegam pelo menu lateral para abrir uma tela.

O acesso e a busca de rotinas pela Nova Home ainda estão evoluindo, então não existe uma recomendação única e definitiva — o ideal é avaliar caso a caso, testando o script no ambiente com a Nova Home habilitada.

### Habilitando a Nova Home nos testes

Para que os testes considerem a Nova Home, adicione a seguinte chave no arquivo de configuração do TIR (`config.json`):

```json
{
    "NewHome": true
}
```

### Acessando rotinas: `SetLateralMenu` x `SetProgram`

**Como era antes**, usando apenas o caminho do menu:

```python
oHelper.SetLateralMenu("Atualizações > Cadastro > Produto")
```

**Com a Nova Home**, pode ser necessário informar também o nome do programa e o módulo, para garantir que a rotina certa seja encontrada:

```python
oHelper.SetLateralMenu(
    "Atualizações > Cadastro > Produtos",
    program_name="MATA410",
    module="AGD"
)
```

**Alternativa mais simples e direta**: se o script não depende do caminho do menu (ou seja, não precisa navegar pelos submenus para validar algo), prefira acessar a rotina diretamente pelo nome do programa com `SetProgram`:

```python
# Exemplo simples
oHelper.SetProgram("MATA010")

# Selecionando o módulo pelo nome
oHelper.SetProgram("MATA010", "Faturamento")

# Selecionando o módulo pela sigla
oHelper.SetProgram("MATA010", "SIGAFIN")
```

**Dica prática**: use `SetLateralMenu` só quando o script realmente precisa validar a navegação pelo menu. Nos demais casos, `SetProgram` é mais simples e mais estável.

## Novo Browse (POUI)

O Novo Browse é a nova grade de listagem de registros. Os botões, a busca e algumas ações mudaram de nome ou de comportamento em relação ao browse legado (WebApp).

A boa notícia: o TIR identifica automaticamente qual browse está em uso e traduz a maioria dos comandos legados para o equivalente no POUI. Na maior parte dos scripts, nenhuma alteração é necessária.

### Como saber qual browse está sendo usado

Se precisar tomar uma decisão diferente dependendo do tipo de browse, use:

```python
oHelper.IsNewBrowse()
```

| Retorno | Significado |
|---|---|
| `False` | Browse legado (WebApp) |
| `True` | Novo Browse (POUI) |

Na maioria dos casos você não precisa chamar esse método diretamente — ele é mais útil quando o mapeamento automático (explicado a seguir) não é suficiente.

### Mapeamento automático de botões

O TIR já traduz automaticamente os botões mais comuns quando você usa `SetButton()`:

| Comando no script | O que acontece no browse legado | O que acontece no Novo Browse |
|---|---|---|
| `SetButton("Incluir")` | Clica em "Incluir" | Clica em "Incluir" |
| `SetButton("Alterar")` | Clica em "Alterar" | Clica em "Editar" |
| `SetButton("Visualizar")` | Clica em "Visualizar" | Clica no ícone "Visualizar" |
| `SetButton("Excluir")` | Clica em "Excluir" | Clica em "Excluir" |
| `SetButton("Outras Ações", ...)` | Abre o menu "Outras Ações" | Abre "Ações de Registro" |

Isso funciona de forma transparente quando o `SetButton` é chamado logo depois do `SearchBrowse`:

```python
oHelper.SearchBrowse("D MG 01 0001")   # identifica o tipo de browse
oHelper.SetButton("Incluir")           # já é traduzido automaticamente
```

**Quando o botão pertence ao próprio browse** (e não a uma tela que abriu depois), use `is_browse=True` para garantir que o TIR confira o tipo de browse exatamente no momento do clique:

```python
oHelper.SetButton("Incluir", is_browse=True)
oHelper.SetButton("Outras Ações", "Excluir", is_browse=True)
```

### Quando o script precisa de ajuste manual

Existem alguns cenários em que o mapeamento automático não é suficiente e o script precisa tratar os dois casos (legado e POUI) explicitamente.

**1. O nome do botão mudou entre os layouts** (por exemplo, "Copiar" virou "Duplicar"):

```python
if not oHelper.IsNewBrowse():
    oHelper.SetButton("Copiar")
else:
    oHelperPOUI.ClickButton("Duplicar")
```

**2. Existe uma ação intermediária que "quebra" a detecção automática** (por exemplo, um `SetKey("F12")` entre a busca e o clique no botão):

```python
oHelper.SearchBrowse("D MG 01 0001")
oHelper.SetKey("F12")   # essa ação no meio do caminho quebra o mapeamento automático

if not oHelper.IsNewBrowse():
    oHelper.SetButton("Incluir")
else:
    oHelperPOUI.ClickButton("Incluir")
```

**3. A ação está dentro de "Outras Ações"**:

```python
if not oHelper.IsNewBrowse():
    oHelper.SetButton("Outras Ações", "Excluir")
else:
    oHelperPOUI.ClickButton("Excluir")
```

**4. Uma única ação legada corresponde a mais de uma ação no POUI** (exemplo: "Baixar"):

```python
if not oHelper.IsNewBrowse():
    oHelper.SetButton("Outras Ações", "Baixar")
else:
    oHelperPOUI.ClickButton("Ações de Registros")
    oHelperPOUI.ClickPopUp("Baixar")
```

Também é possível simplificar esse mesmo caso com `ClickDropdown`:

```python
oHelperPOUI.ClickDropdown("Ações de Registro", ["Baixar"])
```

### Pesquisando registros: de `SearchBrowse` para `FilterBrowse`

No browse legado, a busca era feita com um termo único de texto. No Novo Browse, a busca passa a ser feita por **filtros estruturados**, ou seja, um valor específico para cada campo.

| | Antes (legado) | Agora (POUI) |
|---|---|---|
| Forma de busca | Termo único | Filtros por campo |
| Método | `SearchBrowse("D MG 01 0001")` | `FilterBrowse(filters=[...])` |

Existem duas formas de adaptar seus scripts a essa mudança:

**Opção 1 — Compatibilidade implícita (recomendada)**

Continue usando `SearchBrowse` normalmente, mas passe também o parâmetro `filters`. O TIR decide automaticamente a melhor forma de buscar, dependendo do tipo de browse detectado:

```python
filters = [
    {
        "Filial": "D MG 01",
        "Produto": "COM000000000000000000000000022"
    }
]

oHelper.SearchBrowse(
    "D MG 01 COM000000000000000000000000022",
    filters=filters
)
```

Essa é a forma mais simples: funciona tanto no browse legado quanto no Novo Browse, sem precisar duplicar lógica no script.

**Opção 2 — Compatibilidade explícita (controle total)**

Se preferir controlar manualmente o que acontece em cada caso:

```python
if not oHelper.IsNewBrowse():
    # Fluxo legado
    oHelper.SearchBrowse("D MG 01 COM000000000000000000000000022")
else:
    # Fluxo POUI
    filters = [
        {
            "Filial": "D MG 01",
            "Produto": "COM000000000000000000000000022"
        }
    ]
    oHelperPOUI.FilterBrowse(filters=filters)
```

**Boa prática**: no Novo Browse, sempre que possível, use o parâmetro `filters`. Se ele não for informado, o TIR tenta localizar o registro usando apenas o termo mais longo passado para busca, o que é menos preciso.

Vale lembrar também que, no Novo Browse, cada nova busca via `filters` limpa automaticamente filtros e seleções anteriores, evitando que resultados de execuções passadas interfiram no teste atual.

## Cenários especiais

### Comandos exclusivos de releases mais novas

Se um trecho do script só existe (ou só faz sentido) a partir da release 12.1.2610, use `GetRelease()` para isolar essa lógica:

```python
if oHelper.GetRelease() >= "12.1.2610":
    oHelperPOUI.FilterBrowse(filters=filters)
    oHelperPOUI.ClickButton("Incluir")
```

### Rotinas "Smart X"

Rotinas que passaram por uma reformulação mais profunda (conhecidas como Smart X) tendem a ter um fluxo bem diferente do legado. Nesses casos, em vez de tentar adaptar o script antigo, o recomendado é criar um script novo, dedicado a esse fluxo.

### E se eu encontrar um caso que o mapeamento automático não resolve?

1. Primeiro, tente resolver com um tratamento condicional no próprio script, usando `IsNewBrowse()` ou `GetRelease()`, como nos exemplos acima.
2. Se não for possível, abra uma task no Ryver ou Gitter para o time de Automação avaliar uma evolução no helper.

## Checklist rápido de migração

**Nova Home**

- [ ] Habilitar `"NewHome": true` no `config.json`, quando aplicável.
- [ ] Revisar usos de `SetLateralMenu` e adicionar `program_name` / `module` quando necessário.
- [ ] Avaliar migrar para `SetProgram` quando o caminho do menu não for relevante para o teste.

**Novo Browse**

- [ ] Revisar usos de `SearchBrowse` e avaliar adicionar o parâmetro `filters`.
- [ ] Escolher, por script, entre compatibilidade implícita ou explícita.
- [ ] Revisar cliques em botões, usando `is_browse=True` quando o botão pertence ao próprio browse.
- [ ] Tratar botões renomeados e ações intermediárias com `IsNewBrowse()`.
- [ ] Isolar lógicas exclusivas da nova release com `GetRelease() >= "12.1.2610"`.
- [ ] Para rotinas Smart X, planejar um script dedicado.
- [ ] Validar a execução nas releases 12.1.2510 e 12.1.2610.
