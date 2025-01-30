# GitHub Copilot Workspace VS Code 拡張機能

この Copilot Workspace VS Code 拡張機能を使用すると、VS Code の快適さから GitHub Copilot Workspace を使用できます。既存のセッションを続行し、PR を作成する前に提案された変更を編集およびデバッグします。プランや実装を自然言語で修正するか、ファイルを直接編集するかに関係なく、VS Code とその拡張機能エコシステムのすべての機能を使用しながら、ローカルの編集内容を Web 上の GitHub Copilot Workspace に自動的に同期できます（保存されたファイルの変更は数秒以内にオンラインで表示されます）。

これは現在アルファ版の拡張機能であり、複数のフェーズで拡張機能の強化を展開していきます。

1. **続行:** Copilot Workspace セッションを参照し、変更を同期して、VS Code ローカルでアプリケーションを編集およびデバッグします。他の[VS Code リモート拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)の 1 つを使用するか、独自の[Codespace](https://github.com/features/codespaces)で作業します。

2. **[進行中] AI を使用してワークスペースを更新する**:

    - **利用可能:** ブレインストーミング、プランおよびプラン内のファイルに対する自然言語の修正、プランファイルまたはステップの追加/編集/削除。
    - **計画中**: タスクおよび回答テキストの編集のサポート。

3. **[将来] 新規作成:** 現在は利用できませんが、将来的には VS Code で新しい Copilot Workspace セッションを作成できるようになります。

## はじめに

* [クイックスタート](#quick-start)
* [セッションの参照](#browsing-sessions)
* [セッションの管理](#managing-sessions)
* [プランニングと実装](#plan-and-implement)
* [自然言語の修正](#natural-language-revisions)
* [ブレインストーミング](#brainstorming)
* [既知の制限事項](#known-limitations)

### クイックスタート

1. まだインストールしていない場合は、[Visual Studio Code](https://code.visualstudio.com/)をインストールします。

1. 次に、VS Code で作業を続けたいセッションを[Web 上で](https://copilot-workspace.githubnext.com)開きます。

1. セッション画面で`VS Code`ボタンをクリックします。

    ![Web UXのVS Codeアイコン](./images/vscode/upper-right.png)

1. プロンプトが表示されたら、ブラウザでリンクを VS Code で開くことを許可します。

VS Code に表示される指示に従い、プロンプトが表示されたら選択を行い、セッションをローカルマシンに同期する手順に進みます。これで完了です！　😎

一般的に次のようなことが期待されます：

1. VS Code が開き（まだ実行されていない場合）、Copilot Workspace 拡張機能をインストールし、URI を開くように求められます。拡張機能がすでにインストールされている場合は、URI についてのみ尋ねられます。いずれにせよ、URI を開きます。

    <img src="./images/vscode/ghcw-extn-install.png" title="VS Code拡張機能のインストールとURIの開く通知の画像" width="200px">

1. **[一度だけ]** まだサインインしていない場合は、サインインするように求められます。`サインイン`をクリックし、開いたブラウザでサインインプロセスを完了します。

    <img src="./images/vscode/ghcw-sign-in-notification.png" title="サインイン通知の画像" width="400px">

1. VS Code インスタンスに関連するリポジトリがすでに開かれている場合、拡張機能はすぐにセッションをローカルに同期し始めます。それ以外の場合は、リポジトリをクローンするか、既存のフォルダを選択するように求められることがあります。

    <img src="./images/vscode/ghcw-clone-or-open-folder.png" title="クローンまたはフォルダを開く通知の画像" width="200px">

同期が開始されると、ローカルリポジトリは`ghcw-session`プレフィックスの付いた GitHub Copilot Workspace トラッキングブランチに切り替わります。これはこのセッションの一時的なブランチであるため、ローカルの変更をプッシュするべきではありません。

<img src="./images/vscode/ghcw-branch-example.png" title="ステータスバーのブランチの画像" width="250px">

ローカルファイルに加えた編集はすべて Web セッションに自動的に同期されます。ローカルファイルを保存するだけで、数秒以内にオンラインで変更が表示されます（何もプッシュする必要はありません）。これにより、VS Code のすべての機能を GitHub Copilot Workspace と一緒に使用できます。

ただし、選択したセッションにまだ実装がなく、更新されたファイルを同期する準備ができていない場合は、[実装が完了したら](#planning-and-implementing)同期を開始できることが通知されます。

<img src="./images/vscode/ghcw-uri-sync-not-enabled.png" title="同期が有効になっていない通知の画像" width="400px">

編集やデバッグに加えて、[自然言語の修正](https://github.com/githubnext/copilot-workspace-user-manual/blob/main/vscode.md#natural-language-revisions)を行ったり、[プランと実装](https://github.com/githubnext/copilot-workspace-user-manual/blob/main/vscode.md#planning-and-implementing)を調整したりすることもできます。作業が完了したら、次のいずれかを行います：

-   `Plan`ビューの**Push Changes into Branch...**アイコンをクリックして、ブランチを作成/更新し、オプションで PR を作成します。
-   または、Web に戻って、セッションから元のブランチに更新をプッシュするか、PR を作成します。`Plan`および`Task`ビューの上部にある`...`メニューにクイックアクセスリンクがあります。

## セッションの参照

セッションをローカルに同期していなくても、セッションを参照して詳細を表示できます。セッションを参照および管理するには、まず VS Code ウィンドウの左側にあるアクティビティバーの`GitHub Copilot Workspace`アイコンをクリックします。

<img src="./images/vscode/ghcw-activity-bar-icon.png" title="GitHub Copilot Workspaceアイコンのステータスバーの画像" width="50px">

アクティビティバーアイコンをクリックすると、セッションのリストまたはすでに選択した特定のセッションの詳細が表示されます。

セッションリストはリポジトリごとにソートされます。現在開いている VS Code フォルダに適用されるリポジトリは上部に表示されます。セッションの詳細を表示している場合は、`Task`ビューの`Back to Session List`矢印をクリックするか、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）から**GitHub Copilot Workspace: Back to Session List**コマンドを使用して、セッションリストに戻ることができます。

セッションリストでセッションを選択すると、リストが非表示になり、関連するセッションの詳細が表示されます。`Task`（または Issue または Pull Request）ビューと`Plan`ビューが表示されます。各ビューは、フルスクリーンアイコンをクリックして大きなパネルに拡張できます。

`Task`ビューには、タスクの説明と追加情報へのリンクが含まれています。`Plan`ビューには、セッションの関連プランの詳細（存在する場合）と現在プランに含まれているファイルが表示されます。

[プランがすでに実装されている場合](#planning-and-implementing)、プラン内のファイルをクリックして変更されたファイルを表示できます。

<img src="./images/vscode/ghcw-overview.png" width="700px" />

同期がアクティブな場合、ファイルをクリックすると、同期された内容のローカル変更ビューが開きます。このビューは編集可能で、変更は Web セッションに同期されます。セッションが同期されていない場合、Web セッションに保存されている変更が読み取り専用モードで表示されます。

プラン内のファイルにホバーして`Open File`アイコンをクリックすると、ファイルの変更ビューではなく、新しいタブでファイルを開くことができます。まだ同期していない場合は、セッションの同期を開始するように求められることがあります。

## セッションの管理

プランと初期実装があるセッションのファイル変更をローカルに同期できます。

開いたセッションにまだ実装がない場合は、VS Code から作成する方法については[プランニングと実装](#planning-and-implementing)を参照してください。完了したら、その内容をローカルに同期できます。

### 変更の同期を停止する

クイックスタートでセッションの変更をローカルに同期する方法を強調しましたので、次に変更の同期を停止する方法を説明します。

セッションリストが表示されている場合、現在同期されているセッションの横に緑色のチェックボックスが表示されます。このセッションにホバーすると、`Stop Syncing Changes`ボタンが表示されます。セッションの詳細が表示されている場合は、同じボタンが`Plan`ビューに表示されます。いずれかの場所でこのボタンをクリックして同期を停止します。

| セッションリスト | セッションの詳細 |
| :--- | :--- |
| <img src="./images/vscode/ghcw-session-list-button.png" title="セッションリストの画像" width="300px"> | <img src="./images/vscode/ghcw-session-details-button.png" title="セッション詳細の画像" width="300px"> |

または、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）を使用して、セッションの詳細を表示しているときに**GitHub Copilot Workspace: Stop Syncing Changes**コマンドを選択できます。

同期の開始時にいたブランチに戻るか、他に何もない場合は**main**（または master）に戻ります。同期がアクティブな場合、ローカルで行った変更は自動的に同期されるため、作業ツリーもクリーンアップされ、セッションの出入りが簡単になります。

次回同じセッションを同期すると、セッションはこのトラッキングブランチに戻り、GitHub Copilot Workspace の最新の変更が再び表示されます。

手動でブランチを同期開始時に設定されたものから変更した場合、同期も自動的に停止します。ただし、この場合、行った変更は作業ツリーに保持され、意図したものを失わないようにします。上記の手順で同期を停止すると、他の変更を続けるためのクリーンな作業ツリーが確保されます。

### 変更のローカル同期

クイックスタートで説明したように、GitHub Copilot Workspace Web UI の VS Code アイコンをクリックして変更のローカル同期を開始できます。ただし、VS Code 内から直接セッションの同期を開始することもできます。

ただし、前述のセクションで説明したように、[プランと初期実装](#planning-and-implementing)があるセッションのみがローカルに同期できます。

セッションリストが表示されている場合、現在同期されていないセッション（緑色のチェックボックスがない）にホバーすると、`Stop Syncing Changes`ボタンが表示されます。セッションの詳細が表示されている場合は、同期が無効な場合に同じボタンが`Plan`ビューに表示されます。このボタンをクリックして、セッションの変更をローカルに同期します。

同じリポジトリの既存のセッションがすでに同期されている場合は、自動的に同期が停止されるため、競合を心配する必要はありません。

| セッションリスト | セッションの詳細 |
| :--- | :--- |
| <img src="./images/vscode/ghcw-session-list-no-sync.png" title="セッションリストの画像" width="300px"> | <img src="./images/vscode/ghcw-session-details-no-sync.png" title="セッション詳細の画像" width="300px"> |

同様に、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）を使用して、セッションの詳細ビューにいるときに**GitHub Copilot Workspace: Sync Changes Locally**コマンドを選択して同期を開始できます。

次に、次のようにプロンプトが表示される場合があります：
1. 現在、VS Code でセッションのリポジトリが開かれていない場合は、リポジトリを含むフォルダを開くか、新しい場所にリポジトリをクローンするように求められます。
1. 正しいリポジトリが開かれているが、現在の作業ツリーにコミットされていない変更がある場合は、それらをどうするかを尋ねられます。

いずれの場合も、これが完了すると、ローカルリポジトリはステータスバーに表示される`ghcw-session`プレフィックスの付いた GitHub Copilot Workspace トラッキングブランチに切り替わります。

<img src="./images/vscode/ghcw-branch-example.png" title="ステータスバーのブランチの画像" width="250px">

いずれにせよ、ローカルファイルに加えた編集は Web セッションに同期されるため、コミットや変更の喪失を心配する必要はありません。

### 同期ステータスと処理状態の可視性

作業中に常に`Plan`ビューが表示されているわけではないため、GitHub Copilot Workspace にはその時点で拡張機能が何をしているかを理解するのに役立つステータスバーアイテムがあります。以下は、表示される内容の例です：

| 例 | 説明 |
| :--- | :--- |
| <img src="./images/vscode/status-bar-not-syncing.png" title="拡張機能がアイドル状態のときのGitHub Copilot Workspaceのステータスバーの画像"> | 拡張機能はサインインしていますが、アイドル状態です。 |
| <img src="./images/vscode/status-bar-syncing.png" title="同期が有効だが拡張機能がアイドル状態のときのGitHub Copilot Workspaceのステータスバーの画像"> | セッションの同期が有効ですが、拡張機能は現在アイドル状態です。 |
| <img src="./images/vscode/status-bar-working.png" title="拡張機能がアクティブに作業しているときのGitHub Copilot Workspaceのステータスバーの画像"> | 拡張機能が操作を実行していることを示すテキスト（`Starting implementation...`）とスピニングローディングまたは同期アイコン（ファイルが転送されているとき）があります。 |
| <img src="./images/vscode/status-bar-error.png" title="同期エラーが発生したときのGitHub Copilot Workspaceのステータスバーの画像"> | ここでは、同期中にエラーが発生しました。ステータスバーアイテムをクリックすると、詳細情報が表示されます。 |

このステータスバーアイテムをクリックすると、同期しているセッションの詳細（または複数のリポジトリを持つマルチルートワークスペースで複数のセッションを同期している場合はセッションリスト）に移動します。同期エラーが発生した場合、ステータスバーは赤くなり、クリックすると問題を解決するためのオプションが表示されます。

#### プランビューのバナー

ただし、`Plan`ビューが表示されている場合は、ステータスバナーを見て、何が起こっているかを確認し、現在の状態に基づいて迅速なアクションを実行できます。

<img src="./images/vscode/ghcw-plan-view-banner.png" title="ステータスバーのGitHub Copilot Workspaceの画像" width="300px">

### セッションの変更をブランチまたは PR にプッシュする

拡張機能は変更を自動的に Web に同期しますが、セッションからブランチに変更をプッシュしたり、PR を作成したりすることもできます。これは、セッションが完了したときや、.gitignore ファイルや通知を受け取った大きなファイルなど、自動的に同期されないものを保持したい場合に便利です。

幸いなことに、セッションを同期している場合、`Plan`ビューの次のボタンを使用してこれらのアクションを実行できます。この表のコマンド名は、適切なセッションがサイドバーに表示されているときに**コマンドパレット**（F1 または Ctrl/Cmd+Shift+P）に表示されるコマンド名でもあります。

| ボタン | コマンド | 説明 | 場所 |
| :--- | :--- | :--- | :--- |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/repo-push.svg" width="24px" style="background-color:white;">               | Push Changes into Branch... | 変更を新しいまたは既存のローカルブランチにプッシュし、オプションでリモートにもプッシュします。 | ファイル同期が有効な場合のプランビュー、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/git-pull-request-create.svg" width="24px" style="background-color:white;"> | Create PR from Changes...   | 変更を指定されたリモートブランチにプッシュし、VS Code で PR UX を開いてリクエストの詳細を入力します。 | ファイル同期が有効な場合のプランビュー、`...`コンテキストメニュー。 |

### セッションの削除

セッションを削除するには、セッションリストの項目の横にあるゴミ箱アイコンをクリックします。現在セッションの詳細を表示している場合は、`Task`または`Plan`ビューの`...`ボタンをクリックして表示されるコンテキストメニューから**Delete Session**を選択します。

または、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）を使用して、セッションの詳細を表示しているときに**GitHub Copilot Workspace: Delete Session**コマンドを選択できます。

## プランニングと実装

セッションの詳細が表示されている場合（`Task`および`Plan`ビューが表示されている場合）、VS Code からセッションのプランと関連する実装を変更できます。

実際、セッションにまだプランがない場合は、初期プランを生成して実装することもできます。

`Plan`ビューの`...`ボタンをクリックすると、プランと対話するためのさまざまなオプションが表示されます。ただし、最も一般的なアクションはアイコンとして表示されます。以下の表は、それぞれの機能を説明しています。この表のコマンド名は、適切なセッションがサイドバーに表示されているときに**コマンドパレット**（F1 または Ctrl/Cmd+Shift+P）に表示されるコマンド名でもあります。

| ボタン | コマンド | 説明 | 場所 |
| :--- | :--- | :--- | :--- |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/project.svg"  width="24px" style="background-color:white;"> | Generate Plan | セッションのプランを生成し、初期実装を作成します。 | プランが存在しない場合のプランビュー。再生成プランはその後`...`コンテキストメニューに表示されます。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/sparkle.svg"  width="24px" style="background-color:white;"> | Implement Plan | プランビューで選択された項目を実装（または再実装）します。 | プランが存在する場合のプランビュー、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/comment.svg" width="24px" style="background-color:white;"> | Revise Plan | 自然言語を使用してプラン全体を修正します。要求された変更を自動的に実装します。 | プランが存在する場合のプランビュー、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/sync.svg"  width="24px" style="background-color:white;"> | Sync Changes Locally | セッションの変更をローカルに同期します。 | 実装があり、セッションがまだ同期されていない場合のプランビュー、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/sync-ignored.svg"  width="24px" style="background-color:white;"> | Stop Syncing Changes | セッションの変更のローカル同期を停止します。 | すでに同期されているセッションのプランビュー、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/repo-push.svg" width="24px" style="background-color:white;">               | Push Changes into Branch... | 変更を新しいまたは既存のローカルブランチにプッシュし、オプションでリモートにもプッシュします。 | ファイル同期が有効な場合のプランビュー、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/git-pull-request-create.svg" width="24px" style="background-color:white;"> | Create PR from Changes...   | 変更を指定されたリモートブランチにプッシュし、VS Code で PR UX を開いてリクエストの詳細を入力します。 | ファイル同期が有効な場合のプランビュー、`...`コンテキストメニュー。 |

プラン内のファイルや項目にホバーすると、`...`コンテキストメニューも表示されます。このコンテキストメニューを使用して、ファイルの表示、変更の表示、リスト項目の編集、移動、削除などを行うことができます。

### 自然言語の修正

プランと実装を自然言語で修正することもできます。これは、前述のようにプラン全体に対して行うこともできますし、プラン内のファイルに対してターゲットを絞った修正を行うこともできます。プランに別のファイルを追加し、一度に修正することもできます。

ファイルレベルの修正を簡単に行うために、プランの一部となるファイルの任意の開いているエディタウィンドウの右上にボタンがあります。

<img src="./images/vscode/ghcw-editor-actions.png" title="エディタアクションの画像" width="700px">

これらの修正をトリガーする場所の概要は次のとおりです：

| ボタン | コマンド | 説明 | 場所 |
| :--- | :--- | :--- | :--- |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/comment.svg" width="24px" style="background-color:white;"> | Revise Plan | 自然言語を使用してプラン全体を修正します。要求された変更を自動的に実装します。 | プランが存在する場合のプランビュー、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/target.svg"  width="24px" style="background-color:white;"> | Revise File | 自然言語を使用してファイルをターゲットにした修正を行います。ファイルをプランに追加するか、既存のエントリにステップを追加し、要求された変更を実装します。 | プランファイル項目（ホバー）、エディタアクション（右上）、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/add.svg"  width="24px" style="background-color:white;"> | Add File to Plan | ファイルをプランに追加しますが、修正は行いません。 | エディタアクション（右上）、`...`コンテキストメニュー。 |

## ブレインストーミング

> この機能は Copilot Workspace に新しく追加されたものであるため、他の部分よりも粗削りな部分があるかもしれません。フィードバックがあればお知らせください！

ブレインストーミングは、実行したいタスクを洗練させるために Copilot Workspace と対話する方法を提供します。提案された質問を選択してタスクの潜在的なオプションについて学び、計画および実装時に使用する追加のコンテキストとして回答を追加できます。この機能は現在 VS Code で利用可能であり、エディタから直接初期タスクとプランを洗練することができます。

### ブレインストーミングパネルへのアクセス

ブレインストーミングにアクセスする方法はいくつかあります。まず、次のボタンのいずれかをクリックして開始できます。このドキュメントの他のケースと同様に、コマンド列には、適切なセッションがサイドバーに表示されているときに**コマンドパレット**（F1 または Ctrl/Cmd+Shift+P）に表示されるコマンド名が含まれています。

| ボタン | コマンド | 説明 | 場所 |
| :--- | :--- | :--- | :--- |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/lightbulb.svg" width="24px" style="background-color:white;"> | Brainstorm | `Brainstorming`パネルを開きます。質問「このタスクをどのように解決すべきか？」がまだ回答されていない場合（つまり、「仕様」がまだ作成されていない場合）、この時点で開始されます。 | タスクビュー、`...`コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/question.svg"  width="24px" style="background-color:white;"> | Answer New Question... | Copilot Workspaces に特定の質問をすることができ、`Brainstorming`パネルに回答が表示されます。 | タスクビュー、`...`コンテキストメニュー。 |

`Task`ビューには、すでにタスクに追加された質問や回答のリストも含まれています。これらのいずれかをクリックすると、`Brainstorming`パネルに回答が表示され、ブレインストーミングを続けることができます。

<img src="./images/vscode/ghcw-task-view-brainstorm.png" title="ブレインストーミングを含むタスクビューの画像" width="300px">

### ブレインストーミングパネルの使用

`Brainstorming`パネルを開くと、現在の質問に対する回答が表示されます。デフォルトでは、タスクに常に追加される質問「このタスクをどのように解決すべきか？」が表示されます。次に、可能なアクションを示す一連のボタンが上部に表示されます。

<img src="./images/vscode/ghcw-brainstorm-panel.png" title="ブレインストーミングパネルの画像" width="700px">

表示される可能性のあるボタンとその機能を見てみましょう。

| ボタン | 説明 |
| :--- | :--- |
| **Add to Task** | 現在の回答をタスクに追加します。これにより、「このタスクをどのように解決すべきか？」の質問/仕様の再生成が自動的にトリガーされます。タスクに追加された質問の回答は、`Task`ビューのタスク説明の下に表示されます。 |
| **Remove from Task** | 現在の回答をタスクから削除します。これにより、「このタスクをどのように解決すべきか？」の質問/仕様の再生成が自動的にトリガーされます。 |
| **Regenerate** | Copilot Workspace に質問の再回答を依頼します。 |
| **Delete** | 質問と関連する回答をリストから削除します。 |
| **Answer** | Copilot Workspace に新しい質問をすることができます。 |
| **Open Existing** | すでに生成された回答のリストを表示し、`Brainstorming`パネルで開くことができます。タスクに追加された回答にはチェックが付いています。タスクに回答を追加したり削除したりした場合に便利です。 |

#### 複数の回答

場合によっては、質問に対する複数の回答が表示されることもあります。この場合、オプションの横にある空の円をクリックしてタスクに追加する回答を選択できます。これにより、緑色のチェックマークが表示され、追加されたことが示されます。気が変わった場合は、チェックマークをクリックして削除できます。

<img src="./images/vscode/ghcw-brainstorm-multiple-answers.png" title="複数の回答があるブレインストーミングパネルの画像" width="700px">

#### 提案された質問

さらに、現在の質問に対する回答の下には、タスクに適用される可能性のある**提案された質問**のリストが表示されます。これらのいずれかをクリックすると、`Brainstorming`パネルに回答が表示されます。

### ブレインストーミングが完了したらプランを更新する

ブレインストーミングが完了したら、`Plan`ビューの`...`をクリックし、**Regenerate Plan**を選択してプランを再生成できます。（まだプランがない場合は、前述のように`Plan`ビューの`...`をクリックし、**Generate Plan**を選択して生成できます。）

ただし、既存のプランに概ね満足している場合は、新しい情報をより具体的な方法で考慮するために**[自然言語の修正](#natural-language-revisions)**を行うことができます。

## 既知の制限事項

**機能:** 上記のように、次の機能はまだ VS Code で利用できないため、Web UI を使用する必要があります：
* 新しいセッションの開始
* タスクや回答された質問のテキストの直接編集

**ファイル同期:**
* 技術プレビュー中、バイナリファイル、特定のパスやファイルタイプ、特定のサイズを超えるファイルの同期を制限するなど、ファイル同期にはいくつかの制限があります。これらの制限は、改善が進むにつれて変更される可能性があります。VS Code 拡張機能を直接使用する場合、これらの制限に達したときに通知され、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）から**GitHub Copilot Workspace: Show Files Ignored While Syncing**コマンドを使用して無視されたファイルを確認できます。
* ファイル同期のステータスは、開いているウィンドウ間で共有されません。そのため、同じフォルダ（およびリポジトリ）に対して複数のウィンドウを開いており、それぞれが同期している場合、同じファイル内容を複数回送信または適用し、更新の適用に失敗する可能性があります。これを避けるためには、特定のリポジトリに対して単一のウィンドウを使用するか、複数のウィンドウでファイル同期を開始しないようにします。
* GitHub Copilot Workspace Web UI によって開始された Codespace から作業する場合、同期中に無視されたファイルに関する通知は表示されません。この場合、拡張機能の使用はオプションです。ファイル同期はスタンドアロンプロセスによって処理されます。

予期しないことが発生した場合は、詳細を確認するために出力ビューを確認できます。ファイルメニューから**表示** > **出力**を選択し、ドロップダウンから**GitHub Copilot Workspace**を選択します。これにより、何が起こったかを特定し、発生した問題の診断に役立ちます。