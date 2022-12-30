# 拡張機能

## 数式

数式を使うことができます．いくつか設定が必要になります．まず、javascriptファイルを用意します．ここでは `docs/js/mathjax.js` とします．

```javascript
window.MathJax = {
  tex: {
    inlineMath: [["\\(", "\\)"]],
    displayMath: [["\\[", "\\]"]],
    processEscapes: true,
    processEnvironments: true
  },
  options: {
    ignoreHtmlClass: ".*|",
    processHtmlClass: "arithmatex"
  }
};

document$.subscribe(() => {
  MathJax.typesetPromise()
})
```

次にmkdocs.ymlでjavascriptファイルを追加します．

```yml
extra_javascript: 
  - js/mathjax.js
  - https://polyfill.io/v3/polyfill.min.js?features=es6
  - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
```

そして、数式拡張機能を有効にします．

```yml
markdown_extensions:
  - pymdownx.arithmatex:
      generic: true
```

これで設定完了です．数式は、ブロックの場合 `$$...$$` や `\[...\]`、インラインの場合 `$...$` や '\(...\)' とします．


```
$$
P\cdot Q = \|P\|\|Q\|\cos\alpha \tag{1}
$$

\[
P\cdot Q = \|P\|\|Q\|\cos\alpha
\]

てすと $P\cdot Q = \|P\|\|Q\|\cos\alpha$．

$$
\text{$a=1$}
$$

\[
\begin{cases}
a = 1 && \text{$a=1$} \\[2ex]
b = 0 && \text{if $a=0$}
\end{cases}
\]

$$
\begin{cases}
a = 1 && a=1 \\[2ex]
v = 0 && \text{if $a=0$}
\end{cases}
$$

$$
aaaa
$$
```

$$
P\cdot Q = \|P\|\|Q\|\cos\alpha \tag{1}
$$

\[
P\cdot Q = \|P\|\|Q\|\cos\alpha
\]

てすと $P\cdot Q = \|P\|\|Q\|\cos\alpha$．

$$
\text{$a=1$}
$$

\[
\begin{cases}
a = 1 && \text{$a=1$} \\[2ex]
b = 0 && \text{if $a=0$}
\end{cases}
\]

$$
\begin{cases}
a = 1 && a=1 \\[2ex]
v = 0 && \text{if $a=0$}
\end{cases}
$$

$$
aaaa
$$


## 注釈

```yml
markdown_extensions:
  - admonition
```

注釈は次のように使います．

```
!!! Note
    これはノートです。
    
!!! Tip
    ヒントです。

!!! Warning
    これは警告です。

!!! Danger
    これは危険です

!!! Success
    これは成功です。

!!! Failure
    これは失敗です。

!!! Bug
    これはバグです。

!!! summary
    これは概要です。
```

!!! Note
    これはノートです。
    
!!! Tip
    ヒントです。

!!! Warning
    これは警告です。

!!! Danger
    これは危険です

!!! Success
    これは成功です。

!!! Failure
    これは失敗です。

!!! Bug
    これはバグです。

!!! summary
    これは概要です。


## 詳細ブロック

注釈拡張機能に似ていますが、こちらは折り畳みブロックです．

```yml
markdown_extensions:
  - pymdownx.details
```

次の用に使います．

```
??? Note
    これはノートです。
    
??? Tip
    ヒントです。

??? Warning
    これは警告です。

??? Danger
    これは危険です

??? Success
    これは成功です。

??? Failure
    これは失敗です。

??? Bug
    これはバグです。

??? summary
    これは概要です。
```

??? Note
    これはノートです。
    
??? Tip
    ヒントです。

??? Warning
    これは警告です。

??? Danger
    これは危険です

??? Success
    これは成功です。

??? Failure
    これは失敗です。

??? Bug
    これはバグです。

??? summary
    これは概要です。


## 定義リスト

```yml
markdown_extensions:
  - def_list
```

定義リストは次のように使います．

```
定義語
:   ここに説明を書きます
```

定義語
:   ここに説明を書きます


## 脚注

```yml
markdown_extensions:
  - footnotes
```

脚注は次のように使います．

```
Mkdocs とは静的サイトジェネレータです。
コンテンツは基本的に markdown[^1] 形式で記述したソースファイルになります。

[^1]: 文書を記述するための軽量マークアップ言語のひとつ
```

Mkdocs とは静的サイトジェネレータです。
コンテンツは基本的に markdown[^1] 形式で記述したソースファイルになります。

[^1]: 文書を記述するための軽量マークアップ言語のひとつ


## アイコンと絵文字

ドキュメント中にアイコンや絵文字を使うことができます．アイコンには以下のものが使えます．

