# はじめに

## <i class="fa fa-arrow-circle-right" aria-hidden="true"></i> MkDocsとは

mkdocs は静的サイトジェネレータです。コンテンツは基本的に markdown 形式で記述したソースファイルになります。またHTML形式のファイルを使うこともできます。この記事では Windows で個人的な最低限の作成環境をまとめました。

- [MkDocs](http://www.mkdocs.org/)


## <i class="fa fa-arrow-circle-right" aria-hidden="true"></i> インストール

まずは、python をインストールします．次に pip を使って mkdocs をインストールします。

```
pip install mkdocs
```


私は次の環境で動作確認しました．

```
python                       3.9.5
mkdocs                       1.4.2
mkdocs-material              8.5.11
mkdocs-material-extentions   1.1.1
pymdown-extensions           9.9
```


## MkDocsの基本コマンド

プロジェクトを新規に作成するには `mkdocs new` を使います．

```
mkdocs new
```

次に、サイトに必要なファイルを生成するにはビルドを行います。ビルドは以下のコマンドを実行します。

```
mkdocs build
```

正常に生成されるとsiteフォルダに作成されます。インターネット上に公開する場合はこのフォルダ内をアップロードします。ビルドした内容を公開する前に、ローカルで確認したい場合は`serve`コマンドを実行し、サーバーを起動します。

```
mkdocs serve
```

コマンドの出力に `Serving on http://127.0.0.1:8000` のようにアドレスとポート番号が表示されますので、そのアドレスをブラウザに入力して確認できます。

serveを実行している間はファイルの追加や変更が検知されて自動的にビルドされます。


## mkdocs.yml

mkdocs.yml ファイルを編集することでドキュメントの構成やカスタマイズを行うことができます。このファイルにはサイトのタイトルやテーマ、拡張機能の設定などを記述します。プロジェクトの作成を行うと、このファイルは自動で作成されます。


## ドキュメントの構成

mkdocs.ymlの`nav`に指定します.

```yml
nav:
  - 初期画面: index.md
  - introduction.md
  - material.md
  - section1:
      section1-1:
        section1-1-1:
          section1-1-1.md
      section1-2:
        section1-2-1:
          section1-2-1.md
  - section2:
    - page2-1.md
    - page2-2.md
```

