## トラブルシューティング

### はじめに

Copilot Workspace のトラブルシューティングガイドへようこそ！このセクションでは、Copilot Workspace で組織やプライベートリポジトリを使用する際に遭遇する可能性のある一般的な問題に対する役立つヒントと解決策を提供します。私たちの目標は、スムーズで生産的な体験を提供することです。それでは始めましょう！

### アクセスのトラブルシューティング

初めて Copilot Workspace を試す際に「アクセス拒否」エラーが表示される場合、以下の手順が役立つかもしれません：

- 有効な有料の Copilot ライセンスを持っていることを確認してください。トライアルライセンスは、サブスクリプションが有料プランにアップグレードされるまでアクセスを許可しません。
- 現時点では、[エンタープライズ管理ユーザー（EMUs）](https://docs.github.com/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-enterprise-managed-users)はサポートされていませんが、EMUs のサポートは進行中です。
- アカウントに[貿易制限](https://docs.github.com/en/site-policy/other-site-policies/github-and-trade-controls)がないことを確認してください。
- Copilot が有効になっている組織が、**Copilot プレビュー機能**設定と**Copilot 拡張機能設定**の両方をオンにしていることを確認してください。必要に応じて、組織の管理者に連絡して支援を求めてください。Copilot の組織設定の詳細については、[ドキュメント](https://docs.github.com/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization)を参照してください。

### 組織のトラブルシューティング

Copilot Workspace で組織を使用する際に、いくつかの一般的な問題に遭遇することがあります。以下のトラブルシューティングのヒントを参考にして解決してください：

- **OAuth アプリの承認が必要な組織にアクセスしています**。ログインの一環として、さまざまな組織に OAuth アプリを承認します。組織のポリシーに応じて、OAuth アプリへのアクセスをリクエストし、組織が承認することができます。再度アクセスをリクエストする必要がある場合や、すべてのアクセスを取り消す必要がある場合は、[OAuth アプリとの接続の状態を制御](https://github.com/settings/connections/applications/903eccd8a9d2ff50288f)できます。

- **正しい認証資格情報を持っているように見えますが、`github`組織は OAuth アプリのアクセス制限を有効にしており、サードパーティへのデータアクセスが制限されています**。これは、組織が OAuth アプリを制限しているためです。組織が OAuth アプリをまったく許可しない場合、一部の認証試行が失敗することがあります。これは、OAuth アプリへのアクセスを拒否する組織のパブリックリポジトリへのアクセスにも影響を与える可能性があります。

- **組織の SAML 強制によって保護されたリソースです。OAuth トークンにこの組織へのアクセスを許可する必要があります**。SAML 制御を持つ組織にログインしている可能性があります。例：Microsoft。次の手順を実行してください：
  1. Copilot Workspace からログアウトします。
  2. 組織のリポジトリなどを表示してブラウザで SAML 認証を行います。
  3. その後、Copilot Workspace に再度ログインします。
- **組織内での作業に関するその他の既知の制限事項：**
  1. エンタープライズ（または組織）は、Copilot 機能プレビューにオプトインする必要があります。[GitHub.com で機能プレビューを有効にする方法を学ぶ](https://docs.github.com/en/get-started/using-github/exploring-early-access-releases-with-feature-preview)。
  2. エンタープライズ（または組織）は、Copilot 拡張機能ポリシーを有効に設定する必要があります。これは、組織/エンタープライズの設定で Copilot > Copilot ポリシーの下にあります。
  3. エンタープライズは EMUs を使用していない必要があります。
  4. エンタープライズ（または組織）内の開発者は、有料の Copilot ライセンスを持っている必要があります。

### プライベートリポジトリのトラブルシューティング

- **自分のアカウントのプライベートリポジトリにアクセスできません**。ログイン後、OAuth アプリのアクセスを削除していない限り、個人のプライベートリポジトリにアクセスできるはずです。問題が発生した場合、共有リンクを介して Copilot Workspace にアクセスしたためにパブリックリポジトリの権限しか付与されていない可能性があります。ログアウトして再度ログインすると、アクセスが復元されるはずです。それでも問題が解決しない場合は、[OAuth アプリとの接続の状態を確認](https://github.com/settings/connections/applications/903eccd8a9d2ff50288f)してください。

## 曖昧さの警告

Copilot Workspace がタスクが過度に曖昧/不明確であると検出した場合（例：リポジトリの目標/焦点と一致していないように見える場合）、そのタスクをさらに明確にするように警告し、続行する前にタスクを明確にするように求めることがあります。これは、仕様の幻覚を防ぎ、ワークフローの後続のステージが十分な詳細で最適に機能するようにするためです。

<img src="images/further-techniques/ambiguous-spec.png" width=600 alt="曖昧な仕様">

*タスクが曖昧すぎるため、意図を明確にする必要があるという警告*

### Codespaces のトラブルシューティング

- **新しい Codespace の請求可能な所有者を特定できませんでした。リポジトリは Codespace に使用できません**。CW OAuth アプリが請求可能な所有者の組織にインストールされていません。

Codespaces に関する詳細情報や一般的なエラーのトラブルシューティングについては、[Codespaces ガイド](codespaces-guide.md)を参照してください。
