# Failure Detection with Paxos Algorithm

コンセンサスアルゴリズムの一種である　[Paxos algorithm](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)　を組み込んだサーバーダウン検知システム。サーバーの集合がお互いを監視しあい、どのサーバーがダウンしているのかという情報を全てのサーバー間で共有する。

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
- Paxos プロセス　(成功ケース)は下記の4つのフェーズで構成される

### Phase 1: Prepare & Promise
1. サーバー クラッシュを検知したサーバーが　Paxos プロセスを始動し、同時にProposerの役割を担う
2. Proposer が他の全てのサーバーにどのサーバーがダウンしたのかを知らせる
3. 他のサーバーが Proposer からのメッセージを受け取り、それに Promise で応える。その場合、そのサーバーは Acceptor の役割を担う
4. Proposer がシステム内のダウンしていないサーバーの過半数から Promise を受け取る

### Phase 2: Propose
1. Proposer が Acceptor に 新しいシステムの情報を持つ Proposal を送る
2. Acceptor が同様のサーバーダウンを検知していた場合、Proposal を承認する

### Phase 3: Broadcast
1. Proposal を承認した Acceptor　が他の全てのサーバーに Broadcast メッセージを送る
2. このフェーズでは全てのサーバーが Learner の役割を担い、Acceptor からの Broadcase メッセージを受け取る
3. 過半数の Acceptor から Broadcast メッセージを受け取った場合、ローカル、グローバルのシステム状況をアップデートする


## :hammer: 使用技術
|||
| ---- | ---- |
|  言語  | Golang Ver. 1.18   |
|  ライブラリ  |  [Tracing Library](https://pkg.go.dev/github.com/DistributedClocks/tracing)  |
|  ネットワーク可視化ソフトウェア  | [ShiViz](https://bestchai.bitbucket.io/shiviz/) |

## ShiViz Log　
### シナリオ
- システム内のサーバー数：５
- サーバー5（黄色）がダウン

![ShiViz1](https://user-images.githubusercontent.com/81115999/166919675-10e1f639-7337-4310-b023-b0280741313b.png)


