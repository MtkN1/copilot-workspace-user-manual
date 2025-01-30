# Codespaces スターターガイド

このドキュメントには、ワークスペースセッションでターミナル/Codespace を使用するための有用な情報が含まれています。

## Codespaces の制限

### 全体的な使用

技術プレビューには、カレンダー月の開始時にリセットされる限定的な無料の Codespaces コンピュート使用が含まれています。

### 全体的な制限

技術プレビューでは、合計 Codespaces および合計アクティブ Codespaces の制限が適用される場合があります。ワークスペースセッションを閉じてもこれらの問題が解決しない場合は、[こちら](https://github.com/githubnext/copilot-workspace-user-manual?tab=readme-ov-file#feedback)からお問い合わせください。

### 組織ベースの制限とポリシー

リポジトリを所有する組織が Codespaces の使用に関するポリシーを設定している場合、それらのポリシーがワークスペースの Codespaces の作成に適用されます。ポリシーの調整が必要な場合は、組織の管理者に連絡してください。

## 一般的なエラー

#### Copilot Workspace の使用制限に達しました

次のカレンダー月の開始時に無料の使用制限がリセットされ、ワークスペースの使用を続けることができます。使用制限に関するフィードバックは[こちら](https://github.com/githubnext/copilot-workspace-user-manual?tab=readme-ov-file#feedback)からお寄せください。

#### アクティブな Copilot Workspace の制限に達しました

オープンなワークスペースセッションを閉じ、以前のセッションがシャットダウンするのを待ってから新しいセッションを作成してください。

#### Copilot Workspace の制限に達しました

オープンなワークスペースセッションを閉じ、以前のセッションがシャットダウンするのを待ってから新しいセッションを作成してください。

#### リポジトリは Codespace に使用できません

これは、リポジトリまたは組織のポリシーが Codespaces の作成を制限しているためかもしれません。Codespaces の使用を妨げている設定がないか、組織またはリポジトリの設定を確認してください。問題が解決しない場合は、[技術プレビューフィードバックチャネル](https://github.com/githubnext/copilot-workspace-user-manual?tab=readme-ov-file#feedback)にお問い合わせください。

#### 割り当てられた場所が現在利用できません

数分後に再試行してください。さらに、このエラーが特定の地域で続く場合は、ユーザー設定でデフォルトの Codespaces リージョンを変更できます。詳細は[こちらの公開ドキュメント](https://docs.github.com/en/codespaces/setting-your-user-preferences/setting-your-default-region-for-github-codespaces)をご覧ください。

#### 提供された`devcontainer.json`を有効な JSON に解析できません

選択したリポジトリで`devcontainer.json`の構文エラーを修正する必要があるかもしれません。`devcontainer.json`の構文については、[こちらの公開ドキュメント](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers)をご覧ください。

#### 組織が OAuth アプリのアクセス制限を有効にしているため、Copilot Workspace へのアクセスが制限されています

組織の管理者に連絡して、Copilot Workspace OAuth アプリへのアクセスを許可してください。
