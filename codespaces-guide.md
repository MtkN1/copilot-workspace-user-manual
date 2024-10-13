# コードスペーススターターガイド

このドキュメントには、ワークスペースセッションでターミナル / コードスペースを使用するための有用な情報が含まれています。

## コードスペースの制限

### 全体的な使用

技術プレビューには、カレンダー月の開始時にリセットされる限定的な無料のコードスペースコンピューティング使用が含まれています。

### 全体的な制限

技術プレビューでは、合計コードスペースおよび合計アクティブコードスペースの制限が適用される場合があります。これらの問題が解決しない場合は、[こちら](https://github.com/githubnext/copilot-workspace-user-manual?tab=readme-ov-file#feedback)からお問い合わせください。

### 組織ベースの制限とポリシー

リポジトリを所有する組織がコードスペースの使用に関するポリシーを設定している場合、それらのポリシーがワークスペースのコードスペース作成に適用されます。ポリシーの調整については、組織の管理者にお問い合わせください。

## 一般的なエラー

#### Copilot Workspaceの使用制限に達しました

次のカレンダー月の開始時に無料の使用制限がリセットされ、ワークスペースの使用を続けることができます。使用制限についてのフィードバックは[こちら](https://github.com/githubnext/copilot-workspace-user-manual?tab=readme-ov-file#feedback)からお問い合わせください。

#### アクティブなCopilot Workspaceの制限に達しました

オープンなワークスペースセッションを閉じ、以前のセッションがシャットダウンするのを待ってから新しいセッションを作成してください。

#### Copilot Workspaceの制限に達しました

オープンなワークスペースセッションを閉じ、以前のセッションがシャットダウンするのを待ってから新しいセッションを作成してください。

#### リポジトリはコードスペースに使用できません

これは、リポジトリまたは組織のポリシーがコードスペースの作成を制限しているためかもしれません。コードスペースの使用を妨げている設定がないか、組織またはリポジトリの設定を確認してください。問題が解決しない場合は、[技術プレビューフィードバックチャネル](https://github.com/githubnext/copilot-workspace-user-manual?tab=readme-ov-file#feedback)にお問い合わせください。

#### 割り当てられた場所が現在利用できません

数分後に再試行してください。さらに、このエラーが特定のリージョンで続く場合は、ユーザー設定でデフォルトのコードスペースリージョンを変更できます。詳細は[こちらの公開ドキュメント](https://docs.github.com/en/codespaces/setting-your-user-preferences/setting-your-default-region-for-github-codespaces)をご覧ください。

#### 提供された `devcontainer.json` が有効な JSON に解析できません

選択したリポジトリで `devcontainer.json` の構文エラーを修正する必要があります。`devcontainer.json` の構文について詳しくは、[こちらの公開ドキュメント](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers)をご覧ください。

#### 組織がOAuthアプリのアクセス制限を有効にしているため、Copilot Workspaceへのアクセスが制限されています

Copilot Workspace OAuthアプリへのアクセスを許可するように、組織の管理者にお問い合わせください。
