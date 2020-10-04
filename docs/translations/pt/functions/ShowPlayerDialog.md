---
id: ShowPlayerDialog
title: ShowPlayerDialog
description: Mostra um dialog (janela) as�ncrono (um �nico por vez).
tags: ["player"]
---

:::warning

Esta fun��o foi adicionada no SA-MP 0.3a e n�o funcionar� em vers�es anteriores!

:::

## Descri��o

Mostra um dialog (janela) as�ncrono (um �nico por vez).

| Par�metro      | Descri��o                                                                                                                             |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| playerid  | ID do jogador que ir� ver o dialog                                                                                             |
| dialogid  | ID do dialog (ser� usado para processar as respostas). ID m�ximo 32767. Usar valores negativos fechar� qualquer dialog aberto. |
| style     | The [style](../resources/dialogstyles.md) of the dialog.                                                                                |
| caption[] | T�tulo mostrado no topo do dialog. O tamanho do caption n�o deve ultrapassar 64 caracteres, ou ser� cortado.       |
| info[]    | Texto que ser� mostrado no corpo do dialog. Use \n para iniciar uma nova linha e \t para espa�o (TAB).                                                  |
| button1[] | Texto do bot�o esquerdo.                                                                                                            |
| button2[] | Texto do bot�o direito. Manter vazio, caso queira ocultar o button2.                                                                         |

## Retorno

1: A fun��o foi executada corretamente.

0: A fun��o falhou ao executar. Isto significa que o jogador n�o est� conectado.

## Exemplos

```c
// Define os dialogid dentro de uma enum
enum
{
    DIALOG_LOGIN,
    DIALOG_WELCOME,
    DIALOG_WEAPONS
}

// Alternativamente, por meio de macros:
#define DIALOG_LOGIN 1
#define DIALOG_WELCOME 2
#define DIALOG_WEAPONS 3

// Enums s�o recommendadas, j� que voc� n�o pode reutilizar IDs. No entanto, enums usam mem�ria para armazenar as defini��es, enquanto as define s�o pr�-processadas na compila��o.

// Exemplo para DIALOG_STYLE_MSGBOX:
ShowPlayerDialog(playerid, DIALOG_WELCOME, DIALOG_STYLE_MSGBOX, "Notice", "You are connected to the server", "Close", "");

// Exemplo para DIALOG_STYLE_INPUT:
ShowPlayerDialog(playerid, DIALOG_LOGIN, DIALOG_STYLE_INPUT, "Login", "Enter your password below:", "Login", "Cancel");

// Exemplo para DIALOG_STYLE_LIST:
ShowPlayerDialog(playerid, DIALOG_WEAPONS, DIALOG_STYLE_LIST, "Weapons", "AK47\nM4\nSniper Rifle", "Option 1", "Option 2");

// Exemplo para DIALOG_STYLE_PASSWORD:
ShowPlayerDialog(playerid, DIALOG_LOGIN, DIALOG_STYLE_PASSWORD, "Login", "Enter your password below:", "Login", "Cancel");

// Exemplo para DIALOG_STYLE_TABLIST:
ShowPlayerDialog(playerid, DIALOG_WEAPONS, DIALOG_STYLE_TABLIST, "Buy Weapon", "Deagle\t$5000\t100\nSawnoff\t$5000\t100\nPistol\t$1000\t50", "Select", "Cancel");

// Exemplo para DIALOG_STYLE_TABLIST_HEADERS:
ShowPlayerDialog(playerid, DIALOG_WEAPONS, DIALOG_STYLE_TABLIST_HEADERS, "Buy Weapon", "Weapon\tPrice\tAmmo\nDeagle\t$5000\t100\nSawnoff\t$5000\t100\nPistol\t$1000\t50", "Select", "Cancel");
```

## Notas

:::tip

� recomendado usar enumera��es (enums - veja abaixo) ou constantes (#define) para determinar quais dialogid's est�o sendo usados, para evitar confus�es no futuro. Voc� nunca deve usar n�meros direto, porque isso gera confus�es.

:::

:::tip

Use cores embutidas para m�ltiplas cores no texto. Usando -1 como dialogid fecha todos os dialogs abertos na tela do cliente (jogador).

:::

## Fun��es relacionadas

- [TextDrawShowForPlayer](TextDrawShowForPlayer.md): Apresenta um textdraw para certo jogador.
- [OnDialogResponse](../callbacks/OnDialogResponse.md): � chamada quando um jogador responde a um dialog.
