# MkDocsによるドキュメント作成

## <i class="fa fa-arrow-circle-right" aria-hidden="true"></i> はじめに

mkdocs は 静的サイトジェネレータです。コンテンツは基本的に markdown 形式で記述したソースファイルになります。またHTML形式のファイルを使うことも出来ます。この記事では Windows で個人的な最低限の作成環境をまとめました。

## <i class="fa fa-arrow-circle-right" aria-hidden="true"></i> mkdocs のインストール

python をインストールします。2.x 系でも 3.x 系でもどちらでも構いません。ちなみに私は 2.7.11 で確認しています。

次に pip を使って mkdocs をインストールします。

    pip install mkdocs

## <i class="fa fa-arrow-circle-right" aria-hidden="true"></i> プロジェクトの作成

実行に必要な最低限のフォルダとファイルを作成するコマンドが用意されています。例えば test というプロジェクトを作成する場合は以下のコマンドを実行します。

    mkdocs new test

実行したカレントフォルダに test というフォルダが作られ、その中にも初期ファイルが作成されます。今後、mkdocs のコマンドを実行する場合は プロジェクトフォルダ（test）に作業ディレクトリにしておきます。

コンテンツのソースファイルは `docs` フォルダに入れます。（設定で別のフォルダに変更することが出来ます）