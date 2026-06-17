# azure-paas-handson
<img width="1251" height="198" alt="image" src="https://github.com/user-attachments/assets/26da4c25-0c0c-4f5b-b2c5-9ea40a1c66fe" />
・GitHub Repository: ソースコードを管理する場所です。

・GitHub Actions: コードがプッシュされると自動的に起動し、ビルドやテストを行い、Azureへ配信する役割を担います。

・OIDC（OpenID Connect）認証: 通常、クラウドへのデプロイには「サービスプリンシパルの資格情報（秘密鍵など）」をGitHubに保存する必要がありますが、OIDCを使うことで「資格情報をGitHubに保存せずに」安全にAzureと認証・通信を行っています。

・Azure Storage: $web: 静的Webサイトをホスティングするためのコンテナです。安価で拡張性が高く、フロントエンドのファイルを置く場所として最適です。

・Azure Front Door: 単なるCDN（コンテンツ配信ネットワーク）以上の役割を果たしています。

・コンテンツ配信: 世界中のエッジサーバーにキャッシュすることで、ユーザーへの表示を高速化します。

・HTTPS公開: カスタムドメインに対してSSL/TLS証明書を自動管理し、安全なHTTPS通信を提供します。

１．セキュリティの確保: OIDCによる鍵管理の不要化と、Front Doorによるエッジでの保護。

２．運用効率化: 手動デプロイではなくGitHub Actionsによる完全自動化。

３．パフォーマンス: CDN利用による高速なレスポンス。

# My Portfolio Site
[https://yuri-profile-gwd0gyh9htc7gadg.z03.azurefd.net/](https://yuri-profile-gwd0gyh9htc7gadg.z03.azurefd.net/)

## 概要
Azureの静的ホスティング機能を活用したポートフォリオサイトです。
インフラ設計から自動デプロイまでを、現役エンジニアのベストプラクティスを意識して構築しました。

## 技術スタック
- Azure Storage ($web)
- Azure Front Door (CDN)
- GitHub Actions (CI/CD)
- OIDC認証によるセキュアなデプロイ

## こだわりポイント
- **自動デプロイ**: GitHub ActionsとOIDC認証を用い、手動作業を一切排除。
- **堅牢な配信**: Front DoorによるCDN構成でHTTPS配信と高速化を実現。

工夫した点

・セキュアな認証の実現: 認証情報（シークレット）を直接 GitHub に保存せず、OIDC（OpenID Connect）認証を採用したことで、セキュリティレベルを向上させました。

・CI/CD による自動化: GitHub Repository へのプッシュをトリガーに、ビルドからAzure Blob Storageの静的Webサイト機能へのデプロイまでを完全に自動化し、人的ミスを排除するとともに開発効率を最大化しました。

・最初はAzure Static Web Appsを検討しましたが、Azureサービスを組み合わせた構成を学ぶため、あえてAzure StorageとFront Doorを分離する構成を選択しました。その結果、構成の自由度と堅牢性を学べました。

苦労した点

・OIDC認証の実装：AzureとGitHub Actions間のフェデレーション設定において、適切な権限付与に苦戦しました。公式ドキュメントを参照しながらサービスプリンシパルの権限を一つずつ精査し、最小権限の原則に基づいて正しくデプロイできる状態へと最適化しました。

・CDN キャッシュの制御: Azure Front Door 経由でサイトを配信する際、新しいコンテンツをデプロイした後に、CDN のキャッシュを適切にパージ（削除）して最新版が即座に反映されるようにする仕組みの調整に苦労しました。








