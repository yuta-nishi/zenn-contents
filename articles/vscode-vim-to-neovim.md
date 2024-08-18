---
title: "VSCodeVimからVSCode Neovimに移行したのでメモ"
emoji: "📝"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [Vim, Neovim, VSCode]
published: true
---

## はじめに

こんにちは、[VSCodeVim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)から[VSCode Neovim](https://marketplace.visualstudio.com/items?itemName=asvetliakov.vscode-neovim)に移行したので、それに関するメモをまとめました。

Neovimの環境は[LazyVim](https://github.com/LazyVim/LazyVim)を使用しています。その他のプラグインを使用している場合は適宜読み替えてください。

@[card](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)
@[card](https://marketplace.visualstudio.com/items?itemName=asvetliakov.vscode-neovim)

:::message
全体の設定は私の[dotfiles](https://github.com/yuta-nishi/dotfiles)を参照してください。
:::

## なぜ移行を考えたか

普段からVimエディタは使用せず、VSCodeVimを用いてVS Codeでコーディングをしました。

ただ、`.`での繰り返しや`:`を用いたコマンドを使いこなせておらず、Vimをちゃんと勉強したいなと思い、最近になって[crafzdogさんの設定](https://www.devas.life/effective-neovim-setup-for-web-development-towards-2024/)を参考にLazyVimを用いた[Neovim](https://neovim.io/)の環境を整えて少し触っていました。

@[card](https://www.devas.life/effective-neovim-setup-for-web-development-towards-2024/)

結局、GitHub Copilot ChatやRemote SSHなどの有用な拡張機能が手放せないのでVS Codeを利用することにしたのですが、Neovimを触ったことでVSCodeVimのもっさり感が気になったため、VSCode Neovimに移行することを考えました。

## 移行するメリット

VSCodeVimとVSCode Neovimの違いは[yubrotさんの記事](https://zenn.dev/yubrot/articles/1bf4b8d79d7cae)にまとまっていますので、こちらを参照してください。

@[card](https://zenn.dev/yubrot/articles/1bf4b8d79d7cae)

筆者のVSCodeVim環境ではundoが壊れるということはありませんでしたが、カーソルの移動がもっさりしたり、Saveが重くなったりすることがあったので、やはりVSCode Neovimよりは劣っているように感じます。

特に、以下のように`:h`などの主要コマンドが実装されていなかったり、コマンドの入力が分かりやすく表示されないのは我慢できませんでした。その点、VSCode Neovimはきちんと動作します。

![VSCode Neovimの場合](/images/vscode-vim-to-neovim-1.png =500x)
*VSCode Neovimでコマンドを打つと上部に表示され、見やすい*

![VSCodeVimの場合](/images/vscode-vim-to-neovim-2.png =500x)
*VSCodeVimでコマンドを打つと下部に表示され、対応していないコマンドもある*

## VSCodeVimの設定

VSCodeVimは以下のように設定していました。
少し長いです。

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

VSCode NeovimはローカルのNeovimと設定ファイルを以下のように設定して読み込みます。

```json:settings.json
  "vscode-neovim.neovimExecutablePaths.darwin": "/opt/homebrew/bin/nvim",
  "vscode-neovim.neovimInitVimPaths.darwin": "/Users/yutanishi/.config/nvim/init.lua",
```

### `init.lua`

pathに指定した`init.lua`は以下のように設定しています。

```lua:init.lua
require("config.lazy")
```

### `lazy.lua`

`lazy.lua`での条件分岐は以下のように設定しています。

```lua:lazy.luaの抜粋
-- Set up lazy.nvim
if not vim.g.vscode then
  require("lazy").setup({
    spec = {
      -- LazyVim core plugins
      {
        "LazyVim/LazyVim",
        import = "lazyvim.plugins",
        opts = {
          colorscheme = "everforest",
          news = { lazyvim = true, neovim = true },
        },
      },

      -- Import extra modules
      { import = "lazyvim.plugins.extras.linting.eslint" },
      { import = "lazyvim.plugins.extras.formatting.prettier" },
      { import = "lazyvim.plugins.extras.lang.typescript" },
      { import = "lazyvim.plugins.extras.lang.json" },
      { import = "lazyvim.plugins.extras.lang.rust" },
      { import = "lazyvim.plugins.extras.coding.copilot" },
      { import = "lazyvim.plugins.extras.util.mini-hipatterns" },
      { import = "plugins" },
    },

    defaults = {
      -- Don't lazy-load custom plugins by default
      lazy = false,
      -- Use the latest git commit
      version = false,
    },

    checker = {
      -- Automatically check for plugin updates
      enabled = true,
    },

    performance = {
      cache = {
        -- Enable caching for all plugins
        enabled = true,
      },
      rtp = {
        -- Disable some rtp plugins
        disabled_plugins = {
          "gzip",
          "netrwPlugin",
          "rplugin",
          "tarPlugin",
          "tohtml",
          "tutor",
          "zipPlugin",
        },
      },
    },

    debug = false,
  })
else
  require("config.keymaps")
  require("config.options")
  require("lazy").setup({
    -- Surround plugin
    {
      "kylechui/nvim-surround",
      version = "*", -- Use for stability; omit to use `main` branch for the latest features
      event = "VeryLazy",
      config = function()
        require("nvim-surround").setup({
          -- Configuration here, or leave empty to use defaults
        })
      end
    }
  })
end
```

`vim.g.vscode`でVSCode Neovimを使用する場合の判定をしています。`lazy.nvim`と`packer.nvim`ではデフォルトで提供されているので楽です。

`keymaps`と`options`を有効にしています。
プラグインは`nvim-surround`だけ入れています。

参考：
@[card](https://github.com/vscode-neovim/vscode-neovim?tab=readme-ov-file#neovim-configuration)

:::message
自分のディレクトリ構成は以下です。

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

`keymaps.lua`の設定を先述しましたが、VSCode Neovimではinsert modeに対するカスタムマッピング設定は適用できません。公式ドキュメントの通りに`settings.json`を設定して解決しました。

:::message alert
元々、`keybindings.json`に設定を記載していましたが、V1.11.0から`settings.json`に記載するように変更されました。
:::

@[card](https://github.com/vscode-neovim/vscode-neovim/pull/1917)
@[card](https://github.com/vscode-neovim/vscode-neovim?tab=readme-ov-file#composite-escape-keys)

```json:settings.jsonの抜粋
  "vscode-neovim.compositeKeys": {
    "jk": {
      "command": "vscode-neovim.escape",
    }
  },
```

### SpaceをLeaderに割り当てられない

`options.lua`に`vim.g.mapleader = " "`を設定しているのでSpaceがLeaderに割り当てられています。しかし、VSCode NeovimではLeaderを用いた操作が想定されていないようでこの設定は反映されませんでした。

仕方ないので、Spaceを用いたVS Codeの操作は`keybindings.json`で設定して解決しました。

```json:keybindings.jsonの抜粋
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
多分LazyVimのデフォルトの設定でそうなっていたので、VSCode Neovimでもコピーされるように`options.lua`で明示的に設定しました。

```lua:options.luaの抜粋
vim.opt.clipboard = "unnamedplus"
```

## 解決できなかったこと

VSCode NeovimはLeaderの設定が反映されなかったので、下記のようにVS Codeの機能ではないLeaderを用いたカスタムキーバインドが適用できませんでした。**もしわかる方がいらっしゃれば、コメントしていただけると嬉しいです。**

ただ、普段からあまり使わない設定ばかりだったので、ダメージは0です。

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

VSCode Neovimに移行して快適にコーディングができています。満足です。
Neovimの操作感が欲しいけど、プラグインの管理が面倒くさいという方におすすめです。
