# Failure Detection with Paxos Algorithm

コンセンサスアルゴリズムの一種である　[Paxos algorithm](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)　を組み込んだサーバーダウン検知システム。

## :pushpin:　開発概要
- 6人によるチーム開発
- 約2ヶ月の製作期間　（コーディング、ドキュメント作成、テスト）

## :scroll:　機能概要

### クライアント
- ダウンしていないサーバーから、システムの状況（どのサーバーがダウンしているか/していないか）を取得

### サーバー 
- システムへのジョイン
- システム内の自身以外のサーバーの監視
- クラッシュしたサーバーの検知
- Paxos プロセスの始動


## :thought_balloon:　Paxos プロセスについて
- 全てのサーバーは　Proposer/Acceptor/Learner　のすべての役割を担う
- サーバー クラッシュを検知したサーバーが　Paxos プロセスを始動し、Proposerの役割を担う

### Phase 1: Prepare & Promise

### Phase 2: Propose

### Phase 3: Broadcast

### Phase 4: Learn


## :hammer: 使用技術
|||
| ---- | ---- |
|  言語  | Golang Ver. 1.18   |
|  ライブラリ  |  [Tracing Library](https://pkg.go.dev/github.com/DistributedClocks/tracing)  |
|  ネットワーク可視化ソフトウェア  | [ShiViz](https://bestchai.bitbucket.io/shiviz/) |

## ShiViz Log
![ShiViz1](https://user-images.githubusercontent.com/81115999/166919675-10e1f639-7337-4310-b023-b0280741313b.png)


