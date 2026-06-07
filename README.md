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

