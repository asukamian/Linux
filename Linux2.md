## Linux2
- プロセス：プログラムの実行中のインスタンス
 - インスタンス：あらかじめ定義されたプログラムをメモリに展開して処理実行できる状態にしたもの
 - メモリのアドレス空間、所有者権限などのセキュリティプロパティ、プログラムコードの１つ以上の実行スレッド、プロセス状態
 - 親プロセスは自身のアドレス空間をforkして子プロセスを作る




- シェルスクリプト
 - 変数=$(($変数+1))とか。
 - ${変数}:変数の値を表す。
 - $()


- 権限
 - 削除：読み取り＆書き込みの権限がある場合できる？


- umaskの設定
  - .bash_profileと.bashrcにumask 007を追記⭐︎→これ何
- 認証keyでのsshlogin
  - ssh -i .ssh/review3_key student@servera
- /etc/ssh/ssh_configについて:PermitRootLoginやPasswordauthentication
- ln -s ファイル名　シンボリックリンク名
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

- シェルスクリプトの書き方:man bash



- 試験の注意
 - selinuxの後に、restorecon -Rvを忘れない
 - うまくいかないときはjournalctl -xn -xeをみる。
 - ディレクトリかファイルかを気をつける
 - cronの時は実行可能ファイル(chmod +x)にする
 - /etc/fstab のtype はマウントされるディスクのファイルシステムのタイプ
 - blkidでUUIDを確認
 - ストレージデバイスにファイルシステムが含まれている場合はUUIDもある。
 - パーティションを区切る時名前付を忘れない

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
 - semnage fcontext -a -t type '/lab(/.*)' , restorecon -R
 - pgrep sshd でプロセスIDがわかる。
 - tuned-adm
 - スクリプト内でssh接続してコマンドをする場合は、ssh student@servera "cat ~"
 - 正規表現について、 grep -v '^CPU'のように一重引用符の中に正規表現
 - →シェルでなくコマンドによって解釈されるように
 - '$'だとシェルのプロンプトとして認識されてしまう。
 - grep -v '^$'は空行を除くということ
 - dog$: dogで終わるもの
 - echo $? 前のやつの終了コード
 - コマンド "$(コマンド)"
 - cd "$(ls - )"
 - 環境変数：子シェルにも引き継がれる
 - ディレクトりごとのdiskのusage はduコマンド
 - yum localinstall
 - mount -o remount,rw /sysroot
 - chroot /sysroot
 - passwd root
 - touch /.autorelabel
 - rsync -av
 - tar -czf
 - tar -tzf
 - tar -xzf 確認
 - date -d "+90 days":90日あとはいつかを確認
 - ls /etc/sudoers.d/
 - chage コマンド
 - ~/.bashrc: ユーザーユニークな環境 PS1とか
 - 第３章ファイル間のリンクの作成

- インストール
 - インストール用メディア：インストールプログラム、anaconda、BaseOSやAppstreamのパッケージ含まれてる
 バイナリDVD :リポジトリが含まれてる
 - BaseOS:OSの動作に不可欠な（最小限必要な）パッケージ群:firewalldとかglibcとかkernelとか。。
 - Appstream:開発者が用いるパッケージ群:pythonとか。いくつかのバージョンから選択してパッケージを
 インストールできる。




- もう一回確認したいこと
 - vmlinuzとinitrdやinitramfs
  - vmlinuz:カーネルのバイナリファイル
  - initrd:初期RAMディスク
 - kickstartファイルでのインストール
 - パスワードの期限決め

 - stickybitとGUIDはもう一度確認したい
 - .bash_profileと.bashrcとumask
 - stratis
 - リンクの作り方　シンボリックリンクとハードリンク
 - stratis
 - systemd.tmpfiles.cleantimer
 - stratis
 - name = /baseurl=/ gpgcheck=/enabled= /gpgkey=
 - ldap
 - podman search registry.lab.example.com/ でイメージ全部見れる。
 - サービスとしてのコンテナの管理
 - コンテナツールの名前を知りたいときは:yum module list | grep
 - chown -R 下全部
 - skopeo inspect repoタグをみる
 - podmanの時、su は直接やるように気をつける
 - コンテナを立てるときはユーザに注意


