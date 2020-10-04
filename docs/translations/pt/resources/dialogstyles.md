---
title: Dialog Styles
---

:::note

- Em [OnDialogResponse](../callbacks/OnDialogResponse), pressionar **button1** define **response** para **1**, enquanto pressionar **button2** define **response** para **0**.
- Todo dialog tem um button2 opcional. Para que ele n�o seja mostrado, mantenha o par�metro vazio, como no primeiro exemplo. Os jogadores n�o poder�o clic�-lo, mas eles ainda poder�o apertar ESC e chamar [OnDialogResponse](../callbacks/OnDialogResponse) com **response** = **0**.
- [ShowPlayerDialog](../functions/ShowPlayerDialog): As cores embutidas podem ser utilizadas nos par�metros: **caption**, **info**, **button1** e **button2**.

:::

- Esta p�gina descreve o comportamento de [ShowPlayerDialog](../functions/ShowPlayerDialog) e [OnDialogResponse](../callbacks/OnDialogResponse).
- Por v�rias limita��es, visite a p�gina de [Limites](../resources/limits).
- Para exemplos de resposta, o seguinte c�digo ser� usado:

```c
public OnDialogResponse( playerid, dialogid, response, listitem, inputtext[ ] )
{
    printf( "playerid = %d, dialogid = YOUR_DIALOGID, response = %d, listitem = %d, inputtext = '%s' (size: %d)", playerid, response, listitem, inputtext, strlen( inputtext ) );
    return 1;
}
```

## Estilo 0: `DIALOG_STYLE_MSGBOX`

![](/images/dialogStyles/Dialog_style_msgbox.png)

Visualiza��o:

:::note

- **\t** adiciona um TAB (mais espa�o).
- **\n** cria uma nova linha.
- Cores embutidas n�o resetar�o ap�s \n ou \t

:::

```c
ShowPlayerDialog(playerid, YOUR_DIALOGID, DIALOG_STYLE_MSGBOX, "Caption", "Info\n\tInfo", "Button 1", "");
```

### Sa�da de Resposta

:::note

- **listitem** � sempre **-1**.
- **inputtext** � sempre vazio.

:::

```c
// Bot�o pressionado
playerid = 0, dialogid = YOUR_DIALOGID, response = 1, listitem = -1, inputtext = '' (size: 0)

// ESC pressionado (j� que o segundo bot�o n�o est� vis�vel)
playerid = 0, dialogid = YOUR_DIALOGID, response = 0, listitem = -1, inputtext = '' (size: 0)
```

## Estilo 1: `DIALOG_STYLE_INPUT`

![](/images/dialogStyles/Dialog_style_input.png)

Visualiza��o:

:::note

- **\t** adiciona um TAB (mais espa�o).
- **\n** cria uma nova linha.
- Cores embutidas n�o resetar�o ap�s \n ou \t

:::

```c
ShowPlayerDialog(playerid, YOUR_DIALOGID, DIALOG_STYLE_INPUT, "Caption", "Enter information below:", "Button 1", "Button 2");
```

### Sa�da de Resposta

:::note

- **listitem** � sempre **-1**.
- **inputtext** � o texto escrito pelo usu�rio, incluindo poss�veis cores.

:::

```c
// Escreveu "input" e apertou o bot�o esquerdo
playerid = 0, dialogid = YOUR_DIALOGID, response = 1, listitem = -1, inputtext = 'input' (size: 5)

// Escreveu "input" e apertou o bot�o direito
playerid = 0, dialogid = YOUR_DIALOGID, response = 0, listitem = -1, inputtext = 'input' (size: 5)
```

## Estilo 2: `DIALOG_STYLE_LIST`

![](/images/dialogStyles/Dialog_style_list.png)

Visualiza��o:

:::note

- **\t** adiciona um TAB (mais espa�o).
- **\n** cria uma nova linha.
- Cores embutidas n�o resetar�o ap�s \n ou \t

:::

```c
ShowPlayerDialog(playerid, YOUR_DIALOGID, DIALOG_STYLE_LIST, "Caption", "Item 0\n{FFFF00}Item 1\nItem 2", "Button 1", "Button 2");
```

### Sa�da da Resposta:

:::note

- **listitem** � o n�mero da linha selecionado, iniciando em **0**.
- **inputtext** � o texto contido no item, incluindo as cores.

:::

