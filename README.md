# 議事録
# 9.23 Sat - 24 Sun - 各自でステージ１に取り掛かる＋疑問点の共有
<br />

ステージ１：クライアント->サーバーにUDP通信で送信したメッセージが全クライアントに共有される
<br/>
## やったこと
・各メンバーのコードを見せ合い挙動を説明
<br />
・不明瞭な箇所の共有、知識のすり合わせ
<br />
・ステージ１部分を各自実装→比較、それぞれのいい部分を取り入れつつyutoさんのコードをベースとしてdevelopにマージ
<br />
・ソケット経由でUDP通信によってメッセージを送るクライアントと、setに保存したクライアント全員に対して受信したメッセージを配信するサーバーの実装
<br />

## 課題
・コンフリクトを最大限避けるためのissueの割り振り方（機能ごと？クラス単位？）　=> 要件ごと、場合によっては機能ごと
<br />
・チャットルーム作成時、どのようにTCP通信を組み込むか => TCPサーバーを定義してるファイル内で
<br />



## 次回MTG（9.27 Wed) => 変更(9.28 Thu)
・（当日まで）各自ドキュメントやRecursionバックエンドカリキュラムの復習
<br />
・stage2要件定義（当日までにも必要と感じたことはissueにあげていく)
<br />
・タスク割り振り
<br />
<br />
<br />

# 9.28 Thu Stage2タスク要件確認・タスク振り分け方法の決定
<br/>

## やったこと
・並行処理について疑問点共有、理解度合わせ
<br />
・TCP通信用サーバー、UDP通信用サーバー、クライアントのひな形作成
<br />
・要件が具体的に求めていることを１つずつ確認
<br />
・タスク分担方法：ひな形push後、機能もしくは要件ごとに各自でissueを立てて取り掛かっていく
<br />

## 次回MTG(10.2)
・進捗報告
・(stage3実装方法の検討)
<br />
<br />
<br />

# オフィスアワー(9.30 Sat)で得られた回答
TCP、UDPの仕様について

・TCP通信はあくまでトークンをクライアントに発行・送信するための手段
<br />
・トークンを持つクライアントのみ、ルーム入場可
<br />
・トークン発行後はTCP切断→自動的にUDP通信に移行
<br />
・UDP通信は片方向の連絡しかできず、もとからコネクションレス
<br />
・なので、一定時間クライアントからのメッセージ送信操作がなかった場合、手動でそのクライアントのトークン削除＝ルームからの退出を行う必要がある 

## 課題
・TCP通信で発行したクライアント用トークンの保存先
<br />
・↑作成・参加共通で、ChatClientクラスにtokenを持たせることで保存？(空だと部屋に参加できないようにする)
<br />
・↑部屋作成の場合は作成者＝ホストなので、room_name:token をChatRoomクラスのroomsに保存することで、ホストユーザーを識別できる？
<br />
<br />
・入出中のクライアントからの操作で、手動退出=持ってるトークンの削除を行えるようにする(message == "exit"で退出？)
<br />
・自動退出(settimeout)