- [Material Design](https://materialdesignicons.com/)
- [FontAwesome](https://fontawesome.com/search?m=free)
- [Octicons](https://octicons.github.com/)
- [Simple Icons](https://simpleicons.org/)

有効にするためには、次のようにします．

```yml
markdown_extensions:
  - attr_list
  - pymdownx.emoji:
      emoji_index: !!python/name:materialx.emoji.twemoji
      emoji_generator: !!python/name:materialx.emoji.to_svg
```

```
:material-at: 
:woman_gesturing_no:
:simple-dogecoin:
:fontawesome-regular-face-laugh-wink:
:octicons-link-external-16: [MkDocs](http://www.mkdocs.org/)
```

:material-at: 
:woman_gesturing_no:
:simple-dogecoin:
:fontawesome-regular-face-laugh-wink:
:octicons-link-external-16: [MkDocs](http://www.mkdocs.org/)


絵文字は次のように使います．

```
ここに \:smile: と記述すると :smile: になります
```

ここに \:smile: と記述すると :smile: になります


## 特殊シンボル

```yml
markdown_extensions:
  -  pymdownx.smartsymbols
```

* `(tm)` : (tm)
* `(c)` : (c)
* `(r)` : (r)
* `c/o` : c/o
* `+/-` : +/-
* `-->` : -->
* `<--` : <--
* `<-->` : <-->
* `=/=` : =/=
* `1.4, etc.` : 1.4, etc.
* `1st 2nd etc.` : 1st 2nd etc.


## キーボードキー表示

PCでのキーボード操作を説明するときにキーコードを解りやすく装飾してくれる拡張機能です。ただし、material テーマのみ使えます。使用するには拡張機能リストに `pymdownx.keys` を追加します。

```yml
markdown_extensions:
  - pymdownx.keys
```

`++ctrl+alt+delete++` と記述すると ++ctrl+alt+delete++ と表示されます。


## コードハイライト

```yml
markdown_extensions:
  - pymdownx.highlight:
      use_pygments: true
      noclasses: true
      pygments_style: monokai
      linenums: true
```

```c++
#include <iostream>
void main() {
  std::cout << "Hello world!" << std::endl;
}
```

コード番号の表示をブロックごとに変えたい場合は `linenums` を使います．

```
 ```c++ linenums="1"
 #include <iostream>
 void main() {
   std::cout << "Hello world!" << std::endl;
 }
 ```
 ```c++ linenums="0"
 #include <iostream>
 void main() {
   std::cout << "Hello world!" << std::endl;
 }
 ```
```

```c++ linenums="1"
#include <iostream>
void main() {
  std::cout << "Hello world!" << std::endl;
}
```

```c++ linenums="0"
#include <iostream>
void main() {
  std::cout << "Hello world!" << std::endl;
}
```

また、個別に行をハイライト表示できます．`hl_lines`で行を指定します．

```c++ hl_lines="2 3"
#include <iostream>
void main() {
  std::cout << "Hello world!" << std::endl;
}
```

!!! Warning
    use_classesと相性が悪いようです．


## コードフェンス

さまざまなブロックをネストして使用できるようになります．

```yml
markdown_extensions:
  - pymdownx.superfences
```

コードフェンスを使えば次のような書き方ができます．

```
!!! Note
    ここは注釈ブロックです．

    ```yml
    markdown_extensions:
      - pymdownx.superfences
    ```
```

!!! Note
    ここは注釈ブロックです．

    ```yml
    markdown_extensions:
      - pymdownx.superfences
    ```

また、コードフェンスの機能を使ってMermaidで作図できます．

```yml
markdown_extensions:
  - pymdownx.superfences:
      custom_fences:
        - name: mermaid
          class: mermaid
          format: !!python/name:pymdownx.superfences.fence_code_format
```

次のように使います．

```
graph LR
  A[Start] --> B{Error?};
  B -->|Yes| C[Hmm...];
  C --> D[Debug];
  D --> B;
  B ---->|No| E[Yay!];
```

``` mermaid
graph LR
  A[Start] --> B{Error?};
  B -->|Yes| C[Hmm...];
  C --> D[Debug];
  D --> B;
  B ---->|No| E[Yay!];
```

```
sequenceDiagram
  Alice->>John: Hello John, how are you?
  loop Healthcheck
      John->>John: Fight against hypochondria
  end
  Note right of John: Rational thoughts!
  John-->>Alice: Great!
  John->>Bob: How about you?
  Bob-->>John: Jolly good!
```

``` mermaid
sequenceDiagram
  Alice->>John: Hello John, how are you?
  loop Healthcheck
      John->>John: Fight against hypochondria
  end
  Note right of John: Rational thoughts!
  John-->>Alice: Great!
  John->>Bob: How about you?
  Bob-->>John: Jolly good!
```





## タスクリスト

```yml
markdown_extensions:
  - pymdownx.tasklist:
      custom_checkbox: true
      clickable_checkbox: true
```

`custom_checkbox`を有効にするとチェックボックスの見た目が良くなります（推奨らしいです）．`clickable_checkbox`を有効にするとクリックで切り替えられるようになります（どこかに保存されるわけではないのでページを再読み込みすればリセットされます）.

```
- [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
- [ ] Vestibulum convallis sit amet nisi a tincidunt
    * [x] In hac habitasse platea dictumst
    * [x] In scelerisque nibh non dolor mollis congue sed et metus
    * [ ] Praesent sed risus massa
- [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque
```

- [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
- [ ] Vestibulum convallis sit amet nisi a tincidunt
    * [x] In hac habitasse platea dictumst
    * [x] In scelerisque nibh non dolor mollis congue sed et metus
    * [ ] Praesent sed risus massa
- [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque


## タブブロック

ドキュメント内でタブがついたブロックを作ることができます．

```yml
markdown_extensions:
  - pymdownx.tabbed:
      alternate_style: true
```

次のように使います．

```
=== "Unordered list"

    * Sed sagittis eleifend rutrum
    * Donec vitae suscipit est
    * Nulla tempor lobortis orci

=== "Ordered list"

    1. Sed sagittis eleifend rutrum
    2. Donec vitae suscipit est
    3. Nulla tempor lobortis orci
```

=== "Unordered list"

    * Sed sagittis eleifend rutrum
    * Donec vitae suscipit est
    * Nulla tempor lobortis orci

=== "Ordered list"

    1. Sed sagittis eleifend rutrum
    2. Donec vitae suscipit est
    3. Nulla tempor lobortis orci


## ボタン

```yml
markdown_extensions:
  - attr_list
```

次のように使います．

```
[Subscribe to our newsletter](#){ .md-button }
```

[Subscribe to our newsletter](#){ .md-button }

```
[Subscribe to our newsletter](#){ .md-button .md-button--primary }
```

[Subscribe to our newsletter](#){ .md-button .md-button--primary }

