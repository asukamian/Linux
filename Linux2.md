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
  - .bash_profileと.bashrcにumask 007を追記⭐︎→これ何
- 認証keyでのsshlogin
  - ssh -i .ssh/review3_key student@servera
- /etc/ssh/ssh_configについて:PermitRootLoginやPasswordauthentication

- tar
  - tar -cf ○.tar file 1 file 2
  - tar -cvf ディレクトリごとやる
  - ↑複数のファイルからtarファイルを作成
  - tar -xf アーカイブファイルを展開
  - tar -tf アーカイブ内のファイル一覧を表示

- ブートの順序とか、ブートメニューの編集は復習、
 - systemd.unit=rescue.targetをブートメニューで編集は覚えておく。→/etc/fstabが間違っていた
 時

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
 - selinuxはサービスなのか？？？
 - 13-4は何をしているかわからないので質問したい
 - sealert -a /var/log/audit/audit.logでなんのコマンドをやれば良いか教えてくれる。
 - or joutanalctl -xeを見てみる。


 - root passwordを忘れた時→Linuxの最後の行にrd.breakを追加
 - そして、mount -o remount,rw /sysroot
 - そして、chroot /sysroot
 - そして、passwd root
 - touch /.autorelabel →空のファイルを作っておくと、次回起動時に自動的にSELinuxの再ラベルづけ
 - 小文字大文字も気をつける!!!
 - ""じゃないと$(コマンド)は認識されない


- インストール
 - インストール用メディア：インストールプログラム、anaconda、BaseOSやAppstreamのパッケージ含む
 バイナリDVD :リポジトリが含まれてる
 - BaseOS:OSの動作に不可欠な（最小限必要な）パッケージ群:firewalldとかglibcとかkernelとか。。
 - Appstream:開発者が用いるパッケージ群:pythonとか。いくつかのバージョンから選択してパッケージを
 インストールできる。



- もう一回確認したいこと
 - vmlinuzとinitrdやinitramfs
 - kickstartファイルでのインストール
 - パスワードの期限決め
 - rootpassword紛失時の対応
 - stickybitとGUIDはもう一度確認したい
 - .bash_profileと.bashrcとumask
