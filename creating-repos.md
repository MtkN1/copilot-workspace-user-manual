# テンプレートからリポジトリを作成する

Copilot Workspace を使用すると、自然言語を使用してテンプレートからリポジトリを作成できます。

## GitHub.com から「このテンプレートを使用」を使用する

Copilot Workspace を使用してリポジトリを作成するには、GitHub.com のテンプレートリポジトリに移動し、「このテンプレートを使用」を選択します。次のようになります：

<img src="images/creating-repos/create-repo-from-template.png" width=400 alt="Create repository from template"><br>*Copilot Workspace を使用してテンプレートからリポジトリを作成する*

タスクは、作成するソフトウェアの説明とテンプレートリポジトリの README に基づいています。この種のタスクを開始するには、[新しいセッションを作成](#using-new-session-on-the-dashboard)することもできます。リポジトリ作成タスクを開始すると、次のようになります：

<img src="images/creating-repos/repo-task-timeline-representation.png" width=600 alt="Repo task timeline representation"><br>*タスクは「リポジトリ」とラベル付けされ、「テンプレート」パネルにはテンプレートリポジトリが表示されます*

その後、Copilot Workspace は提供された説明に基づいてリポジトリの仕様を生成し、それを作成するための計画を立て、最終的な実装を行います。

## ダッシュボードで「新しいセッション」を使用する

[Copilot Workspace ダッシュボード](https://copilot-workspace.githubnext.com)で「新しいセッション」ボタンをクリックし、テンプレートを検索することで、テンプレートからリポジトリを作成することもできます。これにより、作成したいソフトウェアを説明する新しいタスクがワークスペースに開かれます。

## URL を使用する

任意のリポジトリ URL に`?template=true`というクエリパラメータを追加することで、「リポジトリ作成」モードをオンにすることもできます。例えば：

https://copilot-workspace.githubnext.com/githubnext/hello-world?template=true

受信 URL の場合、次のリポジトリはデフォルトでテンプレートとして扱われます：

- 任意の GitHub テンプレートリポジトリ
- `templates`を含む組織内の任意のリポジトリ（大文字小文字を区別せず、先頭または末尾にダッシュがある場合）
- 名前に`-template`、`-scaffold`、`-starter`、または`-boilerplate`を含む任意のリポジトリ（大文字小文字を区別せず、先頭または末尾にダッシュがある場合）
