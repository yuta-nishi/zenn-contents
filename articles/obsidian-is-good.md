---
title: "Obsidianがいい感じ"
emoji: "🪨"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: [Obsidian, Markdown, Vim]
published: true
---

## はじめに

こんにちは、みなさんはどのメモアプリを使用していますか？
[Notion](https://www.notion.so/)や[Evernote](https://evernote.com/)などの有名なアプリを使っている方も多いんじゃないでしょうか。

しかし、私の使い方ではこれらの有名なアプリではなく、**Obsidian**がもっとも適していました。
@[card](https://obsidian.md/)
この記事では、Obsidianについての詳細な説明は省き、私がどのようにObsidianを使用しているかをまとめます。

:::message
Obsidianについて知りたい方は[**Obsidian.Zenn**](https://zenn.dev/estra/books/obsidian-dot-zenn/viewer/1-oz-begin)などがオススメです。
Obsidianを使いたい方は[**Obsidianでつなげる情報管理術【完成版】**](https://www.amazon.co.jp/gp/product/B0CHY6MK42/)がオススメです。
:::

## この記事の主な対象読者

- Obsidianに興味を持っている人
- Obsidianの具体的な使い方の一例を知りたい人

## 自己紹介

私は元々、ノートを取る習慣がなく、記録するという行動に対しては怠惰な人間でした。
しかし、大学の学年が上がるにつれて日々のタスク管理や思考の整理などを行う必要性を感じ、普段から使用している**VS Codeを使ってMarkdown形式**でdairy note、論文の感想、タスク管理のためのメモなどをまとめるようになりました。

Obsidian歴は**2週間程度**です。はじめは「Obsidian 〇〇」で調べて出てきた記事を参考に設定をしていましたが、全体的には把握できていませんでした。**Obsidianでつなげる情報管理術**を読んで自分好みの環境を作ることができたので、その内容をこの記事にまとめています。
@[card](https://www.amazon.co.jp/gp/product/B0CHY6MK42/)

:::message
もし、Obsidianに興味があるのなら、ブログやYouTubeなどの断片的な情報を集めるよりもはじめに本を1冊買うことをオススメします。（もちろんこの本でなくても良いです）
:::

## VS CodeでのMarkdown執筆環境

VS CodeでMarkdownを書くときに使用しているExtensionをまとめるつもりでしたが、この記事はObsidianに関する記事なので割愛します。（別の記事で後日まとめます）

執筆環境は以下の画像の通りです。キーバインドに[VSCodeVim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)を用いています。

![VS Code執筆環境](/images/obsidian-is-good-1.png)

## なぜ、Obsidianに移行したか

VS Codeなどのコードエディタからの移行を考えている方もいるかもしれないので、移行の理由についても述べておきます。

### VS Codeからメモ専用アプリへの移行を考えた理由

- VS Codeはあくまでコードエディタであり、日頃のメモは専用のアプリで管理すべきと考えたから
- ランチャーツールとして[Raycast](https://www.raycast.com/)を使用しており、ホットキーでアプリを移動しているため、機能単位でアプリを分けると移動が楽だから
- 作る側の人間として色々なアプリを触った方が良いし、どのような機能があるのか興味があったから

基本的には現状に満足していましたが、専用アプリを使うことでさらに良くなるのではないかという好奇心から移行することにしました。後ほど詳しく説明しますが、その結果は期待以上でした。

### 移行するメモアプリに対する要件

- 移行前の使用方法を再現できること
- **Vim**が使用できて、設定できること
- Markdownをローカルで管理すること

VS Codeの環境を再現できることがマストです。
日本語入力にVimを使うと日英変換を連打することになるのですが、普通の入力よりもVimの方が速いのでできるだけVimをカスタマイズできると嬉しいです。

これら3つの要件を満たし、かつユーザー数が多いアプリはObsidianしか存在しませんでした。
そのため、**Obsidianを選択しました。**

選択肢が限られていましたが、第一印象にネガティブな印象はなく、Vimのように本体が提供する機能は最小限で、有志によるプラグインが豊富に存在するコミュニティは非常に魅力的でした。

## 外観

Obsidianの外観はこんな感じです。

![外観](/images/obsidian-is-good-2.png)

### テーマ

**Solarized**を選択
@[card](https://github.com/harmtemolder/obsidian-solarized)

### CSSスニペット

**見出し**に対して自作スタイルを適用
@[card](https://gist.github.com/yuta-nishi/2a3ddd2b3a7958459d9ef9fe0a90621a?file=__header-style.css)

tadashi-aikawaさんの**Minerva**が綺麗で好みだったのでテーマとCSSを参考にしました。
@[card](https://minerva.mamansoft.net/Home)

CSSスニペットの適用方法は**カスタムCSSスニペットでデザインしよう**を参照してください。
@[card](https://zenn.dev/estra/books/obsidian-dot-zenn/viewer/b-oz-css-snippets)

## ディレクトリ構成

ディレクトリ構成はこんな感じです。

```bash
.
├── article # 外部に公開するファイル置き場
├── assets # 画像などのアセット置き場
├── canvas # キャンバス置き場
├── dairy # デイリーノート置き場
├── notes # 外部公開、デイリー・ウィークリーノート以外のすべてのファイル置き場
├── tasks.md # Tasksプラグインで未完了のタスクを集計して表示するファイル
├── templates # テンプレートファイル置き場
└── weekly # ウィークリーノート置き場
```

**タグ**があるので、ディレクトリを深くする必要はないと考えてこのような浅い構成にしています。

新規ノートの作成場所やテンプレートフォルダの場所などの設定はこのディレクトリ構成に合わせて設定しています。分からない場合は**がんばらないObsidianノート術**を参照してください。
@[card](https://qiita.com/YUM_3/items/80cf5705a54f70ad7e5b#設定からディレクトリを紐付ける)

## 使用しているプラグイン

使用しているプラグインを以下にまとめます。
ここでプラグインに関する説明はしません。どのように使用しているかを説明します。
一応、自分が使う上で参照したドキュメントがあれば添付します。

星の数は有用度を示しています。具体的な基準は以下の通りです。

| 星の数 |           意味           |
| :----: | :----------------------: |
|  ★★★   |           必須           |
|   ★★   |       あると嬉しい       |
|   ★    | 有用だが使用機会が少ない |

### 2Hop Links Plus ★

@[card](https://github.com/L7Cy/obsidian-2hop-links-plus)
`Show Image in the 2hop Links`のみOnにして運用しています。まだノート数が少ないので使っていません。2hop linksの思想は良いと思っています。

### Auto Link Title ★️️️️️️️★★

@[card](https://github.com/zolrath/obsidian-auto-link-title)
説明：**ObsidianでURLリンクを見やすくするいくつかのプラグイン**
これのおかげでURLをそのまま貼って、変換してから編集しています。memosを使用する場合は適用されないので、`Enhance existing URL with link and title`を後から使用しています。
@[card](https://note.com/natsuki_ass/n/n434e02505257)

### Calendar ️★★️★

@[card](https://github.com/liamcain/obsidian-calendar-plugin)
説明：**Obsidianを快適にしてくれたプラグイン、現在のデイリーノート【まとめ】**
`Show week number`をOnにしていて、dairy noteとweekly noteの作成に使用しています。デザインが良いです。
@[card](https://note.com/6kuga0/n/n015c5da1a391)

### Clear Unused Images ️★

@[card](https://github.com/ozntel/oz-clear-unused-images-obsidian)
説明：**[Obsidian Plugins] Clear Unused Images | Pouhon**
画像をよく使う場合は有用です。自分用のメモに画像を全然使用しないのでまだ使っていません。
@[card](https://note.com/pouhon01/n/n43c72a738c6c)

### Editor Syntax Highlight ️️★★

@[card](https://github.com/deathau/cm-editor-syntax-highlight-obsidian)
とくに設定せず使っています。

### Note Refactor ★

@[card](https://github.com/lynchjames/note-refactor-obsidian)
まだ、refactorする機会がなくて使用していません。

### Hover Editor ★

@[card](https://github.com/nothingislost/obsidian-hover-editor)
基本的にライブプレビューなので使用していません。

### Iconize ★★️

@[card](https://github.com/FlorianWoelki/obsidian-iconize)
説明：**[Obsidian Plugins] Icon Folder｜Pouhon**
フォルダにアイコンをつけています。
とくに理由はありませんが、日頃お世話になっているので[Lucide Icon](https://lucide.dev/icons/)を使用しています。
@[card](https://note.com/pouhon01/n/n20fe8aa48783)
※ カードが取得できていませんがアクセスできます。

### Linter ★️★★

@[card](https://github.com/platers/obsidian-linter)
説明：**[Obsidian Plugins] Linter｜Pouhon**
alias、tag、created、updatedのフロントマターの自動生成・自動更新とsortを設定しています。また、見出しの前後に空白行を入れたり、最終行に空白行を追加したりなどなど色々な設定をしています。LinterというよりFormatterのように使用しています。
@[card](https://note.com/pouhon01/n/n9c33e77c95b8)
※ カードが取得できていませんがアクセスできます。

### Obsidian Git ★★️

@[card](https://github.com/denolehov/obsidian-git)
説明：**Obsidian Gitを導入してみた**
12時間ごとに自動でGitHubにバックアップを取るように設定しています。ただ、Obsidianを再起動しないとバックアップが取られないようです。
@[card](https://zenn.dev/ayumukob/articles/3b034fcb6874d2)

### Obsidian Memos ★★️★

@[card](https://github.com/Quorafind/Obsidian-Memos)
説明：**Obsidian-memos - hatobato.com**
「## メモ」以下に記述するように設定しています。基本的にメモはリストを使っています。タスクを細分化する時にチェックボックスを使用しています。
@[card](https://hatobato.com/Publish/Cards/Obsidian-memos)

### TagFolder ★★️

@[card](https://github.com/vrtmrz/obsidian-tagfolder)
説明：**[Obsidian] TagFolderとタグの使い方に迫る！ (対談企画03)**
あまり使う機会はありませんが、tagの順番によらずにフォルダのように振る舞ってくれるのでファイル間の関係がわかりやすいです。
@[card](https://pouhon.net/obsidian-tagfolder/7552/)

### Tasks ★★️★

@[card](https://github.com/obsidian-tasks-group/obsidian-tasks)
説明：**Tasks User Guide**
`in progress`や`canceled`も使いたいので、チャックボックスのスタイリングに**Obsidian--ITS-Themeのcheckboxに適用しているcss**を適用しています。

具体的なタスク管理方法は実際の運用方法で述べます。
@[card](https://publish.obsidian.md/tasks/Introduction)
@[card](https://github.com/SlRvb/Obsidian--ITS-Theme/blob/main/Guide/Alternate-Checkboxes.md)

### Various Complements ★★️★

@[card](https://github.com/tadashi-aikawa/obsidian-various-complements-plugin)
説明：**[Obsidian] Various Complementsに迫る！ (対談企画01)**
`Strategy`を日本語にしています。
@[card](https://pouhon.net/obsidian-various_complements/7515/)

### Vimrc Support ★★️★

@[card](https://github.com/esm7/obsidian-vimrc-support)
`.obsidian.vimrc`を以下のように設定しています。
普段使いの設定の他に、ヤンクがOSのクリップボードに保存されるように設定しています。
@[gist](https://gist.github.com/yuta-nishi/2a3ddd2b3a7958459d9ef9fe0a90621a?file=.obsidian.vimrc)

## 実際の運用方法

どのようにタスク管理・思考の整理をしているか、デイリーノート・ウィークリーノート・Tasksに分けてまとめます。

それ以外のノートは読書メモや論文メモ、単語の定義などその用途に応じたテンプレートを用意してまとめています。

### デイリーノート

デイリーノートの**テンプレート**がこんな感じです。

@[gist](https://gist.github.com/yuta-nishi/01c37f6aeb6e5ed84e29450862f35dad?file=dairy-note.md)

#### フロントマター

createdとupdatedを作成時に自動入力します。

#### やること

期日が記載されていて未完了の3日後までのタスクを表示します。

#### やりたいこと

当日中に終わりそうな軽いタスクは期日を設定せずに記入します。
時間がかかりそうな重いタスクは期日を設定して記入します。

#### 今後やること

レポートの提出やゼミの発表など期日が明確なものを記入します。

#### メモ

memosで書いた内容がtimestamp付きで記入されます。

#### やったこと

メモの内容を要約します。
別のノートにまとめてリンクを貼る場合が多いです。

### ウィークリーノート

ウィークリーノートのテンプレートがこんな感じです。
@[gist](https://gist.github.com/yuta-nishi/01c37f6aeb6e5ed84e29450862f35dad?file=weekly-note.md)

#### フロントマター

createdとupdatedを作成時に自動で入力します。
デイリーノートと紐付けます。

#### やったこと

期日が記載されていて完了済みの今週のタスクを表示します。

#### 来週やること

期日が記載されていて未完了の来週のタスクを表示します。

### Tasks

未完了タスクを閲覧するファイルがこんな感じです。
期日が記載されていて未完了のタスクをすべて表示します。

@[gist](https://gist.github.com/yuta-nishi/01c37f6aeb6e5ed84e29450862f35dad?file=tasks.md)

## 移行した感想

移行してから2週間弱経ちますが、大満足です。
もちろん、選定時の機能要件はすべて満たしていますし、それに加えてデフォルトのライブプレビュー機能やアウトゴーイングリンク・バックリンク機能などのメモアプリ特有の機能が充実していて段違いに使いやすくなりました。

とくに良かった点や不満点を以下にまとめます。

### 良かった点

- デフォルトの機能が有能すぎる
（スペルチェック、ウィキリンク、ライブプレビュー、ローカルだから軽い）
- メモアプリ特有のコミュニティプラグインが有能すぎる
（Tasks、Obsidian memos、Auto Link Title）
- VS Codeと遜色ない環境を再現できるコミュニティプラグインが有能すぎる
（Linter、Vimrc Support、Obsidian Git）

とくにウィキリンクが最高です。メモアプリとして求められている機能のすべてがここに集約されていると言っても過言ではありません。Obsidianのサジェストに[PKM](https://en.wikipedia.org/wiki/Personal_knowledge_management)や[Zettelkasten](https://gigazine.net/news/20200604-zettelkasten-note/)がよく出てきますが、この思想を体現するのにこれ以上適した形式はありません。

また、Tasksプラグインが自分の想像以上に使いやすいプラグインでした。チェックボックス形式で記述し、そのデータを取得するための必要最低限の機能が揃っている点がとても優秀です。NotionのToDoリストテンプレートなどの高度な機能が必要ない自分にとってはベストマッチでした。

また、メモアプリでMarkdownlintに基づいたFormatやVimの設定をここまでできると思っていませんでした。ドキュメントをしっかり読んで設定する必要があり、はじめは時間がかかりますが満足な結果が得られました。

### 不満点

- Vimの挙動が異なる。

普段一番使用しているVimキーバインドがVS CodeのVimエミュレータなのでそれと比較した時の不満点です。日本語のwordに対する挙動がよくないです。具体的に`w`や`e`や`b`で移動する箇所を`,`で表すと以下のようになります。

#### VS CodeのVimキーバインド

普段一番使用`,`している`,`Vim`,`キーバインド`,`が`,`VS `,`Code`,`の`,`Vim`,`エミュレータ`,`なのでそれと`,`比較`,`した`,`時`,`の`,`不満点`,`です`,`。

**漢字、ひらがな、カタカナ、ローマ字、句読点で区切られます。**

#### ObsidianのVimキーバインド

普段一番使用しているVimキーバインドがVS `,`CodeのVimエミュレータなのでそれと比較した時の不満点です`,`。

**空白と句読点で区切られます。**

比較したように、ObsidianのVimキーバインドは日本語に対してword区切りが使い物になりません。よく使う`ciw`や`yiw`は使えなくなりました。

これ以外は非常に満足しています。

## さいごに

ここまでお読みいただきありがとうございます。長くなりましたが、Obsidianの魅力が伝わっていれば幸いです。

メモアプリを自分好みにカスタマイズし、使いやすくする理由は、生産性の向上にあります。ここまでまとめた内容はすべて、情報の場所を構造化し、迅速にアクセスするための設定です。

しかし、もっとも重要なことはそうした設定ではなく、実際にメモを取って思考を言語化する行為自体です。どんなに高度なツールを使っても、それを活用しなければ意味がありません。

その点で、Obsidianは根が怠惰な自分に合っていました。最小限の機能を提供し、プラグインがカスタマイズできる点が唯一無二のメモアプリだと思います。

ぜひ、Obsidianを触ってみてください。
