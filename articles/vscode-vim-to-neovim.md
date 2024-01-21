---
title: "VSCodeVimからVSCode Neovimに移行したのでメモ"
emoji: "📝"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [Vim, Neovim, VSCode]
published: false
---

## はじめに

こんにちは、今回は[VSCodeVim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)から[VSCode Neovim](https://marketplace.visualstudio.com/items?itemName=asvetliakov.vscode-neovim)に移行したので、それに関するメモをまとめて記事にしています。

Neovimの環境は[LazyVim](https://github.com/LazyVim/LazyVim)を使用しています。その他のプラグインを使用している場合は適宜読み替えてください。

@[card](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)
@[card](https://marketplace.visualstudio.com/items?itemName=asvetliakov.vscode-neovim)

:::message alert
VimのプラグインをVS Codeで使えるようにする設定はしていません。
keymapsとoptionsを設定します。
:::

:::message
全体の設定は私の[dotfiles](https://github.com/yuta-nishi/dotfiles/tree/main)を参照してください。
:::

## この記事の主な対象読者

- VSCodeVimを使っている方
- VSCode Neovimに興味がある方

## なぜ移行を考えたか

まず、筆者のVim歴は**1年弱程度**です。普段からVimエディタは使用せず、VSCodeVimを用いてVS Codeでコーディングをしています。

ただ、`.`での繰り返しや`:`を用いたコマンドを使いこなせておらず、Vimをちゃんと勉強したいなと思い、最近になって[crafzdogさんの設定](https://www.devas.life/effective-neovim-setup-for-web-development-towards-2024/)を参考にLazyVimを用いた[Neovim](https://neovim.io/)の環境を整えて少し触っていました。

@[card](https://www.devas.life/effective-neovim-setup-for-web-development-towards-2024/)

結局、Copilot ChatやRemote SSHなどの有用な拡張機能が手放せないのでVS Codeを利用することにしたのですが、Neovimを触ったことでVSCodeVimが使いづらいと感じたため、VSCode Neovimに移行することを考えました。

## 移行するメリット

VSCodeVimとVSCode Neovimの違いは[yubrotさんの記事](https://zenn.dev/yubrot/articles/1bf4b8d79d7cae)にまとまっていますので、こちらを参照してください。

@[card](https://zenn.dev/yubrot/articles/1bf4b8d79d7cae)

筆者のVSCodeVim環境ではundoが壊れるということはあまりありませんでしたが、カーソルの移動がもっさりしたり、Saveが重くなったりすることがあったので、やはりVSCode Neovimよりは劣っているように感じます。

特に`:h`などの主要コマンドが実装されていなかったり、コマンドの入力が分かりやすく表示されないのは我慢できませんでした。その点、VSCode Neovimはこの要件を満たしています。

![]()
![]()

## VSCodeVimの設定

VSCodeVimは以下のように設定していました。

```json:settings.json
/* Vim Settings */
  "vim.hlsearch": true,
  "vim.easymotion": true,
  "vim.leader": "<space>",
  "vim.useSystemClipboard": true,
  "vim.visualstar": true,
  "vim.camelCaseMotion.enable": true,
  "vim.insertModeKeyBindings": [
    {
      "before": [
        "j",
        "k"
      ],
      "after": [
        "<ESC>"
      ]
    }
  ],
  "vim.normalModeKeyBindings": [
    {
      "before": [
        "u"
      ],
      "commands": [
        {
          "command": "undo"
        }
      ]
    },
    {
      "before": [
        "<C-r>"
      ],
      "commands": [
        {
          "command": "redo"
        }
      ]
    },
    {
      "before": [
        "j"
      ],
      "after": [
        "g",
        "j"
      ]
    },
    {
      "before": [
        "k"
      ],
      "after": [
        "g",
        "k"
      ]
    },
    {
      "before": [
        "n"
      ],
      "after": [
        "n",
        "z",
        "z"
      ]
    },
    {
      "before": [
        "N"
      ],
      "after": [
        "N",
        "z",
        "z"
      ]
    },
    {
      "before": [
        "*"
      ],
      "after": [
        "*",
        "z",
        "z"
      ]
    },
    {
      "before": [
        "#"
      ],
      "after": [
        "#",
        "z",
        "z"
      ]
    },
    {
      "before": [
        "+"
      ],
      "after": [
        "<C-a>"
      ]
    },
    {
      "before": [
        "-"
      ],
      "after": [
        "<C-x>"
      ]
    },
    {
      "before": [
        "<Leader>",
        "/"
      ],
      "commands": [
        {
          "command": "editor.action.commentLine"
        }
      ]
    },
    {
      "before": [
        "<Leader>",
        "s"
      ],
      "after": [],
      "commands": [
        {
          "command": "workbench.action.files.save",
        }
      ]
    },
    {
      "before": [
        "<Leader>",
        "w"
      ],
      "after": [],
      "commands": [
        {
          "command": "workbench.action.closeActiveEditor",
        }
      ]
    },
    {
      "before": [
        "<C-h>",
      ],
      "after": [
        "^"
      ]
    },
    {
      "before": [
        "<C-l>",
      ],
      "after": [
        "$"
      ]
    },
    {
      "before": [
        "<Leader>",
        "m"
      ],
      "after": [
        "%"
      ]
    },
    {
      "before": [
        "<Leader>",
        "z"
      ],
      "commands": [
        ":noh"
      ]
    }
  ],
  "vim.visualModeKeyBindings": [
    {
      "before": [
        "<C-h>",
      ],
      "after": [
        "^"
      ]
    },
    {
      "before": [
        "<C-l>",
      ],
      "after": [
        "$"
      ]
    },
    {
      "before": [
        "<Leader>",
        "m"
      ],
      "after": [
        "%"
      ]
    },
  ]
```

この設定は[VimmerのVimmerによるVimmerのためのVSCode環境構築](https://fe-notes.work/posts/20200708_vsvim01/)を参考にしています。
上記の設定をVSCode Neovimで同じように設定します。

@[card](https://fe-notes.work/posts/20200708_vsvim01/)

## VSCode Neovimの設定

### `settings.json`

VSCode NeovimはローカルのNeovimと設定ファイルを以下のように設定して読み込ませます。

```json:settings.json
  /* NeoVim Settings */
  "vscode-neovim.neovimExecutablePaths.darwin": "/opt/homebrew/bin/nvim",
  "vscode-neovim.neovimInitVimPaths.darwin": "/Users/yutanishi/.config/nvim/init.lua",
```

### `init.lua`

pathに指定した`init.lua`は以下のように設定しています。

```lua:init.lua
if vim.g.vscode then
  require("config.keymaps")
  require("config.options")
else
  require("config.lazy")
end
```

`vim.g.vscode`でVSCode Neovimを使用する場合の判定をしています。
`keymaps`と`options`のみを反映させたいので上記のようにしています。

:::message
LazyVimの場合、ディレクトリ構成は以下になります。

- init.lua
- lua
  - config
    - autocmds.lua
    - keymaps.lua
    - lazy.lua
    - options.lua
  - plugins
    - colorscheme.lua
    - ...
:::

### `keymaps.lua`

`keymaps.lua`は以下のように設定しています。

```lua:keymaps.lua
local keymap = vim.keymap
local opts = { noremap = true, silent = true }

-- Insert mode mapping
keymap.set("i", "jk", "<ESC>", opts)

-- Normal mode mappings
keymap.set("n", "<C-h>", "^", opts)
keymap.set("n", "<C-l>", "$", opts)

-- Inc/Dec settings
keymap.set("n", "+", "<C-a>", opts)
keymap.set("n", "-", "<C-x>", opts)

-- To avoid easymotion
keymap.set("n", "s", '"_s', opts)

-- Visual mode mappings
keymap.set("v", "<C-h>", "^", opts)
keymap.set("v", "<C-l>", "$", opts)
```

### `options.lua`

`options.lua`は以下のように設定しています。
ただ、元々多くの設定をしているのでどれが反映されているか分かっていません。
意図的に追加した設定を抜粋しています。

```lua:options.luaの抜粋
vim.g.mapleader = " "
vim.opt.clipboard = "unnamedplus"
```

## 設定で詰まったところ

Neovim移行で詰まったところは以下の3点です。

### insert mode mappingが反映されない

`keymaps.lua`の設定を先述しましたが、VSCode Neovimではinsert modeに対するカスタムマッピング設定は適用できません。[公式ドキュメント](https://github.com/vscode-neovim/vscode-neovim?tab=readme-ov-file#composite-escape-keys)の通りに`keybindings.json`を設定して解決しました。

@[card](https://github.com/vscode-neovim/vscode-neovim?tab=readme-ov-file#composite-escape-keys)

```json:keybindings.jsonの抜粋
  /* Neovim Settings */
  {
    "key": "j",
    "command": "vscode-neovim.compositeEscape1",
    "when": "neovim.mode == insert && editorTextFocus",
    "args": "j"
  },
  {
    "key": "k",
    "command": "vscode-neovim.compositeEscape2",
    "when": "neovim.mode == insert && editorTextFocus",
    "args": "k"
  }
```

### SpaceをLeaderに割り当てられない

`options.lua`に`vim.g.mapleader = " "`を設定しているのでSpaceがLeaderに割り当てられています。しかし、VSCode NeovimではLeaderを用いた操作が想定されていないようでVSCodeVimのような操作はできませんでした。

仕方ないので、Spaceを用いたVS Codeの操作は`keybindings.json`で設定して解決しました。

```json:keybindings.jsonの抜粋
  /* Neovim Settings */
  {
    "key": "space s",
    "command": "workbench.action.files.save",
    "when": "neovim.mode == normal && editorTextFocus"
  },
  {
    "key": "space /",
    "command": "editor.action.commentLine",
    "when": "neovim.mode == normal && editorTextFocus"
  },
  {
    "key": "space w",
    "command": "workbench.action.closeActiveEditor",
    "when": "neovim.mode == normal && editorTextFocus"
  }
```

### yankがclipboardにコピーされない

元々のLazyVimではカスタムの設定を追加しなくてもyankがclipboardにコピーされていました。
多分LazyVim側の設定でそうなっていたので、VSCode Neovimでもコピーされるように`options.lua`で明示的に設定しました。

```lua:options.luaの抜粋
vim.opt.clipboard = "unnamedplus"
```

:::message
unnamedとunnamedplusの違い
:::

## 解決できなかったこと

VSCode NeovimはLeaderの設定が反映されなかったので、下記のようなLeaderを用いたカスタムキーバインドが適用できませんでした。**もしわかる方がいらっしゃれば、コメントしていただけると嬉しいです。**

ただ、普段からあまり使わない設定ばかりなのでダメージは0です。

```json:settings.jsonの抜粋
    {
      "before": [
        "<Leader>",
        "m"
      ],
      "after": [
        "%"
      ]
    }
```

## さいごに

VSCode Neovimに移行してからまだ1日しか経っていませんが、挙動のもっさり感もなくなり、普段使いのコマンドはすべて使えるので大満足です。
私はVimライト層なので、VS Codeで使う場合はプラグインを入れる運用をしないつもりですが、色々とカスタマイズのしがいがありそうで良い拡張機能だと思いました。
