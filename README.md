# Glinefy
## 概要
Gmail に届いた問い合わせメールをトリガーに、LINE に通知を送るためのサーバーレス通知ツール。
- Gmail の特定アドレスへのメール受信をトリガーにする
- AWS Lambda を経由して LINE にプッシュ通知を送る
- 個人ブログやサービスの問い合わせ通知に最適

## 構成
- Gmail API（watch 設定で push 通知を受け取る）
- Google Cloud Pub/Sub（Gmail の通知を受けるエンドポイント）
- AWS Lambda（Pub/Sub 経由で起動し、通知処理を実行）
- LINE Notify API（LINE に通知を送信）

## 必要なもの
- Google Cloud プロジェクト（Pub/Sub 用）
- Gmail API の有効化と認証情報
- AWS アカウント（Lambda 実行用）
- LINE Notify のアクセストークン

## セットアップ手順（ざっくり）
1. Gmail API の有効化と `watch` 対象ラベルの設定
2. Google Cloud Pub/Sub トピックとサブスクリプションの作成
3. Lambda 関数のデプロイ（Node.js or Python）
4. LINE Notify トークンを環境変数または Secrets Manager に設定
5. Lambda に Pub/Sub からのトリガー設定
6. 動作確認（問い合わせメールを送って LINE 通知が来るか確認）

## 環境変数例
```env
LINE_NOTIFY_TOKEN=xxxxx
GMAIL_LABEL_ID=Label_123456