- autofs
 - クライアントが現在マウントされてないシステムにアクセスしようとすると、autofsファイルシステムは
 その要求に介入し、automountdを呼び出して要求されたディレクトリをマウントする。automountdは
 ディレクトリを検索してマウントする
 - 間接マップ：サブディレクトリがある場合
 - マスターマップファイル:/etc/auto.master.d/auto.autofs ここにauto.directを書く
 - auto.indirect:間接マップファイル
 - 直接マップファイル:auto.indirect
 - マップファイルには -rw,sync,fstype=nfs4のオプション



 - 注意点・質問
  - autofsについてどのセクション
  - balancedでよかったのか
  - ネットワークの設定：onboot yesにしなかった。
  - パッケージを探すとき: yum guile
  - モジュールのところもう一度読む
  - rpmとyum
  - rpm -p -q パッケージ名　-i
  - yum localinstall のところstudentじゃなきゃいけない？
  - findコマンドを使って、ファイルにまとめとく奴とかはどれの項目？
  - extendするときにfsもextend
  - VDO
  - swap のファイルシステム
  - vfat
  - lsblk -fp
  - ownerが誰々のファイルを全部かく
  - xmlファイルの中で　ichを含む行だけ取り出せ
  - 15章システム上でのファイルの検索
  - 大文字と小文字を区別しないとき -i
  - 15章もう一度
  - findコマンド --mmin
  - locateコマンドの前はupdatedb
  - findコマンドのサイズについて
  - ログ：ファシリティと優先度：例userとdebug
  - logger -p : priorityの指定
  - journalctl _PID  -p(優先度)
  - journalctl --since "10min"
  - journalctl _SYSTEMD_UNIT="sshd.service"
  - systemd.journaldについて、/etc/systemd/journald.confのStorage=persistentにすると
  /var/log/journalができる　ちなみにvolatileだとどうなるか？
  - jounralctlのログはデフォルトでは再起動じに消えるようになっている。
  - tzselectでtimezoneを設定
  - /etc/chrony.conf でserver classroom.example.com iburstを追加したあとに、timedatectl set- yes
  - timedatectl -set-timezone ●　→確認したいときはtimedatectl list-timezones | grep
  - setfacl 権限なしの設定
  - usermod -s /sbin/nologin user03
  - usermod -L ログインロック
  - cant generate files
  - ネットワークの設定はrebootしたときにautoconnectionのやつやってなかった
  - 5-2の問題の質問４番

  - .bash_profileには環境変数だったり、PCの設定で必要な記述をする。ログイン時に自動で読まれる
  - .bashrcにはコマンドラインで使うエイリアスやターミナルの設定を書いていく：シェル自体によって使用される(別のシェル実行時にも起動される)
  - シェル変数はsetコマンドで見れるがどのファイルにある？
  - export PATHだけではログインし直すと消えてしまう。
  - だから、~/.bash_profileに設定すると良い。→ログインすると必ず適用される。（永続的）
  - bash_profileはプロセス間で環境変数が引き継がれる。


  - touch tvseason{1,2}_episode{1..6}とやると、１２こまとめて作れる
  - systemctl list-dependencies
  - ソフトリンク作成：絶対パスを使う。
  - vgcreateとかpvcreateを振り返る：lvmについて
  - シンボリックリンクについて；異なるファイルシステム上のファイルにリンク可能というのはどういう状態？？
  違うデバイスにマウントされてると無理ということ？
  - tuned-adm active と tuned-adm recommend
  - partedのところでsystemctl daemon-reloadをしないとどうなるか
  - vfat fat16 fat32
  - 再起動しない場合はswapon /dev/vdbをする。また、/etc/fstabに描く場合は、systemctl daemon-reload
  をする？
  - 疑問:swaponをしなくても、/etc/fstabに書けば勝手にアクティブになる？
  - vfatはfat16で良さそう
  - udevadm settle の意味はなに。やらなくても良い？
  - vfatについて調べる
  - https://access.redhat.com/documentation/ja-jp/red_hat_enterprise_linux/8/html/building_running_and_managing_containers/proc_mounting-a-container-filesystem_assembly_working-with-containers
  - fine -iname  大文字と小文字区別しない
  - find -mmin -mmin +3 ３分以上前に更新されたファイル
  -  -mtime 指定される日程より前に更新
  - -atime 指定される日程より前にアクセス
  - find -executable
  - -perm -g+s SGIDのファイル
  - -u -o全て -g
  - ファイルに出力するとき、エラーは出力しないように気をつける　1>
  - bytesでfindのときは100c⭐︎




 - 今日やりたいこと
  - rootパス紛失じの対応もう一回
  - スティッキービットとGID
  - パスの通し方
  - autofs


