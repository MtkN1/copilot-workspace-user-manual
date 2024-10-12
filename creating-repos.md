# テンプレートからリポジトリを作成する

Copilot Workspaceを使用すると、自然言語を使用してテンプレートからリポジトリを作成できます。

## GitHub.comから「Use this template」を使用する

Copilot Workspaceを使用してリポジトリを作成するには、GitHub.comのテンプレートリポジトリに移動し、「Use this template」を選択します。次のようになります：

<img src="images/creating-repos/create-repo-from-template.png" width=400 alt="Create repository from template"><br>*Copilot Workspaceを使用してテンプレートからリポジトリを作成する*

タスクは、作成するソフトウェアの説明とテンプレートリポジトリのREADMEに基づいています。また、[新しいセッションを作成](#using-new-session-on-the-dashboard)することで、この種のタスクを開始することもできます。リポジトリ作成タスクを開始すると、次のようになります：

<img src="images/creating-repos/repo-task-timeline-representation.png" width=600 alt="Repo task timeline representation"><br>*タスクは「リポジトリ」とラベル付けされ、「テンプレート」パネルにはテンプレートリポジトリが表示されます*

その後、Copilot Workspaceは提供された説明に基づいてリポジトリの仕様を生成し、それを作成するための計画を立て、最終的な実装を行います。

## ダッシュボードの「新しいセッション」を使用する

[Copilot Workspaceダッシュボード](https://copilot-workspace.githubnext.com)の「新しいセッション」ボタンをクリックし、テンプレートを検索することで、テンプレートからリポジトリを作成することもできます。これにより、作成したいソフトウェアを説明するタスクがワークスペースに開かれます。

## URLを使用する

任意のリポジトリURLに`?template=true`というクエリパラメータを追加することで、「リポジトリ作成」モードをオンにすることもできます。例えば：

https://copilot-workspace.githubnext.com/githubnext/hello-world?template=true

受信URLの場合、次のリポジトリはデフォルトでテンプレートとして扱われます：

- 任意のGitHubテンプレートリポジトリ
- `templates`を含む組織内の任意のリポジトリ（大文字小文字を区別せず、先頭または末尾にダッシュがある場合）
- 名前に`-template`、`-scaffold`、`-starter`、または`-boilerplate`を含む任意のリポジトリ（大文字小文字を区別せず、先頭または末尾にダッシュがある場合）
