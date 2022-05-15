# Failure Detection with Paxos Algorithm

コンセンサスアルゴリズムの一種である　[Paxos algorithm](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)　を使用したサーバーダウン検知システム。

## :pushpin:　開発概要
- 6人によるチーム開発
- 約1ヶ月の製作期間　（コーディング、ドキュメント作成、テスト）

## :scroll:機能概要

### クライアント
- ダウンしていないサーバーからシステムの状況（どのサーバーがダウンしているか/していないか）を取得

### サーバー 
- システムへのジョイン
- システム内の自身以外のサーバーの監視
- クラッシュしたサーバーの検知
- Paxos プロセスの始動

### Paxos プロセス



### ShiViz Log
![ShiViz1](https://user-images.githubusercontent.com/81115999/166919675-10e1f639-7337-4310-b023-b0280741313b.png)


