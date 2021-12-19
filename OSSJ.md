1. OSSJをみる
2. 初めてのDockerを復習
3. サーバー課題を見つける
---------------------------------------

## OSSJ
SODA 2020年６月に生まれた
yahoo japan
daily strage operartion
storage user request ticket
ticket system をSODAに移す


Soda foundation

⭐︎SODA - An Open Collaboration for Data and Storage ⭐︎
+ スピーカー: Steven Tan, Futurewei; Tomoko Kondo, Softbank; Kei Kusunoki, NTT Communications

+ サマリ:
　 SODA foundationのdata lake projectについて
　 データ管理の問題とそのソリューション

+ 詳細

 - SODA Foundationのミッション
   オープンソースのデータ、ストレージ管理ソフトウェアを促進する

 - SODALAKEについて
データの量（Global data creation）は2045年には現在の４５倍程度になる。データは、データセンターやAWSやGoogle Cloudに分散しており、インターフェイスもそれぞれ違い、データはサイロ化してしまう。
そこで、SODA Lakeというバーチャルデータレイクを作り、単一のインターフェイスでアクセスできるようにし、versatileでscalableにする。


- soda lakeのユースケース(まだ仮説段階)
speaker: softbank　近藤さん
Customer Aは会社と、AWSと、Azureにストレージオブジェクトがあるとする。
Customer Aはsoda lake agentをアプリケーションにインストールして、キャリアデータセンターにあるSODA lake contorollerに接続すると、SODA Lake contorollerが一つのバーチャルデータレイクとして管理しているデータに、アクセスできる。

キャリアデータセンター、クラウドストレージ、Customer Datacenterを繋ぐネットワークはclosed networkになっている。

- 所感

データがあちこちに分散し、データストレージのサイロ化という問題があることは私にとっては初めての発見でした。
