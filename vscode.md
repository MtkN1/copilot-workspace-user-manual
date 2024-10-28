# GitHub Copilot Workspace VS Code extension

この Copilot Workspace VS Code 拡張機能を使用すると、VS Code の快適さから GitHub Copilot Workspace を使用できます。既存のセッションを続行し、PR を作成する前に提案された変更を編集およびデバッグします。計画や実装を自然言語で修正する場合でも、ファイルを直接編集する場合でも、VS Code とその拡張機能エコシステムのすべての機能を使用しながら、編集内容を Web 上の GitHub Copilot Workspace に同期できます。

これは現在アルファ版の拡張機能であり、複数のフェーズで拡張機能の強化を展開していきます。

1. **続行:** Copilot Workspace セッションを参照し、変更を同期して、VS Code ローカルでアプリケーションを編集およびデバッグします。他の [VS Code リモート拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) の 1 つを使用するか、独自の [Codespace](https://github.com/features/codespaces) で行います。

2. **[進行中] AI を使用してワークスペースを更新する**:

    - **利用可能:** 計画および計画内のファイルを作成、編集、および自然言語で修正します。
    - **計画中**: タスク、仕様、およびブレインストーミングに情報を追加/編集するサポート、チャットへの統合。

3. **[将来] 新規作成:** 現在は利用できませんが、VS Code で新しい Copilot Workspace セッションを作成できるようになります。


## はじめに

* [クイックスタート](#quick-start)
* [セッションの参照](#browsing-sessions)
* [セッションの管理](#managing-sessions)
* [計画と実装](#plan-and-implement)
* [自然言語の修正](#natural-language-revisions)
* [既知の制限](#known-limitations)

### クイックスタート

1. まだインストールしていない場合は、[Visual Studio Code](https://code.visualstudio.com/) をインストールします。

1. 次に、VS Code で作業を続行したいセッションを [Web 上で](https://copilot-workspace.githubnext.com) 開きます。

1. セッション画面で `VS Code` ボタンをクリックします。

    ![Web UX の VS Code アイコン](./images/vscode/upper-right.png)

1. プロンプトが表示されたら、ブラウザが VS Code でリンクを開くことを許可します。

VS Code に表示される指示に従い、プロンプトが表示されたら選択を行い、セッションをローカルマシンに同期する手順に従います。これで完了です！😎

一般的に次のようなことが期待されます：

1. VS Code が開き（まだ実行されていない場合）、Copilot Workspace 拡張機能をインストールし、URI を開くように求められます。拡張機能が既にインストールされている場合は、URI についてのみ尋ねられます。いずれにせよ、URI を開きます。

    <img src="./images/vscode/ghcw-extn-install.png" title="VS Code 拡張機能のインストールと URI の開く通知の画像" width="200px">

1. **[一度だけ]** まだサインインしていない場合は、サインインするように求められます。`サインイン` をクリックし、開いたブラウザでサインインプロセスを完了します。

    <img src="./images/vscode/ghcw-sign-in-notification.png" title="サインイン通知の画像" width="400px">

1. VS Code インスタンスに関連するリポジトリを含むフォルダーが既に開かれている場合、拡張機能はすぐにセッションをローカルに同期し始めます。それ以外の場合は、リポジトリをクローンするか、既存のフォルダーを選択するように求められることがあります。

    <img src="./images/vscode/ghcw-clone-or-open-folder.png" title="クローンまたはフォルダーを開く通知の画像" width="200px">

同期が開始されると、ローカルリポジトリは `ghcw-session` プレフィックスを持つ GitHub Copilot Workspace トラッキングブランチに切り替わります。ステータスバーで確認できます。

<img src="./images/vscode/ghcw-branch-example.png" title="ステータスバーのブランチの画像" width="250px">

ローカルファイルに加えた編集は Web セッションに同期されます。これにより、VS Code のすべての機能を GitHub Copilot Workspace と一緒に使用できます。

ただし、まだ実装がないセッションを選択した場合は、[実装がある](#planning-and-implementing) と通知され、同期を開始できます。

<img src="./images/vscode/ghcw-uri-sync-not-enabled.png" title="同期が有効になっていない通知の画像" width="400px">

## セッションの参照

セッションをローカルに同期していなくても、セッションを参照して詳細を表示できます。セッションを参照および管理するには、まず VS Code ウィンドウの左側のアクティビティバーにある `GitHub Copilot Workspace` アイコンをクリックします。

<img src="./images/vscode/ghcw-activity-bar-icon.png" title="GitHub Copilot Workspace アイコンのステータスバーの画像" width="50px">

アクティビティバーアイコンをクリックすると、セッションのリストまたは選択した特定のセッションの詳細が表示されます。

セッションリストはリポジトリごとにソートされます。現在開いている VS Code フォルダーに関連するリポジトリは上部に表示されます。セッションの詳細を表示している場合は、`タスク` ビューの `セッションリストに戻る` 矢印をクリックするか、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）から **GitHub Copilot Workspace: Back to Session List** コマンドを使用して、セッションリストに戻ることができます。

セッションリストでセッションを選択すると、リストが非表示になり、関連するセッションの詳細が表示されます。`タスク`（または Issue または Pull Request）ビューと `計画` ビューが表示されます。各ビューは、`全画面` アイコンをクリックすることで拡大できます。

`タスク` ビューには、タスクの説明と追加情報へのリンクが含まれています。`計画` ビューには、セッションの関連計画（存在する場合）および計画内のファイルの詳細が表示されます。

[計画が既に実装されている](#planning-and-implementing) 場合は、計画内のファイルをクリックして変更されたファイルを表示できます。

<img src="./images/vscode/ghcw-overview.png" width="700px" />

同期がアクティブな場合、ファイルをクリックすると、同期された内容のローカル変更ビューが開きます。このビューは編集可能で、変更は Web セッションに同期されます。セッションが同期されていない場合は、Web セッションに現在保存されている変更が読み取り専用モードで表示されます。

また、計画内のファイルをホバーすると表示される `ファイルを開く` アイコンをクリックして、ファイルを新しいタブで開くこともできます。まだ同期していない場合は、セッションの同期を開始するように求められることがあります。

## セッションの管理

計画と初期実装があるセッションについては、セッションのファイル変更をローカルに同期できます。

開いたセッションにまだ実装がない場合は、VS Code から作成する方法について [計画と実装](#planning-and-implementing) を参照してください。完了したら、その内容をローカルに同期できます。

### 変更の同期を停止する

クイックスタートでは、セッションの変更をローカルに同期するための迅速な方法を強調しましたので、次に変更の同期を停止する方法を説明します。

セッションリストが表示されている場合、現在同期中のセッションには緑色のチェックボックスが表示されます。このセッションにホバーすると、`変更の同期を停止` ボタンが表示されます。セッションの詳細が表示されている場合は、`計画` ビューに同じボタンが表示されます。いずれかの場所でこのボタンをクリックして同期を停止します。

| セッションリスト | セッションの詳細 |
| :--- | :--- |
| <img src="./images/vscode/ghcw-session-list-button.png" title="セッションリストの画像" width="300px"> | <img src="./images/vscode/ghcw-session-details-button.png" title="セッション詳細の画像" width="300px"> |

または、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）を使用して、セッションの詳細を表示しているときに **GitHub Copilot Workspace: Stop Syncing Changes** コマンドを選択できます。

同期が停止されると、同期を開始したときにいたブランチに戻ります。何もない場合は **main**（または master）に戻ります。同期がアクティブな場合、ローカルで行った変更は自動的に同期されるため、作業ツリーもクリーンアップされ、セッションのジャンプインとジャンプアウトが簡単になります。

次回このセッションを同期すると、セッションはこのトラッキングブランチに戻り、GitHub Copilot Workspace の最新の変更が再び表示されます。

手動でブランチを変更した場合、同期も自動的に停止されます。ただし、この場合、行った変更は作業ツリーに保持され、意図したものを失わないようにします。上記のように同期を停止すると、クリーンな作業ツリーが確保され、他の変更を続けることができます。

### 変更のローカル同期

クイックスタートで説明したように、GitHub Copilot Workspace Web UI の VS Code アイコンをクリックして、変更のローカル同期を開始できます。ただし、VS Code 内から直接セッションの同期を開始することもできます。

ただし、前述のセクションで説明したように、[計画と初期実装](#planning-and-implementing) があるセッションのみがローカルに同期できます。

セッションリストが表示されている場合、現在同期されていないセッション（緑色のチェックボックスがない）にホバーすると、`変更の同期を開始` ボタンが表示されます。セッションの詳細が表示されている場合は、`計画` ビューに同じボタンが表示されます（このセッションの同期がアクティブでない場合）。このボタンをクリックして、セッションの変更をローカルに同期します。

同じリポジトリの既存の他のセッションが既に同期されている場合は、自動的に同期が停止されるため、競合を心配する必要はありません。

| セッションリスト | セッションの詳細 |
| :--- | :--- |
| <img src="./images/vscode/ghcw-session-list-no-sync.png" title="セッションリストの画像" width="300px"> | <img src="./images/vscode/ghcw-session-details-no-sync.png" title="セッション詳細の画像" width="300px"> |

同様に、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）を使用して、セッションの詳細ビューにいるときに **GitHub Copilot Workspace: Sync Changes Locally** コマンドを選択して同期を開始できます。

次に、次のようにプロンプトが表示される場合があります：
1. セッションのリポジトリが VS Code で現在開かれていない場合、リポジトリを含むフォルダーを開くか、新しい場所にリポジトリをクローンするように求められます。
1. 正しいリポジトリが開かれているが、現在の作業ツリーにコミットされていない変更がある場合、変更をどうするかを尋ねられます。

いずれにせよ、これが完了すると、ローカルリポジトリは `ghcw-session` プレフィックスを持つ GitHub Copilot Workspace トラッキングブランチに切り替わります。ステータスバーで確認できます。

<img src="./images/vscode/ghcw-branch-example.png" title="ステータスバーのブランチの画像" width="250px">

ローカルファイルに加えた編集は Web セッションに同期されるため、変更をコミットしたり失ったりする心配はありません。

### セッションの削除

セッションを削除するには、セッションリストの項目の横にあるゴミ箱アイコンをクリックします。セッションの詳細を表示している場合は、`タスク` または `計画` ビューの `...` ボタンをクリックして表示されるコンテキストメニューから **セッションの削除** を選択します。

または、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）を使用して、セッションの詳細を表示しているときに **GitHub Copilot Workspace: Delete Session** コマンドを選択できます。

## 計画と実装

セッションの詳細が表示されている場合（`タスク` および `計画` ビューが表示されている場合）、VS Code から直接セッションの計画および関連する実装を変更できます。

実際、セッションにまだ計画がない場合は、初期計画を生成して実装することもできます。

`計画` ビューの `...` ボタンをクリックすると、計画とその関連実装を操作するためのさまざまなオプションが表示されます。ただし、最も一般的なアクションはアイコンとして表示されます。各アイコンの機能を見てみましょう。

| ボタン | コマンド | 説明 | 場所 |
| :--- | :--- | :--- | :--- |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/project.svg"  width="24px" style="background-color:white;"> | 計画の生成 | セッションの計画を生成し、初期実装を作成します。 | 計画ビューに計画がない場合。計画の再生成はその後 `...` コンテキストメニューに表示されます。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/sparkle.svg"  width="24px" style="background-color:white;"> | 計画の実装 | 計画ビューで選択された項目を実装（または再実装）します。 | 計画ビューに計画がある場合、`...` コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/comment.svg" width="24px" style="background-color:white;"> | 計画の修正 | 自然言語を使用して計画全体を修正します。要求された変更を自動的に実装します。 | 計画ビューに計画がある場合、`...` コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/sync.svg"  width="24px" style="background-color:white;"> | 変更のローカル同期 | セッションの変更をローカルに同期します。 | 計画ビューに実装があり、セッションが既に同期されていない場合、`...` コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/sync-ignored.svg"  width="24px" style="background-color:white;"> | 変更の同期を停止 | セッションの変更の同期を停止します。 | セッションが既に同期されている場合の計画ビュー、`...` コンテキストメニュー。 |

これらの同じコマンドは、コマンドパレット（F1 または Ctrl/Cmd+Shift+P）でも利用できます。

`...` コンテキストメニューは、計画内のファイルや項目をホバーすると表示されます。このコンテキストメニューを使用して、ファイルを表示したり、変更を表示したり、リスト項目を編集、移動、削除したりできます。

### 自然言語の修正

計画と実装を自然言語で修正することもできます。これは、前述のように計画全体に対して行うこともできますし、計画内のファイルに対してターゲットを絞った修正を行うこともできます。計画に別のファイルを追加し、一度に修正することもできます。

ファイルレベルの修正を簡単に行うために、計画の一部となるファイルの任意の開いているエディタウィンドウの右上にボタンがあります。

<img src="./images/vscode/ghcw-editor-actions.png" title="エディタアクションの画像" width="700px">

以下は、これらの修正をトリガーできる場所の概要です：

| ボタン | コマンド | 説明 | 場所 |
| :--- | :--- | :--- | :--- |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/comment.svg" width="24px" style="background-color:white;"> | 計画の修正 | 自然言語を使用して計画全体を修正します。要求された変更を自動的に実装します。 | 計画ビューに計画がある場合、`...` コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/target.svg"  width="24px" style="background-color:white;"> | ファイルの修正 | 自然言語を使用してファイルにターゲットを絞った修正を行います。ファイルを計画に追加するか、既存のエントリにステップを追加し、要求された変更を自動的に実装します。 | 計画ファイル項目（ホバー）、エディタアクション（右上）、`...` コンテキストメニュー。 |
| <img src="https://raw.githubusercontent.com/microsoft/vscode-codicons/refs/heads/main/src/icons/add.svg"  width="24px" style="background-color:white;"> | ファイルを計画に追加 | ファイルを計画に追加しますが、修正は行いません。 | エディタアクション（右上）、`...` コンテキストメニュー。 |

## 既知の制限

1. 上記のように、次の操作は VS Code ではまだ利用できないため、Web UI を使用する必要があります：
    1. 新しいセッションの開始
    1. タスク/仕様/ブレインストーミングの編集
    1. セッションからの PR の作成
1. ファイル同期のステータスは開いているウィンドウ間で共有されません。そのため、同じフォルダー（およびリポジトリ）に対して複数のウィンドウを開いており、それぞれが同期している場合、同じファイルの内容を複数回送信または適用し、更新の適用に失敗する可能性があります。これを避けるために、特定のリポジトリに対して単一のウィンドウを使用するか、複数のウィンドウでファイル同期を開始しないでください。
1. セッションリストには、Web のセッションリストにも表示されるセッションのみが表示されます。たとえば、アーカイブされたセッションやタスクのみを含むセッションは除外されます。ただし、セッションが Web UI にある限り、`VS Code で開く` ボタンをクリックして VS Code で開くことができます。