```c
// Selecionou o primeiro item e apertou o bot�o esquerdo
playerid = 0, dialogid = YOUR_DIALOGID, response = 1, listitem = 0, inputtext = 'Item 0' (size: 6)

// Selecionou o segundo item e apertou o bot�o direito
playerid = 0, dialogid = YOUR_DIALOGID, response = 0, listitem = 1, inputtext = 'Item 1' (size: 6)
```

## Estilo 3: `DIALOG_STYLE_PASSWORD`

:::note

- Similar ao **DIALOG_STYLE_INPUT**.

:::

![](/images/dialogStyles/Dialog_style_password.png)

Visualiza��o:

:::note

- **\t** adiciona um TAB (mais espa�o).
- **\n** cria uma nova linha.

:::

```c
ShowPlayerDialog(playerid, YOUR_DIALOGID, DIALOG_STYLE_PASSWORD, "Caption", "Enter private information below:", "Button 1", "Button 2");
```

### Sa�da da Resposta:

:::note

- **listitem** � sempre **-1**.
- **inputtext** � o texto digitado pelo jogador, sem poss�veis cores.

:::

```c
// Escreveu "input" e apertou o bot�o esquerdo
playerid = 0, dialogid = YOUR_DIALOGID, response = 1, listitem = -1, inputtext = 'input' (size: 5)

// Escreveu "input" e apertou o bot�o direito
playerid = 0, dialogid = YOUR_DIALOGID, response = 0, listitem = -1, inputtext = 'input' (size: 5)
```

## Estilo 4: `DIALOG_STYLE_TABLIST`

:::tip Este estilo foi adicionado na vers�o **SA-MP 0.3.7** e n�o funcionar� em vers�es anteriores!

:::

:::note

- Similar ao **DIALOG_STYLE_LIST**.

:::

![](/images/dialogStyles/Dialog_style_tablist.png)

Visualiza��o:

:::note

- **\t** adiciona um TAB (mais espa�o).
- **\n** cria uma nova linha.
- Cores embutidas n�o resetar�o ap�s \n ou \t.

:::

```c
ShowPlayerDialog(playerid, YOUR_DIALOGID, DIALOG_STYLE_TABLIST, "Caption",
"Deagle\t$5000\t100\n\
{FF0000}Sawnoff\t{33AA33}$5000\t100\n\
Pistol\t$1000\t50",
"Button 1", "Button 2");
```

:::note

- **inputtext** � o texto existente na _primeira coluna_ do item **listitem** selecionado, sem as cores.

:::

```c
// Selecionou o primeiro item e apertou o bot�o esquerdo
playerid = 0, dialogid = YOUR_DIALOGID, response = 1, listitem = 0, inputtext = 'Deagle' (size: 6)

// Selecionou o segundo item e apertou o bot�o direito
playerid = 0, dialogid = YOUR_DIALOGID, response = 0, listitem = 1, inputtext = 'Sawnoff' (size: 7)
```

## Estilo 5: `DIALOG_STYLE_TABLIST_HEADERS`

:::tip Este estilo foi adicionado na vers�o **SA-MP 0.3.7** e n�o funcionar� em vers�es anteriores!

:::

:::note

- Similar ao **DIALOG_STYLE_LIST**.

:::

![](/images/dialogStyles/Dialog_style_tablist_headers.png)

Showing:

:::note

- **\t** cria uma nova coluna.
- **\n** cria um novo item na lista.
- Cores embutidas reiniciar�o ap�s \n e \t. A primeira linha **info** define o cabe�alho.

:::

```c
ShowPlayerDialog(playerid, YOUR_DIALOGID, DIALOG_STYLE_TABLIST_HEADERS, "Caption",
"Header 1\tHeader 2\tHeader 3\n\
Item 1 Column 1\tItem 1 Column 2\tItem 1 Column 3\n\
{FF0000}Item 2 Column 1\t{33AA33}Item 2 Column 2\tItem 2 Column 3",
"Button 1", "Button 2");
```

:::note

- **inputtext** � o texto contido na _primeira coluna_ do item **listitem** selecionado, sem as poss�veis cores.

:::

```c
// Selecionou o primeiro item da lista e clicou com o bot�o esquerdo
playerid = 0, dialogid = YOUR_DIALOGID, response = 1, listitem = 0, inputtext = 'Item 1 Column 1' (size: 15)

// Selecionou o primeiro item da lista e clicou com o bot�o direito
playerid = 0, dialogid = YOUR_DIALOGID, response = 0, listitem = 1, inputtext = 'Item 2 Column 1' (size: 15)
```
