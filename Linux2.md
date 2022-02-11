## Linux2
- プロセス：プログラムの実行中のインスタンス
 - インスタンス：あらかじめ定義されたプログラムをメモリに展開して処理実行できる状態にしたもの
 - メモリのアドレス空間、所有者権限などのセキュリティプロパティ、プログラムコードの１つ以上の実行スレッド、プロセス状態
 - 親プロセスは自身のアドレス空間をforkして子プロセスを作る




- シェルスクリプト
 - 変数=$(($変数+1))とか。


- 権限
 - 削除：読み取り＆書き込みの権限がある場合できる？


- umaskの設定
  - .bash_profileと.bashrcにumask 007を追記
- 認証keyでのsshlogin
  - ssh -i .ssh/review3_key student@servera
- /etc/ssh/ssh_configについて

- tar
  - tar -cf ○.tar file 1 file 2
  - tar -cvf ディレクトリごとやる
  - ↑複数のファイルからtarファイルを作成
  - tar -xf アーカイブファイルを展開
  - tar -tf アーカイブ内のファイル一覧を表示

- ブートの順序とか、ブートメニューの編集は復習、
 - systemd.unit=rescue.targetをブートメニューで編集は覚えておく。

- manの使い方
 - man -k キーワードを含むmanを検索



- 試験の注意
 - ディレクトリかファイルかを気をつける
 - cronの時は実行可能ファイル(chmod +x)にする
 - /etc/fstab のtype はマウントされるディスクのファイルシステムのタイプ
 - blkidでUUIDを確認
 - ストレージデバイスにファイルシステムが含まれている場合はUUIDもある。
 - lvdisplayで見れたUUIDと/dev/extra_storage/vol_homeのパーティションのUUIDが違った なぜか

 - setfacl：aclの設定