- bootについて
 - 電源投入されると、CPUはメモリのある地点から実行を開始する。
 - メモリのその領域にはBIOSが格納されてるROMがマップされている。
 - 次にブートローダを探す
 - ブートローダ(GRUB2)：OSをディスクから読み込み起動する役目を持つプログラム
 - カーネルの実行バイナリ: vmlinuz
 - カーネルは全ての初期化を終えると初期RAMディスク（initrd, initramfs）を展開し、仮のルートファイルシステムとしてマウント
 - カーネルはinitrdのマウントに成功した後に、initrdに含まれるinit(systemd)を実行する




- 次の試験に向けて
 - usermod -L operator : アカウントロック
 - data -d '+90days'
 - chage -d 0 operator1 : パスワード変更を強要
 - chage -E 2019-07-24 operator1
 - /etc/login.defs は全員分の
 - usermod -c コメント　を付け加えれる
 - userdel -r ホームディレクトリごと削除
 - groupadd -g 10000 group   gidを指定
 - groupmod -n group0022 group02 新しいnameに変更　-g 新しいGID
 - usermod -aG なら補助グループを追加、複数になる

 - コマンドラインショートカット：https://rol.redhat.com/rol/app/courses/rh124-8.2/pages/ch02s05
 - PEERDNS=no にするとDHCPサーバからDNS情報を受け取らない
 - find -size +70k -mmin +180 -user user -group group -type b
 - journalctl -p err
 - journalctl --since '-1 hour'
 - journalctl -b 最新のシステムブートのみ：/var/log/journalに保存される場合
 - journalctl -b -1 前回のブート
 - vi /ec/chrony.confにserver classroom.example.comを追加。
 - logger -p authpriv.alert で試せる
 - /etc/systemd/journald.confのstorageパラメータを変えてリブート後もジャーナルが保持される
 ようにする　auto,persistent,volatile
 - メッセージの種類：ファシリティ
 - tzselectで確認してtimedatectl set-timezone
 - kill -l でSIGTERMとかの番号がわかる。
 - 比較演算子　: gt>ge>=le<=lt<ne!=
 - [ -z "$STRING" ] stringが０である。testコマンドと同じ
 - [ -n "$STRING" ] stringが０でない。
 - 正規表現にはシェルのメタ文字 ($、*、{} など) が含まれることがあるため、正規表現を一重引用符によりカプセル化することをお勧めします。
 - これにより、コマンドによって解釈される。
 - grep -v '^[#;]' /etc/ethertypesについて　２の方
 - swapon -a を忘れない（mount -a）swapon --showで見れる。＆mkswapも
 - set 1(number) lvm on
 - niceレベル -20が最高　19が最低
 - ps u $(pgrep sha1sum) : CPU使用率
 - ps -o comm,nice,pid  
 - semanage port -l :一覧見る
 - semanage port -a -t ...
 - -aの代わりの-dは削除、-mは変更
 - */7は７分ごと
 - echo 'コマンド' | at now +3min
 - 0 9 * * 1-5 mutt -s "Checking in" boss@example.com % Hi there boss, just checking in.
 - while ! test -f my_first_cron_job.txt; do sleep 1s; done
 - w -h : 上の説明がなし　w -h | wc -l : ユーザ数
 - sysstat-collect.timer : /etc/systemd/system/sysstat-colect.timerに/usr/lib/以下のを
 コピー。そこから編集。/var/log/sa以下に追加される。
 - systemd-tmpfiles timerはデフォルトで(usr/libに書いてある)15分ごとにsystemd-tmpfiles cleanをトリガーし、
 systemd-tmpfiles --cleanコマンドを実行
 - /etc/tmp.files.d/ *.confにしたがって、たとえばsystemd-tmpfiles --cleanコマンドが
 ５分で/tmpを一掃　。/usr/lib/tmpfiles.d/tmp.confをコピーする。
 - とりあえず、/etc/tmpfiles.d/*.confを作って、systemd-tmpfiles --createをする。
 - run-parts コマンドは、毎日、毎週、毎月のジョブも実行しますが、異なる設定ファイル /etc/anacrontab から呼び出されます。
 - /etc/anacrontabは毎日毎週のジョブの定義をして、/etc/crontabは自分で定義可能？
 - /etc/crontabとcrontab -e の違いは、ユーザを追加する（前者）かそうじゃないか
 - nfsのオプション rw,sync
 - 自動直接マップは絶対パス
 - -rw,sync,fstype=nfs4
 - swapon -aを忘れない
 - コンテナでloginctl enable-lingerを忘れない
 - umaskをデフォルトで設定するときは~/.bashrcと ~/.bash_profileに書き込む

- 質問したいこと

 -　質問: The services for podsvc start at boot とはなに。loginctl？でもリブートしてもコンテナは立ってる。。
 ユーザーサービスが自動的に起動されるとは。ユーザーサービスとは

 - 質問: vfat 0 2 ?
 - マウントオプション asyncとは。ファイルシステム上での非同期の入/出力を許可します。とはつまり？
 - envコマンドはどこを読み取っているのか。どのファイル？
 -


 - デフォルトの設定と今あるやつの適用と二回やる。setfacl
 - nfsのオプションはdefaultsじゃなく、rw,sync
 - -sigcont:プロセス再開
 - kill -l でオプション見れる。
 - デフォルトじゃないkeyを作る
 - ssh-keygen -f .ssh/key2
 - ssh-copy-id -i .ssh/key2.pub operator1@servera keyを渡す。
 - ssh -i .ssh/key2 operator1@servera hostname keyの指定
 - eval $(ssh-agent)のあと、ssh-add .ssh/key2で、次keyを利用してsshするときにkey自体の認証はいらなくなる。

 - 語数はw -w 文字数はw -c
 - date +%rは12時間表示
 - ソフトリンクのときは絶対パス
 - chmodをやるときはroot権限でやろう
 - chage -m 10 -M 30 user名
 - chage -d 0 user名　: パスワード変更強制
 - export PATH=${PATH}:/home/user/sbin パスを追加
 - bashrcの中でexport EDITOR=nanoのようにエディタ設定可能
 - シェルから実行するプログラムの場合に適用する変数：環境変数, 例えばviとか


 帰ったら
 - vdoとstratisやる.
 - vgextend やる。
 - /etc/fstabのおぷしょん




 - 質問
  - DHCPはインターフェイスが起動すると... : https://rol.redhat.com/rol/app/courses/rh124-8.2/pages/ch12s09

  - wget使いまくりでよかったのか？
  - 初歩的な質問：パッケージのインストールとは？インストールってどういうことをいうのか。
  - - echo -n "$@ ": 入力を受け取って出力？
  - systemd が新しい設定を登録できるようとは　https://rol.redhat.com/rol/app/courses/rh134-8.2/pages/ch06
　- vfatについてdefaults?
  - ext4 ファイルシステムの場合、ルートファイルシステムには 1 を https://rol.redhat.com/rol/app/courses/rh134-8.2/pages/ch06
  - 物理エクステントの移動について　https://rol.redhat.com/rol/app/courses/rh134-8.2/pages/ch07s03　
  - データが移動するということ？
  - LVMよりもすごいバージョン？用途はVDOと同じ？論理ボリュームを作るということは。。
  - stratisは、ファイルシステムを全部のストレージに割り当てない。
  - 普通はファイルシステムを構築すると全部ストレージに割り当てるけど、？？
  - そのため、ファイルシステムのサイズは 1 TiB と表示されても、実際にプールから割り当てられるストレージは 100 GiB しかない可能性があります。
  - 何が良いのか　実際のサイズ知らないと困らないか？
  - https://rol.redhat.com/rol/app/courses/rh134-8.2/pages/ch08s05 削除しても変わらなかった　なぜ？
