# Material for MkDocs

Material for MkDocs は MkDocsのテーマの1つです．
率直に言って、標準のテーマやreadthedocsもイマイチなので、テーマを自作しないのであればMaterialテーマ一択だと思います．このドキュメントではMaterialテーマを使用することを前提とします．

## カラー

テーマカラーを指定できます．指定できるカラーは次のとおりです．

```
red, pink, purple, deep purple, indigo,
blue, light blue, cyan, teal,
green, light green, lime, yellow, 
amber, orange, deep orange, brown,
grey, blue grey, black,, white
```

テーマカラーは `theme.palette.primary` で指定します．

```yml
theme:
  palette:
    primary: pink
```

ライトテーマやダークテーマといったようにテーマを切り替えるボタンを追加できます．
次のように指定します．

```yml
theme:
  palette:
    - scheme: default
      primary: pink
      toggle:
        icon: material/brightness-7
        name: Switch to dark mode
    - scheme: slate
      toggle:
        icon: material/brightness-4
        name: Switch to light mode
```

検索ボックスの左側にテーマを切り替えるボタンが追加され、ボタンを押すとテーマを切り替えることができます．
各テーマごとに色をcssで調整することもできます．

```css
[data-md-color-scheme=default] {
  --md-default-fg-color--light: #222 !important;
}
[data-md-color-scheme=slate] {
  --md-default-fg-color--light: #fefefe !important;
  --md-typeset-a-color: #fc0 !important;
}
```


## フォント

通常フォントと固定幅フォントをそれぞれ指定できます．フォントはGoogleFontにあるものを指定できます．
必要なcssファイルも自動で設定してくれますので、カスタムcssで登録する必要はありません．

```yml
theme:
  font:
    text: Noto Sans JP
    code: Inconsolata
```


## 言語

複数の言語を指定できます．

```yml
extra:
  alternate:
    - name: English
      link: /en/
      lang: en
    - name: Japanese
      link: /
      lang: ja
```

検索ボックスの隣に言語を切り替えるボタンが追加されます．各ドキュメントはリンク


## ロゴ、ファビコン、ホームページ

それぞれ、次のように設定できます．

```yml
theme:
  logo: assets/logo.png
  favicon: images/favicon.png

extra:
  homepage: https://example.com
```


## クッキー使用の同意

一般データ保護規則(GDPR)によりEU圏内からのアクセスがあった場合にサイトでCookieを利用して情報収集している場合は確認を取る必要があります．Googleアナリティクスなどを使用していれば必要になります．
Materialテーマにはクッキーの使用について同意するポップアップを表示する機能が用意されています．使い方は次のようになります．

```yml
extra:
  consent:
    title: Cookie consent
    description:
      We use cookies to recognize your repeated visits and preferences, as well
      as to measure the effectiveness of our documentation and whether users
      find what they're searching for. With your consent, you're helping us to
      make our documentation better.
```

標準でGoogleアナリティクスとGitHubが有効になっています．追加したい場合は `extra.content.cookies` で指定します．

```yml
extra:
  consent:
    cookies:
      analytics: Custom name
```

他に、ポップアップのボタンをカスタマイズできます．通常は「承認」と「管理」が表示されます．それ以外だと「拒否」があります．

```yml
extra:
  consent:
    actions:
      - accept
      - manage
      - reject
```


## ナビゲーション

### タブ

タブは `theme.features` で有効にします．

```yml
theme:
  features:
    - navigation.tabs
```

トップレベルのセクションがタブになります．画面をスクロールするとタブ画面が隠れますが、常に表示したい場合は `navigation.tabs.sticky` を追加します．


```yml
theme:
  features:
    - navigation.tabs
    - navigation.tabs.sticky
```


### セクションの折り畳み

階層が深いコンテンツの場合、サイドバーにあるセクション一覧で折り畳む機能が入っています．それを無効にして全てフラットに表示したい場合、`navigation.sections` を指定します．

```yml
theme:
  features:
    - navigation.sections
```

また、`navigation.expand`を指定すると、最初からすべて展開された状態になります．

```yml
theme:
  features:
    - navigation.expand
```

セクションごとにインデックスページを指定する場合、`navigation.indexes` を指定します．

```yml
theme:
  features:
    - navigation.indexes
```

ドキュメントの構成は次のようにします．

```yml
nav:
  - Section:
    - section/index.md
    - Page 1: section/page-1.md
    - Page 2: section/page-2.md
```

この場合、`section/index.md`がセクションの項目に統合されます．


### トップに戻るボタン

`navigation.top`を追加します．確認したところ、常時ではなく上方向にスクロールしたときに表示されます．

```yml
theme:
  features:
    - navigation.top
```


### サイドバーを無効化

タブを有効にしているなど、サイドバーを無効にしたい場合、コンテンツ側で次のように指定します．

```
---
hide:
  - navigation
---
```


## 検索

