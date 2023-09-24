# 議事録
9.23 Sat - 24 Sun - 各自でステージ１に取り掛かる＋疑問点の共有
<br />

ステージ１：クライアント->サーバーにUDP通信で送信したメッセージが全クライアントに共有される
<br/>
## やったこと
・各メンバーのコードを見せ合い挙動を説明
・不明瞭な箇所の共有、知識のすり合わせ
・ステージ１部分を各自実装→比較、それぞれのいい部分を取り入れつつyutoさんのコードをベースとしてdevelopにマージ
・ソケット経由でUDP通信によってメッセージを送るクライアントと、setに保存したクライアント全員に対して受信したメッセージを配信するサーバーの実装
<br>

## 課題
・コンフリクトを最大限避けるためのissueの割り振り方（機能ごと？クラス単位？）
・チャットルーム作成時、どのようにTCP通信を組み込むか
<br />

## 次回MTG（9.27 Wed)
・（当日まで）各自ドキュメントやRecursionバックエンドカリキュラムの復習
・stage2要件定義（当日までにも必要と感じたことはissueにあげていく)
・タスク割り振り