プラグインとして実装されました．検索プラグインは標準で入っています．日本語検索を有効にする場合は次のようにします．

```yml
plugins:
  search:
    lang: 'ja'
```


## Googleアナリティクス

Googleアナリティクスは次のように設定します．

```yml
extra:
  analytics:
    provider: google
    property: UA-XXXXXXXX-X
```


## ブログ

まだ実験段階ですが、ブログ機能がプラグインとして実装されているようです．今はスポンサーのみ使用することができるようです．興味のある人は[Setting up a blog](https://squidfunk.github.io/mkdocs-material/setup/setting-up-a-blog/)を参照してください．


## ヘッダーとフッター

### タイトルバー

タイトルバーは常時表示されますが、`header.autohide`を有効にすることで隠れるようになります．

```yml
theme:
  features:
    - header.autohide
```

### ソーシャルリンク

TwitterやFacebook、GitHubなどのアイコンを設定できます．

```yml
extra:
  social:
    - icon: fontawesome/brands/twitter
      link: https://twitter.com/mebiusbox2
      name: mebiusbox2 on Twitter
    - icon: fontawesome/brands/github
      link: https://github.com/mebiusbox/MkDocsTest
```


### 著作権表記

次のように指定します．最初に `&copy;` とする場合はダブルクォーテーションで囲みます．

```yml
site_name: Mkdocs Test
copyright: "&copy; 2022 mebiusbox"
```


### ジェネレータの表記

フッターにMkDocsで生成されたことが自動で表示されますが、これを非表示にできます．

```yml
extra:
  generator: false
```


### Prev/Nextリンクの非表示

各ページには前／次のページリンクが表示されますが、これを非表示にしたい場合、ページ側で指定します．

```
---
hide:
  - footer
---
```


## Gitリポジトリリンクの設定

右上にGitリポジトリのリンクを追加できます．自動でスター数とフォーク数が表示されます．

```yml
repo_url: https://github.com/mebiusbox/MkDocsTest
repo_name: mebiusbox/MkDocsTest
```

アイコンを変更したい場合、次のようにします．

```yml
theme:
  icon:
    repo: fontawesome/brands/github
```

例えば、GitLabアイコンにしたい場合は次のようになります．

```yml
theme:
  icon:
    repo: fontawesome/brands/gitlab
```


## コメント機能

[giscus](https://giscus.app/)がサポートされています．手順としては次のようになります．

1. 対象のリポジトリのgiscusアプリをインストールする（GitHubをフリー版で利用しているならパブリックである必要があります）
2. リポジトリのDicussionを有効にします
3. giscusページで必要な情報を入力します．設定は特に必要がなければ初期のままでいいです．「giscusを有効にする」のところに表示されるコードをコピーする．
4. カスタムテーマを有効にする
5. コメントのテンプレートを編集してペーストする

カスタムテーマを有効にするには次のようにします．

```yml
theme:
  custom_dir: overrides
```

コメントテンプレート(overrides/partials/comments.html)ファイルを作成して、以下をペーストします．

```html
{% if page.meta.comments %}
  <h2 id="__comments">{{ lang.t("meta.comments") }}</h2>
  <!-- Insert generated snippet here -->

  <!-- Synchronize Giscus theme with palette -->
  <script>
    var giscus = document.querySelector("script[src*=giscus]")

    /* Set palette on initial load */
    var palette = __md_get("__palette")
    if (palette && typeof palette.color === "object") {
      var theme = palette.color.scheme === "slate" ? "dark" : "light"
      giscus.setAttribute("data-theme", theme) 
    }

    /* Register event handlers after documented loaded */
    document.addEventListener("DOMContentLoaded", function() {
      var ref = document.querySelector("[data-md-component=palette]")
      ref.addEventListener("change", function() {
        var palette = __md_get("__palette")
        if (palette && typeof palette.color === "object") {
          var theme = palette.color.scheme === "slate" ? "dark" : "light"

          /* Instruct Giscus to change theme */
          var frame = document.querySelector(".giscus-frame")
          frame.contentWindow.postMessage(
            { giscus: { setConfig: { theme } } },
            "https://giscus.app"
          )
        }
      })
    })
  </script>
{% endif %}
```

このコードにある `<!-- Insert generated snippet here -->` の下に、giscusでコピーしたコードをそのまま貼り付けます．これで設定完了です．


## GitHub Pages で公開

GitHub Actionを使ってリポジトリからビルドして公開するには、GitHub Actionのワークフローファイル(.github/workflows/ci.yml)を作成します．

```yml
name: ci 
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: 3.x
      - run: pip install mkdocs-material python-markdown-math fontawesome_markdown
      - run: mkdocs gh-deploy --force
```

CIが正常終了すれば、`<username>.github.io/<repository>`に配置されます．`pip install mkdocs-material...` の部分は利用する拡張機能があれば追記する必要があります．

